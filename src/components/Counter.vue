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
    sum1() {
      this.num = sum(1,2)
    },
    increment() {
      this.$emit("incre");
    },
    decrement() {
      this.$emit("decre");
    },
    get() {
      axios.get("./data.json", {
        params: {
          userId: "123"
        },
        headers: {
          token: "jack"
        }
      }).then(res=> {
        this.num = res.data;
      }).catch(error=> {
        this.num = error
      })
    },
    post() {
      axios.post("./data.json", {
        userId: "999"
      },{
        headers: {
          token: "tom"
        }
      }).then(res=> {
        this.num = res.data
      }).catch(error=> {
        this.num = error
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
