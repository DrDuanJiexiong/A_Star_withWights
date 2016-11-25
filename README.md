# A_Star_withWights
an implementation of A star algorithm with wights

#main.cpp

#include <iostream>  
#include <stdlib.h>
#include <ctime>
#include <fstream>
#include <chrono>
#include "a-star.h"

using namespace std;

int main()
{
	//初始化地图，用二维矩阵代表地图
	vector<vector<int>> maze = {
		{ 10, 30, 60, 80, 40 },
		{ 999, 10, 90, 10, 40 },
		{ 999, 999, 20, 10, 100},
		{ 120, 30, 10, 180, 80 },
		{ 10, 130, 110, 1000, 10 },
		};
  
	Astar astar;
	astar.InitAstar(maze);

	//设置起始和结束点  
	Point start(0, 0);
	Point end(36, 44);
	//A*算法找寻路径
	auto start_time = chrono::system_clock::now();
	list<Point *> path = astar.GetPath(start, end, true);
	auto end_time = chrono::system_clock::now();

	cout << "本次寻路耗时" << chrono::duration_cast<chrono::microseconds>(end_time - start_time).count() << "毫秒" << endl;


	//打印  
	for (auto &p : path)
		cout << '(' << p->x << ',' << p->y << ')' << endl;

	system("pause");
	return 0;
}
