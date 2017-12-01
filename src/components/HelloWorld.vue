<template>
  <div class="hello">

  <div>
    <h1>{{ sss }}</h1>
    <input v-model="newItem" v-on:keyup.enter="onEnter">
    <ol>
      <li v-for="item in items" v-bind:class="[{finish:item.ifFinished},liClass]" @click="toggle(item)">{{item.label}}</li>
      </ol>
  </div>

    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
import Store from '../store'
// console.log(Store)
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App xuncl2',
      sss: 'This is a todo list:',
      items: Store.fetch(),
      liClass: 'thisisli',
      newItem: ''
    }
  },
  methods: {
    toggle: function (e) {
      // 置反
      console.log(e.ifFinished = !e.ifFinished)
    },
    onEnter () {
      console.log(this.newItem)
      this.items.push({label: this.newItem, ifFinished: false})
      this.newItem = ''
    }
  },
  watch: {
    items: {
      handler (val, oldVal) {
        console.log(val)
        Store.save(val)
      },
      deep: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.finish{
  color: #42b983;
}
.thisisli{
  background: yellow;
}
h1, h2 {
  font-weight: normal;

}ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
