<template>
	<AppHeaderTodo />
	<AppFiltersTodo :active-filter="activeFilter" @set-filter="setFilter"  />
	<main class="app-main">
		<AppListTodo :todos="filetredTodos" @toggle-todo="toggleTodo" @remove-todo="removeTodo" />
		<AppAddTodo @add-todo="addTodo" />
	</main>
	<AppFooterTodo :remaining-count="remainingTodosCount" :completed-count="completedTodosCount" />
</template>

<script lang="ts">
	import { defineComponent } from 'vue'
	import { AppAddTodo, AppFiltersTodo, AppHeaderTodo, AppListTodo, AppFooterTodo } from '../components/todos'
	import { Todo } from '@/types/Todo'
	import { Filter } from '@/types/Filter'

	interface state {
		todos: Todo[],
		activeFilter: Filter
	}
	export default defineComponent({
		components: {
			AppAddTodo,
			AppFiltersTodo,
			AppHeaderTodo,
			AppListTodo,
			AppFooterTodo
		},
		data(): state {
			return {
				todos: [
					{ id: 0, text: 'Learn the basics of Vue', completed: true },
					{ id: 1, text: 'Learn the basics of Typescript', completed: false },
					{ id: 2, text: 'oskaldev', completed: false },
				],
				activeFilter: 'All'
			}
		},
		computed: {
			filetredTodos(): Todo[] {
				switch (this.activeFilter) {
					case 'Active':
						return this.todos.filter(todo => !todo.completed)
					case 'Done':
						return this.todos.filter(todo => todo.completed)
					case 'All':
					default:
						return this.todos
				}
			},
			completedTodosCount(): number {
				return this.todos.filter(todo => todo.completed).length
			},
			remainingTodosCount(): number {
				return this.todos.filter(todo => !todo.completed).length
			}
		},
		methods: {
			addTodo(todo: Todo) {
				this.todos.push(todo)
			},
			toggleTodo(id: number) {
				const targetTodo = this.todos.find((todo: Todo) => todo.id === id)
				if (targetTodo) {
					targetTodo.completed = !targetTodo.completed
				}
			},
			removeTodo(id: number) {
				this.todos = this.todos.filter((todo: Todo) => todo.id !== id)
			},
			setFilter(filter: Filter) {
				this.activeFilter = filter
			}
		}
	})
</script>

<style scoped></style>