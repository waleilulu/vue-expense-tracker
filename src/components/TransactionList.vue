<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <li v-for="transaction in transactions" :key="transaction.id"
            :class="transaction.amount < 0 ? 'minus' : 'plus'">

            {{ transaction.text }} <span>${{ transaction.amount }}</span>
            <button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
        </li>
    </ul>
</template>

<!-- <script>
export default {
    data() {
        return {
            transactions: [
                { id: 1, text: 'Flower', amount: -19.99 },
                { id: 2, text: 'Salary', amount: 300 },
                { id: 3, text: 'Book', amount: -27.99 },
                { id: 2, text: 'Cash dividend', amount: 90 },
            ],
        };
    },
};
</script> -->
<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});

const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id) => {
    emit('transactionDeleted', id);
};
</script>