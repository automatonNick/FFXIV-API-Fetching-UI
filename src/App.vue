<template>
  <img alt="FFXIV logo" src="https://www.finalfantasyxiv.com/imgs/xivlogo.png">

  <NavTemplate></NavTemplate>

</template>

<script>
import NavTemplate from './components/NavTemplate.vue'


export default {
  name: 'App',
  components: {
    NavTemplate
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=PT+Serif&family=Unbounded&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:#e8f5ff;
  text-shadow: 2px 2px 5px #004eaa;


}
img{
  height: 200px;

}
html{
  margin: 0;
  background-image: url("https://www.finalfantasyxiv.com/imgs/bg.jpg");
background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

</style>
