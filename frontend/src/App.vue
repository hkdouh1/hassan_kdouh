<template>
  <div id="app">
    <h1>{{ message }}</h1>
    <button @click="fetchMessage">Get Message from Flask</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Click the button!'
    }
  },
  methods: {
    async fetchMessage() {
      try {
        const response = await fetch('http://localhost:5000/api/hello');
        const data = await response.json();
        this.message = data.message;
      } catch (error) {
        this.message = 'Error: ' + error;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  margin-top: 20px;
}
</style>
