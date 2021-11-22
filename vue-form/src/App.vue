<template>
  <form v-on:submit.prevent="submitEvent">
    <div>
      <label for="username">id: </label>
      <input type="text" id="username" v-model="usernames"/>
    </div>
    <div>
      <label for="password">pw: </label>
      <input type="password" id="password" v-model="passwords"/>
    </div>
    <button type="submit">send</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitEvent: function() {
      const url = 'https://jsonplaceholder.typicode.com/users';
      const data = {
        username: this.username,
        password: this.password,
      }
      axios.post(url, data)
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });

    }
  }
}
</script>

<style>

</style>