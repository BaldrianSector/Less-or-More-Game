<script>

import ComponentHeader from './components/ComponentHeader.vue'
import Card from './components/Card.vue'

export default {
  data() {
    return {
      count: 0,
    }
  },
  components: {
    ComponentHeader,  
    Card,
  },
}

</script>

<template>
  <ComponentHeader class="fixed w-screen px-5 py-2"></ComponentHeader>
  <div class="flex h-screen bg-black text-white flex-col justify-evenly">  
    <div id="top-section" class="flex items-center justify-evenly">
      <h1>{{ count }}</h1>
    </div>
    <div id="mid-section" class="flex bg-black text-white items-center justify-evenly">
      <Card title="Card 1" info="This is some more text"></Card>
      <h2>OR</h2>
      <Card title="Card 2" info="This is some other text"></Card>
    </div>
    <div id="bottom-section" class="flex items-center justify-evenly">
      <h1>This is some more text to test</h1>
    </div>
  </div>

</template>