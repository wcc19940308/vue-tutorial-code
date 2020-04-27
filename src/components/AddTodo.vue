<template>
    <dir>
        <!-- 阻止表单默认行为，并使用addTodo-->
        <form @submit.prevent="addTodo">
            <!-- v-model这里用于数据绑定 -->
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </dir> 
</template>

<script>
// import uuid from "uuid"
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
            // e.preventDefault();
            const newTodo = {
                // id: uuid.v4(),
                title: this.title,
                completed: false
            }
            // Send to parent and carry the argument newTodo
            this.$emit('add-todo', newTodo);
            this.title = ''
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>