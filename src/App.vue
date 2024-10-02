<template>
  <div id="app">
    <h1>Track Your Remaining Time in Days, Hours, Minutes, and Seconds</h1>
    <AgeTimer />
  </div>
</template>

<script>
import AgeTimer from './components/AgeTimer.vue';

export default {
  components: {
    AgeTimer,
  },
};
</script>

<style>
#app {
  text-align: center;
  margin: 50px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

h1 {
  color: #42b983;
}

input {
  padding: 8px;
  margin: 10px 0;
  font-size: 16px;
}

button {
  padding: 10px 15px;
  font-size: 16px;
  color: #fff;
  background-color: #42b983;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

h2 {
  margin-top: 20px;
  color: #42b983;
}

p {
  font-size: 24px;
  font-weight: bold;
}
</style>
