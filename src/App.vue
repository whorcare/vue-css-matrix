<template>
  <div id="app">
    <button @click="change">变换</button>
    
    <div>scaleX:<input v-model="scaleX"/></div>
    <div>scaleY:<input v-model="scaleY"/></div>
    <div>translateX:<input v-model="translateX"/></div>
    <div>translateY:<input v-model="translateY"/></div>
    <div>rotateX:<input v-model="rotateX"/></div>
    <div style="margin-top: 300px">
      <img alt="Vue logo" class="img" :style="css" src="./assets/logo.png">
    </div>
    
  </div>
</template>

<script>
import { scale, translate, rotate, generateMatrix, generateCSS } from './matrix.js'

export default {
  name: 'App',
  data() {
    return {
      css: null,
      scaleX: 2,
      scaleY: 2,
      translateX: 50,
      translateY: 50,
      rotateX: 30
    }
  },
  created() {
  },
  methods: {
    change() {
      const css = generateCSS(scale(this.scaleX, this.scaleY), translate(this.translateX, this.translateY), rotate('x', this.rotateX));  
      console.log(css);
      this.css = `transform: ${css}`;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.img {
  transition: all linear 2s;
  width: 300px;
}
</style>
