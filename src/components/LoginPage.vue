<template>
    <h3 class="pageHead">Login</h3>

   <div class="form">
  <input type="email" placeholder="Enter Email" v-model="email"/>
  <input type="password" placeholder="Enter Password" v-model="password"/>
  <button v-on:click="login">Login</button>

  <p>
    <router-link to="/signup">Sign Up</router-link>
  </p>

</div>
</template>
<script>
import axios from "axios"
export default{
    name:'LoginPage',
    data()
    {
        return{
            email:'',
            password:''
        }
    },
    methods:
    {
        async login()
        {
            let result = await axios.get(
                `http://localhost:3000/users?email=${this.email}&password=${this.password}`
            )
            console.warn(result);

            if(result.status == 200 && result.data.length>0)
        {
          this.$router.push({name:'HomePage'})
          localStorage.setItem("user-info",JSON.stringify(result.data[0]))

        }
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