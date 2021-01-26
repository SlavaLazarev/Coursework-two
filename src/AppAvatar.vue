<template>
	<div v-for="avatar in avatars" :key="avatar" class="avatar" >
		<img :src="avatar.avatars">
	</div>
</template>

<script>
export default {
	props: ['avatars']
}
</script>

<style scoped>
	.avatar {
		display: flex;
		justify-content: center;
	}

	.avatar img {
		width: 150px;
		height: 150px;
		border-radius: 50%;
	}
</style>