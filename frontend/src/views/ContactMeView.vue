<template>
    <body>
        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" v-model="name" required>
          </div>
          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" required>
          </div>
          <div class="form-group">
            <label for="message">Message:</label>
            <textarea id="message" v-model="message" required></textarea>
          </div>
          <button class="submit-button" type="submit">Submit</button>
        </form>
    </body>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        email: '',
        message: ''
      }
    },
    methods: {
      submitForm() {
        const formData = new FormData();
        formData.append('name', this.name);
        formData.append('email', this.email);
        formData.append('message', this.message);
        
        fetch('/submit-form', {
          method: 'POST',
          body: formData
        })
        .then(response => {
          if (response.ok) {
            alert('Form submitted successfully!');
            this.name = '';
            this.email = '';
            this.message = '';
          } else {
            alert('Form submission failed. Please try again later.');
          }
        })
        .catch(error => {
          alert('Form submission failed. Please try again later.');
          console.error(error);
        });
      }
    }
  };
  </script>
  
  <style scoped>

  body{
    position: relative;
    background-image: url('https://i.postimg.cc/4ymwDgqT/Archie-Vable-Gaming-Logo.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    font-family: Arial, sans-serif;
    margin: 0;
    z-index: 1;
  }
  .contact-form {
    max-width: 500px;
    margin: 0 auto;
    padding: 100px;
    border-radius: 5px;
    box-shadow: 0 2px 5px white;
    z-index: 1;
    color: white;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    font-size: 16px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  input[type="text"],
  input[type="email"],
  textarea {
    display: block;
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    border: none;
    font-size: 16px;
    box-shadow: inset 0 1px 2px white;
  }
  
  textarea {
    height: 150px;
  }
  
  .submit-button {
    background-color: #3498db;
    color: #fff;
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }
  
  .submit-button:hover {
    background-color: #2980b9;
  }
  </style>
  