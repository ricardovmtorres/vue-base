
<style src="./assets/css/App.css"></style>

<template>
  <div class="form-group centered mx-auto">
      <form @submit.prevent="register">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
        <button type="submit">Register</button>
      </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    async register() {
      try {
        await axios.post('https://localhost:7175/api/Auth/register', {
          username: this.username,
          password: this.password
        }).then(response =>{
          console.log(response);
        });
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>