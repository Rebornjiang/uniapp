<template>
	<view class="content">
		<tabbar></tabbar>
		<view v-for="(item, index) in 100">{{item + ' ' + '内容'}}</view>
	</view>
</template>

<script>
	import tabbar from '@/components/tabbar/tabbar/tabbar.vue'
	export default {
		components:{
			tabbar
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
	
	}
</style>
