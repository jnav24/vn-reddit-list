<template>
  <view class="container">
      <text class="text-color-primary">My Vue Native App</text>
      <TextInput
          :style="{
              borderColor: 'grey',
              borderWidth: 1,
              height: 40,
              width: 150,
          }"
          v-model="search"/>
	  <Button
		  @press="buttonEvent()"
	  	  title="Click me"
	      color="#841584"
	      accessibility-label="Learn more about this button"/>
	  <TouchableOpacity
		  class="button"
		  @press="buttonEvent()">
		  <Text class="button-text">Login</Text>
	  </TouchableOpacity>

	  <View v-for="(country, index) in countries" :key="index">
		  <Text>{{ country.name }}</Text>
	  </View>
  </view>
</template>

<script>
    export default {
        data() {
            return {
                search: 'from search',
				countries: [
					{ name: 'Japan' },
					{ name: 'United States' },
				]
            }
        },
		methods: {
        	buttonEvent() {
        		alert('button clicked');
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
  .text-color-primary {
	  color: #900;
	  font-size: 28;
	  margin-bottom: 20;
  }
</style>
