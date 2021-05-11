## 提高vue性能的方式

1. v-if 和 v-for不要同时使用

2. 使用路由懒加载可以提高首页渲染速度

   ``` component: () => import(/* webpackChunkName: "about"  */'../views/About.vue') ```

3. 

