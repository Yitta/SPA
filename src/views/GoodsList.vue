<template>
    <div>
        <button @click="increment"> + </button>
        <button v-on:click="decrement"> - </button>
        <button @click="get">GET</button>
        <button @click="post">POST</button>
        <button @click="sum1">sum</button>

        <p>
            <span>{{num}}</span>
            <span>user id:{{$route.params}}</span>
            <span>item id:{{$route.params.item_id}}</span>
        </p>
    </div>
</template>

<script>
import axios from 'axios'
import {sum} from './util.js'
export default {
  name: "Counter",
  data() {
    return {
      num: 0
    };
  },
  methods: {
    
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
