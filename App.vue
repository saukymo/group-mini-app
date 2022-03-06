<script>
	export default {
		globalData: {
			data: {
				request_url: 'http://localhost:8080/'
			},
			get_request_url(endpoint) {
				return this.data.request_url + endpoint;
			}
		},
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
