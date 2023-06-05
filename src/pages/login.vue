<template>
    <div>
      <h2>Registration</h2>
      <form @submit.prevent="register">
        <div>
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="name" required>
        </div>
        <div>
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email" required>
        </div>
        <div>
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required>
        </div>
        <div>
          <button type="submit">Register</button>
        </div>
      </form>
      <p v-if="errorMessage">{{ errorMessage }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: '',
        password: '',
        errorMessage: '',
      };
    },
    methods: {
      register() {
        // Validasi input sebelum proses registrasi
        if (!this.name || !this.email || !this.password) {
          this.errorMessage = 'Please fill in all fields.';
          return;
        }
  
        // Proses registrasi
        // ...
  
        // Reset input setelah registrasi berhasil
        this.name = '';
        this.email = '';
        this.password = '';
        this.errorMessage = '';
      },
    },
  };
  </script>
  