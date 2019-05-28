<template>
  <div class="home">
      <AddTodo @add-todo="addTodo" />
      <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>

<script>
    import Todos from '@/components/Todos'
    import AddTodo from '@/components/AddTodo'

    export default {
        name: 'Home',
        components: {
            Todos, AddTodo
        },
        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: 'Todo One',
                        completed: false
                    },
                    {
                        id: 2,
                        title: 'Todo Two',
                        completed: true
                    },
                    {
                        id: 3,
                        title: 'Todo Three',
                        completed: false
                    },
                ]
            }
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id)
            },
            addTodo(newTodo) {
                this.todos = [...this.todos, newTodo]
            }
        }
    }
</script>
