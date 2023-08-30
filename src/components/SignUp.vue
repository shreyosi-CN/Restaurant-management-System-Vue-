<template>
<h3 class="pageHead">Sign Up</h3>
<div class="form">
  <input type="text" placeholder="Enter Name" v-model="name"/>
  <input type="email" placeholder="Enter Email" v-model="email"/>
  <input type="password" placeholder="Enter Password" v-model="password"/>
  <button v-on:click="signUp">Sign Up</button>

  <p>
    <router-link to="/login">Login</router-link>
  </p>

</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data()
    {
      return{
        name:'',
        email:'',
        password:''
      }
    },
    methods:
    {
      async signUp()
      {
        console.log("Signup",this.name,this.email,this.password)

        let result = await axios.post("http://localhost:3000/users",
        {name:this.name,email:this.email,password:this.password});
        console.warn(result);
        if(result.status == 201)
        {
          this.$router.push({name:'HomePage'})
        }
         localStorage.setItem("user-info",JSON.stringify(result.data))
      }
     

    },
    mounted()
    {
      let user = localStorage.getItem("user-info");
      if(user)
      {
        this.$router.push({name:'HomePage'})

      }
    }

}
</script>

<style>

</style>
