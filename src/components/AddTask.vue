<template>
    <div class="flex-container">
        <div class="input-wrap">
            <input placeholder="Enter new task" v-model="text" />
            <label
                for="new-task"
                class="input-warning"
                ref="warning"
            >* обязательное поле</label>
        </div>
        <button class="btn" @click="createTask">ADD</button>
        <button class="btn hide-btn" @click="hideTasks" ref="hideBtn"></button>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            text: ''
        }
    },

    methods: {
        createTask: function() {
            if(this.text.trim()) {
                this.$refs.warning.style = 'display:none';
                this.$emit('write-name-task', this.text);
                this.text = '';
            } else {
                this.$refs.warning.style = 'display:block';
            }
        },

        hideTasks: function() {
            document.querySelector('.tasks-list').classList.toggle('hide');
            this.$refs.hideBtn.classList.toggle('hide-btn-active');
        }
    }
}
</script>

<style scoped>

.flex-container {
    display: flex;
    justify-content: space-between;
}

.input-warning {
    display: none;
    font-size: 12px;
    padding: 10px;
    color: red;
}

.input-wrap {
    width: 67%;
    display: inline-block;
    vertical-align: top;
}

input,
button {
    height: 46px;
    font-family: inherit;
    font-size: 18px;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid gray;
}

input {
    width: 100%;
}

.btn {
    width: 20%;
    cursor: pointer;
    vertical-align: top;
    background-color: lightgray;
}

.hide-btn {
    width: 10%;
    background-image: url(../assets/images/eye.png);
    background-repeat: no-repeat;
    background-size: 35px 25px;
    background-position: center;
}

.hide-btn-active {
    opacity: 0.4;
}

</style>