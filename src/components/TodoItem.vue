<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <!-- <p>Todo Item</p> -->
        <!-- 调用props中的todo的成员 -->
        <p>{{todo.title}}
            <input type="checkbox" v-on:change="markComplete" />
            <!-- 点击时会通过emit触发del-to事件，并鞋带上todo.id -->
            <button @click="$emit('del-todo', todo.id)" 
            class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    // 添加属性
    props: ["todo"],
    methods: {
        markComplete() 
        {
            this.todo.completed = !this.todo.completed
        }
    }    
}
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>