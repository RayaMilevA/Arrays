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
