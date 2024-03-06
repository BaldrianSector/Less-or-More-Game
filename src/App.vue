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
      ],

      random1 : 0,
      random2 : 0,
    }
  },

  mounted() {
    this.generateRandomNumbers();
  },

  methods: {
    handleClick(clickedValue, otherValue) {
      if (clickedValue > otherValue) {
        this.count++;
      } else {
        this.count = 0;
      }
      this.generateRandomNumbers();
    },
    
    generateRandomNumbers() {
      let previousRandom1 = this.random1;
      let previousRandom2 = this.random2;

      // Generate random indices for the countries
      while (this.random1 === this.random2 || this.random1 === previousRandom1 || this.random2 === previousRandom2) {
        this.random1 = Math.floor(Math.random() * this.valueList.length);
        this.random2 = Math.floor(Math.random() * this.valueList.length);
      }

      console.log(this.random1, this.random2);
    },
  },

  components: {
    ComponentHeader,  
    Card,
  },
}

</script>

<template>
  <!-- <ComponentHeader class="fixed w-screen px-5 py-2"></ComponentHeader> -->
  
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