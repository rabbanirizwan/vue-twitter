<template>
  <div id="app">
   <HelloWorld/>
   <UserProfile/>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";
export default {
  components: {UserProfile },
  name: 'App',
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