## LeetCode_0017_电话号码的字母组合（中等, 2022-10）
<!--info
tags: [字符串, dfs, lc100]
source: LeetCode
level: 中等
number: '0017'
name: 电话号码的字母组合
companies: []
-->

> [17. 电话号码的字母组合 - 力扣（LeetCode）](https://leetcode.cn/problems/letter-combinations-of-a-phone-number)

<summary><b>问题简述</b></summary>

```txt
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。答案可以按 任意顺序 返回。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

示例 1：
    输入：digits = "23"
    输出：["ad","ae","af","bd","be","bf","cd","ce","cf"]
示例 2：
    输入：digits = ""
    输出：[]
示例 3：
    输入：digits = "2"
    输出：["a","b","c"]
```

<!-- 
<details><summary><b>详细描述</b></summary>

```txt
```

</details>
-->

<!-- <div align="center"><img src="../../../_assets/xxx.png" height="300" /></div> -->

<summary><b>思路</b></summary>

- 组合问题，DFS 模板；

<details><summary><b>Python</b></summary>

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits: return []

        tb = {
            '2': 'abc',
            '3': 'def',
            '4': 'ghi',
            '5': 'jkl',
            '6': 'mno',
            '7': 'pqrs',
            '8': 'tuv',
            '9': 'wxyz'
        }

        ret = []

        def dfs(i, tmp):
            if i == len(digits):
                ret.append(''.join(tmp))
                return
            
            for c in tb[digits[i]]:
                tmp.append(c)
                dfs(i + 1, tmp)
                tmp.pop()  # 回溯

        dfs(0, [])
        return ret
```

</details>
