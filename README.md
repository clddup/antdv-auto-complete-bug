# antdv-auto-complete-bug

antdv  auto-complete组件bug

#复现步骤

1. 输入框输入文本后，出现提示文本列表
2. 通过键盘向下选择第二个或第三个， 回车，此时，输入框内值被更新
3. 这个时候为了防止下次输入框获取焦点还出现提示文本列表， 我会清空文本列表
4. 再次点击回车想进行我的搜索事件，请求远端api（为了简化实例， 没有写这个步骤）
5. 此时输入框的值会被自动更新为 文本提示列表的第一项， 但是我上面第三步已经清空了提示列表

#临时解决

传递 defaultActiveFirstOption 属性 false， 可不出现这个bug， 但是后续可能还需要这个属性为true， 所以还是认为这个是bug， 需要修复

#推测bug原因

怀疑组件内部为了实现 *默认高亮第一个选项* 功能， 将列表第一个选项进行了保存， 但是当我清空列表的时候，值没有更新， 所以会出现这个bug
