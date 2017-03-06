# matlab
## 导入数据
1. 用“导入数据”按钮直接导入数据
2. 在工作区“新建变量”
3. 将数据保存在.txt或.m/.mat文件中，放在当前工作目录中，用load函数调用，文件名=变量名。导出数据用save命令。'save 'b.txt' B -ascii %(把矩阵B的数据,导出到了TXT文件中，名字为b.txt)，注意空格，-ascii 前有空格。'
	
		>> load('portfolio_opt_Mar5_variables.mat')
		
4. 用dlmread函数。

		A=dlmread('data.m')
		
5. 从excel中读取

		A = xlsread('yi.xlsx')
	
	导出到excel
	
		xlswrite('a.xlsx',a)
		
## 数组的引用
对于数组A，下标的引用是***先行后列***，且可以同时引用多行多列。 引用第三行第二列的元素，A（3，2）。
有三种方法可以引用数组：

1. 下标法
	
		A(i,j)
	i和j可以是一维向量、标量、“：”号或者“end”。
	“：”引用所有行所有列；“end“引用最后一行或列；”end-n“引用倒数第n+1行或列。
	例^[1]
	
		>>A=magic(3)

		A =
		     8     1     6
		     3     5     7
		     4     9     2
		     
		>>A(2:3,3:-1:1)

		ans =
		     7     5     3
		     2     9     4
		     
		>>A(:,end)

		ans =
		     6
		     7
		     2
		
		>>A(1,end-1)
		
		ans =
		     1
		
		>>A([2 1 3 3],[1 1 2 2 1])
		
		ans =
		     3     3     5     5     3
		     8     8     1     1     8
		     4     4     9     9     4
		     4     4     9     9     4
2. 索引法
3. 布尔法

## size 数组维度
size()有如下几种用法：^[2]

	d = size(X)
	[m,n] = size(X)
	m = size(X,dim)
	[d1,d2,d3,...,dn] = size(X)
	
1. d = size(X)

返回一个矢量，包括X的行和列。如果X是标量，则返回[1 1]；如果是3*4矩阵，则返回[3 4]。

2. [m,n] = size(X)

如果X是一个矩阵，则返回行与列的大小。

3. m = size(X,dim)

dim是一个标量，这个函数返回第dim纬度的大小，如：
	
	A = rand(2,3,4)
	sz = size(A)
	>> sz = 
		2 3 4
	
	szdim2 = size(A,2)
	%返回第二个维度（列）的大小
	>> szdim2 = 
		3
		
因此当dim=1，返回行数；dim=2时，返回列数。
	
4. [d1,d2,...,dn] = size(X)

分别返回各纬度的大小，如：

	A = rand(3,4,5)
	[d1,d2,d3] = size(A)
	>> d1 = 
		3
	>> d2 = 
		4
	>> d3 = 
		5
	
	[d1,d2] = size(A)
	>> d1 = 
		3
	>> d2 = 
		20
	% 第二第三维的大小一起包括在d2中
	
	[d1,d2,d3,d4,d5] = size(A)
	%d1,d2,d3分别是2，3，4
	>> d4 = 
		1
	>> d5 = 
		1
	%默认大小为1
		

[1]http://blog.sina.com.cn/s/blog_630c70530100i8cb.html
[2]https://cn.mathworks.com/help/matlab/ref/size.html
