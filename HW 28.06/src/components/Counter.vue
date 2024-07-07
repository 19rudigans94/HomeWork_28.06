<template>
    <div class="counter">
        <p>Count: {{ count }}</p>
        <button @click="increment">Increment</button>
        <button @click="reset">Reset</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: 0
        };
    },
    methods: {
        increment() {
            this.count++;
        },
        reset() {
            this.count = 0;
            this.$emit('reset');
        }
    }
};
</script>

<style scoped>
.counter {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f0f0f0;
}

.counter p {
    font-size: 18px;
    font-weight: bold;
}

.counter button {
    margin: 0 5px;
    padding: 8px 12px;
    font-size: 16px;
    cursor: pointer;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 3px;
}

.counter button:hover {
    background-color: #45a049;
}
</style>
