<template>
    <h3>History</h3>


    <ul id="list" class="list" v-if="transactions.length > 0">

        <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'">
            {{ transaction.text }} <span>${{ transaction.amount }}</span>
            <button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
        </li>


    </ul>
    <h1 v-else style="text-align: center; font-size: medium;">No history yet</h1>
</template>

<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(["transactionDeleted"]);

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
});

const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
}

</script>