<template>
	<view class="content">
		<uni-title type="h1" :title="game.name"></uni-title>
		<view class="uni-note">{{game.description}}</view>
		<view class="uni-note">{{game.quota}}</view>
		<view class="uni-note">{{game.author}}</view>
		<view class="uni-note">{{game.publisher}}</view>
		<view class="uni-note">{{game.cover}}</view>
		
		<vendors-list :vendors="vendors"></vendors-list>
		
		<proposals-list :proposals="proposals"></proposals-list>
	</view>
</template>

<script>
	const app = getApp();
	export default {
		data() {
			return {
				game: {
					name: ''
				},
				vendors: {},
				proposals: {}
			}
		},
		onLoad(options) {
			uni.request({
				url: app.globalData.get_request_url('games/' + options.game_id),
				success: (res) => {
					this.game = res.data.game;
				}
			});
			uni.request({
				url: app.globalData.get_request_url('games/' + options.game_id + '/vendors'),
				success: (res) => {
					this.vendors = res.data.vendors;
				}
			});
			uni.request({
				url: app.globalData.get_request_url('games/' + options.game_id + '/proposals'),
				success: (res) => {
					this.proposals = res.data.proposals;
				}
			});
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
