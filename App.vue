<template>
	<app-navigation></app-navigation>
</template>

<script>
	import { StackNavigator } from 'vue-native-router';
	import HomeScreen from './src/components/Home.vue';

	const AppNavigation = StackNavigator(
		{
			Home: HomeScreen,
		},
		{
			initialRouteName: 'Home',
		}
	);

	export default {
		components: { AppNavigation }
	}
</script>
