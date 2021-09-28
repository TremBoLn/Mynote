# 算法笔记

## 一.排序算法

### 1.1 冒泡算法

最好情况：O(n) 基本有序

最坏情况：O(n²)  逆序

每趟可以确定一个元素的最终位置

```js
function BubbleSort(arr) {
    var flag = false;
    var temp;
    for (var i = 0; i < arr.length - 1; i++) {
        for (var j = arr.length - 1; j > i; j--) {
            if (arr[j] < arr[j - 1]) {
                temp = arr[j];
                arr[j] = arr[j - 1];
                arr[j - 1] = temp;
                flag = true;
            }
            if (flag === false) {
                return;
            }
        }
    }
    return arr;
}
```

---

### 1.2 插入排序

最好情况：O(n) 基本有序

最坏情况：O(n²)  逆序

每趟使已排元素有序

```js
function InsertSort(arr) {
  var temp;
  for (var i = 1; i < nums; i++) {
    if (arr[i] < arr[i - 1]) {
      temp = arr[i];
    }
    for (var j = i - 1; j >= 0 && arr[j] > arr[i]; j--) {
      arr[j] = arr[j + 1];
    }
    arr[j] = temp;
  }
  return arr;
}

```

---

## 二、 双指针法



| 题目                             | 题目要求                                                     |
| -------------------------------- | ------------------------------------------------------------ |
| 27、移除元素(eazy)               | 给定一个数组和一个val，要求删除数组中的val，并返回删除后的数组长度 |
| 997、有序数组的平方(eazy)        | 给定一个有序数组，要求升序返回该数组元素的平方的数组         |
| 209、最短子数组(middle)          | 给定一个数组和一个值，求长度最短且元素之和大于给定值的子数组，并返回其长度，若无，则返回0 |
| 24、两两交换链表中的节点(middle) | 两两交换链表中的节点，如第一个和第二个换，第三个和第四个换，第二第三不换 |
| 209、最短子数组(middle)          | 给定一个数组和一个值，求长度最短且元素之和大于给定值的子数组，并返回其长度，若无，则返回0 |
| 15、三数之和(middle)             | 返回给定数组返回所有和为target的三元组                       |
| 18、四数之和(middle)             | 返回给定数组返回所有和为target的四元组                       |
| 344、翻转字符串(eazy)            | 翻转字符串                                                   |
| 541、翻转字符串II(eazy)          | 每隔2k翻转前k个字符，若不足2k则全部翻转                      |
| 剑指offer05、替换空格(middle)    | 将字符串中的空格替换为%20                                    |
| 151、翻转字符串里的单词(middle)  | 将英文语句倒序输出，每个单词之间一个空格分割                 |
| 剑指Offer58-II.左旋转字符串      | 字符串循环左移n个单位                                        |

---

## 三、 逻辑题

| 题目                  | 题目要求                                          |
| --------------------- | ------------------------------------------------- |
| 59.螺旋矩阵II(middle) | 给定一个整数n，输出一个n×n的矩阵，从1开始顺时针+1 |

---

## 四、链表

```js
function ListNode(val, next) { //链表节点定义
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}
//打印链表
function printList(HeadNode) {
  var newNode = HeadNode.next;
  while (newNode != null) {
    console.log(newNode.val);
    newNode = newNode.next;
  }
}
//头插
function head_Insert(HeadNode) {
  while (1) {
    var val = prompt();
    if (val == "!") {
      break;
    }
    var newNode = new ListNode(val, HeadNode.next);
    HeadNode.next = newNode;
  }
  return HeadNode;
}
//尾插
function tail_Insert(HeadNode) {
  var t = HeadNode;
  while (1) {
    var val = prompt();
    if (val == "!") {
      break;
    }
    var newNode = new ListNode(val);
    t.next = newNode;
    t = newNode;
  }
  return HeadNode;
}
//删除所有指定元素
function removeElements(HeadNode, val) { //力扣的链表都是不带虚拟头结点的
  var tNode = HeadNode.next;
  var preNode = HeadNode;
  while (tNode != null) {
    if (tNode.val != val) {
      preNode = preNode.next;
      tNode = tNode.next;
      continue;
    }
    preNode.next = tNode.next;
    tNode.next = null;
    tNode = preNode.next;
  }
  return HeadNode;
}
//翻转链表
var reserveList = function (head) {
  var nextNode = null;
  var tNode = head.next;
  var Node = head.next;
  while (Node) {
    tNode = Node.next;
    Node.next = nextNode;
    head.next = Node;
    nextNode = Node;
    Node = tNode;
  }
  return head;
};
```

| 题号                        | 题目要求                               |
| --------------------------- | -------------------------------------- |
| 19、删除倒数第n个元素(eazy) | 删除倒数第n个元素                      |
| 160、链表相交(eazy)         | 找到两个链表相交的节点                 |
| 142、环形链表II(mid)        | 如果链表有环，返回环入口，无则返回null |

---

## 五、哈希表

| 题号                          | 题目要求                                      |
| ----------------------------- | --------------------------------------------- |
| 242、有效字母的异位词(eazy)   | 判断两个单词是否由相同的小写字母组成          |
| 1002、查找常用字符(eazy)      | 返回每个单词中都出现的字符的数组              |
| 349、两个数组的交集(eazy)     | 返回两个数组中都出现的字符的数组              |
| 203、快乐树(eazy)             | 判断一个数的每位平方相加和不断循环最后能否为1 |
| 1、两数之和(eazy)             | 返回给定数组中唯一一对数之和=target的数组     |
| 20、有效的括号(eazy)          | 括号匹配是否正确                              |
| 150、逆波兰表达式求值(middle) | 给后缀表达式，求结果                          |

---

## 六、查找算法

### 6.1 二分查找

```js
var BinarySearch = function (nums, target) {
  nums.sort((a, b) => a - b);
  console.log(nums);
  let left = 0,
    right = nums.length - 1;
  while (left < right) {
    let middle = Math.round((left + right) / 2);
    if (nums[middle] < target) {
      left = middle + 1;
    } else if (nums[middle] > target) {
      right = middle - 1;
    } else {
      return middle;
    }
  }
  return -1;
};
```

---

### 6.2 KMP

```js
// next[0]、next[1]默认-1，0,其余为当前字符前面字符串的最长相等前后缀长度
var strStr = function (haystack, needle) {
  let getNext = (needle) => {
    var n = needle.length,
      k = -1,
      j = 0;
    var next = [];
    next[0] = -1;
    while (j < n - 1) {
      if (k == -1 || needle[j] == needle[k]) {
        ++k;
        ++j;
        next[j] = k;
      } else {
        k = next[k];
      }
    }
    return next;
  };
  let next = getNext(needle);
  var i = (j = 0);
  while (i < haystack.length && j < needle.length) {
    if (j === -1 || haystack[i] === needle[j]) {
      i++;
      j++;
    } else {
      j = next[j];
    }
  }
  if (j < needle.length) {
    return -1;
  } else {
    return i - needle.length;
  }
};
```

```js
// 当前位置的最长相等前后缀长度-1的next数组,如果是-1代表没有相同前后缀
var getNext = function (s) {
  let next = [];
    let k = -1,
      j = 1;
    next[0] = -1;
    while (j < s.length) {
      while (k >= 0 && s[k + 1] !== s[j]) {
        k = next[k];
      }
      if (s[k + 1] === s[j]) {
        k++;
      }
      next[j] = k;
      j++;
    }
    return next;
};
```

---

## 七、栈

| 题号                           | 描述                 |
| ------------------------------ | -------------------- |
| 20、有效的括号(eazy)           | 括号匹配是否正确     |
| 1047、删除字符串中所有相邻字符 | 直到删除到无法删除时 |
| 150、逆波兰表达式求值(middle)  | 后缀表达式求结果     |

