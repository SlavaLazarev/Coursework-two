<template>
		<div v-for="subtitle in subtitles" :key="subtitle" >
				<h3>{{subtitle.subtitles}}</h3>
		</div>
</template>
	
	<script>
	export default {
		props: ['subtitles']
	}
	</script>
	