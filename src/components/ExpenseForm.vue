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
   
  <script>
  import { ref } from 'vue';

export default {
    // Declare the event that this component emits
  emits: ['add-expense'],
  setup(_, { emit }) {
    // State variables to hold the form input values
    const description = ref('');
    const amount = ref(null);
    const person = ref('');

    // Function to handle form submission
    const submitForm = () => {
      emit('add-expense', {
        description: description.value,
        amount: amount.value,
        person: person.value,
      });
       // Clear the form fields after submission
      description.value = '';
      amount.value = null;
      person.value = '';
    };

    // Return the state variables and functions to the template
    return { description, amount, person, submitForm };
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
  