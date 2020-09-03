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

UI库的css注意事项（css最小影响原则）

1. 不能使用scoped

- 因为data-v-xxx中的xxx每次运行可能不同
- 必须输出稳定不变的class选择器，方便使用者覆盖

2. 必须加前缀

- .button不行，很容易被使用者覆盖
- .uiu-button可以，不太容易被覆盖
- .theme-link不行，很容易被使用者覆盖
- .uiu-theme-link可以，不太容易被覆盖


## 制作Dialog组件

API设计

```
  <Dialog :visible="true" title="标题" @yes="fn1" @no="fn2" />
```


## 制作Tabs组件

API设计

```
<Tabs>
  <Tab title="导航1">内容1</Tab>  
  <Tab title="导航2"><Component1 /></Tab>  
  <Tab title="导航3"><Component1 x="hi" /></Tab>  
</Tabs>
或者
<Tabs :data="[
  {title: '导航1', content: '内容1'},
  {title: '导航2', content: Component1},
  {title: '导航3', content: h(Component1, {x: 'hi'})},
]" />
```

如何在运行时确认子组件的类型?

通过检查context.slots.default()返回的数组


总结

- 用JS获取插槽内容

```ts
const default = context.slots.default()
```

- 钩子

```ts
onMounted(fn)
onUpdated(fn)
watchEffect(fn)
```

- TypeScript泛型
```ts
const indicator = ref<HTMLDivElement>(null)
```

- 获取宽高和位置

```ts
const {width, left} = el.getBoundingClientRect()
```
- ES6析构赋值的重命名语法

```ts
const {left: left1} = x.getBoundingClientRect()
const {left: left2} = y.getBoundingClientRect()
```