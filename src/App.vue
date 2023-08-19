<template>
  <div class="container" :class="theme">
    <div class="sidebar">
      <h2>Login</h2>
      <div class="login-inputs">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
      </div>
      <button @click="connect">Connect</button>
      <label class="switch">
        <input type="checkbox" v-model="isDark" @change="toggleTheme" />
        <span class="slider round"></span>
      </label>
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
      password: '',
      theme: 'dark',
      isDark: true
    };
  },
  methods: {
    connect() {
      console.log('Connect button clicked.');
      // TODO: Add connection logic
    },
    toggleTheme() {
      this.theme = this.isDark ? 'dark' : 'light';
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

  body {
    font-family: 'Inter', sans-serif;
  }
  .container {
    display: flex;
    height: 100vh;
  }
  .sidebar {
    width: 20%;
    padding: 40px 20px;
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
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
  }
  button {
    padding: 15px 30px;
    border: none;
    border-radius: 12px;
    color: #ffffff;
    cursor: pointer;
    font-weight: 600;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
    margin-top: 10px;
  }

  /* Dark Theme */
  .dark {
    background-color: #2c2c2c;
    color: #ffffff;
  }
  .dark .sidebar {
    background-color: #353535;
  }
  .dark input {
    background-color: #3a3a3a;
  }
  .dark button {
    background-color: #4a4a4a;
  }

  /* Light Theme */
  .light {
    background-color: #f2f2f7;
    color: #000000;
  }
  .light .sidebar {
    background-color: #ffffff;
  }
  .light input {
    background-color: #f2f2f7;
  }
  .light button {
    background-color: #007aff;
  }

  /* Toggle Switch */
  .switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 34px;
    margin-top: 15px;
  }
  .switch input {
    display: none;
  }
  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    transition: 0.4s;
  }
  .slider:before {
    position: absolute;
    content: "";
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    transition: 0.4s;
  }
  input:checked + .slider {
    background-color: #007aff;
  }
  input:checked + .slider:before {
    transform: translateX(26px);
  }
  .slider.round {
    border-radius: 34px;
  }
  .slider.round:before {
    border-radius: 50%;
  }
</style>

