<template>
	<view class="container">
		<text class="text-color-primary">My Vue Native App</text>
		<View class="flex-container">
			<TextInput
				placeholder="Enter Channel"
				:style="{
					borderColor: 'grey',
					borderWidth: 0.5,
					height: 40,
					width: 150,
				}"
				v-model="search"/>
			<TouchableOpacity
				class="button"
				@press="getPosts()">
				<Text class="button-text">Login</Text>
			</TouchableOpacity>
		</View>

		<ScrollView :style="{
		  	width: '100%'}">
			<View
				class="list"
				v-for="(post, index) in posts"
				:key="index">
				<TouchableOpacity
					@press="handleListTap(post)"
					class="flex-container">
					<image
						:style="{
							borderRadius: 25,
							height: 50,
							marginRight: 8,
							width: 50,
						}"
						:source="{uri: post.data.thumbnail}"
					/>
					<Text>{{ post.data.title }}</Text>
				</TouchableOpacity>
			</View>
		</ScrollView>
	</view>
</template>

<script>
	export default {
		props: {
			navigation: {
				type: Object
			}
		},
		mounted() {
			this.search = 'kittens';
			this.getPosts();
		},
		data() {
			return {
				posts: [],
				search: '',
			}
		},
		methods: {
			handleListTap(post) {
				this.navigation.navigate("List", {
					post,
				});
			},
			getPosts() {
				const search = this.search.replace(/\s+/, '');
				this.search = '';

				fetch(`http://reddit.com/r/${search}.json`)
					.then(response => response.json())
					.then(data => {
						this.posts = data.data.children;
					})
			},
		},
	}
</script>

<style>
	.container {
		align-items: center;
		background-color: white;
		flex: 1;
		justify-content: center;
		padding-top: 15;
	}
	.button {
		background-color: #900;
		padding-bottom: 10;
		padding-left: 20;
		padding-right: 20;
		padding-top: 10;
	}
	.button-text {
		color: #fff;
	}
	.flex-container {
		align-content: center;
		align-items: center;
		flex-direction: row;
	}
	.list {
		border-bottom-width: 1;
		border-color: grey;
		padding: 15;
		width: 100%;
	}
	.text-color-primary {
		color: #900;
		font-size: 28;
		margin-bottom: 20;
	}
</style>
