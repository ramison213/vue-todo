<template>
    <div class="wrapper">
        <h1>TODO LIST (VUE)</h1>
        <add-task
            @write-name-task="createTask"
        />
        <todo-list
            :tasks="tasks"
            @remove-task="removeTask"
            @done-task="doneTask"
        />

        <p v-if="!tasks.length" class="empty-list">No tasks yet</p>
    </div>
</template>

<script>

import TodoList from '@/components/TodoList'
import AddTask from '@/components/AddTask'

export default {
    components: { TodoList, AddTask },

    data: function () {
        return {
            tasks: []
        }
    },

    methods: {
        removeTask(id) {
            this.tasks = this.tasks.filter(task => task.id != id)
        },

        doneTask(id) {
            this.tasks.forEach(task => {
                if(task.id == id) {
                    task.completed = !task.completed
                }
            })
        },

        createTask(text) {
            let newTask = {
                id: Date.now(),
                text: text,
                completed: false
            }

            this.tasks.push(newTask)
        }
    }
}
</script>

<style>

* {
    box-sizing: border-box;
}

ul {
    list-style: none;
    padding: 0;
}

body {
    font-family: Verdana;
    margin: 0;
}

h1 {
    text-align: center;
}

.wrapper {
    width: 520px;
    margin: 0 auto;
    padding: 0 10px;
}

.hide .done {
    display: none !important;
}

.empty-list {
    text-align: center;
    padding: 15px 0;
    color: #ccc;
    font-size: 1.5rem;
    border-radius: 5px;
    border: 1px solid gray;
    margin: 16px 0;
}

</style>