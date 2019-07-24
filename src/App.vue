<template>
  <div id="app">
    <Header />
    <SearchBar  v-on:todo-submitted="addTodo" v-bind:todos="todos"  />
    <TodoList v-bind:todos="todos" v-on:remove-todo=removeTodo(todos.id) />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import TodoList from './components/Todo-List.vue'
import SearchBar from './components/Search-Bar.vue'

export default {
  name: 'app',
  components: {
    Header,
    SearchBar,
    TodoList
  }, 
  data(){
      // let newToDo = {
      //           id: Number,
      //           completed: false,
      //           title: String
      //       }

    return {
      todos: []
    }
  },
  methods: {
    removeTodo(id) {
      // eslint-disable-next-line
      console.log('The delete button has been clicked')
        // eslint-disable-next-line
        console.log(this.todos.id)
      // console.log(this.todos)
      return this.todos.splice(id, 1)
    },
    addTodo(ToDo){
      // eslint-disable-next-line
      console.log('The add ToDo submit button was clicked')
      // For Debugging purposes 
      // console.log(ToDo);
      fetch("https://jsonplaceholder.typicode.com/todos/", {
      method: 'post',
      headers: {'Content-Type': 'application/json; charset=UTF-8 '},
      body: JSON.stringify(ToDo)
    })
      .then((response) => {
        // console.log(response)
        return response.json()
      }).then(res => console.log(res))
      .catch(error => console.error('Error:', error));
      return this.todos.push(ToDo)
    }
  },
   mounted: function() {
    fetch("https://jsonplaceholder.typicode.com/todos/?_limit=5", {
      method: 'get'
    })
      .then((response) => {
        // console.log(response.json())
        return response.json()
      })
      .then((jsonData) => { return this.todos = jsonData })
  }
}
</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.4;
  /* color: #2c3e50; */
}

</style>
