<template>
  <div class="home">
      <AddTodo @add-todo="addTodo" />
      <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
    import Todos from '@/components/Todos'
    import AddTodo from '@/components/AddTodo'
    import axios from 'axios'

    export default {
        name: 'Home',
        components: {
            Todos, AddTodo
        },
        data() {
            return {
                todos: []
            }
        },
        methods: {
            deleteTodo(id) {
                axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                     .then(_ => this.todos = this.todos.filter(todo => todo.id !== id))
                     .catch(err => console.log(err));
            },
            addTodo(newTodo) {
                const { title, completed } = newTodo;

                axios.post('https://jsonplaceholder.typicode.com/todos', {
                    title,
                    completed
                }).then(res => res.data)
                  .then(todo => this.todos = [...this.todos, todo])
                  .catch(err => console.log(err));
            }
        },
        created() {
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(res => res.data)
                .then(todos => this.todos = todos)
                .catch(err => console.log(err));
        }
    }
</script>
