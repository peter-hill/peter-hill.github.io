## 刷题计划

### DataStructure

#### Array

|  Easy   | Medium  |
| :-----: | :-----: |
| 001/268 | 078/090 |

```python
# 001
from typing import List


class Solution:

    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            j = i+1
            for j in range(len(nums)):
                if nums[i] + nums[j] == target:
                    a = []
                    a.append(j)
                    a.append(i)
                    return a


if __name__ == "__main__":
    S = Solution
    nums = [2, 7, 11, 15]
    target = 9
    print(S.twoSum(S, nums,target))

```

```python
# 268
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        for i in range(0, n+1):
            if i not in nums:
                return i
```

```python
# 78
# 递归 依次在已有的字列表加上新的元素 形成新的子集
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        result = [[]]

        for num in nums:
            for i in result:
                result = result + [i + [num]]
                # continue本次循环
                # break当前循环
                # return整个函数
        return result
```

```python
# 78(1)
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
      result = [[]]
      
      for num in nums:
        result += [a + [num] for a in result]
        
      return result
```

```python
# 90
# 排序的原因是列表是有序的，若nums存在重复项且中间夹杂了其他数，会产生重复子集
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        result = [[]]

        nums1 = sorted(nums)

        for num in nums1:
            for curr in result:
                tmp = curr + [num]
                # result = result + tmp
                if tmp in result:
                    continue
                else:
                    result = result + [tmp]

        return result
```

* 列表的`list +=` 和 `list = list +`的区别是，前者与extend一致，仅加在当前对象的当前地址，后者是copy了对象，放在新的地址
  * 存在的问题是：在问题`78`中用列表生成式用前者没有问题，使用双层循环是用前者会死循环?
* break：跳出所在的当前整个循环，到外层代码继续执行。
* continue：跳出本次循环，从下一个迭代继续运行循环，内层循环执行完毕，外层代码继续运行。
* return：直接返回函数，所有该函数体内的代码（包括循环体）都不会再执行。

---



#### linkedlist

|  Easy   | Medium  |
| :-----: | :-----: |
| 344/021 | 002/024 |

```python
# 344
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        # len(s)
        # # 挨个更改地址指向
        # print(s[0])
        # print(s[1])
        for i in range(0, int(len(s)/2)):
            tmp = s[i]
            s[i] = s[(len(s)-1)-i]
            s[(len(s)-1)-i] = tmp
            
```

```python
#22
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        res = ListNode()
        cur = res
        while l1 != None and l2 != None:
            if l1.val <= l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next

            cur = cur.next

        cur.next = l1 or l2
        return res.next
```



#### Queue

|  Easy   | Medium  |
| :-----: | :-----: |
| 933/225 | 622/641 |

#### Stack

|  Easy   | Medium  |
| :-----: | :-----: |
| 020/232 | 071/394 |

#### Heap

|   Easy   | Medium  |
| :------: | :-----: |
| 703/1046 | 215/692 |

#### Hash Table

|  Easy   | Medium  |
| :-----: | :-----: |
| 217/389 | 049/560 |

#### Tree

|    Easy     | Medium  |
| :---------: | :-----: |
| 938/700/144 | 094/145 |



### Algorithm

#### Binary Search

|  Easy   | Medium  |
| :-----: | :-----: |
| 704/035 | 074/162 |

#### Two pointers

|    Easy    | Medium |
| :--------: | :----: |
| 27/344/125 |  287   |

#### Sliding Window

| Easy | Medium  |
| :--: | :-----: |
|      | 003/424 |

#### Backtracking

| Easy |   Medium    |
| :--: | :---------: |
| 401  | 046/078/077 |

#### 广度优先搜索BFS

|  Easy   | Medium  |
| :-----: | :-----: |
| 559/690 | 200/207 |

#### 深度优先搜索DFS

|  Easy   | Medium  |
| :-----: | :-----: |
| 100/101 | 200/721 |

#### 分治法Divide & Conquer

|  Easy   | Medium  |
| :-----: | :-----: |
| 169/052 | 215/240 |

#### 递归Recursion

|  Easy   | Medium |
| :-----: | :----: |
| 687/783 |  938   |

#### 拓扑排序Topologic Sort

|  Easy   | Medium |
| :-----: | :----: |
| 207/210 |        |

#### Trie

|  Easy   | Medium  |
| :-----: | :-----: |
| 720/211 | 692/676 |

#### Union Find

|  Easy   | Medium  |
| :-----: | :-----: |
| 200/547 | 721/130 |

#### 动态规划

|  Easy   | Medium  |
| :-----: | :-----: |
| 070/121 | 05/1143 |



---

位置参数 默认参数 包裹位置 包关键字



使用默认参数要放在*args之后（放在之后不可修改）



修改默认要放在*args之前，不可以是开头

