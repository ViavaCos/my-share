<template>
    <view>
        <view class="share-wrap" wx:if="{{visible}}" catchtouchmove="preventDefault">
        <view class="share-back"></view>
        <view class="share-container">
            <view class="close" bindtap="handleClose"></view>
            <image mode="widthFix" src="{{sharePath}}" class="share-image" />
            <view class="share-tips">保存图片，叫伙伴们来参与吧</view>
            <view class="save-btn" bindtap="handlePhotoSaved"></view>
        </view>
        </view>
        <painter style="position: absolute; top: -9999rpx;" palette="{{imgDraw}}" bind:imgOK="onImgOK" />
    </view>
</template>

<script>
import painter from './painter'
export default {
  components: { painter }
}
</script>

<style>
.share-wrap {
  width: 100%;
}

.share-back {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 888;
}

.share-container {
  width: 100%;
  background: #FFF;
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 999;
}

.close {
  width: 30rpx;
  height: 30rpx;
  overflow: hidden;
  position: absolute;
  right: 64rpx;
  top: 64rpx;
}

.close::after {
  transform: rotate(-45deg);
}

.close::before {
  transform: rotate(45deg);
}

.close::before,
.close::after {
  content: '';
  position: absolute;
  height: 3rpx;
  width: 100%;
  top: 50%;
  left: 0;
  margin-top: -2rpx;
  background: #9C9C9C;
}

.share-image {
  width: 420rpx;
  margin: 66rpx auto 0;
  display: block;
  border-radius: 16rpx;
  box-shadow: 0px 4rpx 8px 0px rgba(0, 0, 0, 0.1);
}

.share-tips {
  width: 100%;
  text-align: center;
  color: #3C3C3C;
  font-size: 28rpx;
  margin: 32rpx 0;
}

.save-btn {
  width: 336rpx;
  height: 96rpx;
  margin: 0 auto 94rpx;
  background: url('https://qiniu-image.qtshe.com/20190506save-btn.png') center center;
  background-size: 100% 100%;
}
</style>