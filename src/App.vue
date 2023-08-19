<template>
  <div class="container">
    <div class="sidebar">
      <h2>Channels</h2>
      <ul>
        <li v-for="channel in channels" :key="channel">#{{ channel }}</li>
      </ul>
    </div>
    <div class="main">
      <div class="header">
        <h2>#general</h2>
      </div>
      <div class="chat">
        <div class="message">User1: Hello, world!</div>
        <div class="message">User2: Hi, User1!</div>
      </div>
      <div class="input">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
        <input type="text" placeholder="Type your message..." />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      channels: [],
      username: '',
      password: ''
    };
  },
  created() {
    // Simulate joining channels
    setTimeout(() => this.channels.push('general'), 1000);
    setTimeout(() => this.channels.push('help'), 2000);
    setTimeout(() => this.channels.push('random'), 3000);
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
  }
  .main {
    width: 80%;
    display: flex;
    flex-direction: column;
  }
  .header {
    padding: 20px;
    background-color: #3a3a3a;
  }
  .chat {
    flex: 1;
    padding: 20px;
    overflow-y: scroll;
  }
  .message {
    margin-bottom: 10px;
  }
  .input {
    padding: 20px;
    background-color: #3a3a3a;
  }
  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: none;
    border-radius: 4px;
  }
</style>

