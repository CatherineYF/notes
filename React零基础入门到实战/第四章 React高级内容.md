## 一、React Develop Tools 使用

- React线上版本——黑色图标
- React开发版本——粉色图标



## 二、 PropTypes和DefaultProps的应用

react组件通过props传递参数，其中：

propTypes规定了props的类型

defaultProps定义了props的默认值

```react
import React,{ Component } from 'react'
import PropTyps from 'prop-types' // 引入prop-types包
class TodoItem extends Component{
  constructor(props){
    
  }
}
TodoItem.propTypes = { // 可以限制传值类型
  content: PropTypes.arrayOf(PropTypes.string,PropTypes.number),// content既可以是string，也可以是number
  deleteItem: PropTypes.func,
  index: PropTypes.number,
  test:PropTypes.string.isRequired // 表示该属性值为必输项
}
TodoItem.defaultProps = {
  test: 'hello world'  // 给test设置默认值
}
```



## 三、props、state与render函数



当**数据**（props、state）发生变化的时候，会触发`render`函数执行从而更新视图



## 四、 React中的虚拟DOM

react中的虚拟DOM是一个javascript对象

**React的执行机制（虚拟DOM底层原理）：**

1. 准备好state数据

2. 准备好JSX模板

3. 数据 + 模板 生成虚拟DOM（它是一个JS对象，用来描述真实DOM）（有一定的性能损耗）

4. 用虚拟DOM的结构生成真实的DOM，来显示`<div id='abc'><span>hello world</span></div>`

5. state发生变化

6. 新数据 + 模板 生成新的虚拟DOM(极大的提升了性能)

   ['div',{id:'abc'},['span',{},'bye bye']]

7. 比较原始虚拟DOM和新的虚拟DOM的区别（Diff算法），找到区别是span中的内容（极大的提升了性能）

8. 操作DOM，改变span中的内容



JSX -> JS对象(虚拟DOM)->真实DOM



**虚拟DOM的优点：**

1. 性能提示（DOM的比对变成了JS对象的比对）
2. 使得跨端应用得以实现



**虚拟DOM中的Diff算法**

同级比较： 两个虚拟DOM做比对，若父级两个虚拟DOM不同，则将DOM全部替换掉

大大减少了不同层进行比对的算法对性能的消耗

key值应该使用稳定的值，不应该使用index



## 五、React中Ref的使用

ref是一个引用，用来在react中操作DOM



有时在setState后用ref获取Dom时，DOM获取不及时，需要把这个操作放到setState的回调之中

## 六、React的生命周期函数

`生命周期函数`是指在某一个时刻，组件会自动调用的函数



