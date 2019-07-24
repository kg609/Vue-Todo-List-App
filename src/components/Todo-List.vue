<template>
    <div>
        <div>
            <h2>Add items that you need to do your list</h2>
        </div>
        <div class="list">
            
            <ul class="list-items" v-for="todo in todos" v-bind:key="todo.id">
                <input type="checkbox" />
                <li v-bind:class="{'isChecked':todo.completed}"> {{todo.title}} </li>
                <button v-on:click="removeTodos()" class="delete">X</button>
            </ul>
            
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TodoList',
        props: ["todos"],
        methods: {
            // Send up to parent element
            removeTodos(){
                this.$emit('remove-todo')
            }
        }
    }
</script>

<style scoped>

h2 {
    text-align: center;
}

 .list {
     /* border: 1px solid black; */
     height: auto;
     width: 100%;
     max-width: 900px;
     margin: 20px auto;
     border: 1px solid gray;
 }

.list-items {
    display: flex;
    list-style-type: none;
    padding: 10px 20px;
    background: #2c3e50;
    border-bottom: 1px solid #ddd;
    color: #ddd;
}

.list-items:hover {
    opacity: .6;
}

input[type="checkbox"] {
    margin-right: 10px;   
}

.isChecked {
    text-decoration: line-through;
}

.delete {
    padding: 3px 5px;
    border-radius: 50%;
    background: red;
    color: #FFF;
    border-color: red;
    margin: 0 10px;
}



</style>