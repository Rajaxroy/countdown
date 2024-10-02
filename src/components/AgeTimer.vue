<template>
    <div>
        <h2>Embrace Every Moment</h2>
      <input v-model.number="age" type="number" placeholder="Enter your age" />
      <button @click="startTimer" :disabled="timerRunning">Start Timer</button>
      <div v-if="timeRemaining">
        <h2>Time Remaining:</h2>
        <p>{{ hours }} hours, {{ minutes }} minutes, {{ seconds }} seconds</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        age: null,
        timeRemaining: null,
        timerRunning: false,
        timerInterval: null,
      };
    },
    computed: {
      hours() {
        return Math.floor(this.timeRemaining / 3600);
      },
      minutes() {
        return Math.floor((this.timeRemaining % 3600) / 60);
      },
      seconds() {
        return this.timeRemaining % 60;
      },
    },
    methods: {
      startTimer() {
        if (this.age < 0) {
          alert("Please enter a valid age.");
          return;
        }
        
        this.timerRunning = true;
        const yearsRemaining = 80 - this.age;
        this.timeRemaining = yearsRemaining * 365 * 24 * 3600; // Convert years to seconds
  
        this.timerInterval = setInterval(() => {
          if (this.timeRemaining > 0) {
            this.timeRemaining--;
          } else {
            clearInterval(this.timerInterval);
            this.timerRunning = false;
            alert("Time's up!");
          }
        }, 1000);
      },
    },
    beforeUnmount() { // Change here
      clearInterval(this.timerInterval); // Clear the timer when the component is destroyed
    },
  };
  </script>
  
  <style scoped>
  /* Add styles here */
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
  }
  
  p {
    font-size: 24px;
    font-weight: bold;
  }
  </style>
  