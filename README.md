# vue-study

## 3. 你知道vue中key的作用和工作原理吗？说说你对它的理解。
##### 解答：key可以提高diff的效率，当遍历元素比较少的时候，并不能提高效率，反倒速度不如重新渲染，但是当遍历元素特别多的时候能够大大的提升元素复用效率。不要用index作为key的绑定值。

## 2. Vue组件data选项为什么必须是个函数而Vue的根实例则没有此限制？

##### 解答：在官网风格指南 -> 组件数据中可以看到
##### 当 data 的值是一个对象时，它会在这个组件的所有实例之间共享。想象一下，假如一个 TodoList 组件的数据是这样的：
```
    data: {
        listTitle: '',
        todos: []
    }
```
##### 我们可能希望重用这个组件，允许用户维护多个列表 (比如分为购物、心愿单、日常事务等)。这时就会产生问题。因为每个组件的实例都引用了相同的数据对象，更改其中一个列表的标题就会改变其它每一个列表的标题。增删改一个待办事项的时候也是如此。

##### 取而代之的是，我们希望每个组件实例都管理其自己的数据。为了做到这一点，每个实例必须生成一个独立的数据对象。在 JavaScript 中，在一个函数中返回这个对象就可以了：

```
    data: function () {
        return {
            listTitle: '',
            todos: []
        }       
    }
```


## 1.v-if和v-for哪个优先级高？如果两个同时出现，应该怎么优化得到更好的性能？

##### 答案：v-for 比 v-if 优先级高，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候，必要情况下应该替换成 computed 属性。
```
    <ul>
        <li 
            v-for="{item, index} in activeUsers" 
            :key="item.id">
            {{ item.content }}
        </li>
    </ul>
    computed: {
        activeUsers: function () {
            return this.item.filter(function (item) {
                return item.isActive
            })
        }
    }

```
