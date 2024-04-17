# Arrays
## IS - First Course 2023

### Task - Average 

След въвеждане на цяло число n, да се инициализира масив от n на брой цели числа, като потребителят въвежда n на брой числа. След това да се обходи масива и да се изведат в конзолата всички числа. След това отново да се направи обхождане на масива и да се сметне средното аритметично на числата. (Да се направи и с масив от реални числа).
```
#include <iostream>
#include <cmath>
using namespace std;
/**/

void print(double arr[], size_t len) {
    for (size_t i = 0; i < len; i++)
    {
        cout << "arr[ " << i << " ]= " << arr[i] << endl;
    }
}

double average(double arr[], size_t len) {
    double sum = 0;
    for (size_t i = 0; i < len; i++)
    {
        sum += arr[i];
    }
    return sum / len;
}


int main()
{
    constexpr int SIZE = 4;
    double arr[SIZE] = {3,10,10,3};

    print(arr, SIZE);
    cout << average(arr, SIZE);

}

/*

Getting array from console

int main()
{
    const int i = 3;
    double arr[i];
    for (int i = 0; i < 3; i++)
        cin >> arr[i];

    print(arr, i);
    cout << average(arr, i);

}
*/
```

### Task - Reverse
Въведете масив от n елемента, отпечатайте елементите му наобратно!
```
#include <iostream>
#include <cmath>
using namespace std;
/**/

void reverse(int arr[], int start, int end) {
    while (start < end)
    {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;

        start++;
        end--;
    }
}

void print(int arr[], int size) {
    for (size_t i = 0; i < size; i++)
    {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main()
{
    const int n = 5;
    int arr[n];

    for (size_t i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    reverse(arr, 0, n - 1);
    print(arr, n);
    
    return 0;
}
```

### Task - Min, Max, Second Max, Second Min
Въведете масив от n елемента. Да се изведат в конзолата най - големия срещан елемент в масива и най - малкия. Да се изведат също втория по големина елемент и втория най - малък елемент.
```
#include <iostream>
#include <cmath>
using namespace std;
/**/

int findMinValue(int arr[], size_t len) {
    int min1 = arr[0];
    if (len < 1)
    {
        return -1;
    }
    for (size_t i = 1; i < len; i++)
    {
        if (arr[i] < min1) {
            min1 = arr[i];
        }
        
    }
    return min1;
}

int findNextMinValue(int arr[], size_t len, int min1) {
    if (len < 2) 
    {
        return -1;
    }

    int min2 = -1;
    bool found = false;

    for (size_t i = 0; i < len; i++)
    {
        if (arr[i] != min1 && (arr[i]<min2 || !found))
        {
            min2 = arr[i];
            found = true;
        }
    }
    return min2;
}

int findMaxValue (int arr[], size_t len){
    int max1 = arr[0];
    if (len < 1)
    {
        return -1;
    }

    for (size_t i = 1; i < len; i++)
    {
        if (arr[i] > max1)
        {
            max1 = arr[i];
        }
    }
    return max1;
}

int findNextMaxValue(int arr[], size_t len, int max1) {
    if (len < 2)
    {
        return -1;
    }

    int max2 = -1;
    bool found = false;
    for (size_t i = 0; i < len; i++)
    {
        if (arr[i] != max1 && (!found || max2 < arr[i]))
        {
            max2 = arr[i];
            found = true;
        }
    }
    return max2;
}

int main()
{
    constexpr int n = 5;
    int arr[n];
    for (size_t i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    int minValue = findMinValue(arr, n);
    int maxValue = findMaxValue(arr, n);

    cout << "MinValue = " << minValue << endl
         << "MaxValue = " << maxValue << endl
         << "SecondMin = " << findNextMinValue(arr, n, minValue) << endl
         << "SecondMax = " << findNextMaxValue(arr, n, maxValue) << endl;

    return 0;
}
```
Втори начин за решаване на задачата:
```
#include <iostream>

void arrayInput(int arr[], const int SIZE) {
	for (size_t i = 0; i < SIZE; i++)
	{
		std::cin >> arr[i];
	}
}

void arrayReverse(int arr[], int start, int end) {
	while (start < end)
	{
		int temp = 0;
		temp = arr[start];
		arr[start] = arr[end];
		arr[end] = temp;

		start++;
		end--;
	}	
}

int arrayMin(int arr[], const int SIZE) {
	int min = arr[0];
	for (size_t i = 0; i < SIZE; i++)
	{
		if (min >= arr[i])
		{
			min = arr[i];
		}
	}
	return min;
}

int arraySecondMin(int arr[], const int SIZE) {

    int min = arrayMin(arr, SIZE);
	int secondMin = arr[0] != min ? arr[0] : arr[1];

	for (size_t i = 0; i < SIZE; i++)
	{
		if (arr[i] < secondMin && arr[i] != min)
		{
			secondMin = arr[i];
		}
	}
	
	return secondMin;
}

int arrayMax(int arr[], const int SIZE) {
	int max = arr[0];

	for (size_t i = 0; i < SIZE; i++)
	{
		if (arr[i] >= max)
		{
			max = arr[i];
		}
	}
	return max;
}

int arraySecondMax(int arr[], const int SIZE) {
	int max = arrayMax(arr, SIZE);
	int secondMax = arr[0] != max ? arr[0] : arr[1];

	for (size_t i = 0; i < SIZE; i++)
	{
		if (arr[i] > secondMax && arr[i] != max)
		{
			secondMax = arr[i];
		}
	}
	return secondMax;
}

void arrayOutput(int arr[], const int SIZE) {
	for (size_t i = 0; i < SIZE; i++)
	{
		std::cout << "arr[" << i << "]= " << arr[i] << std::endl;
	}
}

int main() {
	
	const int SIZE = 5;
	int arr[SIZE];
	
	arrayInput(arr, SIZE);
	//arrayReverse(arr, 0, SIZE - 1);
	std::cout << arrayMin(arr, SIZE) << std::endl;
	std::cout << arraySecondMin(arr, SIZE) << std::endl;
	std::cout << arrayMax(arr, SIZE) << std::endl;
	std::cout << arraySecondMax(arr, SIZE) << std::endl;
	//arrayOutput(arr, SIZE);

	return 0;
}

```
### Task - Duplicates
Въведете масив от n елемента и цяло положително число.Да се изведе на конзолата колко пъти го има това число в масива.Също да се изведе на кои позиции сме го срещнали при обхождане.
```
#include <iostream>
#include <cmath>
using namespace std;
/**/

int timesNumSeen(int arr[], int len, int n) {
    int counter = 0;
    for (size_t i = 0; i < len; i++)
    {
        if (arr[i] == n)
        {
            counter++;
        }
    }
    return counter;
}

void positionsNumIsSeen(int arr[], int len, int n) {
    bool found = false;
    cout << "Positions are: ";
    for (size_t i = 0; i < len; i++)
    {
        if (arr[i] == n)
        {
            found = true;
            cout << i << " ";
        }
    }
    if (!found)
    {
        cout << "Number not seen";
    }
}

int main()
{
    constexpr int SIZE = 5;
    int arr[SIZE]; 
    for (size_t i = 0; i < SIZE; i++)
    {
        cin >> arr[i];
    }
    int n;
    cin >> n;

    cout << timesNumSeen(arr, SIZE, n) << endl;
    positionsNumIsSeen(arr, SIZE, n);

    return 0;
}

```

### Task - Linear Search

```
#include <iostream>
using namespace std;

int MyLinearSearch (const int arr[], int len, int n) {
	for (size_t i = 0; i < len; i++)
	{
		if (arr[i] == n)
		{
			return i;
		}
	}
	return -1;
}

int main()
{
	unsigned int n;
	cin >> n;
	constexpr int arrSIZE = 5;
	int arr[arrSIZE] = { 1,2,3,4,5 };
	bool isFound = MyLinearSearch(arr, arrSIZE, n) >= 0;
	cout << isFound;

	return 0;
}
```

### Task - Mirror Array
Въведете масив от n елемента и цяло положително число. Да се провери дали един масив е огледален спрямо средата си.

```
#include <iostream>

void arrayInput(int arr[], const int SIZE) {
	for (size_t i = 0; i < SIZE; i++)
	{
		std::cin >> arr[i];
	}
}



bool isMirror(int arr[], const int SIZE) {
	for (size_t i = 0; i < SIZE / 2; i++)
	{
		if (arr[i] != arr[SIZE - i - 1])
		{
			return false;
		}
	}
	return true;
}

int main() {
	
	const int SIZE = 5;
	int arr[SIZE];
	arrayInput(arr, SIZE);

	if (isMirror(arr, SIZE))
	{
		std::cout << "YES";
	}
	else
	{
		std::cout << "NO";
	}
	return 0;
}
```
