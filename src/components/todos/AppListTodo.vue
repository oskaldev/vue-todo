<template>
	<ul class="todo-list">
		<AppItemTodo v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-todo="toggleTodo" @remove-todo="removeTodo" />
	</ul>
</template>
<script lang="ts">
	import { defineComponent } from 'vue'
	import AppItemTodo from './AppItemTodo.vue'
	import { Todo } from '@/types/Todo'

	interface state {
		todos: Todo[]
	}

	export default defineComponent({
		components: {
			AppItemTodo
		},
		data(): state {
			return {
				todos: [
					{ id: 0, text: 'Learn the basics of Vue', completed: true },
					{ id: 1, text: 'Learn the basics of Typescript', completed: false },
					{ id: 2, text: 'oskaldev', completed: false },
				]
			}
		},
		methods: {
			toggleTodo(id: number) {
				const targetTodo = this.todos.find((todo: Todo) => todo.id === id)
				if (targetTodo) {
					targetTodo.completed = !targetTodo.completed
				}
			},
			removeTodo(id: number) {
				this.todos = this.todos.filter((todo: Todo) => todo.id !== id)
			},
		},
	})
</script>

<style scoped></style>