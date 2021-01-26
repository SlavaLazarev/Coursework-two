<template>
	<div class="container">
		<p v-if="comment.length === 0">
			<button class="btn primary" @click="$emit('load')">Загрузить комментарии</button>
		</p>
		<div class="card" v-else-if="comment.length > 0">
			<h2>Комментарии</h2>
			<ul class="list">
				<li class="list-item" v-for="com in comment" :key="com">
					<div>
						<p><strong>{{com.email}}</strong></p>
						<small>{{com.body}}</small>
					</div>
				</li>
			</ul>
		</div>
		</div>
</template>

<script>
export default {
	emits:['load'],
	props: ['comment']
	}
</script>

<style scoped>

</style>