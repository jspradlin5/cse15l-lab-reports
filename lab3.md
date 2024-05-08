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

Screenshot of tests running:

![Image](Test_failure.png)

Before fixing the bug:
```
 static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
```
After fixing the bug:
```
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i += 1) {
        int new = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = new;
    }
}
```

In the original implementation, each element of the array was being overwritten with the element located at the mirrored position from the end of the array. This resulted in all elements in the array becoming the same as the last element, effectively losing the original content of the array. The fix corrects the issue by properly swapping elements in the array. In the corrected version, each element is swapped with its corresponding element from the reversed position in the array.



