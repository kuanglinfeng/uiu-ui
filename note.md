## 制作Switch组件

知识点

- value="true" 和 :value="true"的区别
- 使用 CSS transition 添加过渡动画
- 使用 ref 创建内部数据
- 使用 :value 和 @input 让父子组件进行通信
- 使用 $event
- 使用 v-model
- 框架就是把你框起来：不准改 props

Vue2 和 Vue3 的区别

- 新 v-model 替代以前的v-model和.sync
- 新增context.emit，与this.$emit作用相同

## 制作Button组件

API设计

```
<Button
  @click=?
  @focus=?
  @mouseover=?
  theme="button or link or text"
  level="main or normal or minor"
  size="big normal small"
  disabled
  loading
>按钮<Button>
```

Vue3属性绑定

- 默认所有属性都绑定到根元素
- 使用inheritAttrs: false可以取消默认绑定
- 使用$attrs 或者 context.attrs获取所有属性
- 使用v-bind="$attrs"批量绑定属性
- 使用const {size, ...rest} = context.attrs将属性分开

props VS attrs

区别如下：

- props要先声明才能取值，attrs不用先声明
- props不包含事件，attrs包含
- props没有声明的属性，会跑到attrs里
- props支持string及以外的类型，attrs只支持string类型

UI库的css注意事项

1. 不能使用scoped

- 因为data-v-xxx中的xxx每次运行可能不同
- 必须输出稳定不变的class选择器，方便使用者覆盖

2. 必须加前缀

- .button不行，很容易被使用者覆盖
- .uiu-button可以，不太容易被覆盖
- .theme-link不行，很容易被使用者覆盖
- .uiu-theme-link可以，不太容易被覆盖