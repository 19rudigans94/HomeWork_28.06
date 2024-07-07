<template>
    <div class="filter-sort-list">
        <div class="filters">
            <label>Filter by Name:</label>
            <input type="text" v-model="filterName">
        </div>
        <div class="filters">
            <label>Sort by:</label>
            <select v-model="sortBy">
                <option value="name">Name</option>
                <option value="age">Age</option>
            </select>
        </div>
        <ul class="list">
            <li v-for="item in filteredList" :key="item.id" class="list-item">
                {{ item.name }} - {{ item.age }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            list: [
                { id: 10, name: 'Jack', age: 65 },
                { id: 13, name: 'Mallory', age: 80 },
                { id: 14, name: 'Nancy', age: 85 },
                { id: 3, name: 'Charlie', age: 20 },
                { id: 4, name: 'David', age: 35 },
                { id: 5, name: 'Eve', age: 40 },
                { id: 6, name: 'Frank', age: 45 },
                { id: 11, name: 'Kate', age: 70 },
                { id: 8, name: 'Henry', age: 55 },
                { id: 12, name: 'Luke', age: 75 },
                { id: 7, name: 'Grace', age: 50 },
                { id: 2, name: 'Bob', age: 30 },
                { id: 9, name: 'Isaac', age: 60 },
                { id: 1, name: 'Alice', age: 25 },
            ],
            filterName: '',
            sortBy: 'name'
        };
    },
    computed: {
        filteredList() {
            let filtered = this.list;
            if (this.filterName) {
                filtered = filtered.filter(item => item.name.toLowerCase().includes(this.filterName.toLowerCase()));
            }
            return filtered.sort((a, b) => {
                if (this.sortBy === 'name') {
                    return a.name.localeCompare(b.name);
                } else if (this.sortBy === 'age') {
                    return a.age - b.age;
                }
                return 0;
            });
        }
    }
};
</script>

<style scoped>
.filter-sort-list {
    margin-bottom: 20px;
}

.filter-sort-list .filters {
    margin-bottom: 10px;
}

.filter-sort-list label {
    margin-right: 10px;
}

.filter-sort-list select,
.filter-sort-list input {
    padding: 8px 12px;
    font-size: 16px;
}

.filter-sort-list ul {
    list-style-type: none;
    padding: 0;
}

.filter-sort-list .list-item {
    margin-bottom: 5px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f0f0f0;
}

.filter-sort-list .list-item:hover {
    background-color: #e0e0e0;
}
</style>
