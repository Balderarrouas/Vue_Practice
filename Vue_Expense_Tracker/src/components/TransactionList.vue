<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <li 
        v-for="transactionItem in transactions"
        :key="transactionItem.id"
        :class="transactionItem.amount < 0 ? 'minus' : 'plus'"
        >
        {{ transactionItem.text }} <span>${{ transactionItem.amount }}</span>
        <button class="delete-btn">x</button>

        </li>
    </ul>
</template>

<script setup>
//import { defineProps } from 'vue'; - no longer needed

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
});
</script>