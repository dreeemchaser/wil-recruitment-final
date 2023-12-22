<template>
<div class="topnav">
  <a class="active">
    href="home">HOME</a>
  <a href ="staff">Staff</a>
  <a href ="companies">Companies</a>
  <a href ="students">Students</a>
  <a href ="login">Login</a>
  <a href ="about">About</a>
  <a href ="news">News</a>
</div>
</template>

<script>
export default {
  name: "HomePage"
}
</script>

<style scoped>

.topnav{
  background-color: #2c3e50;
  overflow: hidden;
}

.topnav a{
  float: left;
  color:#449c9a;
  text-align: center;
  padding: 14px 16px;
  text-decoration:none;
  font-size:17px;

}
.topnav a:hover{
  background-color: #ddd;
  color: black;

}

.topnav a active{
  background-color: #ddd;
  color:white;
}
</style>