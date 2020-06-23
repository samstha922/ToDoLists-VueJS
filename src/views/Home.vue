
<template>
  <div class="home">
    <Addtodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-td="deletetodo"/>
  </div>
</template>


<script>
import Todos from '../components/Todos';
import Addtodo from '../components/Addtodo';
import axios from 'axios';
export default {
  // name, methods, props, computed,data, el etc. can be exported
  name: 'Home',
  components: {
    Todos,
    Addtodo 
  },

  data(){
    return{
      todos:[]
    }
  },
// inbuilt fxn to load data at first
  created(){
      // console.log('fits');
      // axios to make server request and response; axios: promise based http client for the browser and nodejs
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response=> this.todos = response.data)
        .catch(err=> console.log(err));
  },

  methods:{
    deletetodo(object){
      console.log(object.id);
      var result = this.todos.filter(todo => todo.id !== object.id)
      console.log(result);
      axios.delete('https://jsonplaceholder.typicode.com/todos/'+object.id)
        .then(this.todos = this.todos.filter(todo => todo.id !== object.id))
        .catch(err => console.log(err));

      ////filter the contents to not include the deleted object
      //this.todos=this.todos.filter(todo => todo.id !== object.id);
    },

    addTodo(newtodo){

      const{ title, completed} = newtodo;

      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
      //// typescrippt .... spread operator to append new data in existing
     // this.todos = [...this.todos, newtodo];
    },

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>




