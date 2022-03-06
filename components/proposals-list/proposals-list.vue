<template>
	<view>
		<uni-title type="h1" :title="title"></uni-title>
		<uni-list>
			<uni-list-item v-for="proposal in proposals" :key="proposal.proposal_id" :to="'/pages/proposal/proposal?proposal_id=' + proposal.proposal_id">
				<template v-slot:body>
					<view class="uni-content">
							<view class="uni-note">{{proposal.data_time}}</view>
							<view class="uni-note">{{proposal.description}}</view>
							<view class="uni-note">{{proposal.price}}</view>
							<view class="uni-note">{{proposal.quota}}</view>
					</view>
				</template>
				
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		name: "玩家组局",
		props: {
			title: {
				type: String,
				default: '玩家组局'
			},
			proposals: {
				type: Array,
				default: []
			}
		}
	}
</script>

<style>
</style>
