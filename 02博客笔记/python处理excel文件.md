---
title: python处理excel文件
date: 2020-03-04 01:25:16
categories:
- python
---
## python处理excel文件
**起因**：女朋友在手动处理excel文件，说她处理得好烦。我就看了一下需求，。发现可以用python来处理。  
**需求**：一个excel表格，只有一列的内容，每隔五行为一道选择题，需要把每道题都拎出来成为独立一行。放入到一个新的表格中。  
**格式**：  
输入表
  
  
| A1 |
| - |
| A2 |
| A3 |
| A4 |
| A5 |
| B1 |
| B2 |
| B3 |
| B4 |
| B5 |
  
  
输出表
  
  
| A1 | A2 | A3 | A4 | A5 |
| --- | :--: | :--: | :--: | :--: |
| B1 | B2 | B3 | B4 | B5 |
  
  
**代码**：
```
#!coding:utf8
import xlrd    #读取模块
import openpyxl  #写入模块

# 设置好输入和输出文件
f1 = xlrd.open_workbook(r'C:\Users\53517\Desktop\人工智能导论题库 (100题).xlsx')
sheet1 = f1.sheet_by_index(1)  #读取excel表格中的第一个表格
num = sheet1.col_values(1)  #第一个表格中的第一列

workbook = openpyxl.Workbook()  #临时存储对象
sheet = workbook.active
sheet.title = 'test'  #新生成表的名字
long = len(num)     #总行数
print(long)


k = 0
for i in range(0, long/5):
    for j in range(0, 5):
        sheet.cell(row=i + 1, column=j + 1, value=str(num[k]))
        k += 1
workbook.save(r'C:\Users\53517\Desktop\output1.xlsx')
```


