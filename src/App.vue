<template>
  <div id="app">
    <p class="head">
      <Header/>
    </p>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos= "todos" v-on:del-todo= "deleteTodo"/>
    <footer><Footer/></footer>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import axios from 'axios'
import Footer from './components/layout/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
    Footer
  },
  data(){
    return{
      todos: []
    }
  },
  methods:{
    deleteTodo(id){
      this.todos= this.todos.filter(todo=> todo.id !== id);

    },
    addTodo(newTodo){
      if (newTodo.title=="") {
        alert
      }
      this.todos = [...this.todos, newTodo]
    }
  },
  created(){
    axios.get('http://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res=> this.todos= res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.7;
  
}

.btn{
  
  border: none;
  background: #555;
  color: #fff;
  padding: 8px 434px;
  cursor: pointer;
  
}

.btn:hover{
  background: #666;
}
.head{
  background: #333;
  color: #fff;
  padding: 10px;
}

 

</style>
