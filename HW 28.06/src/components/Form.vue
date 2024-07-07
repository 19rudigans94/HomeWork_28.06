<template>
    <form @submit.prevent="handleSubmit" class="form">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name">
        <br>
        <label for="age">Age:</label>
        <input type="number" id="age" v-model.number="age">
        <br>
        <button type="submit">Submit</button>
        <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </form>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            age: null,
            errorMessage: ''
        };
    },
    methods: {
        handleSubmit() {
            if (!this.name || !this.age) {
                this.errorMessage = 'Please fill out all fields.';
                return;
            }
            if (isNaN(this.age) || this.age <= 18) {
                this.errorMessage = 'Age must be a number greater than 18.';
                return;
            }
            // Emit form data if validation passes
            this.$emit('submit', { name: this.name, age: this.age });
            this.resetForm();
        },
        resetForm() {
            this.name = '';
            this.age = null;
            this.errorMessage = '';
        }
    }
};
</script>

<style scoped>
.form {
    margin-bottom: 20px;
}

.form label {
    font-weight: bold;
}

.form input,
.form button {
    margin-bottom: 10px;
    padding: 8px 12px;
    font-size: 16px;
}

.form button {
    cursor: pointer;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 3px;
}

.form button:hover {
    background-color: #45a049;
}

.form .error {
    color: red;
    font-size: 14px;
}
</style>
