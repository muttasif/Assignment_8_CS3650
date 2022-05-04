# Threaded Merge Sort Experiments

## Host 1: HP-ProBook-455-G7

- CPU: AMD Ryzen 5 4500U
- Cores: 6
- Cache size: 3MB
- RAM: 16GB
- Storage: 512 SSD
- OS: 20.04.1-Ubuntu

### Input data

Tested with 4 different text files, each with 100000000 integers.
Files were generated using cmd `shuf -i 1-100000000 > data<#>.txt`

To make test more objective each number of threades were tested with each data file (in description belowe we have average execution value for each file ).

Common steps:
```
DATA_SIZE=100000000
shuf -i 1-${DATA_SIZE} > data1.txt
shuf -i 1-${DATA_SIZE} > data2.txt
shuf -i 1-${DATA_SIZE} > data3.txt
shuf -i 1-${DATA_SIZE} > data4.txt
```

### Single thread

Summary:
- 18.53 seconds
- 18.59 seconds
- 19.01 seconds
- 19.11 seconds

### Experiments

#### 1 Threads

Command: `MSORT_THREADS=1 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 18.62 seconds
2. 18.92 seconds
3. 18.51 seconds
4. 19.27 seconds

#### 2 Threads

Command: `MSORT_THREADS=2 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 7.97 seconds
2. 7.99 seconds
3. 7.82 seconds
4. 8.03 seconds

#### 3 Threads

Command: `MSORT_THREADS=3 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 7.64 seconds
2. 7.82 seconds
3. 7.81 seconds
4. 7.69 seconds

#### 4 Threads

Command: `MSORT_THREADS=4 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 7.95 seconds
2. 7.99 seconds
3. 7.91 seconds
4. 7.94 seconds

#### 5 Threads

Command: `MSORT_THREADS=5 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 7.92 seconds
2. 8.11 seconds
3. 8.01 seconds
4. 7.99 seconds

#### 6 Threads

Command: `MSORT_THREADS=6 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 7.96 seconds
2. 8.03 seconds
3. 8.16 seconds
4. 7.97 seconds

## Host 2: HP-ProBook-455-G7

- CPU: AMD Ryzen 5 4500U
- Cores: 6
- Cache size: 3MB
- RAM: 16GB
- Storage: 512 SSD
- OS: 20.04.1-Ubuntu

Tested with the same 4 files as described for previous host (files were identically the same)

Used the same testing procedure as for previous host.

**Note**: to test it on Windows OS cygwin (is a POSIX-compatible programming and runtime environment that runs natively on Microsoft Windows.) with all required packages was used.

Common steps:
```
DATA_SIZE=100000000
```
### Single thread

Summary:
- 24.31 seconds
- 24.19 seconds
- 24.81 seconds
- 24.86 seconds

### Experiments

#### 1 Threads

Command: `MSORT_THREADS=1 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 24.57 seconds
2. 24.19 seconds
3. 24.91 seconds
4. 25.11 seconds

#### 2 Threads

Command: `MSORT_THREADS=2 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 14.17 seconds
2. 14.79 seconds
3. 14.11 seconds
4. 14.93 seconds

#### 3 Threads

Command: `MSORT_THREADS=3 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 14.02 seconds
2. 13.91 seconds
3. 14.31 seconds
4. 13.79 seconds

#### 4 Threads

Command: `MSORT_THREADS=4 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 14.72 seconds
2. 14.81 seconds
3. 14.64 seconds
4. 14.44 seconds

#### 5 Threads

Command: `MSORT_THREADS=5 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 14.81 seconds
2. 14.12 seconds
3. 14.28 seconds
4. 14.32 seconds

#### 6 Threads

Command: `MSORT_THREADS=6 ./tmsort $DATA_SIZE < data<#>.txt > /dev/null`

Sorting portion timings:

1. 15.11 seconds
2. 15.29 seconds
3. 14.97 seconds
4. 15.25 seconds

## Observations and Conclusions

After analyzing all the result we could say that conclusion is quite simple -  we must be sure that each thread has a reasonable amount of work to do. Despite on host machine we see that significant improvements occurred only when we switched from 1 to 2 threads in all cases.
Also it may depend on the amount of data which we have (e.g. for smaller testing data set to sort it may happen that we will have improvements in a few seconds with a higher number of threads).
Also for such tasks size and type of cache memory is quite important and can have a great impact on overall performance.

One more interesting thing is that in the second case when we used the same machine, but with cygwin environment on windows OS we observe that performance was deteriorated.



