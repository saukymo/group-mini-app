<template>
	<view class="content">

		<games-list :games="games"></games-list>
		
		<vendors-list :vendors="vendors"></vendors-list>
		
		<proposals-list :proposals="proposals"></proposals-list>
		
		<uni-popup ref="popup" :mask-click="false">
			<button type="default" @click="get_user_info()">登录</button>
		</uni-popup>
	</view>
	
</template>

<script>
	const app = getApp();
	export default {
		data() {
			return {
				games: [],
				vendors: [],
				proposals: []
			}
		},
		onLoad() {
			// this.$refs.popup.open('bottom');
			
			wx.login({
			  success (res) {
			    console.log(res.code);
				uni.request({
					url: app.globalData.get_request_url('login?code=' + res.code),
					success: (res) => {
						console.log(res.data);
					}
				})
			  }
			})
			this.init_data();
		},
		methods: {
			init_data() {
				uni.request({
					url: app.globalData.get_request_url('games'),
					success: (res) => {
						this.games = res.data.games;
					}
				})
				uni.request({
					url: app.globalData.get_request_url('vendors'),
					success: (res) => {
						this.vendors = res.data.vendors;
					}
				});
				uni.request({
					url: app.globalData.get_request_url('proposals'),
					success: (res) => {
						this.proposals = res.data.proposals;
					}
				});
			},
			get_user_info(info) {
				console.log(info);
				uni.getUserProfile({
					desc: '登录',
					success: (res) => {
						console.log(res);
					}
				});
				this.$refs.popup.close();
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
