# task-10
#include <iostream>
#include <vector>

using namespace std;

void swapByPointer(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int sumByPointer(const int *p, int size) {
    int suma = 0;
    const int *end = p + size;
    while (p < end) {
        suma += *p;
        p++;
    }
    return suma;
}

int *findMax(int *p, int size) {
    if (size <= 0) return nullptr;
    int *max_ptr = p;
    int *end = p + size;
    p++;
    while (p < end) {
        if (*p > *max_ptr) {
            max_ptr = p;
        }
        p++;
    }
    return max_ptr;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int n;
    if (!(cin >> n)) return 0;

    vector<int> a(n);
    for (int i = 0; i < n; ++i) {
        cin >> a[i];
    }

    int suma = sumByPointer(a.data(), n);
    cout << "suma " << suma << "\n";

    int *max_ptr = findMax(a.data(), n);
    int max_index = max_ptr - a.data();
    cout << "max " << *max_ptr << " index " << max_index << "\n";

    swapByPointer(a.data(), max_ptr);

    cout << "pislia obminu";
    int *p = a.data();
    int *end = a.data() + n;
    while (p < end) {
        cout << " " << *p;
        p++;
    }
    cout << "\n";

    return 0;
}
