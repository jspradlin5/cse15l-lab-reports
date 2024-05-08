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


**Part 2:**

`grep-n`:
```
$ grep -n "Introduction" ./technical/biomed/1468-6708-3-1.txt
5:        Introduction
```

`grep-c`:
```
$ grep -c "planes" ./technical/911report/chapter-1.txt
16
```


`grep-w`:
```
$ grep -w "Cardiovascular" ./technical/biomed/1468-6708-3-1.txt
          Study design: The Cardiovascular Health
          The Cardiovascular Health Study (CHS) is a
        CHS Cardiovascular Health Study
```


`grep-l`:
```
$ grep -l "planes" ./technical/911report/*.txt
./technical/911report/chapter-1.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
```
