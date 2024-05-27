<template>
    <div class="container mt-4">
      <h1 class="mb-4">Category Details</h1>
      <div v-if="category" class="card">
        <div class="card-body">
          <h5 class="card-title">{{ category.name }}</h5>
          <p class="card-text">{{ category.description }}</p>
          <router-link :to="{ name: 'edit-category', params: { id: category.id } }" class="btn btn-secondary">Edit</router-link>
          <router-link to="/categories" class="btn btn-primary">Back to Categories</router-link>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'show-categories',
    props: ['id'],
    data() {
      return {
        category: null,
      };
    },
    created() {
      this.fetchCategoryDetails();
    },
    methods: {
      async fetchCategoryDetails() {
        try {
          const response = await axios.get(`http://127.0.0.1:8000/api/category/show/${this.id}`);
          if (response.data.success) {
            this.category = response.data.data;
          }
        } catch (error) {
          console.error('Error fetching category details:', error);
        }
      },
    },
  };
  </script>
  