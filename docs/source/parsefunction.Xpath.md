##### xpath定位中starts-with、contains和text()的用法

[xpath_resource](https://devhints.io/xpath)

1. starts-with 匹配一个属性开始位置的关键字
2. contains 匹配一个属性值中包含的字符串

3. text（） 匹配的是显示文本信息，此处也可以用来做定位用



  查找name属性中开始位置包含'name1'关键字的页面元素

```
//input[starts-with(@name,'name1')] 
```

   查找name属性中包含na关键字的页面元素

```
//input[contains(@name,'na')]  
```

###### text()定位示例:

示例1:

```html
<a href="http://www.baidu.com">百度搜索</a>
```

```
 //a[text()='百度搜索'] or

//a[contains(text(),"百度搜索”)]
```

示例2:

```html
<td><a href="/scripts/cder/daf/index.cfm?event=overview.process&ApplNo=018916" title="Click to view HEPARIN SODIUM 5,000 UNITS IN SODIUM CHLORIDE 0.9% (HEPARIN SODIUM)">HEPARIN SODIUM 5,000 UNITS IN SODIUM CHLORIDE 0.9%<br />NDA   #018916</a></td>
```

提取药名和ID

方法 sibling：

```json
{drug_name:"//td/a/text()[following-sibling::br]",
 id: "//td/a/text()[preceding-sibling::br]"}
```

text与\<br>都是同级节点，drug_name 后的xpath代表提取同级节点中的弟弟节点为br的text

方法 index：

```json
{drug_name: "//td/a/text()[1]",
id: "/td/a/text()[2]"}
```

