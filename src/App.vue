<template>
  <div class="container" :class="{dark: isDark}">
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
  data() {
    return {
      username: '',
      password: '',
      isDark: true,
    };
  },
  methods: {
    connect() {
      // Connection logic will go here
    },
    toggleTheme() {
      this.isDark = !this.isDark;
    },
  },
};
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}
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
  gap: 10px;
}
input {
  padding: 10px;
  border-radius: 8px;
  border: none;
  outline: none;
}
button {
  margin-top: 20px;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
.theme-switch {
  display: flex;
  align-items: center;
  margin-top: 15px;
}
.theme-switch span {
  margin-right: 10px;
}
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
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
  transition: .4s;
}
.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  transition: .4s;
}
input:checked + .slider {
  background-color: #2196F3;
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

/* Light theme styles */
body, .sidebar, input, button {
  background-color: #ffffff;
  color: #333333;
}

/* Dark theme styles */
.dark body, .dark .sidebar, .dark input, .dark button {
  background-color: #333333;
  color: #ffffff;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    align-items: center;
  }
  .sidebar {
    width: 100%;
    padding: 20px 10px;
    box-sizing: border-box;
  }
  .login-inputs {
    width: 90%;
  }
  .theme-switch {
    justify-content: center;
  }
}
</style>

