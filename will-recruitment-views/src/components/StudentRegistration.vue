<template>


<div class="Registration">
    <h1>Student Registration</h1>


    <form>
                     <!-- Personal Details -->         
         <div class="details-heading">
            <h3>Personal Details</h3> 
         </div>
        <br>    
            <div class="inputGroup">
                 <input type="text" required="" autocomplete="off">
                <label for="name">First Name</label>
            </div>

            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Surname</label>
            </div>
            
            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">ID Number</label>
            </div>

            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Phone Number</label>
            </div>
            
                          <!-- University Details -->  
         <div class="details-heading">
            <h3>University Details</h3>
         </div>
        <br>                       
            <div class="inputGroup">
                 <input type="text" required="" autocomplete="off">
                <label for="name">Student Number</label>
            </div>

            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Student Email</label>
            </div>
            
            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Faculty Name</label>
            </div>

            <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Department</label>
            </div>

             <div class="inputGroup">
                <input type="text" required="" autocomplete="off">
                <label for="name">Course</label>
            </div>


        
   </form>
</div>

</template>    



<script>
    export default {
        name: 'StudentRegistration'
    }
</script>


<style>
 body {
  margin: 0;
  background-color: hsl(0, 0%, 98%);
  color: #333;
  font: 100% / normal sans-serif;
}

main {
  margin: 0 auto;
  padding: 4rem 0;
  width: 100%;
  max-width: 60rem;
}

form {
  box-sizing: border-box;
  padding: 2rem;
  border-radius: 1rem;
  background-color: hsl(0, 0%, 100%);
  border: 4px solid hsl(0, 0%, 90%);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.full-width {
  grid-column: span 2;
}

.inputGroup {
  font-family: 'Segoe UI', sans-serif;
  max-width: 190px;
  position: relative;
}

.inputGroup input {
  font-size: 80%;
  padding: 0.8em;
  outline: none;
  border: 2px solid rgb(200, 200, 200);
  background-color: transparent;
  border-radius: 20px;
  width: 100%;
}

.inputGroup label {
  font-size: 80%;
  position: absolute;
  left: 0;
  padding: 0.8em;
  margin-left: 0.5em;
  pointer-events: none;
  transition: all 0.3s ease;
  color: rgb(100, 100, 100);
}

.inputGroup :is(input:focus, input:valid)~label {
  transform: translateY(-50%) scale(.9);
  margin: 0em;
  margin-left: 1.3em;
  padding: 0.4em;
  background-color: #e8e8e8;
}

.inputGroup :is(input:focus, input:valid) {
  border-color: rgb(0, 0, 0);
}

.details-heading{
   position: relative;
   left: 50%;
   text-decoration: underline;
}

</style>