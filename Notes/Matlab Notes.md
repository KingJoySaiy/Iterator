## 注意点

* **下标从1开始**，控制语句以**end结束**；
* **^** 符意为power而非xor，**~=** 符意为不等；
* **bool** 仅用0和1表示；
* 缩进非必要（区别于Python），但建议 **多缩进**以保证可读性；
* 多用 **help [keyword]** 以查看reference；
* 测试环境为 **Octave** 而非 **Matlab** ，可能有部分语法不兼容；

### I. 基础

### 1.1 常用操作符

| Operator       |                      |
| -------------- | -------------------- |
| %              | 单行注释             |
| %{......%}     | 多行注释             |
| +-*/           | 四则运算 |
| a ^ b          | a的b次方             |
| a == b / a~= b | 判断是否相等         |
| && / \|\|      | 逻辑与或（返回0或1） |
|xor(a, b)|逻辑异或（返回0或1）|
| bitand(a, b) / bitor(a, b) / bitxor(a, b) | 按位与 / 或 / 异或 |
|0:1:10|三目运算，表示[0,10]区间步长为1的序列|

### 1.2 关键字

| Keyword |      |
| ------- | ---- |
| pi | 圆周率常量（double） |
| int8(a) / int16(a) / int32(a) | 强制转换为8 / 16 / 32位有符号整数 |
| uint8(a) / uint16(a) / uint32(a) | 强制转换为8 / 16 / 32位无符号整数 |
| single(a) / double(a) | 强制转换为单精度 / 双精度浮点数 |
| help [...] | 查看方法的使用规则 |
| type [...] | 查看方法的类型 |
| format [short / long / hex] | 修改默认格式为5/15字长定点数 / 16进制（默认short） |
| who | 查看当前工作空间中的所有变量名 |
| pwd | 查看当前路径（linux通用） |
| ls / dir | 查看当前路径下的所有文件（linux通用） |
| cd '/home/joy' | 更改当前路径（linux通用） |
| load('test.dat') | 加载数据（变量名即为文件名） |
| save test.dat a [-ascii] | 将变量a保存到当前路径的test.dat中（保存为ascii码） |
|clc|清空历史命令|
|clear| 清空所有变量|
|exit / quit|退出matlab / octave程序|
|||


### 1.3 常用方法

| Method |      |
| ------ | ---- |
| sprintf('%.10f', pi) | 格式化输出 |
| disp(a) / display(a) | 输出a |
| floor(a) / ceil(a) | 浮点数向下 / 上取整 |
| round(a) | 四舍五入取整 |
| abs(a) | 取绝对值（整数、浮点数、复数均可） |
| complex(2, 3) | 复数 |
| real(a) / imag(a) | 实部 / 虚部 |
| size(a) / size(a, i) | 获取矩阵的维度 / 第i维的长度 |
| rand / rand(3, 5) | 生成随机数 / 3*5的随机矩阵，范围(0, 1) |
| length(a) | 字符串长度 / 矩阵最大维度 |
| max(a) | 矩阵第一维度的最大值 |
| log(a) | 取对数 |
| exp(a) | 取指数 |
| sum(a) | 矩阵第一维度元素之和 |
| prod(a) | 矩阵第一维度元素之积 |
|error('error!')|终止程序并显示错误信息|
|||


## II. 矩阵

### 2.1 矩阵定义

* `[1:2:10]` [1, 3]闭区间步长为2的行向量
* `[1, 2, 3] / [1; 2; 3]` 行向量 / 列向量
* `ones(2, 3)` 维度为(2*3)的全为1的矩阵
* `zeros(3, 4)` 维度为(3*5)的零矩阵
* `eye(10)` 10阶单位矩阵
* `rand(2, 3)`随机矩阵，范围均为(0, 1)

### 2.2 矩阵操作

* `a(:)` a并入一个列向量
* `a(3, 5)` 第3行第5列元素
* `a(2, :) / a(:,2)` 第2行 / 列所有元素
* `a([1 3], :) / a([1,3], :)` 第1行和第3行所有元素
* `a = [a, [4; 5; 6]] / a = [b, c]` 在右边新添列矩阵（必须行数相等）
* `a = [a; [4, 5, 6]] / a = [b; c]` 在下面新添行矩阵（必须列数相等）
* `a*b` 矩阵乘法（a列数==b行数）
* `a.*b`矩阵对应位置的元素相乘（matlab矩阵不支持broadcasting）
* `a.^2 / a.+1 / a.-3...` 类似的数字运算支持broadcasting
* `a<10` 逐位进行逻辑判断，返回bool矩阵
* `a'` 矩阵的转置
* `inv(a) / pinv(a)` 矩阵的逆 / 伪逆

## III. 绘图

### 3.1 二维线图plot

* `plot(x, y)` 绘制二维图（默认蓝色实线），x和y需要映射关系例如：`x=0:0.1:10, y=sin(x)`
* `plot(x1, y1, x2, y2...)` 绘制多个函数
* `plot(x, y, 'r')` 更改linestyle，颜色：`r, g, b, y, k`红绿蓝黄黑，类型：`-, --, -., .`实,虚,点虚,点
* `xlable('key'), ylable('value')` 标记横轴纵轴名称
* `legend('sin', 'cos'...)` 右上角图例（多个函数可标记多个图例）
* `title('plotTest')` 设置标题
* `print -dpng 'plotTest.png'` 保存plot绘制的图到当前路径（标题已设置）
* `close` 关闭图像
* `figure(1), figure(2)...` 打开多张图（plot将绘制在上一个figure上）
* `subplot(2, 3, 1)` 打开2行3列的6张图，并选择第1张进行绘制
* `axis([1, 10, 2, 233])` 设置横轴刻度[1, 10]，纵轴刻度[2, 233]
* `hold on` 保持当前图不变，新图将在旧图上添加，而不被覆盖
* `clf` 删除当前figure上的所有图形

### 3.2 数据分布图

* `imagesc(a)` 根据矩阵数值不同绘制彩色方格图，不同颜色对应不同值
* `colorbar` 在当前figure上添加颜色条，标注不同颜色对应的数值
* `colormap rainbow` 修改颜色分布，常用：`rainbow, gray, hot, cool, spring, summer, autumn, winter, pink, ocean`

## IV. 控制与函数

### 4.1 for-loop

```matlab
a = [1, 2; 3, 4];
for i = 1 : length(a) # for
  for j = 1 : length(a(i,:))
    if a(i, j) == 2 # if
      disp('it''s 2') # '' means ' in string
    elseif a(i, j) == 3 # elseif
      disp('it''s 3')
    else continue # continue
    endif
    disp(a(i, j));
  endfor
endfor	# endif / endfor / endwhile...can be end
```

### 4.2 while-loop

```matlab
n = 10;
res = 1;
while n # while
  res *= n;
  n--;
  switch n	# switch-case-otherwise
    case 7 disp('seven');
    case 6 disp('six');
    case 5 break; # break
    otherwise continue;
  endswitch
endwhile
disp(res);
```

* `continue, break, switch-case-otherwise`等用法已给出。

### 4.3 函数

```matlab
function y = fun(x)
	y = x^2;
end
disp(fun(3));
```

