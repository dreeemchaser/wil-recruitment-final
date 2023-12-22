<template>
  <div class="card-container card-container-admin">
    <div class="form-container-admin">
      <form @submit.prevent="addCourse">
        <h2 class="form-header">Course</h2>
        <div class="form-group">
          <label for="CourseId">CourseId:</label>
          <input id="courseId" v-model="course.courseId" placeholder="Enter courseId" required type="text">
        </div>
        <div class="form-group">
          <label for="streamId">StreamId:</label>
          <input id="streamId" v-model="course.StreamId" placeholder="Enter streamId" required type="text">
        </div>
        <div class="form-group">
          <label for="courseName">Email:</label>
          <input id="courseName" v-model="course.courseName" placeholder="Enter course name" required type="email">
        </div>
        <div v-if="errorMessage" class="error-message">{{ errorMessage }}</div>
        <div class="button-container">
          <button class="confirm-button button" type="submit"><i class="fas fa-check"></i> Save</button>
          <button @click="goBack" class="deny-button button"><i class="fas fa-arrow-left"></i> Back </button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data(){
    return{
      course:{
        courseId: '',
        streamId: '',
        courseName: ''
      },
      errorMessage: ''
    };
  },
  methods:{
    addCourse(){
      this.errorMessage = '';
      const token = localStorage.getItem('token');
      console.log("token", localStorage.getItem('token'))
      axios.post("http://localhost:8080/api/admin/course/create", this.course, {
        headers: {
          Authorization: `Bearer ${token}`,
          'Content-Type': 'application/json',
        },
      })
          .then(response => {
            console.log('About details have been added successfully');
            console.log(response.data);
            console.log(response);
          })
          .catch(error => {
            console.log(error);
            if (error.response && error.response.status === 400) {
              this.errorMessage = 'Invalid data. Please check the entered values.';
              console.log(error.response.data);
              console.log(error.response.status);
              console.log(error.response);
            } else {
              this.errorMessage = 'An error occurred while adding the Course details.';
            }
          });
      this.resetForm();
    },
    resetForm(){
      this.course = {
        courseId: '',
        streamId: '',
        courseName: ''
      };
    },
    goBack() {
      this.$router.go(-1);
    }
  }
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
