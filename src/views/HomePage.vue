<template>
	<AppHeaderTodo />
	<AppFiltersTodo />
	<main class="app-main">
		<AppListTodo />
		<AppAddTodo />
	</main>
	<AppFooterTodo />
</template>

<script lang="ts">
	import { defineComponent } from 'vue'
	import { AppAddTodo, AppFiltersTodo, AppHeaderTodo, AppListTodo, AppFooterTodo } from '../components/todos'

	export default defineComponent({
		components: {
			AppAddTodo,
			AppFiltersTodo,
			AppHeaderTodo,
			AppListTodo,
			AppFooterTodo
		},
	})
</script>

<style scoped></style>