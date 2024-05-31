<template>
    <div class="container mt-4">
      <h1 class="mb-4">Student List</h1>
      <router-link to="" class="btn btn-primary mb-4">New Student</router-link>
      <ul class="list-group mt-4">
        <li v-for="student in students" :key="student.id" class="list-group-item">
          <h4>{{ student.name }}</h4>
          <p>{{ student.age }}</p>
          <p>{{ student.province }}</p>
          <p>{{ student.score }}</p>
          <p>{{ student.phone_number }}</p>
          <!-- <router-link :to="{ name: 'show-category', params: { id: category.id } }" class="btn btn-info btn-sm">Show</router-link>
          <router-link :to="{ name: 'edit-category', params: { id: category.id } }" class="btn btn-secondary btn-sm">Edit</router-link>
          <button class="btn btn-danger btn-sm" @click="deleteCategory(category.id)">Delete</button> -->
        </li>
      </ul>
    </div>
    <!-- {{ students }} -->
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name:'list-student',
    data() {
      return {
        students: [],
      };
    },
    mounted() {
      this.fetchStudents();
    },
    methods: {
      async fetchStudents() {
        try {
          const response = await axios.get('http://127.0.0.1:8000/api/student/list');
          if (response.data.success) {
            this.students = response.data.data;
          }
        } catch (error) {
          console.error('Error fetching students:', error);
        }
      },
    },
  };
  </script>
  