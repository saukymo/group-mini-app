<template>
	<view>
		<uni-title type="h1" :title="title"></uni-title>
		<uni-list>
			<uni-list-item v-for="vendor in vendors" :key="vendor.vendor_id" :to="'/pages/vendor/vendor?vendor_id=' + vendor.vendor_id">
				<template v-slot:body>
					<view class="uni-content">
							<view class="uni-note">{{vendor.name}}</view>
							<view class="uni-note">{{vendor.address}}</view>
							<view class="uni-note">{{vendor.avatar}}</view>
					</view>
				</template>
				
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		name: "店家",
		props: {
			title: {
				type: String,
				default: '店家'
			},
			vendors: {
				type: Array,
				default: []
			}
		}
	}
</script>

<style>
</style>
