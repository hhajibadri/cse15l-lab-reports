# Lab 3 Report

I choose ArrayExamples and ArrayTests to demonstrate the bug and symptom

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