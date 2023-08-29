<template>
    <HeaderPage />
    <h1>Hello, Welcome to Update Resturant page</h1>
</template>
<script>
import HeaderPage from './HeaderPage.vue'
export default{
    name:"UpdateResturant",
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