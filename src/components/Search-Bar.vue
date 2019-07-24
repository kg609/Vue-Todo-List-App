<template>
  <div class="searchBar" >
      <form v-on:submit.prevent="onSubmit()">
        <input type="text" placeholder="Add to do..."  v-model="title" >

        <input type="submit" value="Submit"  class="btn" />
      </form>
  </div>
</template>

<script>
// import uuid from 'uuid';

    export default {
        name: 'SearchBar',
        // props: ["title","id"],
        data(){
            let ToDo = {
                // id: 0,
                // completed: false,
                title: ''
            }
            return ToDo
        },
        methods: {
            onSubmit() {
                let ToDo = {
                    // id: this.id,
                    completed: false,
                    title: this.title,
                    userId: 1
                }
                // Send to Parent Element
                this.$emit('todo-submitted', ToDo)
                // this.id+=1
                this.title = '' 
                // return ToDo
            }
            // addTodo();

        }
    }
</script>

<style scoped>
form {
    display: flex;
    margin: 20px auto;
    width: 100%;
    max-width: 900px; 
}

input[type="text"] {
    width:100%;
    padding: 10px 20px;
    border: 1px solid #000;
}

input[type="submit"] {
    padding: 10px 50px;
    color: #FFF;
    background: #2c3e50;
    border: 1px solid #2c3e50;
}

input[type="submit"]:hover {
    color: #FFF;
    opacity: .6;
    transition: all .3s ease-in-out;
    cursor: pointer;
}

</style>