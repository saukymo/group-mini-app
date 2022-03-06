<template>
	<view class="content">
		<uni-title type="h1" :title="vendor.name"></uni-title>
		<view class="uni-note">{{vendor.address}}</view>
		<view class="uni-note">{{vendor.avatar}}</view>
		
		<proposals-list :proposals="proposals"></proposals-list>
		
		<games-list :games="games"></games-list>
	</view>
	
</template>

<script>
	const app = getApp();
	export default {
		data() {
			return {
				vendor: {
					name: ''
				},
				games: {
				},
				proposals: {}
			}
		},
		onLoad(options) {
			uni.request({
				url: app.globalData.get_request_url('vendors/' + options.vendor_id),
				success: (res) => {
					this.vendor = res.data.vendor;
					console.log(res.data.vendor);
				}
			});
			uni.request({
				url: app.globalData.get_request_url('vendors/' + options.vendor_id + '/games'),
				success: (res) => {
					this.games = res.data.games;
					console.log(res.data.games);
				}
			});
			uni.request({
				url: app.globalData.get_request_url('vendors/' + options.vendor_id + '/proposals'),
				success: (res) => {
					this.proposals = res.data.proposals;
					console.log(res.data.proposals);
				}
			});
		},
		methods: {
			
		}
	}
</script>

<style>
</style>
