<template>
  <div class="parent-component">
    <h2>Parent Component</h2>

    <div>
      <h3>Counter</h3>
      <counter @reset="handleReset"></counter>
    </div>

    <div>
      <h3>Text Display</h3>
      <text-display :initialText="displayText" ref="textDisplay"></text-display>
      <div>
        <input type="text" v-model="inputText">
        <button @click="updateText">Обновить текст</button>
      </div>
    </div>

    <div>
      <h3>Task List</h3>
      <div v-for="(task, index) in tasks" :key="index">
        <task-item :task="task" @delete="handleDeleteTask(index)"></task-item>
      </div>
    </div>

    <div>
      <h3>Form Submission</h3>
      <Form></Form>
    </div>

    <div>
      <h3>Table</h3>
      <table class="table">
        <thead>
          <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <table-row v-for="(item, index) in tableData" :key="item.id" :row-data="item.data"
            @edit="handleEditRow(index)"></table-row>
        </tbody>
      </table>
    </div>

    <div>
      <h3>Dynamic Components</h3>
      <dynamic-components></dynamic-components>
    </div>

    <div>
      <h3>Filter-Sort List</h3>
      <filter-sort-list></filter-sort-list>
    </div>

  </div>
</template>

<script>
import Counter from './components/Counter.vue';
import TextDisplay from './components/TextDisplay.vue';
import TaskItem from './components/TaskItem.vue';
import TableRow from './components/TableRow.vue';
import DynamicComponents from './components/DynamicComponents.vue';
import FilterSortList from './components/FilterSortList.vue';
import Form from './components/Form.vue';

export default {
  components: {
    Counter,
    TextDisplay,
    TaskItem, 
    TableRow,
    DynamicComponents,
    FilterSortList,
    Form
  },
  data() {
    return {
      displayText: 'Initial Text',
      inputText: '',
      tasks: ['Task 1', 'Task 2', 'Task 3'],
      tableData: [
        { id: 1, data: { name: 'Alice', age: 25 } },
        { id: 2, data: { name: 'Bob', age: 30 } },
        { id: 3, data: { name: 'Charlie', age: 20 } },
        { id: 4, data: { name: 'David', age: 35 } },
        { id: 5, data: { name: 'Eve', age: 40 } },
        { id: 6, data: { name: 'Frank', age: 45 } },
      ],
      formData: {
        name: '',
        age: null
      },
      errorMessage: ''
    };
  },
  methods: {
    handleReset() {
      console.log('Counter has been reset');
    },
    handleDeleteTask(index) {
      this.tasks.splice(index, 1);
    },
    handleFormSubmit() {
      if (this.formData.name && this.formData.age) {
        console.log('Form submitted with:', this.formData);
      } else {
        this.errorMessage = 'Пожалуйста, заполните все поля формы';
      }
    },
    handleEditRow(index) {
      console.log('Edit row with index:', index);
    },
    updateText() {
      this.displayText = this.inputText;
      this.$refs.textDisplay.updateText(this.inputText);
      this.inputText = '';
    }
  }
};
</script>

<style scoped>
.parent-component {
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
}

.parent-component h2 {
  font-size: 24px;
  margin-bottom: 20px;
}

.parent-component .table {
  margin-top: 20px;
  width: 100%;
  border-collapse: collapse;
}

.parent-component th,
.parent-component td {
  padding: 10px;
  text-align: left;
  border: 1px solid #ccc;
}

.parent-component button {
  padding: 8px 12px;
  font-size: 16px;
  cursor: pointer;
  background-color: #2196F3;
  color: white;
  border: none;
  border-radius: 3px;
}

.parent-component button:hover {
  background-color: #1976D2;
}

.error {
  color: red;
  font-size: 14px;
}
</style>

