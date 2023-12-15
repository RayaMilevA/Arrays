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

### Task - 

```

```

