## excel读写
```
from xlutils.copy import copy
import xlrd
import xlwt
# 写
rb = xlrd.open_workbook(excel_path)
wb = copy(rb)
ws = wb.get_sheet(sheet_name)
ws.write(row, col, text)
os.remove(excel_path)
wb.save(excel_path) # 只能保存为xls格式
# 读
rb = xlrd.open_workbook(excel_path)
for rs in rb.sheets():
    rows = rs.nrows
    cols = rs.ncols
    for i in range(rows):
        for j in range(cols):
            print rs.cell(i,j).value
```
## plt画图
https://matplotlib.org/api/pyplot_summary.html
plt颜色板 https://www.cnblogs.com/qianblue/p/10783261.html
```
import matplotlib.pyplot as plt
plt.switch_backend('agg')

fig = plt.figure(0) # 新图 0
plt.plot(x, y, 'o') # 画点
plt.plot(x, y) # 画线
plt.legend()
plt.savefig('1.png')
plt.close(0)
```
## sys
* python导入同级别模块import xxx，要导入下级目录，需要在下级目录中写一个__init__.py文件from dirname import xxx，要导入上级目录，可以使用sys.path：首先sys.path的作用是：当使用import语句导入模块时，解释器会搜索当前模块所在目录以及sys.path指定的路径去找需要import的模块。
```
import sys
sys.path.append('../')
from fatherdirname import xxx
```
##Docker
```sh
docker pull $address
docker run -it -d -rm -v $docker_dst:$dst -u root --name $name $container
docker exec -u root -it $name bash
docker commit container_id new_container # 保存镜像, 在保存之前要把image run起来，container_id在image命令行的前面name@id
```

