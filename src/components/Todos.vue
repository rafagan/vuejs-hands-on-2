<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" @del-todo="$emit('del-todo', todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'

export default {
    name: 'Todos',
    props: ['todos'],
    components: {
        TodoItem
    }
}
</script>

<style scoped>

</style>