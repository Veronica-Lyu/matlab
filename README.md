# matlab
## 导入数据
1. 用“导入数据”按钮直接导入数据
2. 在工作区“新建变量”
3. 将数据保存在.txt或.m文件中，放在当前工作目录中，用load函数调用，文件名=变量名。导出数据用save命令。
		
		save 'b.txt' B -ascii %(把矩阵B的数据,导出到了TXT文件中，名字为b.txt)，注意空格，-ascii 前有空格。
		
4. 用dlmread函数。

		A=dlmread('data.m')
		
5. 从excel中读取

		A = xlsread('yi.xlsx')
	
	导出到excel
	
		xlswrite('a.xlsx',a)
		
## 数组的引用
对于数组A，下标的引用是***先行后列***。 引用第三行第二列的元素，A（3，2）。
有三种方法可以引用数组：
1. 下标法
	
2. 索引法
3. 布尔法