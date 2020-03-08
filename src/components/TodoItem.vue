<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed; // This allows us to toggle on/off completed
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #fafafa;
        padding: 10px;
        border-bottom: 1px #E1E1E1 solid;
        color: #737581;

    }

    .todo-item:hover {
        background: #E1E1E1;
    }

    .is-complete {
        text-decoration: line-through;
        color: #2AC27F;
    }

    .del {
        background: #F61067;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>