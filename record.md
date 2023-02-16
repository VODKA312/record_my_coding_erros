# 优化代码思路记录

### 2023_02_14 优化代码技巧，使用逻辑表达式

该想法来自一个函数编程任务，内容如下：

> 检查函数的输入，确保它们不是字符串。 如果用户输入了一个字符串，该函数应返回 None。
>
> 这个练习可能看起来微不足道，但是如果你尝试在 Python 中输入一个 `'my_string'/2` ，你会收到一个 error 返回 。 调试 error 并避免 error 的出现是一项非常重要的编程技巧。
>

这个函数是用来限制用户输入的，如果用户输入的非法的值，就报错。

从最简单的角度出发，如果用户的输入都没有字符串，那就进行函数的计算功能。否则就报错

```python
def probability_range_improved(low_range, high_range, minimum, maximum):
    # TODO: check if any of the inputs are strings.
    # hint: the python function isinstance() will be useful
    is_low_range_a_string = isinstance(low_range, str)
    is_high_range_a_string = isinstance(high_range, str)
    is_minimum_a_string = isinstance(minimum, str)
    is_maximum_a_string = isinstance(maximum, str) 
    if(is_low_range_a_string == False and is_high_range_a_string == False and is_minimum_a_string == False 
       and is_maximum_a_string == False):
        probability = abs(high_range - low_range) / (maximum - minimum) 
    else:
        assert('input has string')
        probability = None
    return probability
```

这样的代码是可行的，但是书写起来会很费劲。一旦变量变得巨多，这样简单的罗列就会变得麻烦而且很占屏幕。

我提供以下的解决方案，也就是用逻辑表达式简化代码结构。添加一个condition变量，对结果进行或运算。如果或运算的结果为否，则说明用户输入的变量中没有一个字符串，可以进行常规运算。否则，这四个变量中一定有一个是真（即是字符串），就返回异常值。

```python
def probability_range_improved(low_range, high_range, minimum, maximum):
    ...
#以下为改进代码部分
    condition = is_low_range_a_string or is_high_range_a_string or is_minimum_a_string or is_maximum_a_string 
    if(condition == False):
        ···
    else:
        ···
    return probability
```

在学逻辑电路的时候，老师们就说学习逻辑表达式就是为了简化电路。这样的思想同样放在代码中也可行。