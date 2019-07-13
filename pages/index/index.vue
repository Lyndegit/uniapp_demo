<template>
	<view class="content uni-flex uni-column">
		<text class="title">{{title}}</text>
		<view class="flex-item flex-item-V">
            <span>用户名:</span> 
			<input class="uni-input" focus placeholder="请输入用户名" v-model="loginInfoVo.username"/>
		</view> 
		<view class="flex-item flex-item-V">
			<span>密码:</span> 
			<input type="uni-input" focus placeholder="请输入密码"  v-model="loginInfoVo.userpass"/>
		</view>
		<view class="flex-item flex-item-V">
			<button type="primary" class="bt" @tap="fun">获取验证码</button>
		    <span>
				{{yanzhen}}
			</span>
			<input type="text" v-model="useryan"/>
			<button type="primary" @tap="lyn">登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '登录页面',
				yanzhen:'',
				 loginInfoVo: { username: '', password: ''},
				 username:'',
				 userpass:'',
				 useryan:''
			}
		},       
		onLoad() {
			// uni.request({
			// 	url:'https://mockapi.eolinker.com/KeQC41x2b370ab73e042befc2c56a925ab511b5116aec98/demo?username=username&userpass=userpass',
			// 	methods:'POST',
			// 	data:{
			// 		 username: this.loginInfoVo.username,
   //                   password: this.loginInfoVo.password,
			// 	},
			// 	success:res=>{
			// 		console.log(res);
			// 	},
			// 	fall:failResponse => {}
			// })
		},
		methods: {
         fun(){
			 uni.request({
			 	url:'https://mockapi.eolinker.com/KeQC41x2b370ab73e042befc2c56a925ab511b5116aec98/demo',
			 	methods:'GET',
			 	data:{
					username : this.loginInfoVo.username,
					userpass : this.loginInfoVo.userpass
			 	},
			 	success:res=>{
			 		console.log(res)
					this.yanzhen = res.data.yanzhen;
			 	},
			 	fall:failResponse => {
					uni.showToast({
						title:'请求错误!'
					})
				}
			 })
			 },
		 lyn(){
			 if( this.useryan==this.yanzhen)
			 {
				 uni.navigateTo({
				 	url:'../chenggong/chenggong',
				 })
			 }
		 }
			 
		 }
		}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 50upx;
		width: 50upx;
		margin-top: 0upx;
	}

	.title {
		font-size: 56upx;
		color: black;
	}
		
	.bt{
		width: 50%;
	}
</style>
