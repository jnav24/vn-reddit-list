<template>
	<ScrollView :style="{width: '100%'}">
		<View>
			<Image
				v-if="typeof post.data.preview.images[0].source.url !== 'undefined'"
				:style="{height: '100%', width: '100%'}"
				:source="{uri: decodeUrl(post.data.preview.images[0].source.url) }" />
			<!--<Text>{{ post.data.title }}</Text>-->
			<!--<Button title="Go Back" :on-press="() => navigation.goBack()"></Button>-->
		</View>
	</ScrollView>
</template>

<script>
	export default {
		props: {
			navigation: {
				type: Object,
			},
		},
		created() {
			this.post = this.navigation.getParam('post');
		},
		data() {
			return {
				post: {},
			};
		},
		methods: {
			decodeUrl(val) {
				return decodeURI(val).replace(new RegExp('&amp;', 'g'), '&');
			}
		},
	}
</script>
