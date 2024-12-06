<template>
    <div>
      <label>Filter by person:</label>
      <input v-model="filterPerson" placeholder="Enter person" />
      <label>Sort by:</label>
      <select v-model="sortOrder">
        <option value="asc">Ascending</option>
        <option value="desc">Descending</option>
      </select>
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
  