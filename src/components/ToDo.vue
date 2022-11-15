
<template>
    <h1>TODO LIST</h1>
  <form @submit.prevent>

    <label>Enter Your Task:</label>
    <input type="text" v-model="todoList" @keyup="addTodo">
    <div v-for="todo in todos" :key="todo" class="test">
    <input type="checkbox">
     <strong>{{ todo }}</strong>
     <img @click="deletetodo(todo)" src="../assets/delete.png" alt="">
    </div>

  </form>
</template>

<script>
export default {
    data() {
        return {
            todoList: '',
            todos: [],
        }
    },
    methods: {
        addTodo(e) {
           if (e.key === 'Enter' && this.todoList) {
            if (!this.todos.includes(this.todoList)) {
                this.todos.push(this.todoList)
            }
            this.todoList = ''
           }
        },
        deletetodo(todo) {
            this.todos = this.todos.filter((item) => {
                return todo != item
            })
        },
        
    }
}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    -webkit-box-shadow: 0px 3px 6px -1px rgba(0,0,0,0.75);
-moz-box-shadow: 0px 3px 6px -1px rgba(0,0,0,0.75);
box-shadow: 0px 3px 6px -1px rgba(0,0,0,0.75);
}
label {
    color: rgb(0, 0, 0);
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.test{
    width: 95%;
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
    position: relative;
}
.test img{
    width: 4%;
    position: absolute;
    right: 20px;
    top: 6px;
}

</style>
