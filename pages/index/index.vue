<template>
	<view class="uni-padding-wrap uni-common-mt">
          <view class="button-sp-area">
                <view class="button-sp-area">
					<button type="default">跳转A</button>
					<button type="default">跳转B</button>
				
					<navigator url="/pages/qrcode/index">
						<button type="default">显示列表</button>
					</navigator>
					
				</view>
            </view>
	</view>
</template>

<script>
	export default {
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
    .button-sp-area {
        margin: 0 auto;
        width: 60%;
    }

	button {
	    margin-top: 30rpx;
	    margin-bottom: 30rpx;
	}
</style>
