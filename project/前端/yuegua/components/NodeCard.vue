<template>
	<view class="timenode" >
		<view @click="clickpanel">
			<text style="font-size: 24rpx;color: #1890FF;">{{nodedata.nodetime}}</text>
			<view style="font-size: 28rpx;">{{nodedata.title}}</view>
			<view style="margin-top: 5rpx;display: flex;">
				<view v-if="nodedata.typeName == '爆料' && nodedata.imglist.length > 0" style="margin-right: 10rpx;"><u--image width="45" height="45" radius="5" :src="nodedata.imglist[0]" mode="aspectFill"></u--image></view>
				<view style="font-size: 25rpx;color: #666666;
							display: -webkit-box;
							overflow: hidden;
							-webkit-line-clamp: 2;
							-webkit-box-orient: vertical;">{{nodedata.content}}</view>
			</view>
			<view style="position: absolute;top: 13rpx;left: -25rpx;">
				<u-icon name="plus-circle-fill" color="#1890FF" size="20"></u-icon>
			</view>
			<view class="timenodecardtag">{{nodedata.typeName}}</view>
			<view style="position: absolute;top: 53rpx;right: 10rpx;font-size: 20rpx;color: #B2B2B2;">{{nodedata.time}}</view>			
		</view>

		<view class="footerbar">
			<u-icon :name="isfavor?'thumb-up-fill':'thumb-up'" space="0" color="#AEAEAE" labelColor="#AEAEAE" size="23" :label="starCount"  @click="star(nodedata.type,nodedata.ID)" ></u-icon>
			
		</view>
	</view>

</template>

<script>
	import topic from "@/pages/topic/topic.vue"
	import tmMessage from "@/tm-vuetify/components/tm-message/tm-message.vue"
	export default {
		name:"NodeCard",
		props:{
			nodedata:{type:Object},
			
			
		},
		emits:['clickedPanel'],
		data() {
			return {
				isfavor:false,
				starCount:this.nodedata.star
			};
		},
		methods:{
			clickpanel(){
				this.$emit('clickedPanel')
			},
			star(Type,ID){
				this.isfavor=true
				uni.$emit('StarNode',{type:Type,id:ID})
				this.starCount+=1
				
				// topic.methods.Star(this.nodedata.type,this.nodedata.ID)
			},
			
			
		
		},
		
	}
</script>

<style lang="scss">
.timenode{
	padding: 10rpx;
	padding-left: 20rpx;
	border-radius: 20rpx;
	margin-top: 20rpx;
	position: relative;
	background-color: #fff;
	.timenodecardtag{
		height: 40rpx;width: 80rpx;
		text-align: center;line-height: 40rpx;
		color: #fafafa;font-size: 25rpx;
		position: absolute;top: 0;right: 0;border-radius: 0 20rpx 0 20rpx;
		// background:  #007AFF;
		background: linear-gradient(to right,#1890FF, #38B0FF);
	}
	.footerbar{
		display: flex;
		align-items: center;
		justify-content: flex-end;
	}
}
</style>
