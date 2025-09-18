# Source Code for Matrix and Vector Computations

## Point 1: Vector Computation in Python

```python
import numpy as np

# Define parameters
a = 3
N_values = [1, 10, 10**6, 10**8]  # Different values of N

# Store results
results = {}

for N in N_values:
    x = np.full(N, 0.1)  # Vector x with all elements 0.1
    y = np.full(N, 7.1)  # Vector y with all elements 7.1

    # Compute d = a*x + y
    d = a * x + y

    # Test using np.isclose() instead of ==
    all_correct = np.all(np.isclose(d, 7.4, atol=1e-9))  # Tolerance of 1e-9

    # Store the results
    results[N] = all_correct

# Print results
for N, is_correct in results.items():
    print(f"For N = {N}, all elements correct: {is_correct}")
```

## Point 2: Vector Computation in C

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <math.h>

#define EPSILON 1e-9  // Tolerance for floating-point comparison

// Function to check if all elements in array are close to expected value
bool is_close(double *d, double expected, int N) {
    for (int i = 0; i < N; i++) {
        if (fabs(d[i] - expected) > EPSILON) {
            return false;
        }
    }
    return true;
}

int main() {
    int N_values[] = {1, 10, 1000000, 100000000};  // Different sizes of N
    int num_sizes = sizeof(N_values) / sizeof(N_values[0]);

    double a = 3.0;
    double expected_value = 7.4;

    for (int i = 0; i < num_sizes; i++) {
        int N = N_values[i];

        // Allocate memory for vectors
        double *x = (double *)malloc(N * sizeof(double));
        double *y = (double *)malloc(N * sizeof(double));
        double *d = (double *)malloc(N * sizeof(double));

        if (x == NULL || y == NULL || d == NULL) {
            printf("Memory allocation failed for N = %d\n", N);
            exit(1);
        }

        // Initialize x and y
        for (int j = 0; j < N; j++) {
            x[j] = 0.1;
            y[j] = 7.1;
        }

        // Compute d = a * x + y
        for (int j = 0; j < N; j++) {
            d[j] = a * x[j] + y[j];
        }

        // Check if all values are approximately 7.4
        bool all_correct = is_close(d, expected_value, N);

        // Print the result
        printf("For N = %d, all elements correct: %s\n", N, all_correct ? "True" : "False");

        // Free allocated memory
        free(x);
        free(y);
        free(d);
    }

    return 0;
}
```

## Point 3: Matrix Multiplication

### Python Implementation

```python
import numpy as np

# Define matrix sizes
N_values = [10, 100, 10000]

# Store results
results = {}

for N in N_values:
    # Create NxN matrices A and B
    A = np.full((N, N), 3.0)    # A filled with 3
    B = np.full((N, N), 7.1)    # B filled with 7.1

    # Compute matrix multiplication C = A * B
    C = np.dot(A, B)  # Or C = A @ B (same in NumPy)

    # Check if all elements are approximately 21.3 * N
    all_correct = np.all(np.isclose(C, 21.3 * N, atol=1e-9))

    # Store result
    results[N] = all_correct

# Print results
for N, is_correct in results.items():
    print(f"For N = {N}, all elements correct: {is_correct}")
```

### C Implementation

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <math.h>

#define EPSILON 1e-9  // Tolerance for floating-point comparison

// Function to check if all elements in matrix C are close to expected value
bool is_close(double **C, double expected, int N) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (fabs(C[i][j] - expected) > EPSILON) {
                return false;
            }
        }
    }
    return true;
}

int main() {
    int N_values[] = {10, 100, 10000};  // Different sizes
    int num_sizes = sizeof(N_values) / sizeof(N_values[0]);

    double expected_value = 21.3;

    for (int i = 0; i < num_sizes; i++) {
        int N = N_values[i];

        // Allocate memory for matrices
        double **A = (double **)malloc(N * sizeof(double *));
        double **B = (double **)malloc(N * sizeof(double *));
        double **C = (double **)malloc(N * sizeof(double *));
        for (int j = 0; j < N; j++) {
            A[j] = (double *)malloc(N * sizeof(double));
            B[j] = (double *)malloc(N * sizeof(double));
            C[j] = (double *)malloc(N * sizeof(double));
        }

        // Initialize matrices A and B
        for (int j = 0; j < N; j++) {
            for (int k = 0; k < N; k++) {
                A[j][k] = 3.0;
                B[j][k] = 7.1;
            }
        }

        // Compute C = A * B
        for (int j = 0; j < N; j++) {
            for (int k = 0; k < N; k++) {
                C[j][k] = 0;
                for (int l = 0; l < N; l++) {
                    C[j][k] += A[j][l] * B[l][k];
                }
            }
        }

        // Check if all values are approximately 21.3 * N
        bool all_correct = is_close(C, expected_value * N, N);

        // Print the result
        printf("For N = %d, all elements correct: %s\n", N, all_correct ? "True" : "False");

        // Free allocated memory
        for (int j = 0; j < N; j++) {
            free(A[j]);
            free(B[j]);
            free(C[j]);
        }
        free(A);
        free(B);
        free(C);
    }

    return 0;
}
```

## Discussion

### 1. Problems Running the Code?
- No issues were encountered.
- C was **faster** than Python due to **manual memory allocation** and lower-level optimizations.

### 2. Did the Computation Validate Correctly?
- Initially, floating-point **precision issues** caused incorrect results.
- Fixed using **np.isclose()** in Python and **EPSILON-based checks** in C.
- In **Point 3 (Matrix Multiplication)**, the expected value should be **21.3 * N**, not **21.3**.

---

