# 3 Vue

<hr>

## 3.1 vue3比vue2有什么优势？
- 体积更小，引入了Tree shaking，用不到的模块将会被裁剪
- 更好的TS支持，vue3本身是使用TS编写的，提供了更好的TS支持
- 更方便的代码书写方式，vue3提供了组合式API，相比于vue2的选项式API，可以更好地组织代码
- 更强大的数据劫持，vue3当中使用Proxy替换了vue2当中的Obejct.defineProperty
- 更方便的逻辑复用，vue3当中提供了自定义hook的功能，可以更好地复用代码

<hr>

## 3.2 vue3的生命周期
- beforeCreate        setup
- created             setup
- beforeMount         onBeforeMount
- mounted             onMounted
- beforeUpdate        onBeforeUpdate
- updated             onUpdated
- beforeDestroy       onBeforeUnmount
- destroyed           onUnmounted
- onActivated         onActivated
- onDeactivated       onDeactivated

beforeCreate和created被setup所替代，其他的生命周期函数命名方式进行了改变

<hr>

## 3.3 说一说你对选项式API和组合式API的理解？
在vue2当中，我们在编写一个组件的时候，经常会使用data、methods、computed等选项来进行编写，数据统一放在了data这个选项当中，方法统一放到了methods当中，我们的组件逻辑是由一个个的配置项和配置项里面的内容构成的。

在vue3当中，vue提供了组合式API，如ref、reactive、watch等等，这些都是一个个的函数，是可以相互进行组合来完成功能的，我们可以把相关的数据和方法放在一起，维护的时候，比较方便。

选项式API和组合式API各有各的优点，选项式API结构比较清晰，比较容易理解；而组合式API更加方便维护，复用代码也比较方便，我们可以根据实际情况来去选择

<hr>

## 3.4 Vue3.0有什么更新？
- vue3在响应式方面，使用Proxy替换了Object.defineProperty，并且使用了静态提升的技术来提供渲染性能
- 提供了全新的组合式api，提供了自定义hook的代码复用方式
- vue3本身是使用TS编写的，提供了更好的类型提示和自动补全功能
- vue3更改了过渡类名，移除了一些不常用的api，譬如过滤器、.native事件修饰符
- vue3当中组件可以有多个节点，不再需要一个大的根节点进行包裹

<hr>

## 3.5 Vue3当中为什么要使用Proxy替换Object.defineProperty？
- vue2创建的时候，Proxy还未出现，只能是使用Object.defineProperty，而Object.defineProperty存在一些问题，它只能监听到对象属性的get和set，无法监听到属性的新增和删除，也无法监听数组，所以vue2当中提供了Vue.set和Vue.delete，并且重写了数组方法
- 而Proxy则不存在上述的问题，Proxy可以监听到对象属性的增删改查，也可以监听数组，功能比Object.defineProperty更为强大，但是Proxy不支持IE，存在兼容性问题。
- vue2当中，使用Object.defineProperty在进行响应式处理时，进行了递归深层次处理，效率相对比较低，性能也消耗大；在vue3当中，使用Proxy进行响应式处理时，进行的是懒处理，只有当访问到了深层对象的时候，才会为其添加响应式，这提高了效率，也减少了性能消耗

