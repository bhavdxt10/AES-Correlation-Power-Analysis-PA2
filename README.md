[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/nnM899vK)
# pa2-cpa-attack

Template repo for assignment 2 on Correlation Power Attack on AES implementation.

The assignment is divided into four sections:
1. Code given (not to be edited)
2. Analyzing noise
3. noise removal
4. CPA attack: (A) without noise removal (B) with noise removal
5. Correlation plot: (A) without noise removal (B) with noise removal

2. **Analyzing noise**
This section contains plotting the samples for few traces to identify patterns that can help distinguish random noise (250 points) from original power samples (5000 points)

3. **Noise removal** 
This section eliminates consecutive duplicates while keeping the last occurrence for each trace. By choosing position of final duplicate as start index, we keep 5000 points to filter out true power samples.

| Number of Trace | Start Index of Noiseless Power Samples |
|------------------|---------------------------------------|
| Trace 0         | 220                                   |
| Trace 1         | 230                                   |
| Trace 2         | 220                                   |
| Trace 3         | 228                                   |
| Trace 4         | 244                                   |
| Trace 5         | 244                                   |
| Trace 6         | 226                                   |
| Trace 7         | 204                                   |
| Trace 8         | 240                                   |
| Trace 9         | 234                                   |
| Trace 10        | 243                                   |
| Trace 11        | 233                                   |
| Trace 12        | 240                                   |
| Trace 13        | 221                                   |
| Trace 14        | 221                                   |
| Trace 15        | 229                                   |
| Trace 16        | 206                                   |
| Trace 17        | 229                                   |
| Trace 18        | 201                                   |
| Trace 19        | 206                                   |
| Trace 20        | 250                                   |
| Trace 21        | 204                                   |
| Trace 22        | 232                                   |
| Trace 23        | 235                                   |
| Trace 24        | 245                                   |
| Trace 25        | 242                                   |
| Trace 26        | 244                                   |
| Trace 27        | 244                                   |
| Trace 28        | 234                                   |
| Trace 29        | 210                                   |
| Trace 30        | 225                                   |
| Trace 31        | 212                                   |
| Trace 32        | 245                                   |
| Trace 33        | 233                                   |
| Trace 34        | 228                                   |
| Trace 35        | 236                                   |
| Trace 36        | 201                                   |
| Trace 37        | 215                                   |
| Trace 38        | 214                                   |
| Trace 39        | 214                                   |
| Trace 40        | 212                                   |
| Trace 41        | 213                                   |
| Trace 42        | 238                                   |
| Trace 43        | 234                                   |
| Trace 44        | 240                                   |
| Trace 45        | 243                                   |
| Trace 46        | 231                                   |
| Trace 47        | 240                                   |
| Trace 48        | 203                                   |
| Trace 49        | 239                                   |

size of noiseless array:  (50, 5000)


4. **CPA Attack**  
   This section involves forming a 50x256 hypothetical matrix (one row per trace, one column per key guess byte). You will convert the hypothetical matrix to a Hamming weight model, leading to the creation of either:
   - A 256x5250 correlation matrix using the Hamming model and the trace array without noise removal, or
   - A 256x5000 correlation matrix using the Hamming model and the trace array with noise removal.

   You will evaluate the maximum correlation per key to derive the best guess for each key byte.

   - **Accuracy (CPA Attack without Noise Removal):** 6.25%
   - **Accuracy (CPA Attack with Noise Removal):** 100%

5. **Correlation Plot**  
   This section contains the following plots:
   - Max correlation vs. key guesses (for byte 0, byte 1, and the first 3 bytes) without noise removal.
   - Max correlation vs. key guesses (for byte 0, byte 1, and the first 3 bytes) with noise removal.