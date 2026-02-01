# DZ_12_4

#include <iostream>
#include <fstream>
#include <string>
#include <windows.h>
using namespace std;

int main()
{
	//setlocale(LC_ALL, "Russian");
	//SetConsoleCP(1251);
	//SetConsoleOutputCP(1251);

	std::ifstream ifile{ "in.txt" };

	if (!ifile)
	{
		cout << "Ошибка открытия файла\n";
		return 1;
	}

	int a, b;
	ifile >> a >> b;

	int** arr = new int*[a];

	// создаем двумерный массив
	for (int i = 0; i < a; i++)
	{
		arr[i] = new int[b];
	}

	// заполняем массив из файла
	for (int i = 0; i < a; i++)
	{
		for (int j = 0; j < b; j++)
		{
			ifile >> arr[i][j];
		}
	}

	// выводим с разворотом каждой строки
	for (int i = 0; i < a; i++)
	{
		for (int j = b - 1; j >= 0; j--)
		{
			cout << arr[i][j] << " ";
		}
		cout << endl;
	}

	for (int i = 0; i < a; i++) // освобождаем память
	{
		delete[] arr[i];
	}
	delete[] arr;

	ifile.close();

	return 0;
}
