<template>
  <div class="box">
  <div>
    Login
  </div>
  <div>
    <form @submit.prevent="loginUser(email, password)">
      <label for="email">email</label><br>
      <input type="email" v-model="email" required>
      <label for="password">Password</label><br>
      <input type="password" v-model="password" required>
      <button type="submit"> Login </button>
    </form>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return {
      users:[]
      
    }
  },
  methods: {
    async loginUser(email, password){
      try{
        const res = await axios.post('http://localhost:3000/post/login',{
          email: email,
          password: password
        })
        this.$router.push("/dashboard")
      }
      catch(err){
        console.log(err)
      }
    },
    // async getUser(){
      
    //   try{
    //     const res = await axios.get('http://localhost:3000/get/user')
    //     .then((response)=>{
    //       this.users.push(...response.data)
    //     })
    //     console.log(res)        
    //   }
    //   catch(err){
    //     console.log(res)
    //   }
    // },
    
  },
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
