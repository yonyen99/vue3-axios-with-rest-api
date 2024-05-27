<template>
    <div class="container mt-4">
      <h1 class="mb-4">Create Category</h1>
      <form @submit.prevent="createCategory">
        <div class="mb-3">
          <label for="category-name" class="form-label">Name</label>
          <input type="text" class="form-control" id="category-name" v-model="category.name" required />
        </div>
        <div class="mb-3">
          <label for="category-description" class="form-label">Description</label>
          <textarea class="form-control" id="category-description" v-model="category.description" required></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Create Category</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name:'create-category',
    data() {
      return {
        category: {
          name: '',
          description: '',
        },
      };
    },
    methods: {
      async createCategory() {
        try {
          const response = await axios.post('http://127.0.0.1:8000/api/category/create', this.category);
          if (response.data.success) {
            this.$router.push('/categories');
          }
        } catch (error) {
          console.error('Error creating category:', error);
        }
      },
    },
  };
  </script>
  