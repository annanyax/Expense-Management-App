<template>
    <!-- <div>
    <h2>Expense Summary</h2>
    <ul>
      <li v-for="(total, person) in totals" :key="person">
        {{ person }}: {{ total }}€
      </li>
    </ul>
  </div> -->


  <div class="expense-summary">
  <h2>Expense Summary</h2>
  <ul>
    <li v-for="(total, person) in totals" :key="person">
      <span class="person-name">{{ person }}</span>
      <span class="total-amount">{{ total }}€</span>
    </li>
  </ul>
</div>
  </template>
   
  <script>
  import { computed } from 'vue';

export default {
  // Define props to accept the expenses array from the parent component
  props: ['expenses'],

  setup(props) {
    /**
     * Computed property to calculate the total expenses for each person.
     * Loops through the expenses and aggregates the amounts by person.
     */
    const totals = computed(() => {
      return props.expenses.reduce((acc, expense) => {
        acc[expense.person] = (acc[expense.person] || 0) + expense.amount;
        return acc;
      }, {});
    });

    // Return the computed property for use in the template
    return { totals };
  },
};
  </script>
   
  <!-- <style>
  header {
    background-color: #f4f4f4;
    padding: 10px;
    text-align: center;
  }
  </style> -->
  