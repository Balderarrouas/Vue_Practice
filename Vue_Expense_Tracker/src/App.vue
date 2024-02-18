<template>
  <Header />
<div class ="container">
  <Balance :total="total" />
  <IncomeExpense :income="+income" :expenses="+expenses"/>
  <TransactionList :transactions="transactions" />
  <AddTransaction />
</div>
</template>

<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';

import { computed, ref } from 'vue';

const transactions = ref([
    {id: 1, text: 'skateboard', amount: -129.99},
    {id: 2, text: 'lemonade', amount: -971.99},
    {id: 3, text: 'salary', amount: 1400},
    {id: 4, text: 'refund-skateboard', amount: 129.99},
    {id: 5, text: 'membership' , amount: -20.02},
]);

// Get total
const total = computed(() => {
  return transactions.value
  .reduce((acc, transaction) =>{
    return acc + transaction.amount;
  }, 0);
});

// Get income
const income = computed(() => {
  return transactions.value
  .filter((transactions) => transactions.amount > 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2);
});

// Get expenses
const expenses = computed(() => {
  return transactions.value
  .filter((transactions) => transactions.amount < 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2);
});
</script>