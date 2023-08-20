<template>
  <div class="app" :class="{ dark: isDarkTheme }">
    <div class="sidebar">
      <input type="text" v-model="username" placeholder="Username" />
      <input type="password" v-model="password" placeholder="Password" />
      <button @click="connect">Connect</button>
      <div class="theme-switch">
        <input type="range" min="0" max="1" step="1" v-model="isDarkTheme" @input="toggleTheme" />
      </div>
    </div>
    <div class="main">
      <!-- ... other content ... -->
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  data() {
    return {
      username: "",
      password: "",
      isDarkTheme: true,
    };
  },
  methods: {
    toggleTheme() {
      this.isDarkTheme = !this.isDarkTheme;
      document.body.classList.toggle("dark", this.isDarkTheme);
    },
  },
  mounted() {
    this.toggleTheme(); // Apply the default theme on mount
  },
};
</script>

<style>
body, .sidebar, .main, button {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body, .sidebar, .main, button {
  background-color: #ffffff;
  color: #333333;
}

input {
  background-color: #f2f2f2;
  color: #333333;
}

.dark body, .dark .sidebar, .dark .main, .dark button {
  background-color: #333333;
  color: #ffffff;
}

.dark input {
  background-color: #4a4a4a;
  color: #ffffff;
}

.app {
  display: flex;
}

.sidebar {
  width: 20%;
  padding: 1rem;
}

.main {
  width: 80%;
  padding: 1rem;
}

button {
  cursor: pointer;
}

.theme-switch {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
</style>
