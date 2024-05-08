# **Lab Report 3**
---
Associated block of code:
```
public class ArrayExamples {

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Failure inducing input:
```
@Test
public void testReverseInPlace() {
    int[] input1 = {7, 3, 2, 6, 4, 1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1, 4, 6, 2, 3, 7}, input1);
}
```
Non-failure inducing input:
```
@Test
public void testReverseOneElementInPlace() {
    int[] input1 = {5};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5}, input1);
}
```
