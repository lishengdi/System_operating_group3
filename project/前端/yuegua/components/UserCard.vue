<template>
	<view class="card">
		<view v-if="avtarsrc!=''" style="margin-left: 20rpx;"><u-avatar :src="avtarsrc" shape="circle"></u-avatar></view>
		<view style="margin-left: 20rpx;">
			<view style="font-size: 35rpx;">{{uname}}</view>
			<view style="color: #A2A2A2;">{{desc}}</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		name:"UserCard",
		props:{
			avtarsrc:{type:String,default:""},
			uname:{type:String},
			desc:{type:String}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
.card{
	margin: 10rpx;
	padding: 10rpx;
	border-radius: 20rpx;
	background-color: #fff;
	display: flex;
	align-items: flex-start;
}
</style>
