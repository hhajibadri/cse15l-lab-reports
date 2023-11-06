# Lab 3 Report

**I choose ArrayExamples and ArrayTests to demonstrate the bug and symptom.**

```java
@Test
public void testReverseInPlace2()
{
    int[] input1 = { 3, 2 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 2, 3 }, input1);
}
```

This is the failure-inducing input.

```java
@Test
public void testReverseInPlace()
{
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

This input doesn't result in failure because a 1 element array does not need to be reversed.

![Symptom output](symptom_output.png)

Here is the output of JUnit showing the symptom. The second test failed because it did not correctly reverse the array.

```java
static void reverseInPlace(int[] arr)
{
    for(int i = 0; i < arr.length; i++)
    {
        arr[i] = arr[arr.length - 1 - i];
    }
}
```

Before fixing the bug.

```java
static void reverseInPlace(int[] arr)
{
    for(int i = 0; i < arr.length / 2; i++)
    {
        int temp = arr[i];
        arr[i] = arr[arr.length - 1 - i];
        arr[arr.length - 1 - i] = temp;
    }
}
```

After fixing the bug. The bug was we were not swapping arr[arr.length - 1 - i] with arr[i]. This is becuase when we assign arr[i] to arr[arr.length - 1 - i] we  lose the value of what arr[i] originally was. To fix this we introduce a temp variable to hold the value of arr[i] so that when we assign arr[i] to arr[arr.length - 1 - i] we can simply assign arr[arr.length - 1 - i] to temp. We also only need to traverse half the array because we are swapping the beginning elements from the ones at the end.

**grep -i**

```shell
hugirhajibadri@Hugirs-MacBook-Pro docsearch % grep -i "convergent evolution" ./technical/*/*
./technical/biomed/1471-2148-3-18.txt:        centers through convergent evolution. Two of these classes
./technical/biomed/1471-2148-3-18.txt:        developed through convergent evolution [ 30 ] seems flawed:
./technical/biomed/1471-2148-3-18.txt:        convergent evolution at a sequence level [ 33 34 ] we
./technical/biomed/1471-2164-3-4.txt:          pressures that led to convergent evolution in two
./technical/biomed/gb-2002-3-5-research0025.txt:          structure might have arisen by convergent evolution from
./technical/biomed/gb-2002-3-5-research0025.txt:          fold and have evolved by convergent evolution in
./technical/biomed/gb-2003-4-2-r14.txt:          lineages or from convergent evolution. Parametric
grep: ./technical/government/About_LSC: Is a directory
grep: ./technical/government/Alcohol_Problems: Is a directory
grep: ./technical/government/Env_Prot_Agen: Is a directory
grep: ./technical/government/Gen_Account_Office: Is a directory
grep: ./technical/government/Media: Is a directory
grep: ./technical/government/Post_Rate_Comm: Is a directory
./technical/plos/journal.pbio.0030021.txt:        the convergent evolution of sex determination related to mating system adaptations. An
```

```shell
hugirhajibadri@Hugirs-MacBook-Pro docsearch % grep -i "octopus" ./technical/*/*             
grep: ./technical/government/About_LSC: Is a directory
grep: ./technical/government/Alcohol_Problems: Is a directory
grep: ./technical/government/Env_Prot_Agen: Is a directory
grep: ./technical/government/Gen_Account_Office: Is a directory
grep: ./technical/government/Media: Is a directory
grep: ./technical/government/Post_Rate_Comm: Is a directory
./technical/plos/journal.pbio.0020430.txt:        “Dr. Octopus,” the villain that terrorizes the city in the most recent film of the
./technical/plos/journal.pbio.0020430.txt:        with the BMI, becomes the villainous Dr. Octopus. At the end of the movie, in a flicker of
./technical/plos/journal.pbio.0020430.txt:        Although Dr. Octopus is a fictional character, a figment of a vivid imagination,
./technical/plos/journal.pbio.0020430.txt:        Octopus. The fictional BMI in 
```


