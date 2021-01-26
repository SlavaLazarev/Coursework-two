<template>
	<div v-for="text in texts" :key="text">
		<p>{{text.texts}}</p>
	</div>
</template>

<script>
export default {
	props: ['texts']
}
</script>