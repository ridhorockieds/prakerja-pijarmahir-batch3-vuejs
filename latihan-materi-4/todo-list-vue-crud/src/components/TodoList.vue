<template>
    <div class="container">
        <div class="row">
        <div class="col-md-6 offset-md-3">
            <h1 class="text-center">Todo List</h1>
            <hr />
            <div id="input">
                <input type="text" class="form-control" placeholder="Add a Todo" v-model="newTodo" />
                <button class="btn btn-success" @click="addTodo">Add</button>
                <!-- <ButtonComp class="btn btn-success" @click="addTodo" type="Add"></ButtonComp> -->
            </div>
            <hr />
            <ol>
                <li v-for="(todo, index) in todos" :key="index">
                    <div class="todos">
                        {{ todo }}
                        <div class="action">
                            <!-- Button Biasa -->
                            <button class="btn btn-warning" @click="editTodo(index)">Edit</button>
                            <button class="btn btn-danger" @click="deleteTodo(index)">Delete</button>
                            <!-- Button Component -->
                            <!-- <ButtonComp class="btn btn-warning" @click="editTodo" type="Edit"></ButtonComp>
                            <ButtonComp class="btn btn-danger" @click="deleteTodo" type="Delete"></ButtonComp> -->
                        </div>
                    </div>
                </li>
            </ol>
            <h3 class="text-center">{{message}}</h3>
            <hr />
        </div>
        </div>
    </div>
</template>

<script>
// import ButtonComp from "./ButtonComp.vue";

export default {
    components: {
        // ButtonComp
    },

    name: "TodoList",
    data() {
        return {
            editedIndex: -1,
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
        editTodo(index) {
            this.editedIndex = index;
            this.newTodo = this.todos[index];
        },
        updateTodo() {
            this.todos[this.editedIndex] = this.newTodo;
            this.newTodo = "";
            this.editedIndex = -1;
        },
        deleteTodo(index) {
            if(confirm("Are you sure want to delete this todo?")) {
                this.todos.splice(index,1);
            }
        }
    },
    computed: {
        message: function() {
            if (this.todos.length == 0) {
                return 'No Todo List';
            } else if (this.todos.length >= 4) {
                return 'Hebat!';
            } else {
                return '';
            }
        }
    }
};
</script>

<style scoped>
.container {
    margin:  0 auto;
    max-width: 1024px;
}

hr {
    margin: 20px 0;
}

.text-center {
    text-align: center;
}

#input {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

#input input {
    width: 100%;
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

.list-group-item {
    width: 100%;
}

.btn {
    margin: 0 5px;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
    border: 1px solid #ccc;
}

.btn-success {
    background-color: #28a745;
    color: #fff;
}

.btn-success:hover {
    background-color: #218838;
    color: #fff;
}

.btn-danger {
    background-color: #dc3545;
    color: #fff;
}

.btn-danger:hover {
    background-color: #c82333;
    color: #fff;
}

.btn-warning {
    background-color: #ffc107;
    color: #fff;
}

.btn-warning:hover {
    background-color: #e0a800;
    color: #fff;
}

.todos {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}

.action {
    display: flex;
    justify-content: space-between;
    align-items: center;
}




</style>