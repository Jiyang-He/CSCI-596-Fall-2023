# CSCI-596 Fall 2023 Project


The project was conducted by Jiyang He, Citina Liang, and Yinxiao Ye, focusing on exploring the fundamental linear algebra function, GEMM. Initially, we developed our own GEMM function using a basic loop-based approach. Progressively, we incorporated optimization techniques including SIMD, Loop Unrolling, Blocking, and Parallelization, documenting the performance impact of each.

In the project's second phase, we evaluated the performance of various Basic Linear Algebra Subprograms (BLAS) such as the Intel Math Kernel Library ([MKL](https://www.intel.com/content/www/us/en/developer/tools/oneapi/onemkl.html)) and OpenBLAS ([OpenBLAS](https://www.openblas.net/)). These BLAS are essential for common linear algebra operations like vector addition, scalar multiplication, dot products, linear combinations, and matrix multiplication, which are crucial for modern numerical software and machine learning. Starting with General Matrix Multiply (GEMM), we extended our analysis to more complex operations like matrix factorization, aiming to provide performance insights and an understanding of the underlying mechanics.


## GEMM from Scratch

We start writing or GEMM function from the basic loop-based approach. Progressively, we incorporated optimization techniques including SIMD, Loop Unrolling, Blocking, and Parallelization, documenting the performance impact of each.

### Setup
For clarity and simplicity, our analysis is confined solely to DGEMM. We conducted ten iterations of the DGEMM operation using 512x512 matrix dimensions for each algorithm. During these iterations, we measured the wall time and subsequently calculated the floating-point operations per second (FLOPS).

### Result

| Algorithm       | Time Taken (s) | Flops | 
| :---------- | :----------: | :-----: |
| Vanilla    | 0.419255 | 3.05303e+09 |
| SSE2    | 0.397518 | 3.21998e+09 |
| SSE2 + Loop Unrolling + Blocking  | 0.254389| 5.03166e+09 |
| AVX2 + Loop Unrolling + Blocking      | 0.174788 | 7.32314e+09 |
| AVX2 + Loop Unrolling + Blocking + OpenMP        | 0.0498716 | 2.00814e+10 | 

## GEMM from OpenBLAS and Intel MKL

| Algorithm       | Time Taken (s) | Flops | 
| :---------- | :----------: | :-----: |
| OpenBLAS (1 thread)    | 0.0737658 | 1.73522e+10 |
| OpenBLAS (All threads)    | 0.0342831 | 3.73362e+10 |





