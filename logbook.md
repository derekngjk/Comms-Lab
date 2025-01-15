# Lab 1

## Exercise 1: Data Types in Labview

First, we create a `string to byte array` unit, which can take in a string as input, and output a byte array, where each element in the array is the ASCII value of each character in the input string.

![string to byte array unit](images/[task1]string-to-byte-array-unit.png)

In the `Panel` tab, we can input whatever value we want into the `string` input, and we can see the ASCII values in the corresponding unsigned byte array:

![string to byte array usage](images/[task1]string-to-byte-array-usage.png)

Next, we want to treat each ASCII value as a Fahrenheit temperature, and we want to convert them into Celsius values. We can perform this using the following block:

![F to C block](images/[task1]f-to-c.png)

Because `C = (F - 32) * 5/9`, in order to multiply the array by a floating point number, we need to cast it to an array of doubles first. This is done using the `DBL` block, then the array is passed through operators which subtract 32 from the values and scale them by 5/9. **Note: it is important that the constants connected to the subtract / multiply blocks are of type `numerical constant`, to ensure that they are scalars, so that the simulator will perform the operation element-wise. Otherwise, if they are accidentally declared as 1d arrays, it will cause undesired behaviour.**

We can verify its functionality as follows:

![F to C output](images/[task1]f-to-c-outut.png)

Next, we use the `Add Array Elements` unit and the `Array Size` unit to get the sum and length of the output array respectively, and divide them to obtain the mean.

![F to C average](images/[task1]avg.png)

This gives the output as expected:

![Average output](images/[task1]avg-out.png)

The last step is to compare the value of the mean against a constant threshold, set at 50. It then outputs 1 if the mean is greater than or equal to 50, else 0.

![Greater than or equal to unit](images/[task1]ge.png)

This gives the following outputs:

![Input abcde](images/[task1]ge-out-abcde.png)

String `abcde` has mean 37.222, hence `is_hot` is false.

![Input zzz](images/[task1]ge-out-zzz.png)

String `zzz` has mean 50. This is becaue `z` has ASCII value 122, hence in Fahrenheit, it is equivalent to `(122-32) * 5/9 = 50`. Hence, `is_hot` is true.

Using surname and first initial as input gives the ASCII values of the characters as follows:

![Input name](images/[task1]name.png)

The final schematic is as follows:

![Final block diagram](images/[task1]schematic-final.png)

