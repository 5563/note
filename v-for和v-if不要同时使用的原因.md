## v-for 和 v-if 为什么不要同时使用

- v-for 和 v-if 在同一标签时候 会优先执行v-for 执行完之后在执行v-if。相当于先执行v-for把所有dom渲染完成后，在通过v-if删除dom元素。从而造成了性能的浪费
- 解决办法 可以嵌套<template>标签

