<template>
	<view>
		<uni-title type="h1" :title="title"></uni-title>
		<uni-list>
			<uni-list-item v-for="game in games" :key="game.game_id" :to="'/pages/game/game?game_id=' + game.game_id">
				<template v-slot:body>
					<view class="uni-content">
							<view class="uni-note">{{game.name}}</view>
							<view class="uni-note">{{game.description}}</view>
							<view class="uni-note">{{game.quota}}</view>
					</view>
				</template>
				
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		name: "剧本列表",
		props: {
			title: {
				type: String,
				default: '剧本'
			},
			games: {
				type: Array,
				default: []
			}
		}
	}
</script>

<style>
</style>
