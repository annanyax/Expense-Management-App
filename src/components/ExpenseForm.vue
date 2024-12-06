<template>
    <form @submit.prevent="submitForm">
    <input v-model="description" placeholder="Description" required />
    <input v-model.number="amount" type="number" placeholder="Amount" required />
    <select v-model="person" required>
      <option disabled value="">Who paid?</option>
      <option>Mario</option>
      <option>Anna</option>
      <option>Luca</option>
    </select>
    <button type="submit">Add Expense</button>
  </form>
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
  