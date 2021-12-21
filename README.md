#include <iostream>

 using namespace std;

int makeArray(int** array, int n, int max, int min)//функция для заполения и вывода двумерного массива

{
    
    int k = 1;
    int z = 0;//счетчик отрицательных чисел

    for (int i = 0; i < n; i++)// заполнение массива и вывод массива
    {

        z = 0;

        

        array[i] = new int[n];

        for (int j = 0; j < n; j++)
        {

            if (i - k%2 >= j)
            {
                array[i][j] = rand() % (max - min + 1) + min;//заполнение массива случайными числами
            
            }
            else
                array[i][j] = 0;

            cout << array[i][j] << " ";// вывод массива

            if (array[i][j] < 0)//если элемент меньше нуля мы его считаем

                z++;

            
            
        }

        if (z > 0)

            cout << " в строке " << z << " отрицательных чисел";

        else

            cout << " в строке нет отрицательных чисел";

        cout << endl;
    
        k++;
    }

    return 0;

}
 int main()
 {
     setlocale(LC_ALL, "rus");
     int r=0;
     int n;//кол-во столбцов и строк
     int max, min;//максимальное минимальное число в массиве
     while (!r)
     {

         cout << "введите колличество столбцов и строк массива > ";
         cin >> n;
         cout << "Введите минимальное значение числа в массиве > ";
         cin >> min;
         cout << "Введите максимальное значение числа в массиве > ";
         cin >> max;
         cout << "массив:" << endl;


         int** array = new int* [n];//инициализация динамического двумерного массива
         for (int i = 0; i < n; i++)
             array[i] = new int[n];
         makeArray(array, n, max, min);


         for (int i = 0; i < n; i++)//удаление массива
             delete[] array[i];
         delete[] array;//удаление самого массива

         cout << "Для расчета введите 0, чтобы закончить нажмите 1 ";
         cin >> r;
     }
     return 0;
 }
