<template>
    <div class="container">
        <h1 class="title">Todo List</h1>
        <div id="input">
            <input v-model="newTodo" placeholder="Add new todo">
            <button v-on:click="addTodo" class="add">Add</button>
        </div>

        <div id="list">
            <ol>
                <li v-for="todo in todos" :key="todo">
                    {{ todo }}
                </li>
            </ol>
        </div>

        <h3>{{countTodos}}</h3>
    </div>
</template>

<script>
export default {
    name: "TodoList",
    data() {
        return {
            newTodo: "",
            todos: []
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim() === "") {
                alert("Please enter a todo!");
            } else if (this.todos.includes(this.newTodo)) {
                alert("Todo already exists!")
            } else {
                this.todos.push(this.newTodo);
                this.newTodo = "";
            }
        },
    },
    computed: {
        countTodos: function() {
            if (this.todos.length == 0) {
                return 'No Todo List';
            } else if (this.todos.length >= 4) {
                return 'Hebat!';
            } else {
                return '';
            }
        }
    }
}
</script>

<style scoped>
.title {
    text-align: center;
}

.container {
    width: 500px;
    margin: 0 auto;
    border: 1px solid #ccc;
    padding: 10px;
}

#input {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}

#input input {
    width: 80%;
    padding: 5px;
    border: 1px solid #ccc;
}

#input button {
    width: 18%;
    padding: 5px;
    border: 1px solid #ccc;
    cursor: pointer;
}

.add {
    background-color: #4CAF50;
    color: white;
}

button:hover {
    background-color: #3b883d;
}

#list ol li{
    font-size: large;
}

h3 {
    text-align: center;
}
</style>
