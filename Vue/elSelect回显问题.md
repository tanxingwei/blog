element ui

例如el-select el-cascader的回显问题

一般来说都是用来form表单里面, 这里直接使用官网的案例.

```vue
<template>
  <el-select v-model="value" placeholder="请选择">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>
</template>

<script>
  export default {
    data() {
      return {
        options: [{
          value: 1,
          label: '黄金糕'
        }, {
          value: 2,
          label: '双皮奶'
        }, {
          value: 3,
          label: '蚵仔煎'
        }, {
          value: 4,
          label: '龙须面'
        }, {
          value: 5,
          label: '北京烤鸭'
        }],
        value: ''
      }
    }
  }
</script>
```

我们进行选择的时候是没有问题的

但是如果是进行修改操作,这个select绑定的value是后端接口返回的情况, 在select的选项框中则会显示一个数字, 原因是类型不匹配, 接口返回的数字value通常会被解析成字符串, 而select中的Option绑定的value是数字类型

所以需要对接口返回的value进行一个parseInt的操作