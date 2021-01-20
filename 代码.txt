#include<iostream>
using namespace std;
#include<vector>
#include<algorithm>
#include<functional>

class solution {
public:
	double findMedianSortArrays(vector<int>& num1, vector<int>& num2){
		int len = num1.size()+ num2.size();
		int size1 = num1.size(), size2 = num2.size();
		int *p = new int[len];
		
		int i = 0, j = 0, num3 = 0;
		while (i < size1 && j < size2) //1、两个数组元素都不为空。
		{
			if (num1[i] <= num2[j]) 
			{
				p[num3] = num1[i];
				i++;
			}
			else 
			{
				p[num3] = num2[j];
				j++;
			}
			num3++;
		}
		while (i < size1) //2、数组1元素不为空，数组2元素为空。
		{
			p[num3++] = num1[i++];
		}
		while (j < size2) //3、数组2元素不为空，数组1元素为空。
		{
			p[num3++] = num2[j++];
		}
		cout << "合并后数组为：";
		for (int i = 0; i < len; i++)//打印合并后的数组
		{
			cout << p[i];
		}
		double result;
		if ((size1 + size2)%2 ==1) //如果元素为奇数，直接取中位数
		{
			result = p[(size1 + size2) / 2];
		}
		else //如果元素为偶数，取中间两元素和的平均。
		{
			result = (double(p[(size1 + size2) / 2]) + double(p[(size1 + size2) / 2 - 1])) / 2;
		}
	
		cout << endl;
		cout << "中位数为 "<<result << endl;//打印中位数结果。
		delete[]p;
		return result;
	
	}
};
int main()
{
	vector<int> v1;
	vector<int> v2;
	v1.push_back(1);
	v1.push_back(3);
	v2.push_back(2);

	solution test;
	
	test.findMedianSortArrays(v1, v2);

	system("pause");
	return 0;
}