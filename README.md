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

--> Equivalence classes for this program are as below:

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

### P1. The function linearSearch searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.

--> Test-case for this program is as follows.

---
