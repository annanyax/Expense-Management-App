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
<script setup>
import ExpenseForm from './components/ExpenseForm.vue';
import ExpenseList from './components/ExpenseList.vue';
import ExpenseSummary from './components/ExpenseSummary.vue';
</script>
 
<style>
main {
  padding: 20px;
}
</style>
