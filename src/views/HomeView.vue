<template>
<div class="box">
  <div>
    Register
  </div>
  <div class="box-border h-32 w-32 p-4 border-4">
    <form @submit.prevent="postUser( email, password)">
      <label for="email">email</label><br>
      <input type="email" v-model="email" required><br>
      <label for="password">Password</label><br>
      <input type="password" v-model="password" required><br>
      <button>Submit</button>
    </form>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  methods: {
    async postUser(email, password){
      try{
        const res = await axios.post('http://localhost:3000/post/user',{
          email: email,
          password: password
        })
        // .then((response))
        this.$router.push("/about")
      }
      catch(err){
        console.log(err)
      }
    },
    // async getUser(){
    //   try{
    //     const res = await axios.get('http://localhost:3000/get/user')
    //     console.log(res)
    //   }
    //   catch(err){
    //     console.log(err)
    //   }
    // },
    
  },
  mounted() {
    
    // this.getUser()
  },
}
</script>

