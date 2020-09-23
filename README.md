<div align="center">

## Triangular Pascals Triangle


</div>

### Description

Prints out pascals triangle in a nice triangular format up to 13 rows
 
### More Info
 
You must input the number of rows of the triangle you wish to view.

The program only handles ints and is limited to what an integer can do


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Josh Hollandsworth](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/josh-hollandsworth.md)
**Level**          |Beginner
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Math](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/math__3-12.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/josh-hollandsworth-triangular-pascals-triangle__3-6890/archive/master.zip)

### API Declarations

iostream and iomanip


### Source Code

```
//Author name: Josh Hollandsworth
//Author email: j_hollandsworth@msn.com
//Source Filename: pascal.cpp
//Purpose: prints out a Pascal’s triangle depending on the number of
//     rows that a user inputs
//Date: 26/9/03       Last Modified 01/10/03 10:32
#include <iostream>
#include <iomanip>
using namespace std;
int fact(int num) {
  //variable to hold the value of
  int num_factorial = 1;
	// while num is greater than one multiply it by the value that is referenced
  // by num_factorial, then reassign it to num_factorial. Finally decrement the
  // value of num and start again
  while(num > 1)  {
    num_factorial *= num;
		num--;
	}  //end of while
	return num_factorial;
}  // end of fact function
//comb finds the value of a combination of 2 numbers
int comb(int n , int k) {
	int combination = (fact(n)/(fact(k) * fact((n-k))));
	return combination;
}  //end of comb function
//printTab prints out a specified number of rows determined by the max rows
//minus the number of the current row
void printTab(int n, int max)  {
  //set the counter equal to max minus the current row
  //then print out 4 spaces during ever iteration
  for(int i =(max-n); i > 0; i--) {
		cout << "  ";
	}  //end of for
}  // end of printTab function
// main function
int main() {
	//vars to hold the variables in each loop
	int max,row,column;
	//print a blank line on execution to prevent the output from being right up against the CLI id
	cout << endl;
	//notes where the beginning of execution is for the goto loop
	// and prompts the user for input
	beginning: cout << "Enter the maximum number of rows: ";
	      cin >> max;
	      cout << endl;
	// if the maximum rows is above 14 go back so we prevent a buffer overflow of sourts
	if (max > 13 || max < 1)  {
	  cout << "Number out of range...Try again!\n";
		goto beginning;
	}    //end of goto if
	//increment row as long as it is less than the max rows;
	for(row = 0; row < max ; row++)  {
		//printTab aides in making output look better by tabbing over a n times depending on current
		//value of the row compared to the maximum number of rows
		cout << setw(2);
		printTab(row,(max - 1));
		//increment column as long as column is less then row +1.
		//this only works since the maximum values of numbers in a row is 1+the row number
		//ie in row 6 there are seven values in Pascal’s triangle,.
		for(column = 0; column < row + 1; column++)  {
			// if the column number equals 0 output "1" since it would pass
			// 0 and 0 to the combination function which would cause execution fail
			// from a divide by zero exception
			if(row == 0)  {
			  cout << setw(4);
				cout << "1";
				break;
			} else {
				//use the iomanip function setw to make the spacing between values to
				//ensure proper output and finally output the value and the spacing
				cout << setw(4);
				cout << comb(row,column) << "  ";
			}    //end of row if else
		}    //end of column for
		//output and end line to ensure the next row starts on a new line
		cout << endl;
	}    //end of row for
	return 0;
}
```

