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
      <br>
      <span>{{ counter }}</span><br>
      <hr>
    </div>

    <select v-model="selected">
      <option value="">Value source type</option>
      <option>Feature</option>
      <option>Generic</option>
      <option>Feature LOV</option>
      <option>Feature Range</option>
    </select>
    <br><br>

    <div v-if="selected === 'Feature'" class="bordered">
      {{ selected }} selected
      <br>
      <label>Provider Feature Id</label><br>
      <input v-model="providerFeatureId" class="mbot1">
      <br>
      <label>Active</label>
      <input type="checkbox" id="checkbox" v-model="checked">

    </div>
    <div v-if="selected === 'Generic'" class="bordered">
      {{ selected }} selected
    </div>
    <div v-if="selected === 'Feature LOV'" class="bordered">
      {{ selected }} selected
    </div>
    <div v-if="selected === 'Feature Range'" class="bordered">
      {{ selected }} selected
    </div>

    <div class="result bordered" v-show="selected">
      <p>Provider Feature Id: {{ providerFeatureId }}</p>
      <label for="checkbox">Active: {{ checked }}</label>
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
        selected: '',
        providerFeatureId: '',
        checked: false,
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

  .mbot1 {
    margin-bottom: 1em;
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

  .bordered {
    border: 1px solid black;
    border-radius: 5px;
    margin-top: 1em;
    padding: 1em;
  }
</style>
