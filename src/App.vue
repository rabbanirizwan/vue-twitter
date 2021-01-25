<template>
  <div id="app">
    <nav>
      <router-link to="/">
         <div>Home</div>
      </router-link>
     
    </nav>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
   <!-- <HelloWorld/> -->
   <router-view/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'App',
  components:{HelloWorld}
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items:center;

}
</style>