### Cout输出控制
头文件：#include <iomanip>
  
#### 进制：	//作用永久

1. dec 置基数为10 相当于"%d"
2. hex 置基数为16 相当于"%X"
3. oct 置基数为8 相当于"%o"

#### 其他：
1. setw(n) 设域宽为n个字符		//作用临时，仅对之后的数字有效，设行宽如果小于precision的值，那么就按precision显示，行宽大于precision值就在数字前进行填充
2. setprecision(n) 设显示小数精度为n位	//作用永久，加在setioflags(ios::fixed)之后可以改变小数点位数
3. setbase (n) 设置输出数字的基数，只能设置为8，10，16
4. setfill(c) 设填充字符为c，前部填充	//作用永久
