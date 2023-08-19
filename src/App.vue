<template>
  <div class="container">
    <div class="sidebar">
      <h2>Login</h2>
      <div class="login-inputs">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
      </div>
      <button @click="connect">Connect</button>
    </div>
    <div class="main"></div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    connect() {
      console.log('Connect button clicked.');
      // TODO: Add connection logic
    }
  }
}
</script>

<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #2c2c2c;
    color: #ffffff;
  }
  .container {
    display: flex;
    height: 100vh;
  }
  .sidebar {
    width: 20%;
    padding: 20px;
    background-color: #353535;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .login-inputs {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }
  .main {
    width: 80%;
  }
  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: none;
    border-radius: 4px;
  }
  button {
    padding: 10px;
    border: none;
    border-radius: 4px;
    background-color: #4a4a4a;
    color: #ffffff;
    cursor: pointer;
  }
</style>

