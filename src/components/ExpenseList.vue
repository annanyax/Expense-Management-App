<!-- <template>
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
   
  <script>
import { ref, computed } from 'vue';

export default {
  props: ['expenses'],
  emits: ['delete-expense', 'update-expense'],
  setup(props, { emit }) {
    const filterPerson = ref('');
    const sortOrder = ref('asc');

    const filteredAndSortedExpenses = computed(() => {
      let filtered = props.expenses.filter((expense) =>
        expense.person.toLowerCase().includes(filterPerson.value.toLowerCase())
      );
      filtered.sort((a, b) =>
        sortOrder.value === 'asc' ? a.amount - b.amount : b.amount - a.amount
      );

      return filtered;
    });

    const deleteExpense = (index) => {
      emit('delete-expense', index);
    };

    const editExpense = (index) => {
      const updatedDescription = prompt(
        'Update description:',
        props.expenses[index].description
      );
      const updatedAmount = parseFloat(
        prompt('Update amount:', props.expenses[index].amount)
      );
      const updatedPerson = prompt(
        'Update person:',
        props.expenses[index].person
      );
      emit('update-expense', index, {
        description: updatedDescription,
        amount: updatedAmount,
        person: updatedPerson,
      });
    };

    return { filterPerson, sortOrder, filteredAndSortedExpenses, deleteExpense, editExpense };
  },
};
</script>
   
  <style>
  header {
    background-color: #f4f4f4;
    padding: 10px;
    text-align: center;
  }
  </style> -->


  <template>
    <div>
      <!-- Filter input -->
      <label>Filter by person:</label>
      <input v-model="filterPerson" placeholder="Enter person" />
  
      <!-- Sorting dropdown -->
      <label>Sort by:</label>
      <select v-model="sortOrder">
        <option value="asc">Ascending</option>
        <option value="desc">Descending</option>
      </select>

      <ul>
  <li v-for="(expense, index) in filteredAndSortedExpenses" :key="index">
    <!-- Expense details container -->
    <div class="expense-details">
      <span class="expense-name">{{ expense.person }}</span>
      <span class="expense-amount">{{ expense.amount }}€</span>
      <span class="expense-description">{{ expense.description }}</span>
    </div>

    <!-- Action buttons -->
    <button @click="deleteExpense(index)">Delete</button>
    <button @click="editExpense(index)">Edit</button>
  </li>
</ul>
  
      
      <!-- Show a message if no expenses match the filter -->
      <p v-if="filteredAndSortedExpenses.length === 0">No expenses found.</p>
    </div>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  
  export default {
    props: ['expenses'], // Receive the expenses array from parent
    emits: ['delete-expense', 'update-expense'], // Events to notify parent of changes
    setup(props, { emit }) {
      // Reactive state for filtering and sorting
      const filterPerson = ref(''); // Stores the filter input
      const sortOrder = ref('asc'); // Stores the selected sort order
  
      /**
       * Computed property to filter and sort the expenses list.
       */
      const filteredAndSortedExpenses = computed(() => {
        // Filter expenses by the person who paid (case-insensitive)
        let filtered = props.expenses.filter((expense) =>
          expense.person.toLowerCase().includes(filterPerson.value.toLowerCase())
        );
  
        // Sort the filtered expenses by amount (ascending or descending)
        filtered.sort((a, b) =>
          sortOrder.value === 'asc' ? a.amount - b.amount : b.amount - a.amount
        );
  
        return filtered; // Return the filtered and sorted list
      });
  
      /**
       * Emit an event to delete an expense.
       * @param {number} index - The index of the expense to delete.
       */
      const deleteExpense = (index) => {
        emit('delete-expense', index);
      };
  
      /**
       * Emit an event to edit an expense.
       * @param {number} index - The index of the expense to edit.
       */
      const editExpense = (index) => {
        const updatedDescription = prompt(
          'Update description:',
          props.expenses[index].description
        );
        const updatedAmount = parseFloat(
          prompt('Update amount:', props.expenses[index].amount)
        );
        const updatedPerson = prompt(
          'Update person:',
          props.expenses[index].person
        );
  
        emit('update-expense', index, {
          description: updatedDescription,
          amount: updatedAmount,
          person: updatedPerson,
        });
      };
  
      // Expose the reactive variables and methods to the template
      return { filterPerson, sortOrder, filteredAndSortedExpenses, deleteExpense, editExpense };
    },
  };
  </script>
  
  <!-- <style>
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    padding: 8px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  button {
    margin-left: 10px;
    padding: 5px 10px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #f4f4f4;
  }
  </style> -->
  
