#include <iostream>
#include <chrono>
#include <cmath>

using namespace std;
using namespace chrono;

// Function to count divisors using a simple approach
int divisors(long long n) {
    int count = 0;
    for (long long i = 1; i <= n; ++i) {
        if (n % i == 0) count++;
    }
    return count;
}

// Function to measure execution time of divisors function
void measure_time(long long n) {
    auto start = high_resolution_clock::now();  // Start timer
    divisors(n);  // Execute divisors function
    auto stop = high_resolution_clock::now();  // Stop timer
    auto duration = duration_cast<milliseconds>(stop - start);  // Calculate duration

    cout << "Execution time for n = " << n << " : " << duration.count() << " ms" << endl;
}

int main() {
    // Large values for testing
    long long values[] = {static_cast<long long>(1e6), static_cast<long long>(1e7),
                          static_cast<long long>(1e8), static_cast<long long>(1e9),
                          static_cast<long long>(1e10)};

    cout << "Divisors function execution times:" << endl;

    for (long long n : values) {
        measure_time(n);
    }

    return 0;
}
