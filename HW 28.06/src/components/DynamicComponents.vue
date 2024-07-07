<template>
    <div class="dynamic-components">
        <button @click="addComponent">Add Component</button>
        <button @click="removeComponent">Remove Component</button>
        <div v-for="component in components" :key="component.id" class="component">
            <component :is="component.type" @deleteComponent="deleteComponent(component.id)"></component>
        </div>
    </div>
</template>

<script>
import Counter from './Counter.vue';
import TextDisplay from './TextDisplay.vue';
import Task from './TaskItem.vue';
import Form from './Form.vue';
import TableRow from './TableRow.vue';

let nextId = 1;

export default {
    data() {
        return {
            components: []
        };
    },
    methods: {
        addComponent() {
            const randomType = Math.floor(Math.random() * 5) + 1;
            let newComponent;
            switch (randomType) {
                case 1:
                    newComponent = { id: nextId++, type: 'Counter' };
                    break;
                case 2:
                    newComponent = { id: nextId++, type: 'TextDisplay', props: { initialText: 'Initial Text' } };
                    break;
                case 3:
                    newComponent = { id: nextId++, type: 'Task', props: { task: 'New Task' } };
                    break;
                case 4:
                    newComponent = { id: nextId++, type: 'Form' };
                    break;
                case 5:
                    newComponent = { id: nextId++, type: 'TableRow', props: { data: { name: 'John Doe', age: 30 } } };
                    break;
                default:
                    break;
            }
            this.components.push(newComponent);
        },
        removeComponent() {
            if (this.components.length > 0) {
                this.components.pop();
            }
        },
        deleteComponent(id) {
            this.components = this.components.filter(comp => comp.id !== id);
        }
    },
    components: {
        Counter,
        TextDisplay,
        Task,
        Form,
        TableRow
    }
};
</script>

<style scoped>
.dynamic-components {
    margin-bottom: 20px;
}

.dynamic-components button {
    margin-right: 10px;
    padding: 8px 12px;
    font-size: 16px;
    cursor: pointer;
    background-color: #9C27B0;
    color: white;
    border: none;
    border-radius: 3px;
}

.dynamic-components button:hover {
    background-color: #7B1FA2;
}

.dynamic-components .component {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f0f0f0;
}
</style>
