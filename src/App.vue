<template>
  <div id="app">
    <h1 class="app-title">VUE JS - Download json data, csv, excel or json file. </h1>
    <Example/>
  </div>
</template>

<script>
import Example from '@/pages/Example'

export default {
  name: 'App',
  components: {
    Example
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  background: rgba(3, 169, 244, 0.08);
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3a50;
  text-align: center;
  margin-top: 60px;
}
.app-title {
  font-size: 35px;
  margin-bottom: 2%;
}
 @media screen and (max-width: 750px){
    .periodic_table {
      width: 100px;
    }
    .datas .editor {
      font-size: 25px;
    }
  }
</style>
