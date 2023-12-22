<template>
  <div class="content-container">
    <div class="card-container">
      <h1>Update Course</h1>
      <table>
        <thead>
        <tr>
          <th @click="sortCourse('courseId')">courseId</th>
          <th @click="sortCourse('streamId')">streamId</th>
          <th @click="sortCourse('courseName')">Course Name</th>
          <th>Edit</th>
          <th>Delete</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="about in sortedCourse" :key="course.courseId">
          <td>{{ course.courseId }}</td>
          <td>
            <input v-model="course.streamId" :disabled="!about.editMode"/>
          </td>
          <td>
            <input v-model="course.courseName" :disabled="!about.editMode"/>
          </td>
          <td>
            <button class="btn-small" @click="toggleEditMode(course)">
              {{ course.editMode ? 'Save' : 'Edit' }}
            </button>
          </td>
          <td>
            <button class="btn-small" @click="deleteCourse(course.courseId)">Delete</button>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  name: 'CourseUpdate',
  data() {
    return {
      user: [],
      sortColumn: '',
      sortDirection: '',
    };
  },
  mounted() {
    this.fetchCourse();
  },
  methods: {
    fetchCourse() {
      axios
          .get('http://localhost:8080/api/admin/course/all')
          .then((response) => {
            this.course = response.data;
          })
          .catch((error) => {
            console.log(error);
          });
    },
    sortCourse(column) {
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
            console.log('About details deleted');
          })
          .catch((error) => {
            console.log(error);
            console.log('Details not deleted');
          });
    },
    toggleEditMode(course) {
      if (course.editMode) {
        this.updateCourse(course);
      }
      course.editMode = !course.editMode;
    },
    updateCourse(course) {
      axios
          .put(`http://localhost:8080/api/admin/course/update/${course.courseId}`, course)
          .then((response) => {
            console.log(response);
            console.log('Course details updated');
          })
          .catch((error) => {
            console.log(error);
            console.log('Course details not updated');
          });
    },
  },
  computed: {
    sortedCourse(){
      let sortedCourse = [...this.course];

      if (this.sortColumn) {
        sorted.sort((a, b) => {
          let valueA = a[this.sortColumn];
          let valueB = b[this.sortColumn];

          if (typeof valueA === 'string') {
            valueA = valueA.toLowerCase();
            valueB = valueB.toLowerCase();
          }

          if (valueA < valueB) {
            return this.sortDirection === 'asc' ? -1 : 1;
          }
          if (valueA > valueB) {
            return this.sortDirection === 'asc' ? 1 : -1;
          }
          return 0;
        });
      }

      return sortedCourse;
    },
  },
};
</script>
<style>
</style>
