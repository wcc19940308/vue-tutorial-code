<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <!-- 调用props中的todo的成员 -->
            <!-- <h3>{{todo.title}}</h3> -->

            <!-- 将v-for中的todo绑定至TodoItem的属性todo中 -->
            <!-- 在这里捕获TodoItem传递的del-todo事件，继续向上传递 -->
            <TodoItem v-bind:todo="todo" 
            v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>    
</template>

<script>

import TodoItem from "./TodoItem"

export default {
    name: "Todos",
    props: ["todos"],
    components: {
        TodoItem
    }
}
</script>

<style scoped>

</style>