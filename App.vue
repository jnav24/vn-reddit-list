<template>
	<app-navigation></app-navigation>
</template>

<script>
	import { StackNavigator } from 'vue-native-router';
	import HomeScreen from './src/components/Home.vue';
	import ListScreen from './src/components/List.vue';

	const AppNavigation = StackNavigator(
		{
			Home: HomeScreen,
			List: ListScreen,
		},
		{
			initialRouteName: 'Home',
		}
	);

	export default {
		components: { AppNavigation }
	}
</script>
