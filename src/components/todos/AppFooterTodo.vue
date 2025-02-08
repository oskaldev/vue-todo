<template>
	<footer class="app-footer">осталось сделать еще {{ remainingCount }}, сделано {{ completedCount }}</footer>
</template>
<script lang="ts">
	import { defineComponent } from 'vue'

	export default defineComponent({
		props: {
			remainingCount: Number,
			completedCount: Number
		}
	})
</script>