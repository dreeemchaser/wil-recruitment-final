<template>
    <StudentLogin/>
</template>


<script>
import StudentLogin from './components/StudentLogin.vue';
export default{
  name: 'App',
  components: {
    StudentLogin
  }
}
</script>



<style >
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}

.logo{
  width: 100px;
}
</style>
