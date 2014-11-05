---
layout: post
title: "Ruby Block notes"
date: 2014-11-05 21:46:51 +0800
comments: true
categories: 
---

##Ruby lambda vs Proc的区别

###只有2个区别：
1. lambda检查传入参赛的个数
2. 当lambda返回的时候，他会把控制权交还给调用他的函数，而Proc则会直接跳出那个方法

代码，来自codecademy

```ruby
def batman_ironman_proc
  victor = Proc.new { return "Batman will win!" }
  victor.call
  "Iron Man will win!"
end

puts batman_ironman_proc

def batman_ironman_lambda
  victor = lambda { return "Batman will win!" }
  victor.call
  "Iron Man will win!"
end

puts batman_ironman_lambda
```
####控制台的结果
Batman will win! <br>
Iron Man will win!

##Ruby block的小习题
```ruby
crew = {
  captain: "Picard",
  first_officer: "Riker",
  lt_cdr: "Data",
  lt: "Worf",
  ensign: "Ro",
  counselor: "Troi",
  chief_engineer: "LaForge",
  doctor:  "Crusher"
}
```
crew是各个职位和该职位的员工姓名的字典
现在需要过滤掉名字首字母不在A－M的。<br>
Solution：
定义一个lambda制定了改规则，穿给crew字典
`before_M = lambda { |key, value| value[0] < 'M' } `
应为要传给字典，所以需要两个lambda的参赛，及`|key, value|`

最后，`A_to_M = crew.select(&before_M)`

##一点心得
ruby中的block是对逻辑或者数据动作的封装，是的程序代码的data和behavior分离，降低了代码的耦合度。通过其传入list, 或者hash的map，each等接口，发挥了函数式编程的特点，避免的大量的循环。