<template>
    <nav class="navbar">
      <ul>
        <li @click="navigateTo('home')" :class="{ active: currentPage === 'home' }">Home</li>
        <li @click="navigateTo('information')" :class="{ active: currentPage === 'information' }">Information</li>
        <li @click="navigateTo('aboutUs')" :class="{ active: currentPage === 'aboutUs' }">About Us</li>
      </ul>
    </nav>
  </template>
  
  <script>
  export default {
    props: ["navigate", "currentPage"],
    methods: {
      navigateTo(page) {
        this.navigate(page);
      },
    },
  };
  </script>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: center;
    background-color: #2c2c2c; /* Darker shade for a sleeker look */
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3); /* Adds a subtle shadow */
    border-radius: 10px; /* Rounded corners for a modern touch */
  }
  
  ul {
    list-style: none;
    display: flex;
    gap: 30px;
  }
  
  li {
    color: #e0e0e0;
    cursor: pointer;
    font-size: 18px;
    font-weight: 600;
    position: relative;
    transition: color 0.3s ease; /* Only change color on hover */
    padding: 10px; /* Stable clickable area */
    min-width: 100px; /* Set a minimum width */
    text-align: center; /* Center text within each item */
  }
  
  li::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #ff69b4; /* Matching hover color for underline */
    bottom: -6px;
    left: 0;
    transform: scaleX(0);
    transition: transform 0.3s ease;
  }
  
  li:hover {
    color: #ff69b4;
  }
  
  li:hover::after {
    transform: scaleX(1); /* Underline grows on hover */
  }
  
  li.active {
    color: #ff69b4; /* Active color for the selected page */
    font-weight: 700; /* Slightly bolder for active page */
  }
  </style>
  