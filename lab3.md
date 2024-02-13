# Lab Report 3 - Isaac Robles
---
The bug I am choosing from the week 4 lab will be shown down below.

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];

    }
    return arr;
  }
```

---

Down below is a test that passes. Notice that we are testing on an empty array `arr` in order for the test to pass because of the how the bug affects the program. The way the program works currently the method will always return 0 for the first element.  

```
  @Test 
  public void testReversedWithoutFailure() {
    int[] inputArray = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(inputArray));
  }
```
```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.
Time: 0.007

OK (1 test)
```

When we write another test that is supposed to pass if the method works as intended, we can see that it fails and instead of the the expected return for the first element being the last element of the original array `arr` (because it should be reversed) we just get 0 for that first element. This lets us pinpoint the bug to how elements are being assigned. 

```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E.
Time: 0.01
There was 1 failure:
1) testReversedWithFailure(ArrayTests)
arrays first differed at element [0]; expected:<5> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversedWithFailure(ArrayTests.java:8)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<5> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)    
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more

FAILURES!!!
Tests run: 2,  Failures: 1
```
So in order to fix this we must change how the method is assigning elements and down below is how we will do so.

```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[arr.length - i - 1] = arr[i];
  }
  return newArray;
}
```

This is able to fix the bug in the method because it is no longer grabbing elements from the already empty array `newArray` and rewriting the elements onto our original array `arr`. Instead it grabs the elements from `arr` starting from the end (reversed order) and rewrites said elements onto the array `newArray`. This will allow for a reversed version of our orignal array `arr` to be created through the array `newArray` and returned back to us corretly reversing everything.

---
