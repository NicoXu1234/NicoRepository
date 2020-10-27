## BUG 源码修改

***
# 1
添加了isMobile的判断，需要在配置的时候配置改字段，用来取消移动端的删除以及模糊查询无法获取焦点的问题
```
/node_modules/element-ui/select.js 560行 props添加isMobile: Boolean
/node_modules/element-ui/select.js 505行改为 !this.filterable || this.multiple || (!isIE && !this.visible && !this.isMobile);
/node_modules/element-ui/select.js 508行改为  var criteria = this.clearable && !this.selectDisabled && (this.inputHovering || this.isMobile) && !this.multiple && this.value !== undefined && this.value !== null && this.value !== '';
```

```
/node_modules/element-ui/input.js props添加isMobile: Boolean。
showClear: function showClear() {
      return this.clearable && !this.disabled && !this.readonly && this.currentValue !== '' && (this.focused || this.hovering || this.isMobile);
    }
```