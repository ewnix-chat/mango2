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
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

  body {
    font-family: 'Inter', sans-serif;
    background-color: #f2f2f7;
    color: #000000;
  }
  .container {
    display: flex;
    height: 100vh;
  }
  .sidebar {
    width: 20%;
    padding: 40px 20px;
    background-color: #ffffff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 12px;
  }
  .login-inputs {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    width: 80%;
  }
  h2 {
    font-weight: 600;
    margin-bottom: 20px;
  }
  input {
    width: 100%;
    padding: 15px;
    margin-bottom: 10px;
    border: none;
    border-radius: 12px;
    background-color: #f2f2f7;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
  }
  button {
    padding: 15px 30px;
    border: none;
    border-radius: 12px;
    background-color: #007aff;
    color: #ffffff;
    cursor: pointer;
    font-weight: 600;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
  }
  .main {
    width: 80%;
  }
</style>

