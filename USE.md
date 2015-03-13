# 使用说明

## 选择器效率问题

> 尽量使用Id选择器，jQuery的选择器使用的API都是基于getElementById或getElementsByTagName，因此可以知道 效率最高的是Id选择器，因为jQuery会直接调用getElementById去获取dom，而通过样式选择器获取jQuery对象时往往会使用 getElementsByTagName去获取然后筛选。

> 样式选择器应该尽量明确指定tagName, 如果开发人员使用样式选择器来获取dom，且这些dom属于同一类型，例如获取所有className为jquery的div，那么我们应该使用的写法 是$('div.jquery')而不是$('.jquery')，这样写的好处非常明显，在获取dom时jQuery会获取div然后进行筛选，而不是 获取所有dom再筛选

> 避免迭代，很多同学在使用jQuery获取指定上下文中的dom时喜欢使用迭代方式，如$('.jquery .child')，获取className为jquery的dom下的所有className为child的节点，其实这样编写代码付出的代价是非常大 的，jQuery会不断的进行深层遍历来获取需要的元素，即使确实需要，我们也应该使用诸如$(selector,context), $('selector1>selector2'), $(selector1).children(selector2), $(selctor1).find(selector2)之类的方式