<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		globalData: {  
		            baseApi: 'http://47.115.216.83:8080'  
		        }
	}
</script>

<style>
	/*每个页面公共css */
	uni-page-body,html,body{  
	            height: 100%;
				background-color: #0E111E;
				
				/* 设置全局字体 */
	        }
				
			
	::-webkit-scrollbar{
	      display: none;
	}		
</style>
