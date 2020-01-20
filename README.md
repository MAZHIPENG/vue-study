# vue-study

## 1.v-if和v-for哪个优先级高？如果两个同时出现，应该怎么优化得到更好的性能？

### 答案：v-for 比 v-if 优先级高，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候，必要情况下应该替换成 computed 属性。
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

## 2.

### 解： 设 