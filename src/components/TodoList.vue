<template>
    <ul class="tasks-list">
        <todo-item 
            v-for="(task, index) in tasks"
            :key="index"
            :task="task"
            @remove-task="removeTask"
            @done-task="doneTask"
        />
    </ul>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
    components: { TodoItem },

    props: {
        tasks: {
            type: Array,
            required: true
        }
    },

    methods: {
        removeTask(id) {
            this.$emit('remove-task', id)
        },
        doneTask(id) {
            this.$emit('done-task', id)
        },


    }
}

</script>

<style scoped>


</style>