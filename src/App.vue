<script>
import ComponentHeader from './components/ComponentHeader.vue'
import Card from './components/Card.vue'

import countryValues from './assets/json/countryValues.json'
import unsplashImages from './assets/json/JSON_SelectedImagesByQuery.json'

export default {
  data() {
    return {
      count: 0,
      timerDuration: 10000,  // Timer starts at 10000 milliseconds (10 seconds)
      timer: null,
      timeLeft: 10,  // Time left in seconds
      
      valueList: countryValues,
      unsplashImages: unsplashImages,

      random1 : 0,
      random2 : 0,

      highscore: 0,
    }
  },

  created() {
    this.assignImages(); 
    this.loadHighScore();
    this.generateRandomNumbers();
  },

  mounted() {
    this.startTimer();
  },

  methods: {
    handleClick(clickedValue, otherValue) {
      if (clickedValue > otherValue) {
        this.count++;
        if (this.count > this.highscore) {
          this.highscore = this.count;
          this.saveHighScore();
        }
        // Decrease timer duration by 10% each click, but not less than 1 second
        this.timerDuration = Math.max(1000, this.timerDuration * 0.95);
        this.resetTimer();
      } else {
        this.count = 0;
        this.timerDuration = 10000; // Reset duration to 10 seconds when the score resets
        this.resetTimer();
      }
      this.generateRandomNumbers();
    },

    startTimer() {
      this.timer = setInterval(() => {
        if (this.timeLeft > 0) {
          this.timeLeft--;
        } else {
          this.count = 0;  // Reset score if timer reaches 0
          this.timerDuration = 10000;  // Reset timer duration to 10 seconds
          this.generateRandomNumbers();
          this.resetTimer();
        }
      }, 1000);  // Update every second
    },

    resetTimer() {
      clearInterval(this.timer);
      this.timeLeft = this.timerDuration / 1000;  // Update time left based on new duration
      this.startTimer();  // Restart the timer
    },

    generateRandomNumbers() {
      let previousRandom1 = this.random1;
      let previousRandom2 = this.random2;
      while (this.random1 === this.random2 || this.random1 === previousRandom1 || this.random2 === previousRandom2) {
        this.random1 = Math.floor(Math.random() * this.valueList.length);
        this.random2 = Math.floor(Math.random() * this.valueList.length);
      }
      console.log(this.random1, this.random2);
    },

    loadHighScore() {
      if (localStorage.getItem('highscore')) {
        this.highscore = parseInt(localStorage.getItem('highscore'));
      }
    },

    saveHighScore() {
      localStorage.setItem('highscore', this.highscore.toString());
    },

    assignImages() {
      Object.values(this.unsplashImages).forEach((item, index) => {
        if (index < this.valueList.length) {
          this.valueList[index].selectedImage = item;
        }
      });
    }
  },

  computed: {
    timerColorClass() {
      if (this.timeLeft <= 1) {
        return 'text-red-800';  // Very urgent - darker red
      } else if (this.timeLeft <= 2) {
        return 'text-red-600';  // Urgent - medium red
      } else if (this.timeLeft <= 3) {
        return 'text-red-400';  // Moderate - lighter red
      } else {
        return 'text-white';    // Normal - white
      }
    }
  },

  components: {
    ComponentHeader,  
    Card,
  },
}
</script>

<template>
  <ComponentHeader class="fixed w-screen px-5 py-2">{{ highscore }}</ComponentHeader>
  
  <div class="flex h-screen bg-gradient-to-b from-sky-500 to-indigo-700 text-white flex-col justify-evenly">  
    
    <div id="top-section" class="flex items-center justify-evenly">
      <h1 class="text-[2rem] uppercase">Which one has the largest population?</h1>
    </div>
    
    <div id="mid-section" class="flex text-white items-center justify-evenly">
      <Card @click="handleClick(valueList[random1].population, valueList[random2].population)" :country="valueList[random1].country" :flag="valueList[random1].flag" :info="valueList[random1].info" :image="valueList[random1].selectedImage[0].urls.regular"></Card>

      <h2>OR</h2>

      <Card @click="handleClick(valueList[random2].population, valueList[random1].population)" :country="valueList[random2].country" :flag="valueList[random2].flag" :info="valueList[random2].info" :image="valueList[random2].selectedImage[0].urls.regular"></Card>
    </div>
    
    <div id="bottom-section" class="flex flex-col items-center justify-evenly">
      <h1 class="text-xl">Current Score: {{ count }}</h1>
      <!-- Display the countdown timer here -->
      <h2 class="text-xl countdown">Time Remaining: <span :class="timerColorClass">{{ timeLeft }} seconds</span></h2>
    </div>

  </div>
</template>

<style>
/* Example CSS for class bindings */
.text-red-800 { color: #e53e3e; } /* Tailwind color for dark red */
.text-red-600 { color: #fc8181; } /* Tailwind color for medium red */
.text-red-400 { color: #feb2b2; } /* Tailwind color for light red */
.text-white { color: #ffffff; }  /* White color */
</style>