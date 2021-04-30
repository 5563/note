## uniapp引入公众号配置

1. 先引入sdk

   ` npm install jweixin-module --save `

2. 使用方法

```js
var jweixin = require('jweixin-module')
jweixin.ready(function(){  
    // TODO  
});
```

#### 具体使用

1. 为了避免每个页面都进行配置参数，自己写一个mixin，再全局引入一下

``` js
const jweixin = require('jweixin-module')
export default {
	data() {
		return {
		}
	},
	onShow() {
        //post调接口必须穿 window.location.href.split('#')[0]
		this.$request('User/getJsApiConfig',{url:window.location.href.split('#')[0]}).then(({data})=>{
			jweixin.config({
			  debug: false, // 开启调试模式,调用的所有api的返回值会在客户端alert出来
			  appId: data.data.appId, // 必填，公众号的唯一标识
			  timestamp: data.data.timestamp, // 必填，生成签名的时间戳
			  nonceStr: data.data.nonceStr, // 必填，生成签名的随机串
			  signature: data.data.signature,// 必填，签名
			  jsApiList: [
				'checkJsApi',
				'onMenuShareTimeline',//分享接口
				'onMenuShareAppMessage',//分享接口
				'onMenuShareQQ',//分享到qq接口
				'onMenuShareWeibo'//分享到微博接口
			  ] // 必填，需要使用的JS接口列表
			});
			jweixin.ready(function(){
                //名字需要和jsApiList列表中对应-用旧版
                jweixin.onMenuShareAppMessage({ 
                    title: '旺乐佳', // 分享标题
                    desc: '弘扬传统文化 服务实体经济', // 分享描述
                    link: 'http://wlj.caomall.cn/#/', // 分享链接，该链接域名或路径必须与当前页面对应的公众号JS安全域名一致
                    imgUrl: 'http://cdn.caomall.net/1619778991891561669.png', // 分享图标
                    success: function () {
                        // 设置成功
                        console.log("success")
                    },
                    fail: function(res) {
                        alert("分享失败")
                    }, 
                }) 
			});
		})
	},
	methods: {
		
	}
}
```

2. 全局引入mixin

``` js
import mymixin from './util/mymixin.js';
Vue.mixin(mymixin)
```



> 至此可以实现每个页面分享