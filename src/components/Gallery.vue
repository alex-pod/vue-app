<template>
  <div>
    <h1>Top notch js service</h1>
    <router-link to="/">Home</router-link> |
    <router-link to="/gallery">Gallery</router-link>
    <div class="image-wrapper">
      <img v-for="image in images" :src="image.thumbnailUrl">
    </div>
  </div>
</template>

<script>
  export default {
    name: "Gallery",
    data() {
      return {
        images: [],
      }
    },
    created() {
      let url = 'https://jsonplaceholder.typicode.com/photos'
      fetch(url)
        .then(response => response.json())
        .then(data => this.images = data)
    }
  }
</script>

<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
    text-align: left;
  }

  li {
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }

  .circle {
    background: #495057;
    border-radius: 0.8em;
    -moz-border-radius: 0.8em;
    -webkit-border-radius: 0.8em;
    color: #ffffff;
    display: inline-block;
    font-weight: bold;
    line-height: 1.6em;
    margin-right: 5px;
    text-align: center;
    width: 1.6em;
  }
</style>
