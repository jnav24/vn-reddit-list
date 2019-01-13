<template>
	<View>
		<Text>List Page</Text>
		<Button title="Go Back" :on-press="() => navigation.goBack()"></Button>
	</View>
</template>

<script>
	export default {
		props: {
			navigation: {
				type: Object,
			},
		},
	}
</script>
