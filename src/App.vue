<template>
  <div>
    <header>
      <h2>Expense Managment App</h2>
    </header>
    <main>
      <ExpenseForm />
      <ExpenseList />
      <ExpenseSummary />
    </main>
    <footer>
      <p>End</p>
    </footer>
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
      expenses.value.push(expense);
      saveToLocalStorage();
    };

    const deleteExpense = (index) => {
      expenses.value.splice(index, 1);
      saveToLocalStorage();
    };

    const updateExpense = (index, updatedExpense) => {
      expenses.value[index] = updatedExpense;
      saveToLocalStorage();
    };

    
  },
};
</script>
 
<style>
main {
  padding: 20px;
}
</style>
