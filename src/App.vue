<template>
  <div id="app">
    <test v-bind:msg="msg"></test>
  </div>
</template>

<script>

import Test from './components/test'

export default {
  name: 'app',
  data (){
    return {
      msg: 'This is a message from your friendly test component'
    }
  },
  components: {
    Test
  }
}
</script>

<style>
/*#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
</style>
