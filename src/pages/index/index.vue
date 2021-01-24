<template>
	<view class="content">
		<view v-if="!imgUrl" class="upload" type="file" @click="upload">点击上传图片</view>
		<view v-else  class="img-content">
			<image class="img" :src="imgUrl" mode="widthFix"></image>
		</view>
		<button class="share-btn" type="primary" @click="share">分享</button>
		<!-- https://developers.weixin.qq.com/community/develop/article/doc/000ac686c5c5506f18b87ee825b013 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgUrl:'' // img url
			}
		},
		onLoad() {

		},
		methods: {
			share() {
				console.log('share， url=', this.imgUrl)
				
				// wx.showShareMenu({
				//   withShareTicket: true,
				//   menus: ['shareAppMessage', 'shareTimeline']
				// })
				
				wx.showShareImageMenu({
					// path: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1442998595,1306184984&fm=26&gp=0.jpg',
					path: this.imgUrl[0],
					success(res){
						console.log('success' ,res)
					},
					fail(res){
						console.log('fail' ,res)
					},
					complete(res){
						console.log('complete' ,res)
					}
				})
			},
			upload(){
				wx.chooseImage({
				  success: (res) => {
				    const tempFilePaths = res.tempFilePaths
					this.imgUrl = tempFilePaths
				  }
				})
			}
		}
	}
</script>

<style>
.content {
	min-height: 100vh;
}
.share-btn {
	margin: 375rpx auto;
	width: 500rpx;
}
.upload {
	width: 555rpx;
	height: 555rpx;
	color: #ccc;
	line-height: 555rpx;
	text-align: center;
	margin: 50rpx auto 25rpx;
	border: 1rpx dashed #4CD964;
}
.img-content {
	display: block;
	width: 555rpx;
	height: 555rpx;
	margin: 50rpx auto 25rpx;
}
.img {
	max-width: 555rpx;
	line-height: 555rpx;
	vertical-align: middle;
}
</style>
