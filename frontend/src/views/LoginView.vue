<template>
    <div class="login-container">
      <form class="login-form" @submit.prevent="login">
        <h1 class="login-title">Login</h1>
        <div class="form-group">
          <label for="username">Username:</label>
          <input type="text" id="username" v-model="username" required>
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required>
        </div>
        <button type="submit" class="login-button">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      login() {
        // Perform login logic here
      }
    }
  }
  </script>
  
  <style scoped>
  .login-container {
    background-color: #000;
    color: #fff;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .login-form {
    background-color: #2ecc71;
    border-radius: 5px;
    padding: 20px;
    width: 300px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
  }
  
  .login-title {
    font-size: 24px;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
  }
  
  input[type="text"],
  input[type="password"] {
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    border: none;
    background-color: #fff;
    color: #000;
  }
  
  .login-button {
    background-color: #000;
    color: #fff;
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .login-button:hover {
    background-color: #fff;
    color: #000;
  }
  </style>
  