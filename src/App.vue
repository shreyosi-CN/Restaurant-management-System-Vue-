<template>
  <router-view/>
</template>

<script>

export default {
  name: 'App',

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.pageHead {
    text-align: center;
    font-size: 35px;
    color: orange;
}

.form input{
  width: 300px;
  height: 40px;
  padding-left:20px;
  display: block;
  margin-bottom:30px;
  margin-left: auto;
  margin-right: auto;
}

.form button{
  width: 320px;
  height:40px;
  cursor: pointer;
}

</style>
