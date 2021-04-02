1，创建工作簿

```python
from openpyxl import Workbook, load_workbook

wb = Workbook()
ws = wb.active
ws1 = wb.create_sheet("Mysheet")
ws2 = wb.create_sheet("Mysheet", 0)
ws3 = wb.create_sheet("Mysheet", -1)
ws.title = "New Title"
print(wb.sheetnames)
for sheet in wb:
    print(sheet.title)
```



2，访问一个单元

```python
c = ws['A4']
ws['A4'] = 4
d = ws.cell(row=4, column=2, value=10)
```



3，访问多个单元格

```python
cell_range = ws['A1':'C2']
for row in ws.iter_rows('A1:C2'):
	for cell in row:
		print(cell)
for row in sheet.iter_cols(min_row=1, min_col=1, max_row=6, max_col=3):
    for cell in row:
        print(cell.value, end=" ")
```

