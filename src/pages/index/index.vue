<template>
    <div class="container" @click="clickHandle('test click', $event)">
        <text>{{userInfo.nickName}}</text>
        <button open-type="getUserInfo" lang="zh_CN" @getuserinfo="bindgetuserinfo">获取用户信息</button>

    </div>
</template>

<script>

	export default {
		data () {
			return {
				userInfo: {}
			}
		},
		methods: {
			clickHandle(){
				console.log( '123:' )
			},
			bindgetuserinfo( e ){
				console.log( 234, e );
				console.log( e.mp.detail.errMsg )
				console.log( e.mp.detail.userInfo )
				console.log( e.mp.detail.rawData )
				this.userInfo = e.mp.detail.userInfo
			},
		},
		mounted(){
			wx.getUserInfo( {
				success: ( res ) => {
					console.log( res );
					this.userInfo = res.userInfo
				}
			} )
		}
	}
</script>

<style scoped>
</style>
