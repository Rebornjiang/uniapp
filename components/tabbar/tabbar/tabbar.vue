<template>
	<view class="content">
		<view class="tabbar-wrap">
			<view class="statusBar" :style="{height: statusBarHeight + 'px'}">		
			</view>
			<view class="navBar" :style="{navbarHeight: navbarHeight + 'px',width: searchWidth + 'px'}">
				<view class="tabbarSearch" :style="{height: searchHeight + 'px'}">
					<view class="searchIcon">
						<!-- <text class="iconfont icon-sousuo"></text>
						 
						 -->
						 <uni-icons type="search" size="16"></uni-icons>
						 
					</view>
					<input type="text" placeholder="uni-app vue react">
				</view>
			</view>
			
		</view>
		<view style="height: 40px;"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				statusBarHeight: 0,
				navbarHeight: 40,
				searchWidth: 375,
				searchHeight: 30,
			};
		},
		created() {
			// 在微信消小程序中需要考虑到状态栏，已经胶囊菜单
			const deviceInfo = uni.getSystemInfoSync()
			this.statusBarHeight = deviceInfo.statusBarHeight
			console.log(deviceInfo, '设备信息')
			this.searchWidth = deviceInfo.windowWidth
			
			// #ifndef APP-PLUS || H5 || MP-ALIPAY
			// 搜索导航栏的高度应该与胶囊菜单的高度相同，并且宽度要给胶囊留出位置来。
			 const menuButtonInfo = uni.getMenuButtonBoundingClientRect() // 此方法不支持App H5 AliApp 中有用，所以要使用条件编译来这串代码仅仅运行在 小程序平台中
			 console.log(menuButtonInfo, '胶囊菜单信息')
			 this.navbarHeight = (menuButtonInfo.bottom - this.statusBarHeight) + (menuButtonInfo.top - this.statusBarHeight)
			 console.log(this.navbarHeight, 'navBarheight')
			 this.searchWidth = menuButtonInfo.left;
			 this.searchHeight = menuButtonInfo.height;
			 console.log(this.searchHeight,' serachHeight')
			 
			// #endif
		}
	}
</script>

<style lang="scss">
.tabbar-wrap {
	width: 100%;	
	background-color: skyblue;	
	position: fixed;
	top: 0;
	left: 0;
	z-index: 98;
	
	.navBar{
		box-sizing: border-box;
		padding: 10px 15px;
		display: flex;
		justify-content: center;
		align-items: center;
		height: 40px;
		.tabbarSearch {
			width: 100%;
			height: 30px;
			background-color: #FFFFFF;
			border-radius: 15px;
			display: flex;
			align-items: center;
			padding: 0 10px;
			box-sizing: border-box;
			.searchIcon {
				
				margin-right: 10px;
			}
		}
	}
}
</style>
