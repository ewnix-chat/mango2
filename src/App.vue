<template>
  <div class="container" :class="theme">
    <div class="sidebar">
      <h2>Login</h2>
      <div class="login-inputs">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
      </div>
      <button @click="connect">Connect</button>
      <div class="theme-switch">
        <label class="switch">
        <input type="checkbox" :checked="isDark" @change="toggleTheme" />
        <span class="slider round"></span>
      </label>
    </div>
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
      this.isDark = !this.isDark;
      this.theme = this.isDark ? 'dark' : 'light';
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

  body, html {
    font-family: 'Inter', sans-serif;
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
  }
  .container {
    display: flex;
    height: 100vh;
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

/* Light theme styles */
  body, .sidebar, button {
    background-color: #ffffff;
    color: #333333;
  }

  input {
    background-color: #f2f2f2;
    color: #333333;
  }

/* Dark theme styles */
  .dark body, .dark .sidebar, .dark button {
    background-color: #333333;
    color: #ffffff;
  }
  
  .dark input {
    background-color: #4a4a4a;
    color: #ffffff;
  }

  .main {
    background-color: #ffffff;
    width: 80%;
    height: 100vh;
  }

  .dark .main {
    background-color: #333333;
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

  .sidebar {
    width: 20%;
    height: 100vh;
    padding: 1em;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

/* Mobile */

  @media (max-width: 768px) {
    .container {
      flex-direction: column;
      align-items: center;
    }
    .sidebar {
      width: 100%;
      padding: 0;
      align-items: center;
    }
    .login-inputs {
      width: 90%;
    }
    .theme-switch {
      justify-content: center;
    }
  }
</style>
