<template>
  <div class="home">
    <div v-show="showForm" class="form-container">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>

      <p v-show="showError" class="error">Please check the information that you have entered.  Be sure to fill in all fields.</p>

      <form v-on:submit.prevent="validateForm">

        <p>
    <label for="username">Username 
        <input type="text" id="username" v-model="username">
    </label>
</p>
<p>
    <label for="email">Email 
        <input type="email" id="email" v-model="email">
    </label>
</p>
<p>
    <label for="password">Password 
        <input type="password" id="password" v-model="password">
    </label>
</p>
<p>
    <label for="passwordVerify">Verify Password 
        <input type="password" id="passwordVerify" v-model="passwordVerify">
    </label>
</p>


        <p><input type="submit" value="Submit"></p>
      </form>
    </div>
    <div v-show="!showForm" class="success-message">
      <h1>Thank you for signing up!</h1>
      <p>Please take our new member survey. <router-link to="Survey">Click here</router-link></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      username: '',
      email: '',
      password: '',
      passwordVerify: '',
      showForm: true,
      showError: false
    }
  },
  methods: {
    validateForm: function () {
      if ((this.username != '') &&
        (this.email != '') &&
        (this.password === this.passwordVerify)){
        console.log('form is valid');
      this.showForm = false;
      } else {
        console.log('form is not valid');
        this.showError = true;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
