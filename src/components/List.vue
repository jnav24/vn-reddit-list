<template>
	<View>
		<Image
			:style="{height: '100%', width: '100%'}"
			:source="{uri: decodeUrl(navigation.getParam('imageSrc')) }" />
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
		data() {
			return {
				image: {uri: decodeURI(this.navigation.getParam('imageSrc'))},
			};
		},
		methods: {
			decodeUrl(val) {
				return decodeURI(val).replace(new RegExp('&amp;', 'g'), '&');
			}
		},
	}
</script>
