# Ternary Search 
## -->Conquer Algorithm<--

**Ternary Search** is a decrease(by constant) and conquer algorithm that can be used to find an element in an array.
It is similar to binary search , Where we can divide the array into three parts. 
The only difference is that , it reduces the time complexity a bit more to O(log n base 3)


## **Algorithm**

**Ternary Search Algorithm** :
-> Array needs to be sorted to perform ternary search on it.
-> Initially l and r will be equal to 0 and n - 1 respectively.(n is the length of the array)
-> mid1 = l + (r - l) / 3
-> mid2 = r - (r - l) / 3

**Steps to perform Ternary Search**:
1 -> We need to compare the key with the element at mid1. If found equal , return mid1.
2 -> If not , then we compare the key with the element at mid2. If found equal , return mid2.
3 -> If not , then we check whether the key is less than the element at mid1. If yes, recur to the first part.
4 -> If not , then we check whether the key is greater than the element at mid2. If yes , then recur to the third part.
5 -> If not , then we recur to the second (middle) part.

[Ternary Search Algorithm]  = https://media.geeksforgeeks.org/wp-content/uploads/ternaryS-3.png

## **CODE  IMPLEMENTATION** 
## Recursive Implementation of Ternary Search(CPP)

```cpp 
// recursive approach to ternary search
#include <bits/stdc++.h>
#include<iostream>
using namespace std;


int ternarySearch(int l, int r, int key, int ar[])
{
	if (r >= l) {

		// Find the mid1 and mid2
		int mid1 = l + (r - l) / 3;
		int mid2 = r - (r - l) / 3;

		// Check if key is present at any mid
		if (ar[mid1] == key) {
			return mid1;
		}
		if (ar[mid2] == key) {
			return mid2;
		}

		// Since key is not present at mid,
		// check in which region it is present
		// then repeat the Search operation
		// in that region
		if (key < ar[mid1]) {

			// The key lies in between l and mid1
			return ternarySearch(l, mid1 - 1, key, ar);
		}
		else if (key > ar[mid2]) {

			// The key lies in between mid2 and r
			return ternarySearch(mid2 + 1, r, key, ar);
		}
		else {

			// The key lies in between mid1 and mid2
			return ternarySearch(mid1 + 1, mid2 - 1, key, ar);
		}
	}

	// Key not found
	return -1;
}

// Driver code
int main()
{
	int l, r, p, key;

	// Get the array
	// Sort the array if not sorted
	int ar[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

	// Starting index
	l = 0;

	// length of array
	r = 9;

	// Checking for 5

	// Key to be searched in the array
	key = 5;

	// Search the key using ternarySearch
	p = ternarySearch(l, r, key, ar);

	// Print the result
	cout << "Index of " << key
		<< " is " << p << endl;

	// Checking for 50

	// Key to be searched in the array
	key = 50;

	// Search the key using ternarySearch
	p = ternarySearch(l, r, key, ar);

	// Print the result
	cout << "Index of " << key
		<< " is " << p << endl;
}
```

## Output
Index of 5 is 4
Index of 50 is -1

```cpp
// C++ program to illustrate
// iterative approach to ternary search

#include <iostream>
using namespace std;

// Function to perform Ternary Search
int ternarySearch(int l, int r, int key, int ar[])

{
	while (r >= l) {

		// Find the mid1 and mid2
		int mid1 = l + (r - l) / 3;
		int mid2 = r - (r - l) / 3;

		// Check if key is present at any mid
		if (ar[mid1] == key) {
			return mid1;
		}
		if (ar[mid2] == key) {
			return mid2;
		}

		// Since key is not present at mid,
		// check in which region it is present
		// then repeat the Search operation
		// in that region

		if (key < ar[mid1]) {

			// The key lies in between l and mid1
			r = mid1 - 1;
		}
		else if (key > ar[mid2]) {

			// The key lies in between mid2 and r
			l = mid2 + 1;
		}
		else {

			// The key lies in between mid1 and mid2
			l = mid1 + 1;
			r = mid2 - 1;
		}
	}

	// Key not found
	return -1;
}

// Driver code
int main()
{
	int l, r, p, key;

	// Get the array
	// Sort the array if not sorted
	int ar[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

	// Starting index
	l = 0;

	// length of array
	r = 9;

	// Checking for 5

	// Key to be searched in the array
	key = 5;

	// Search the key using ternarySearch
	p = ternarySearch(l, r, key, ar);

	// Print the result
	cout << "Index of "<<key<<" is " << p << endl;

	// Checking for 50

	// Key to be searched in the array
	key = 50;

	// Search the key using ternarySearch
	p = ternarySearch(l, r, key, ar);

	// Print the result
	cout << "Index of "<<key<<" is " << p;
}

```
## Output
Index of 5 is 4
Index of 50 is -1


## Resources to Study Ternary Search 
-- >   https://www.geeksforgeeks.org/ternary-search/
-- >   https://cp-algorithms.com/num_methods/ternary_search.html

