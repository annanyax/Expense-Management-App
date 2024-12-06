<template>
    <div>
    <h2>Expense Summary</h2>
    <ul>
      <li v-for="(total, person) in totals" :key="person">
        {{ person }}: {{ total }}€
      </li>
    </ul>
  </div>
  </template>
   
  <script setup>
  const title = 'My Vue 3 Project';
  </script>
   
  <style>
  header {
    background-color: #f4f4f4;
    padding: 10px;
    text-align: center;
  }
  </style>
  