### 手写bind

```js
Function.prototype.mybind = function () {
	const that = this
	const args = Array.prototype.slice.call(arguments)
	const thisVal = args.shift()
	return function () {
		return that.apply(thisVal, args)
	}
}
```

### 手写深拷贝

```js
function deepClone ( obj ) {
	if(typeof obj !== 'object' || obj === null) {
        return obj
    }
    let result
    if( obj instanceof Array) {
        result = []
    }else {
        result = {}
    }
    for (let key in obj) {
        if(obj.hasOwnPrototype(key)){
        	result[key] = deepClone(obj[key])
        }
    }
    return result
}
//obj instanceof Array 判断obj构造函数是否为Array
//obj.hasOwnPrototype(key) 判断key是否存在于obj实例中，不是在原形中
```

>- 基本数据类型和引用数据类型区别
>  1. 基本数据类型 的 数据直接存储在**栈内存**中
>  2. 引用数据类型的数据存储在**堆内存**中**栈内存**中存储的是地址
>- 浅拷贝和深拷贝区别就是：浅拷贝只拷贝一层
>- 赋值就是只对基本数据类型进行了拷贝

### promise加载图片

```js
function loadImg (src) {
	return new Promise((resolve, reject) => {
		var img = new Image()
		img.onload = () => {
			resolve(img)
		}
		img.onerror = (err) => {
			reject(err)
		}
		img.src = src
	})
}
```

### VUE导航守卫

```js
router.beforeEach((to, from, next) => {
    
})
//路由独立共享
routes: [
    {
        path: '/foo',
        component: Foo,
        beforeEnter: (to, from, next) => {
            // ...
        }
    }
]
```

### axios 拦截器

```js
//请求拦截器
axios.interceptors.request.use(function (config) {
	return config
}, functions (err) {
	return Promise.reject(err)
})
// 添加响应拦截器
axios.interceptors.response.use(function (response) {
	// 对响应数据做点什么
	return response;
}, function (error) {
	// 对响应错误做点什么
	return Promise.reject(error);
});
```



### 快速排序

```js
function quicksort(arr, left, right) {
    //因为是回调函数必须有返回条件
    if(left>=right) return
    let l = left
    let r = right
    let temp = arr[l]
    while(l < r) {
        //每次坑位在左面所以从右开始比较
        while(l<r&&arr[r]>temp) {
            r--
        }
        //证明arr[r]<=temp
        if(l<r){
            arr[l] = arr[r]
            l++
        }
        //把坑位再预留给左面
        while(l<r&&arr[l]<temp){
            l++
        }
        if(l<r) {
            arr[r] = arr[l]
            r--
        }
    }
    arr[l] = temp
    quicksort(arr, left, l-i)
    quicksort(arr, l+i, right)
} 
```

### 归并排序

```js
function mergeSort(arr = []) {
    if(arr.length<2) return arr
    let mid = parseInt(arr.length/2)
    return merge(mergeSort(arr.slice(0,mid)),mergeSort(arr.slice(mid)))
}
function merge (left,right) {
    let result = []
    while(left.length&&right.length){
        if(left[0]<right[0]){
            result.push(left.shift())
        }else {
            result.push(right.shift())
        }
    }
    while(left.length){
        result.push(left.shift())
    }
    while(right.length){
        result.push(right.shift())
    }
    return result
}
console.log(mergeSort([5,1,89,66,7]))
```

### watch和computed区别



### call 和apply的区别



