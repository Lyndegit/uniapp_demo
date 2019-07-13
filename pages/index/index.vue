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
			<input type="text" v-model="loginInfoVo.useryan"/>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '登录页面',
				yanzhen:'',
				 loginInfoVo: { username: '', password: '' ,useryan:''},
			}
		},
		onLoad:function demo(e) {
			uni.request({
				url:'',
				methods:'POST',
				data:{
					 username: this.loginInfoVo.username,
                     password: this.loginInfoVo.password,
				},
				success:res=>{
					console.log(res);
				},
				fall:failResponse => {}
			})
		
           
		},
		methods: {
         fun(){
			 if(1) //此处等待后台挂钩子函数demo
			 uni.navigateTo({
			 	url:'../chenggong/chenggong',
			 })
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
