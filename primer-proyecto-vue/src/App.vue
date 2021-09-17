<template>
  <div id="app">
    <input type="text" v-model="teamName" >
    <InfoEquipo v-bind:teamName="this.teamName" />
  </div>
</template>

<script>
import InfoEquipo from './components/InfoEquipo.vue'

export default {
  name: 'App',
  data(){
    return{
        teamName: ''
    }
  },
  components: {
    InfoEquipo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
