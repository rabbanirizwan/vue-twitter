<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <router-link 
    id="list"
    v-for="user in User" 
    :key="user.id"
    :to="{name:'UserProfile',params:{userId:user.id}}"
    >
    {{user.username}}
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import {users} from "../assets/users"
export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  computed:{
    User(){
      return users
    }
  },
  beforeMount(){
    console.log(users)
  }
}
</script>
<style scoped>
#list{
  display: flex;
  flex-direction: column;
}
</style>
