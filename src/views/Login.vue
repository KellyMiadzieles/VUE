<template>
  <div class="home">
    <h1>Create Account</h1>
    <p>
      <input v-model="createUsername" placeholder="Enter username"/>
      <br>
      <br>
      <input v-model="createPassword" placeholder="Enter password"/>
      <br>
      <br>
      <button v-on:click="createUser()">Create Account</button>
    <p/>
    <h2>Login</h2>
    <p>
      <input v-model="enterUsername" placeholder="Enter your username"/>
      <br>
      <br>
      <input v-model="enterPassword" placeholder="Enter your password"/>
      <br>
      <br>
      <button v-on:click="Submit()">Submit</button>
    </p>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      'createUsername': '',
      'createPassword': '',
      'enterUsername': '',
      'enterPassword': ''
    }
  },
  methods: {
    'createUser': function () {
      this.$http.post('/api/public/newUser', {
        username: this.createUsername,
        password: this.createPassword
      })
          .then(response => {
            console.log(response);
            this.token = response.data;
          })
          .catch(response => {
            alert("Error")
          })
    },
    'Submit': function () {
      this.$http.post('/api/public/login', {
        username: this.enterUsername,
        password: this.enterPassword
      })
          .then(response => {
            console.log(response);
            let token = response.data;
            localStorage.setItem("user-token", token)
            this.$http.defaults.headers.common['Authorization'] = "Bearer " + token
          })
          .catch(response => {
            alert("Error")
          })
    }
  }
}
</script>
