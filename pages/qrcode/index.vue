<template>
        <view >
        	<view>
				<uni-search-bar @confirm="search" v-model="searchValue" @clear="clear" cancelButton="none" ></uni-search-bar>
        	</view>
			<view>
				<uni-list>
					<uni-list-item class="uni-list-item--waterfall" :title="item.text"  v-for="(item, index) in dataList" :key="index" >
						<!-- 通过header插槽定义列表左侧图片 -->
						<template v-slot:header>
							<view class="uni-thumb shop-picture">
								<image  :src="item.src" mode="aspectFit"></image>
							</view>
						</template>
						<!-- 通过body插槽定义商品布局 -->
						<view slot="body" class="shop">
							<view>
								<view class="uni-title">
									<text class="uni-ellipsis-2">{{ item.text  + index}}</text>
								</view>
							</view>
							<view>
								<view class="shop-price">
									<text>¥</text>
									<text class="shop-price-text">"{{ item.goods_price }}"</text>
									<text>.00</text>
								</view>
							</view>
						</view>
					</uni-list-item>
				</uni-list>
			</view>
        </view>
</template>

<script>
	export default {
		data() {
			return {
				searchValue: '',
				dataList: [{"src": "https://bjetxgzv.cdn.bspapp.com/VKCEYUGU-uni-app-doc/6acec660-4f31-11eb-a16f-5b3e54966275.jpg", "text": "xxx"},
				{"src": "https://bjetxgzv.cdn.bspapp.com/VKCEYUGU-uni-app-doc/6acec660-4f31-11eb-a16f-5b3e54966275.jpg", "text": "aaa"}]
			}
		},
		onLoad() {

		},
		methods: {
			search(res){
				console.log('search', res)
			},
			clear(res){
				console.log('clear', res)
			},
			imageError(){
				console.log('imageError')
			}
		}
	}
</script>

<style lang="scss">
	@import '@/common/uni-ui.scss';
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	
	.shop {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.shop-picture {
		width: 150px;
		height: 110px;
	}
	
	.uni-ellipsis-2 {
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
	}
	// 默认加入 scoped ，所以外面加一层提升权重
	.list {
		.uni-list--waterfall {

			/* #ifndef H5 || APP-VUE */
			// 小程序 编译后会多一层标签，而其他平台没有，所以需要特殊处理一下
			/deep/ .uni-list {
				/* #endif */
				display: flex;
				flex-direction: row;
				flex-wrap: wrap;
				padding: 5px;
				box-sizing: border-box;

				/* #ifdef H5 || APP-VUE */
				// h5 和 app-vue 使用深度选择器，因为默认使用了 scoped ，所以样式会无法穿透
				/deep/
				/* #endif */
				.uni-list-item--waterfall {
					width: 50%;
					box-sizing: border-box;

					.uni-list-item__container {
						padding: 5px;
						flex-direction: column;
					}
				}

				/* #ifndef H5 || APP-VUE */
			}

			/* #endif */
		}
	}
</style>
