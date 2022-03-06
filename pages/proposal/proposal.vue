<template>
	<view class="content">
		<uni-title type="h1" :title="proposal.proposal_id"></uni-title>
		<view class="uni-note">{{proposal.asset_it}}</view>
		<view class="uni-note">{{proposal.date_time}}</view>
		<view class="uni-note">{{proposal.price}}</view>
		<view class="uni-note">{{proposal.quota}}</view>
		<view class="uni-note">{{proposal.vendor_id}}</view>
		
		<uni-title type="h1" :title="game.name"></uni-title>
		<view class="uni-note">{{game.description}}</view>
		<view class="uni-note">{{game.quota}}</view>
		<view class="uni-note">{{game.author}}</view>
		<view class="uni-note">{{game.publisher}}</view>
		<view class="uni-note">{{game.cover}}</view>
		
		<uni-title type="h1" :title="vendor.name"></uni-title>
		<view class="uni-note">{{vendor.address}}</view>
		<view class="uni-note">{{vendor.avatar}}</view>
		<!-- 参与玩家 -->
	</view>
</template>

<script>
	const app = getApp();
	export default {
		data() {
			return {
				proposal: {
					proposal_id: 0
				},
				game: {
					name: ''
				},
				vendor: {
					name: ''
				}
			}
		},
		onLoad(options) {
			uni.request({
				url: app.globalData.get_request_url('proposals/' + options.proposal_id),
				success: (res) => {
					this.proposal = res.data.proposal;
					this.game = res.data.game;
					this.vendor = res.data.vendor;
				}
			})
		}
	}
</script>

<style>
</style>
