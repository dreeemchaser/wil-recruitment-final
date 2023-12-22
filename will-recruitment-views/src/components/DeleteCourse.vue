<template>
  <div class="card-container">
    <h1>List All Courses</h1>
    <table>
      <thead>
      <tr>
        <th @click="sortCourse('id')">CourseId</th>
        <th @click="sortCourse('address')">StreamId</th>
        <th @click="sortCourse('officeHours')">Course Name</th>
        <th>Delete</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="course in sortCourse" :key="course.courseId">
        <td>{{ course.courseId }}</td>
        <td>{{ course.streamId }}</td>
        <td>{{ course.courseName }}</td>
        <td><button @click="deleteCourse(course.courseId)">Delete</button></td>
      </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  name: 'DeleteCourse',
  data(){
    return {
      course: [],
      sortColumn: '',
      sortDirection: '',
    };
  },
  mounted() {
    this.fetchCourse();
  },
  methods: {
    fetchCourse(){
      axios
          .get('http://localhost:8080/api/admin/Course/all')
          .then((response) => {
            this.course = response.data;
          })
          .catch((error) => {
            console.log(error);
          });
    },
    sortCourse(column){
      if (this.sortColumn === column) {
        this.sortDirection = this.sortDirection === 'asc' ? 'desc' : 'asc';
      } else {
        this.sortColumn = column;
        this.sortDirection = 'asc';
      }
    },
    deleteCourse(courseId){
      axios
          .delete(`http://localhost:8080/api/admin/course/delete/${courseId}`)
          .then((response) => {
            this.fetchCourse();
            console.log(response);
            console.log('Course details deleted');
          })
          .catch((error) => {
            console.log(error);
            console.log('Details not deleted');
          });
    },
  },
  computed: {
    sortedCourse(){
      if (this.sortColumn && this.sortDirection) {
        return this.course.sort((a, b) => {
          const aValue = a[this.sortColumn];
          const bValue = b[this.sortColumn];

          if (typeof aValue === 'string' && typeof bValue === 'string') {
            return this.sortDirection === 'asc' ? aValue.localeCompare(bValue) : bValue.localeCompare(aValue);
          } else {
            return this.sortDirection === 'asc' ? aValue - bValue : bValue - aValue;
          }
        });
      }
      return this.course;
    },
  },
};
</script>

<style>

</style>
