#### 一，特殊字符

| 特殊字符    | 说明                                                         | 补充                                             |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------ |
| .           | 匹配除了换行的任意字符                                       | 如果指定了标签re.S，它将匹配包括换行符的任意字符 |
| ^           | 匹配字符串的开头                                             |                                                  |
| $           | 匹配字符串尾或者在字符串尾的换行符的前一个字符               |                                                  |
| *           | 对它前面的正则式匹配0到任意次重复                            |                                                  |
| +           | 对它前面的正则式匹配1到任意次重复                            |                                                  |
| ?           | 对它前面的正则式匹配0到1次重复                               |                                                  |
| *?，+?，??  | 非贪婪模式                                                   |                                                  |
| {m}         | 对其之前的正则式指定匹配 *m* 个重复                          |                                                  |
| {m,n}       | 对正则式进行 *m* 到 *n* 次匹配，在 *m* 和 *n* 之间取尽量多   |                                                  |
| {m,n}?      | 前一个修饰符的非贪婪模式                                     |                                                  |
| \           | 转义特殊字符                                                 |                                                  |
| []          | 用于表示一个字符集合                                         | 见详细解释                                       |
| \|          | A\|B， *A* 和 *B* 可以是任意正则表达式，创建一个正则表达式，匹配 *A* 或者 *B* |                                                  |
| (?P<name>…) | 命名组合，匹配到的子串组在外部是通过定义的 *name* 来获取的   |                                                  |

[]：

（1）[amk]匹配 'a'、'm'或者'k'

（2）[a-z]、[0-5]\[0-9]。[0-9A-Fa-f] 将匹配任何十六进制数位

（3）特殊字符在集合中，失去它的特殊含义。比如 [(+\*)] 只会匹配这几个文法字符 '('， '+'， '*'， or ')'

（4）字符类如 \w 或者 \S 在集合内可以接受

（5）不在集合范围内的字符可以通过取反来进行匹配。\[^5] 将匹配除 '5'外所有字符，， \[^^] 将匹配除了 '^'外所有字符







#### 二，特殊序列

| 特殊序列 | 说明                                        | 补充 |
| -------- | ------------------------------------------- | ---- |
| \d       | 匹配 [0-9]                                  |      |
| \D       | \d 取非                                     |      |
| \s       | 匹配任何Unicode空白字符，包括 [ \t\n\r\f\v] |      |
| \S       | \s 取非                                     |      |
| \w       | 匹配 [a-zA-Z0-9_]                           |      |
| \W       | 匹配非单词字符的字符                        |      |



#### 三，模块内容

```python
re.compile(pattern, flags=0)
re.findall(pattern, string, flags=0)
re.finditer(pattern, string, flags=0)
re.sub(pattern, repl, string, count=0, flags=0) # count是要替换的最大次数
re.subn(pattern, repl, string, count=0, flags=0) # 行为与sub()相同，但是返回一个元组 (字符串, 替换次数)
re.escape(pattern) # 转义pattern 中的特殊字符
re.purge() # 清除正则表达式的缓存
```



#### 四，正则表达式对象

```python
Pattern.search(string[, pos[, endpos]]) # 扫描整个string寻找第一个匹配的位置，并返回一个相应的 匹配对象。如果没有匹配，就返回 None
Pattern.match(string[, pos[, endpos]]) # 如果string的开始位置 能够找到这个正则样式的任意个匹配，就返回一个相应的匹配对象。如果不匹配，就返回None 
Pattern.fullmatch(string[, pos[, endpos]]) #如果整个string匹配这个正则表达式，就返回一个相应的匹配对象。否则就返回None

```



#### 五，匹配对象

```python
Match.group([group1, ...]) # 返回一个或者多个匹配的子组
Match.groups(default=None) # 返回一个元组，包含所有匹配的子组，default 参数用于不参与匹配的情况，默认为None
Match.groupdict(default=None) # 返回一个字典，包含了所有的命名子组。key就是组名。default 参数用于不参与匹配的组合；默认为None
Match.start([group])
Match.end([group]) # 返回group匹配到的字串的开始和结束标号
```

例1：

```python
>>> m = re.match(r"(?P<first_name>\w+) (?P<last_name>\w+)", "Malcolm Reynolds")
>>> m.group('first_name')
'Malcolm'
>>> m.group('last_name')
'Reynolds'
```

例2：

```python
>>> email = "tony@tiremove_thisger.net"
>>> m = re.search("remove_this", email)
>>> email[:m.start()] + email[m.end():]
'tony@tiger.net'
```

