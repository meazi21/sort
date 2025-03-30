#include <iostream>
#include <algorithm>
using namespace std;

int sequentialSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = (left + right) / 2;
        
        if (arr[mid] == target) {
            return mid;
        }
        else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;
}

int main() {
    int n, target;

    cout << "Enter the number of elements: ";
    cin >> n;
    
    int arr[n];

    cout << "Enter the elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Enter the target element to search: ";
    cin >> target;

    int seqResult = sequentialSearch(arr, n, target);
    if (seqResult != -1) {
        cout << "Sequential Search: Element found at index " << seqResult << endl;
    } else {
        cout << "Sequential Search: Element not found" << endl;
    }

    sort(arr, arr + n);
    cout << "Array after sorting (for Binary Search): ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    int binResult = binarySearch(arr, n, target);
    if (binResult != -1) {
        cout << "Binary Search: Element found at index " << binResult << endl;
    } else {
        cout << "Binary Search: Element not found" << endl;
    }

    return 0;
}
