## 标题栏 \(bui-header\)

页面布局的标题栏。
### 导入组件

```javascript
components: {
    'bui-header': buiweex.buiHeader
}
```

### 使用

`bui-header`可以设置标题栏文字，左右两边元素，并且给它们添加对应的事件

```html
<bui-header title="标题栏" :leftItem="leftItem" :rightItem="rightItem" 
@leftClick="back" @rightClick="rightclick" @centerClick="centerclick">
</bui-header>
```

```javascript
var buiweex = require("bui-weex");
export default {
    data: function () {
        return {
            leftItem: {
                icon: 'icon-back',
            },
            rightItem: {
                text: '更多'
            }
        }
    },
    methods: {
        "back": function () {
            buiweex.pop();
            buiweex.toast('left')
        },
        "rightclick": function () {
            buiweex.toast('right')
        },
        "centerclick": function () {
            buiweex.toast('center')
        }
    }
}

```

### 属性

* `title` 标题栏中间的文本。
* `leftItem`|`rightItem` 标题栏左侧\右侧内容，是一个对象` {icon:''、 text:''}`，icon和text选择其一即可，如果两个都写了将会`从左到右`排列开来。
* `styleEx` 扩展容器样式风格，例如修改背景颜色参考如下：

	```javascript
	data: function () {
	        return {
	            myStyle: { 'background-color': '#ff4e24'}
	        }
	}
	```
	```html
	<bui-header :ios=false title="标题栏" :styleEx="myStyle">
    </bui-header>
	
	```

* `ios` 是否适配iOS的状态栏(多30px)，默认是`true` 会适配，`false`是不适配，参考如下：

  ```html
  <bui-header title="标题栏" ios="false"></bui-header>
  ```

### 事件

* `@leftClick` 是点击标题栏左侧 `leftItem` 触发的事件，参考如下：

  ```html
  <bui-header title="头部" ios="false" @leftClick="left">  </bui-header>
  ```

  ```javascript
  methods: {
    "left": function(event){
      console.log(event)
    }
  }
  ```

* `@rightClick` 是点击标题栏右侧 `rightItem` 触发的事件，用法如 `@leftClick`。

* `@centerClick` 是点击标题栏中间标题 `title` 触发的事件，用法如 `@leftClick`。

### 扩展

标题栏左右侧需加多个内容时，可以添加子元素，左右边的内容用 `slot` 区分，`right` 是右侧 ，`left` 是左侧，参考如下：

```html
<bui-header title="头部">
    <bui-icon slot="left" name="icon-search" size="45px" color="#ffffff" class="pdl10"></bui-icon>
    <bui-icon slot="right" name="icon-search" size="45px" color="#ffffff" class="pdl10"></bui-icon>
</bui-header>
```



