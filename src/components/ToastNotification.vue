<template>
    <div v-if="isVisible" class="toast">
      <p @click="showMessage">🌟 Click me!</p>
      <button @click="dismiss" class="close-btn">✖</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isVisible: true,
      };
    },
    methods: {
      showMessage() {
        alert("Hello! Toast notification.");
        this.isVisible = false;
      },
      dismiss() {
        this.isVisible = false;
        this.$emit("dismiss");
      },
    },
  };
  </script>
  
  <style scoped>
  .toast {
    position: fixed;
    bottom: 20px;
    right: 20px;
    padding: 15px 25px;
    background: #ff69b4;
    color: #fff;
    border-radius: 8px;
    cursor: pointer;
    box-shadow: 0 0 15px rgba(255, 105, 180, 0.6);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .toast p {
    margin: 0;
  }
  
  .close-btn {
    background: transparent;
    border: none;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
  }
  </style>
  