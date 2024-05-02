<script>

import ComponentHeader from './components/ComponentHeader.vue'
import Card from './components/Card.vue'

export default {
  data() {
    return {
      count: 0,
      
      valueList: [
      { country: 'Denmark', info: 'Denmark is known for its rich history and modern lifestyle.', population: 5930564, flag: '🇩🇰', image: 'https://images.unsplash.com/photo-1513622470522-26c3c8a854bc?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Sweden', info: 'Sweden is famous for its stunning landscapes and vibrant cities.', population: 10654127, flag: '🇸🇪', image: 'https://images.unsplash.com/photo-1562263075-da00b5209d88?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Norway', info: 'Norway is renowned for its stunning fjords and coastal scenery.', population: 5501740, flag: '🇳🇴', image: 'https://plus.unsplash.com/premium_photo-1661963290283-a1883fb9582a?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Finland', info: 'Finland is known for its beautiful lakes and forests.', population: 5548489, flag: '🇫🇮', image: 'https://images.unsplash.com/photo-1585727384562-8c1685105af5?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Iceland', info: 'Iceland is a land of natural wonders, featuring glaciers and hot springs.', population: 376936, flag: '🇮🇸', image: 'https://images.unsplash.com/photo-1533562179840-9cce77549aa6?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Netherlands', info: 'The Netherlands is famous for its tulip fields, windmills, and cycling routes.', population: 17618299, flag: '🇳🇱', image: 'https://images.unsplash.com/photo-1605315188787-e3c8f6bf927a?q=80&w=1074&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Belgium', info: 'Belgium is known for its chocolate, waffles, and medieval towns.', population: 11686140, flag: '🇧🇪', image: 'https://images.unsplash.com/photo-1569878165730-a4d34917f3d2?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Luxembourg', info: 'Luxembourg is known for its medieval castles and beautiful countryside.', population: 654768, flag: '🇱🇺', image: 'https://images.unsplash.com/photo-1588336899745-22da91d8f816?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Switzerland', info: 'Switzerland is known for its picturesque landscapes, chocolate, and watches.', population: 8796669, flag: '🇨🇭', image: 'https://images.unsplash.com/photo-1530878902700-5ad4f9e4c318?q=80&w=1034&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Austria', info: 'Austria is famous for its historic cities, classical music, and alpine terrain.', population: 8958960, flag: '🇦🇹', image: 'https://images.unsplash.com/photo-1485081669829-bacb8c7bb1f3?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Germany', info: 'Germany is known for its rich cultural heritage, beer, and automotive industry.', population: 83294633, flag: '🇩🇪', image: 'https://images.unsplash.com/photo-1554072675-66db59dba46f?q=80&w=1173&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Japan', info: 'Japan is renowned for its rich culture, technology, and cuisine.', population: 123294513, flag: '🇯🇵', image: 'https://images.unsplash.com/photo-1526481280693-3bfa7568e0f3?q=80&w=1171&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'South Korea', info: 'South Korea is known for its vibrant pop culture, technology, and delicious cuisine.', population: 51784059, flag: '🇰🇷', image: 'https://images.unsplash.com/photo-1583833008338-31a6657917ab?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Australia', info: 'Australia is famous for its stunning beaches, unique wildlife, and vast Outback.', population: 26439111, flag: '🇦🇺', image: 'https://images.unsplash.com/photo-1624138784614-87fd1b6528f8?q=80&w=1033&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Canada', info: 'Canada is known for its stunning natural landscapes, including mountains, forests, and lakes.', population: 38781291, flag: '🇨🇦', image: 'https://images.unsplash.com/photo-1503614472-8c93d56e92ce?q=80&w=1111&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'New Zealand', info: 'New Zealand is famous for its breathtaking landscapes, adventure sports, and Maori culture.', population: 5228100, flag: '🇳🇿', image: 'https://images.unsplash.com/photo-1597367624841-1d0e501b2a4e?q=80&w=1032&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Brazil', info: 'Brazil is known for its vibrant culture, Amazon rainforest, and beautiful beaches.', population: 216422446, flag: '🇧🇷', image: 'https://images.unsplash.com/photo-1518639192441-8fce0a366e2e?q=80&w=1171&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Mexico', info: 'Mexico is known for its rich history, diverse culture, and delicious cuisine.', population: 128455567, flag: '🇲🇽', image: 'https://images.unsplash.com/photo-1584208632661-f8db31bb6489?q=80&w=1029&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'Argentina', info: 'Argentina is famous for its tango, beef, the Andes mountains and Patagonia.', population: 45773884, flag: '🇦🇷', image: 'https://images.unsplash.com/photo-1617548437735-92d875423353?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'South Africa', info: 'South Africa is known for its diverse cultures, stunning landscapes, and wildlife safaris.', population: 60414495, flag: '🇿🇦', image: 'https://images.unsplash.com/photo-1484318571209-661cf29a69c3?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
      { country: 'India', info: 'India is known for its diverse culture, rich history, and iconic landmarks such as the Taj Mahal.', population: 1428627663, flag: '🇮🇳', image: 'https://images.unsplash.com/photo-1548013146-72479768bada?q=80&w=1176&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' }
      ],

      random1 : 0,
      random2 : 0,

      highscore: 0,
    }
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
      <h1 class="text-2xl uppercase">Which one has the largest population?</h1>
    </div>
    
    <div id="mid-section" class="flex text-white items-center justify-evenly">

      <Card @click="handleClick(valueList[random1].population, valueList[random2].population)" :country="valueList[random1].country" :flag="valueList[random1].flag" :info="valueList[random1].info" :image="valueList[random1].image"></Card>

      <h2>OR</h2>

      <Card @click="handleClick(valueList[random2].population, valueList[random1].population)" :country="valueList[random2].country" :flag="valueList[random2].flag" :info="valueList[random2].info" :image="valueList[random2].image"></Card>

    </div>
    
    <div id="bottom-section" class="flex items-center justify-evenly">
      <h1 class="text-x">Current Score: {{ count }}</h1>
    </div>

  </div>
</template>