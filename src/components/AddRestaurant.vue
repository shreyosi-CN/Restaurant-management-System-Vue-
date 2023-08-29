<template>
    <HeaderPage />
    <h1>Hello, Welcome to Add Resturant page</h1>
</template>
<script>
import HeaderPage from './HeaderPage.vue'
export default{
    name:"AddResturant",
    components:{
        HeaderPage
    },
    mounted()
    {
      let user = localStorage.getItem("user-info");
      if(!user)
      {
        this.$router.push({name:'SignUp'})

      }
    }

};
</script>