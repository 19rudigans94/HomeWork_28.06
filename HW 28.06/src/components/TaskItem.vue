<template>
    <div class="task">
        <p>{{ task }}</p>
        <button @click="deleteTask">Delete</button>
    </div>
</template>

<script>
export default {
    props: {
        task: String
    },
    methods: {
        deleteTask() {
            this.$emit('delete');
        }
    }
};
</script>

<style scoped>
.task {
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f0f0f0;
}

.task p {
    font-size: 16px;
    margin-bottom: 5px;
}

.task button {
    padding: 8px 12px;
    font-size: 14px;
    cursor: pointer;
    background-color: #f44336;
    color: white;
    border: none;
    border-radius: 3px;
}

.task button:hover {
    background-color: #d32f2f;
}
</style>
