---
title: vue 的生命周期
---

  * 生命周期是指 vue 实例对象从创建之初到销毁的过程，vue 的所有功能都是围绕生命周期进行的，在生命周期的不同阶段调用不同的钩子函数来实现组建的数据管理和DOM渲染。

## 一、创建前（beforeCreate）

1. 此阶段为实例化初始后，此时数据观察和事件机制都没有形成，不能获取 DOM 节点。

## 二、 创建后（created）

1. 在这一步，实例已完成以下配置：数据观测、属性和方法的运算，watch/event事件回调，完成了data 数据的初始化，$el还没有。
2. 然而，挂载阶段还没有开始, $el属性目前不可见，这是一个常用的生命周期，因为你可以调用methods中的方法，改变data中的数据，并且修改可以通过vue的响应式绑定体现在页面上，，获取    computed中的计算属性等等。
3. 通常我们可以在这里对实例进行预处理，也有一些人喜欢在这里发ajax请求，值得注意的是，这个周期中是没有什么方法来对实例化过程进行拦截的，因此假如有某些数据必须获取才允许进入页面的话，并不适合在这个方法发请求，建议在组件路由钩子beforeRouteEnter中完成比较好。

## 三、载入前（beforeMount）
1. 挂载开始之前被调用，相关的render函数首次被调用（虚拟DOM），实例已完成以下的配置： 编译模板，把data里面的数据和模板生成html，完成了el和data 初始化，注意的是此时还没有挂在html到页面上。

## 四、载入后（mounted） 

1. 挂载完成，也就是模板中的HTML渲染到页面中，此时一般可以做一些ajax操作，mounted只会执行一次。

## 五、更新前（beforeUpdate）

1. 在数据更新之前被调用，发生在虚拟DOM重新渲染和打补丁之前，可以在该钩子函数中进一步地更改状态，不会触发附加的重复渲染过程。

## 六、更新后（updated）

1. 当data中定义的数据有变化时就会加载updated方法。

## 七、销毁前（beforeDestroy）

1. 这一步还可以用this来获取实例，一般在这一步做一些重置的操作，比如清除掉组件中的定时器 和 监听的dom事件等。

## 八、销毁后(destroyed)

1. 在实例销毁之后调用，调用后，所有的事件监听器均会被移除，所有的子实例也会被销毁，该钩子在服务器端渲染期间不被调用。

* 总结：vue的生命周期的思想贯穿在组件开发的始终，通过熟悉其生命周期调用不同的钩子函数，我们可以准确的控制数据流和其对DOM的影响；vue生命周期的思想是Vnode和MVVM的生动体现和继承。


 



