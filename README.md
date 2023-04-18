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
