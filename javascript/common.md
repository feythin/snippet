#js常用函数
1. 反转字符串：

如：hello -> olleh

```function reverseString(str) {
  str = str.split('').reverse().join('');
  return str;
}
reverseString("hello");
```
2. 检查是否为回文

如：'eye' -> true, 'Zz' -> true, 'race car' -> true, 'never odd or even' -> true, 0_0 (: /-\ :) 0-0 -> true, gua~ -> false 这里主要是一个正则表达式，需要把空格，逗号，句号等标点去掉

```
function palindrome(str) {
  // 统一为小写，除去空格、逗号、句号
  str = str.toLowerCase().replace(/[ |\,|\.|\_|\-|\(|\)]/g,'');
  // 反转
  var rts = str.split('').reverse().join('');

  return str==rts?true:false;
}

palindrome("never odd or even");
```
3. 找出一段文字中的最长单词，返回该单词长度

如：'What is the average airspeed velocity of an unladen swallow' -> 8

```
function findLongestWord(str) {
  return str
    .split(' ')
    .sort(function(a,b){return a.length-b.length;})
    .pop().length;
}

findLongestWord("What is the average airspeed velocity of an unladen swallow");
```
参考了StackOverflow上一位[答主的方法](http://stackoverflow.com/questions/31037076/find-the-longest-word-in-a-string-using-javascript)

sort()默认会将数字转换为字符串进行比较，如果需要定制排序方法，可以给 sort() 自定义一个比较函数，这个函数返回值为负数，顺序不变，反之交换位置。《JS 语言精粹》讲到这里时有更多例子，包括怎样排序包含数字、文字等的复杂列表 etc.

pop()返回Array()最右端的元素.

4. 有二维数组，返回每个子数组中的最大数字

如 ：[[4, 9, 1, 3], [13, 35, 18, 26], [32, 35, 97, 39], [1000000, 1001, 857, 1]] -> [9, 35, 97, 1000000]

```
function largestOfFour(arr) {
  var newArr=[];
  for(var i=0;i<=3;i++){
    newArr[i]=arr[i]
      .sort(function(a,b){return a-b;})	// 数字升序排序
      .pop();
  }
  return newArr;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```
sort()在这里有个小坑，在进行数字比较的时候，会提前将数字转化为字符串，然后进行比较，所以会出现1001<857的情况。我们需要做的跟上一篇中找最长单词类似，就是给sort()指定比较方法

5. 给定一个语句和一个单词，检查语句末尾是否为该单词

如：("What's your name","name") -> ture;("I'm fine","bad" -> false)

```
function confirmEnding(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
  var len = target.length;
  return str.substr(-len) == target?true:false;
}

confirmEnding("Bastian", "n");
```
substr()方法返回字符串中从指定位置开始到指定长度的子字符串。
语法：

```
str.substr(start[, length])
start 为负数时，从右边第start个字符位置开始，即从str.length+start开始
```
6. 


