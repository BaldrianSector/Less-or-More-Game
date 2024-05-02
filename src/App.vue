<script>

import ComponentHeader from './components/ComponentHeader.vue'
import Card from './components/Card.vue'

import countryValues from './assets/json/countryValues.json'
import unsplashImages from './assets/json/JSON_SelectedImagesByQuery.json'

export default {
  data() {
    return {
      count: 0,
      
      valueList: countryValues,
      unsplashImages: unsplashImages,

      random1 : 0,
      random2 : 0,

      highscore: 0,
    }
  },
  created() {
    this.assignImages();
  },

  mounted() {
    this.loadHighScore();
    this.generateRandomNumbers();
  },

  methods: {
        handleClick(clickedValue, otherValue) {
            if (clickedValue > otherValue) {
                this.count++;
                if (this.count > this.highscore) {
                    this.highscore = this.count;
                    this.saveHighScore();
                }
            } else {
                this.count = 0;
            }
            this.generateRandomNumbers();
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
        downloadJSON() {
            const JSONToFile = (obj, filename) => {
            const blob = new Blob([JSON.stringify(obj, null, 2)], {
                type: 'application/json',
            });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `${filename}.json`;
            a.click();
            URL.revokeObjectURL(url);
            };

            JSONToFile(this.valueList, 'countryValues');
            // downloads the object as 'countryValues.json';
        },
        assignImages() {
            Object.values(this.unsplashImages).forEach((item, index) => {
              if (index < this.valueList.length) {
                this.valueList[index].selectedImage = item;
              }
            });
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
    
    <div id="bottom-section" class="flex items-center justify-evenly">
      <h1 class="text-x">Current Score: {{ count }}</h1>
    </div>

  </div>
</template>