<template>
  <div id="app" v-on:mousemove="updateCoordinates">
    <span>Coordinates are: {{ x }} / {{ y }}</span><br>
    <img src="https://javascriptforwp.com/wp-content/uploads/2016/03/badge-js-for-wp-conf.png">
    <router-view/>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        x: 0,
        y: 0,
        link: 'http://tvoi-dom.in.ua'
      }
    },
    methods: {
      updateCoordinates: function (event) {
        this.x = event.clientX
        this.y = event.clientY
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 30px;
  }

  #app img {
    width: 200px;
  }
</style>
