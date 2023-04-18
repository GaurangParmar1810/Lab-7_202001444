# Lab-7_202001444

## Name: Gaurang Parmar
## Student ID: 202001444

## Lab No: 7

## Date : 18/4/2023

## Topic : Black-box and White-box Testing

***

# Section A

Consider a program for determining the previous date. Its input is triple of day, month and year with the
following ranges `1 <= month <= 12`, `1 <= day <= 31`, `1900 <= year <= 2015`.The possible output dates would be
previous date or invalid date. Design the equivalence class test cases?

&raar; Equivalence classes for this program are as below:

`For Day (DD)`:
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E1 | 1 <= DD <= 28 | Valid
| E2 | DD < 1	 | Invalid
| E3 | DD > 31 | Invalid
| E4 | DD=30 | Valid expect for February
| E5 | DD=29 | Valid for leap year
| E6 | DD = 31 | Valid except for April, June, September, November

`For Month(MM)`:
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E7 | 1 <= MM <= 12 | Valid
| E8 | MM < 1 | Invalid
| E9 | MM > 12 | Invalid

`For Year(YYYY)`:
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E10 | 1900 <= YYYY <= 2015 | Valid
| E11 | YYYY < 1900 | Invalid
| E12 | YYYY > 2015 | Invalid

Input date below follows the `DD/MM/YYYY` format.

Test-cases based on `Equivalence Partition`:

| Input Type | Input Data (`DD/MM/YYYY`) | Expected Output
| ---------- | ---------- | ---------------
| Valid Input| 18/10/2002 | 17/10/2002
| Invalid Input| 0/10/2002 | Error Message
| Invalid Input| 32/10/2002 | Error Message
| Invalid Input| 18/-1/2002 | Error Message
| Invalid Input| 18/13/2002 | Error Message
| Invalid Input| 18/10/1898 | Error Message
| Invalid Input| 18/10/2017| Error Message

Test-cases based on `Boundary Analysis`:

| Input Data | Expected Output
| ---------- | --------------
| 01/01/1900 | Error Message
| 31/12/2015 | 30/12/2015
| 29/2/1900  | Error Message
| 31/6/2010  | Error Message
| 28/2/1900  | 27/2/1900
| 29/2/1904  | 28/2/1904

---

### P1. The function `linearSearch` searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that `a[i] == v`; otherwise, -1 is returned.

&rarr; Test-case for this program is as follows.

**allProgramme.java**
```java
package tests;

public class allProgramme {
	int linearSearch(int v, int a[])
	{
		int i = 0;
		while (i < a.length)
		{
			if (a[i] == v)
				return(i);
			i++;
		}
		return (-1);
	}
}

```
**p1_test.java:**

```java
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class p1_test {

	@Test
	public void test1() {
		int arr[] = { 1,2,3,4,5 };
		
		allProgramme program = new allProgramme();
		int result = program.linearSearch(1, arr);
		
		// System.out.println(result);
		assertEquals(0, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { };
		
		allProgramme program = new allProgramme();
		int result = program.linearSearch(1, arr);
		
		// System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 1 };
		
		allProgramme program = new allProgramme();
		int result = program.linearSearch(1, arr);
		
		// System.out.println(result);
		assertEquals(0, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 18 };
		allProgramme program = new allProgramme();
		int result = program.linearSearch(1, arr);
		
		// System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 5, 4, 3, 1, 2 };
		
		allProgramme program = new allProgramme();
		int result = program.linearSearch(10, arr);
		
		// System.out.println(result);
		assertEquals(-1, result);
	}

}

```
**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists</td>
      <td>the index of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v does not exist</td>
      <td>-1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the last index where v is found</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the index where v is found</td>
    </tr>
  </tbody>
</table>
</br>

**Output**:

![image](https://user-images.githubusercontent.com/97961910/232771576-ba7695c3-5106-4226-86e9-b36e069a2fc3.png)

---


### P2.The function countItem returns the number of times a value v appears in an array of integers a.

&rarr; Test-case for this program is as follows.

**allProgramme.java**
```java
package tests;

public class allProgramme {
	int countItem(int v, int a[])
	{
		int count = 0;
		for (int i = 0; i < a.length; i++)
		{
			if (a[i] == v)
				count++;
		}
		return (count);
	}
}

```

**p2_test.java**
```java
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class p2_test {

	@Test
	public void test1() {
		int arr[] = {  };
		allProgramme program = new allProgramme();
		int result = program.countItem(11, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test2() {
		int arr[] = { 10, 101, 25, 30, 10 };
		allProgramme program = new allProgramme();
		int result = program.countItem(5, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test3() {
		int arr[] = { 104,10, 10, 8, 34, 10 };
		allProgramme program = new allProgramme();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 3);
	}
	
	@Test
	public void test4() {
		int arr[] = { 10, 10, 10, 20, 10 };
		allProgramme program = new allProgramme();
		int result = program.countItem(20, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test5() {
		int arr[] = { 10 };
		allProgramme program = new allProgramme();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test6() {
		int arr[] = { 10 };
		allProgramme program = new allProgramme();
		int result = program.countItem(20, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test7() {
		int arr[] = { 1, 1, 2, 3, 1, 1, 1 };
		allProgramme program = new allProgramme();
		int result = program.countItem(1, arr);
		
		assertEquals(result, 5);
	}

}

```
<br>


**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists multiple times</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists only once</td>
      <td>1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
  </tbody>
</table>
</br>
 
**Output**
![image](https://user-images.githubusercontent.com/97961910/232777533-8f1d7e32-e7ab-484e-8662-74defcece0d1.png)
 
---

### P3. The function `binarySearch` searches for a value `v` in an ordered array of integers `a`. If `v` appears in the array `a`, then the function returns an index `i`, such that `a[i] == v`; otherwise, `-1` is returned.

&rarr; Test-case for this program is as follows.

**allProgramme.java**
```java
package tests;

public class allProgramme {
	int binarySearch(int v, int a[])
	{
	    int lo,mid,hi;
	    lo = 0;
	    hi = a.length-1;
	    while (lo <= hi)
	    {
	        mid = (lo+hi)/2;
	        if (v == a[mid])
	        return (mid);
	        else if (v < a[mid])
	        hi = mid-1;
	        else
	        lo = mid+1;
	    }
	    return(-1);
	}
}

```

**p3_test.java**
```java
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class p3_testing {

	@Test
	public void test1() {
		int arr[] = { 6,7,8,9,10 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(8, arr);
		
		assertEquals(2, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { 1,2,3,4,5 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 6,7,8,9,10 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(7, arr);
		
		assertEquals(1, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 1,2,3,4,5 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(6, arr);
		
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 1 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test6() {
		int arr[] = {  };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(1, arr);
		assertEquals(-1, result);
	}
				
	@Test
	public void test7() {
		int arr[] = { 1, 2, 3 };
		allProgramme program = new allProgramme();
		int result = program.binarySearch(3, arr);
			
		assertEquals(2, result);
	}

}

```

**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=8, a=[6,7,8,9,10]</td>
    <td>2</td>
  </tr>
  <tr>
    <td>v=1, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=7, a=[6,7,8,9,10]</td>
    <td>4</td>
  </tr>
  <tr>
    <td>v=6, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=1, a=[]</td>
    <td>-1</td>
  </tr>
	<tr>
    <td>v=3, a=[1 , 2 , 3]</td>
    <td>2</td>
  </tr>
	
</table>

**Boundary Value Analysis:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=6, a=[]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1, 2, 3]</td>
    <td>0 (smallest element in the array)</td>
  </tr>
  <tr>
    <td>v=3, a=[1, 2, 3]</td>
    <td>2 (largest element in the array)</td>
  </tr>
</table>
</br>


**Output**
</br>
![image](https://user-images.githubusercontent.com/97961910/232780675-5c7897fd-9052-4005-84c5-74c5b4ba1aa0.png)

---
### P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). The function `triangle` takes three integer parameters that are interpreted as the lengths of the sides of atriangle. It returns whether the triangle is `equilateral (three lengths equal)`, `isosceles (two lengths equal)`,`scalene (no lengths equal)`, or `invalid (impossible lengths)`.

&rarr; Test-case for this program is as follows.

**allProgramme.java**
```java
public class allProgramme
    {
        final int EQUILATERAL = 0;
        final int ISOSCELES = 1;
        final int SCALENE = 2;
        final int INVALID = 3;
        public int triangle(int a, int b, int c)
        {
            if (a >= b+c || b >= a+c || c >= a+b)
                return(INVALID);
            if (a == b && b == c)
                return(EQUILATERAL);
            if (a == b || a == c || b == c)
                return(ISOSCELES);
            return(SCALENE);

        }
    }
```
**p4_test.java**

```java
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class p4_test {

	@Test
	public void test1() {
		int a = 2, b = 2, c = 2;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 0);
	}
	@Test
	public void test2() {
		int a = 3, b = 3, c = 4;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test3() {
		int a = 6, b = 5, c = 4;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test4() {
		int a = 0, b = 0, c = 0;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test5() {
		int a =-1, b =-1, c = 5;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test6() {
		int a = 2, b = 2, c = 1;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test7() {
		int a = 0, b = 1, c = 1;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test8() {
		int a = 1, b = 0, c = 1;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test9() {
		int a = 1, b = 1, c = 0;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test10() {
		int a = 1, b = 2, c = 3;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test11() {
		int a = 3, b = 1, c = 3;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test12() {
		int a = 5, b = 4, c = 2;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test13() {
		int a = Integer.MAX_VALUE, b = Integer.MAX_VALUE, c = Integer.MAX_VALUE;
		allProgramme program = new allProgramme();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}

}

``` 
**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=2</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=3, c=4</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=6, b=5, c=4</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=0, c=0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=-1, b=-1, c=5</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Valid input: a=1, b=1, c=1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=4, c=5</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=1, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=0, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=1, c=0</td>
    <td>3</td>
  </tr>
</table>
</br>

**Boundary Value Analysis:**
<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Invalid inputs: a = 0, b = 0, c = 0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid inputs: a + b = c or b + c = a or c + a = b (a=3, b=4, c=8)</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Equilateral triangles: a = b = c = 1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Isosceles triangles: a = b ≠ c = 10</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Scalene triangles: a = b + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: b = a + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: c = a + b - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Maximum values: a, b, c = Integer.MAX_VALUE</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Minimum values: a, b, c = Integer.MIN_VALUE</td>
    <td>3</td>
  </tr>
</table>
<br>

**Output**
</br>
![image](https://user-images.githubusercontent.com/97961910/232782320-dfb1ff80-15b1-47d8-b154-b385eaeb73f6.png)

---
### P5. The function `prefix(String s1, String s2)` returns whether or not the string `s1` is a prefix of string `s2` (you may assume that neither s1 nor s2 is null).

&rarr; Test-case for this program is as follows.

**allProgramme.java**

**p4_test.java**

**Output**

---

### P6. In this program we consider program given in P4 but value can be float rather than integers
