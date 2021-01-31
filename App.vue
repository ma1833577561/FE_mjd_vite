<template>
	<div>
		<img alt="Vue logo" src="./assets/logo.png" />
		<HelloWorld msg="Hello Vue 3.0 + Vite" />
		<h1 class="name">FE_mjd</h1>
	</div>
</template>

<script lang="ts">
	import '/@/assets/app.css'
import HelloWorld from '/@/components/HelloWorld.vue'
import data from '/@/assets/FEmjd.json'
const FE_mjd:string='FE_mjd'
export default {
  name: 'App',
  components: {
    HelloWorld
  },
	mounted(){
		console.log(FE_mjd)
		console.log(data.name)
		
	},
}
</script>
<style lang="scss">
	.name{color: pink;}
</style>