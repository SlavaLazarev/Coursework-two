<template>
	<div v-for="title in titles" :key="title" >
		<div>
			<h1>{{title.titles}}</h1>
		</div>
	</div>
</template>

<script>
export default {
	props: ['titles'],
}
</script>



<!-- <h3>{{block.subtitle}}</h3>
<div class="avatar">
<img :src="block.avatar" alt="img"/>
</div>
<p>{{block.text}}</p> -->