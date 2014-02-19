---
layout: post
title: "最大连续子序列和"
date: 2014-02-19 13:23:39 +0800
comments: true
categories: 算法 leetcode 
---
<article>
<section>
<h1>原题：Gas Station</h1>
{% img /images/gas-station.png %}
</section>
<!-- more -->
<section>
<h1>解题方法</h1>
<p>本题总共需要两步，首先需要判断汽车时候可以跑完全程，如果可以，则需要指出汽车开始的位置。</p>
<p>对于汽车能否跑完全程，有一个结论：如果gas总和大于cost总和，则汽车一定能跑完。这个结论可以通过反证法证明。</p>
<p>对于找到汽车的出发点，问题可以转变成求循环数组的最大连续子序列和，这也是本文的重点。</p>
<p>求法有两种，第一种是直接遍历每一个起点和每一个终点，时间复杂度是(n**2)。在这道题时超时了。</p>
<h2>正确解法</h2>
变量sum[i]表示以i结尾的路程的最大子序列和，则
{% codeblock lang:python %}
if sum[i]>0:
	sum[i+1] = sum[i] + gas[i] - cost[i]
else:
	sum[i+1] = sum[i]
{% endcodeblock %}
这样遍历一次就可以得到最大的子序列和以及起始和终止坐标。具体代码如下：
{% codeblock lang:python %}
class Solution:
	def canCompleteCircuit(self, gas, cost):
		if sum(gas)<sum(cost):
			return -1
		length = len(gas)
		data = [gas[i]-cost[i] for i in range(length)]
		beg = -1
		end = -1
		total = -1
		i = 0
		resultBeg = 0
		result = -1
		while beg<gas:
			if i==beg:
				break
			if total<0:
				total = data[i]
				beg = i
			else:
				total = total + data[i]
			if total > result:
				resultBeg = beg
				result = total
			i = (i+1)%length
		return resultBeg
{% endcodeblock %}
