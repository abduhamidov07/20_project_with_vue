<template>
  <div id="app">
   <h1>{{ count }}</h1>
   <button v-on:click="subs">Subs</button>
   <button v-on:click="add">Add</button>
  </div>
</template>



<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    add() {
      this.count += 1;
    },
    subs() {
      this.count -= 1;
    }
  }
} 
</script>

