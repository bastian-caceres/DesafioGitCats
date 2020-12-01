<template>
  <div id="app">
    <GitCats :gifgato="gif"/>
  </div>
</template>

<script>
import GitCats from './components/GitCats.vue'

export default {
  name: 'App',
  data() {
    return {
      gif:[]
    }
  },
  components: {
    GitCats
  },
  created() {
    fetch('https://cataas.com/cat/gif')
    .then(resp => resp.json())
    .then(data => {
      console.log(data)
      this.gif = data;
    })
    .catch(error => console.log(error))
  }
}
</script>

<style>
#app{
  background-color: burlywood;
}
</style>
