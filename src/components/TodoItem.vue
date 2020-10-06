<template>
    <li class="task" :class="{ done: task.completed }">
        <span class="task-text">{{ task.text }}</span>
        <span class="done-btn" @click="$emit('done-task', task.id)"></span>
        <span class="rem-btn" @click="$emit('remove-task', task.id)"></span>
    </li>
</template>

<script>
export default {
    props: {
        task: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>

.task {
    display: flex;
    align-items: center;
    padding: 10px;
    background-color: snow;
    margin-bottom: 5px;
    border: 1px solid gray;
    border-radius: 5px;
}

.task-text {
    margin-right: auto;
}

.done {
    text-decoration: line-through;
    opacity: 0.4;
}

.done-btn, .rem-btn {
    width: 16px;
    height: 16px;
    margin-right: 10px;
    background-image: url(../assets/images/check-mark.png);
    background-repeat: no-repeat;
    background-size: cover;
    cursor: pointer;
}

.rem-btn {
    background-image: url(../assets/images/delete.jpg);
}

.done-btn:hover, .rem-btn:hover {
    transform: scale(1.15);
    transition: 0.4s;
}

</style>