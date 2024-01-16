<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text"><b>Text</b></label>
      <input type="text" id="text" placeholder="Enter name of Expense..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="amount"
        ><b>Amount : </b>(negative - expense, positive - income)</label
      >
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div><br>
    <button class="btn">Add Amount</button>
  </form>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';

const text = ref('');
const amount = ref('');

// Get toast interface
const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error('Both fields must be filled.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit('transactionSubmitted', transactionData);

  // Clear form fields
  text.value = '';
  amount.value = '';
};
</script>
