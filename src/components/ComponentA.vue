<template>
  <div class = "component_a">
    <h1>{{ msg }}</h1>
    <button @click="onClickMe">click me</button>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        msg: 'Hello ComponentA'
      }
    },
    props: [ 'msgFromFather' ],
    methods: {
      onClickMe () {
        alert('A' + this.msgFromFather)
        this.$emit('clild-tell-me-sth', this.msg)
      }
    }
  }
</script>

<style scoped>
  h1 {
    color: blue;
  }
</style>