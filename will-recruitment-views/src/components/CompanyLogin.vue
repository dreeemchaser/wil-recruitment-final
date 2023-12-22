<template>

  <div class="login">
    <form action="action_page.php" method="post">
      <div class="container">
        <h1>Company Login</h1>

        <label for="uname"><b>Username</b></label>
        <input type="text" placeholder="Enter Username" name="uname" required>

        <label for="psw"><b>Password</b></label>
        <input type="password" placeholder="Enter Password" name="psw" required>

        <button type="submit">Login</button>

        <label>Forgot <a href="#">password?</a></label>
      </div>
    </form>
  </div>

</template>



<script>
export default {
  name: 'CompanyLogin'
}
</script>


<style>
form {
  border: 3px solid #f1f1f1;
  background-color: rgb(175, 171, 171);
  width: 410px;
  margin: auto;
  display: flex;
  justify-content: center;
  position: absolute;
  left: 37%;
  top: 30%;
}

/* Full-width inputs */
input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
button {
  background-color: #449c9a;
  color: rgb(0, 0, 0);
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  border-radius: 25px;
}

/* Add a hover effect for buttons */
button:hover {
  opacity: 0.8;
}

/* Add padding to containers */
.container {
  padding: 16px;
  width: 400px;
}

</style>