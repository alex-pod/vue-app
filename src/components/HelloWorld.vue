<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/gallery">Gallery</router-link>
    <div>
      <button v-on:click="increment">+</button>
      <button v-on:click="decrement">-</button>
      <button v-on:click="getValue">Get value</button>
      <hr>
      <span>{{ counter }}</span><br>
    </div>
    <ul class="list-group">
      <li v-for="comment in comments" class="list-group-item">
        <span class="circle">{{ comment.id }}</span>
        {{ comment.title }}
        <hr>
        >> {{ comment.body }}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        counter: 0,
        msg: 'Top notch js service',
        comments: [],
      }
    },
    methods: {
      increment: function() {
        this.counter++
      },
      decrement: function () {
        this.counter--
      },
      getValue: function () {
        alert(this.counter)
      },
    },
    created() {
      let url = 'https://jsonplaceholder.typicode.com/posts'
      fetch(url)
        .then(response => response.json())
        .then(data => this.comments = data)
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
