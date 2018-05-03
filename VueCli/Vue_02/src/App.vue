<template>
    <div id='app'>
      <TodoHeader></TodoHeader>
      <TodoInput  v-on:addTodo="addTodo" ></TodoInput>
      <TodoList   v-bind:test="todoItems"></TodoList>
      <TodoFooter v-on:clearAll="clearAll"></TodoFooter>
    </div>
</template>

<script>
  import  TodoFooter from './Componenets/TodoFooter.vue'
  import  TodoList   from './Componenets/TodoList.vue'
  import  TodoHeader from './Componenets/TodoHeader.vue'
  import  TodoInput  from './Componenets/TodoInput.vue'

  export default{
    data(){
        return {
            todoItems : []
        }
    },
    created() {
        if(localStorage.length > 0 ) {
            for(var i = 0 ; i <localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    methods:{
        addTodo(value){
            localStorage.setItem(value,value);
            this.todoItems.push(value);
        },
        clearAll () {
            localStorage.clear();
            this.todoItems = [];
        }

    },
    components :{
      'TodoHeader': TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList'  : TodoList,
      'TodoFooter': TodoFooter
    }
  }
</script>

<style>
    body{
        text-align: center;
        background-color: #F6F6F8;
    }
    input {
        border-style: groove;
        width:  200px;
    }
    button {
        border-style: groove;
    }
    .shadow{
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
    }
</style>