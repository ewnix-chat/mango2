<template>
  <div class="app" :class="{ dark: isDarkTheme }">
    <div class="sidebar">
      <input type="text" v-model="username" placeholder="Username" />
      <input type="password" v-model="password" placeholder="Password" />
      <button @click="connect">Connect</button>
      <label class="theme-switch">
        <input type="range" min="0" max="1" step="1" v-model="isDarkTheme" @input="toggleTheme" />
      </label>
    </div>
    <div class="main">
      <p>{{ connectionStatus }}</p>
      <!-- ... other content ... -->
    </div>
  </div>
</template>

import { ref } from "vue";
import io from "socket.io-client";

export default {
  name: "App",
  data() {
    return {
      username: "",
      password: "",
      isDarkTheme: true,
      connectionStatus: "",
    };
  },
  methods: {
    toggleTheme() {
      this.isDarkTheme = !this.isDarkTheme;
      document.body.classList.toggle("dark", this.isDarkTheme);
    },
    connect() {
      const socket = io("wss://irc.ewnix.net:8097", {
        transports: ["websocket"],
        secure: true,
      });

      socket.on("connect", () => {
        console.log("Connected to the server");
        this.connectionStatus = "Connected to the server";
        this.authenticate(socket);
      });

      socket.on("connect_error", (error) => {
        console.error("Connection error:", error);
        this.connectionStatus = "Connection error: " + error;
      });
    },
    authenticate(socket) {
      const authPayload = {
        username: this.username,
        password: this.password,
      };

      socket.emit("sasl-auth", authPayload);
    },
  },
  mounted() {
    this.toggleTheme(); // Apply the default theme on mount
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
  height: 100vh;
  padding: 1em;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* For mobile devices */
@media screen and (max-width: 768px) {
  .sidebar {
    width: 100%;
    padding: 0;
    align-items: center;
  }
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

/* Set defaults for .main class */

.main {
  width: 100%;
  height: 100vh;
  background-color: #ffffff;
}

.dark .main {
  background-color: #333333;
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

