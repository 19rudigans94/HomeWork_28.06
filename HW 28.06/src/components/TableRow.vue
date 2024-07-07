<template>
    <tr class="table-row">
        <td>
            <input v-model="editedData.name" type="text" :disabled="!editing">
        </td>
        <td>
            <input v-model.number="editedData.age" type="number" :disabled="!editing">
        </td>
        <td>
            <button @click="toggleEdit">{{ editing ? 'Save' : 'Edit' }}</button>
        </td>
    </tr>
</template>

<script>
export default {
    name: 'TableRow',
    props: {
        rowData: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            editing: false,
            editedData: { ...this.rowData }
        };
    },
    methods: {
        toggleEdit() {
            if (this.editing) {
                // Save changes
                this.$emit('save', this.editedData);
            }
            this.editing = !this.editing;
        }
    }
};
</script>

<style scoped>
.table-row {
    margin-bottom: 10px;
}

.table-row input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
}

.table-row td,
.table-row th {
    padding: 10px;
    text-align: left;
    border: 1px solid #ccc;
}

.table-row button {
    padding: 8px 12px;
    font-size: 14px;
    cursor: pointer;
    background-color: #2196F3;
    color: white;
    border: none;
    border-radius: 3px;
}

.table-row button:hover {
    background-color: #1976D2;
}
</style>
