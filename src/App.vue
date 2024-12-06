<template>
  <div>
    <header>
      <h2>Expense Managment App</h2>
    </header>
    <main>
      <ExpenseForm @add-expense="addExpense" />

      <ExpenseList
        :expenses="expenses"
        @delete-expense="deleteExpense"
        @update-expense="updateExpense"
      />

      <ExpenseSummary :expenses="expenses" />
    </main>
  </div>
</template>

<script>
import {ref} from 'vue';
import ExpenseForm from './components/ExpenseForm.vue';
import ExpenseList from './components/ExpenseList.vue';
import ExpenseSummary from './components/ExpenseSummary.vue';

export default {
  // Register components used in the app
  components: { ExpenseForm, ExpenseList, ExpenseSummary },

  // Reactive variable to store the list of expenses
  setup() {
    const expenses = ref([]);

    //Add, Delete, Update new expenses to the list.
    const addExpense = (expense) => {
      if (expense.description && expense.amount && expense.person) {
        expenses.value.push(expense);
        saveToLocalStorage();
      } else {
        console.error('Invalid expense data', expense);
      }
    };

    const deleteExpense = (index) => {
      expenses.value.splice(index, 1); // Remove the expense from the reactive list
      saveToLocalStorage();
    };

    const updateExpense = (index, updatedExpense) => {
      expenses.value[index] = updatedExpense;
      saveToLocalStorage(); //Updated data to local storage
    };

    const saveToLocalStorage = () => {
      localStorage.setItem('expenses', JSON.stringify(expenses.value)); //Convert array to string
    };

    const loadFromLocalStorage = () => {
      const storedExpenses = localStorage.getItem('expenses'); // Retrieve saved data from local storage
      if (storedExpenses) {
        expenses.value = JSON.parse(storedExpenses); // Parse the string and set it to the reactive list
      }
    };

    loadFromLocalStorage();

  return { expenses, addExpense, deleteExpense, updateExpense };

  },
};
</script>