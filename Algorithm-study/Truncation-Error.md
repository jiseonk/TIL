# Calculate Truncation-Error

Calculate e(1.0) using maclaurin expansion.
The variable 'n' means nth term.

```
#include <stdio.h>
#include <math.h>

void myfunc(int n);
void myfunc2(float S);

int main(void) {

	int n;
	for (n = 10; n > 0; n--) {
		myfunc(n);
	}


}

/* Calculate maclaurin expansion */

void myfunc(int n)
{
	int j, k;
	float fact;

	// step1.
	float S = 1.0;
	// step2.
	for (j = n; j >= 1; j--) {
		fact = 1.0;
		for (k = 2; k <= j; k++) {
			fact = fact * k;
		}

		S = S + 1.0 / fact;

	}

	printf("n: %d, calculated: %f, exact: %f\n",n, S, exp(1.0));

	myfunc2(n, S);
}

/* Find truncation error */
void myfunc2(float S)
{
	float e;
	e = fabsf(S-exp(1.0)) / fabsf(exp(1.0));
	printf("truncation error : %f\n", e);
}

```

The result : 
```
n: 10, calculated: 2.718282, exact: 2.718282
relative error : 0.000000
n: 9, calculated: 2.718281, exact: 2.718282
relative error : 0.000000
n: 8, calculated: 2.718279, exact: 2.718282
relative error : 0.000001
n: 7, calculated: 2.718254, exact: 2.718282
relative error : 0.000010
n: 6, calculated: 2.718055, exact: 2.718282
relative error : 0.000083
n: 5, calculated: 2.716667, exact: 2.718282
relative error : 0.000594
n: 4, calculated: 2.708333, exact: 2.718282
relative error : 0.003660
n: 3, calculated: 2.666667, exact: 2.718282
relative error : 0.018988
n: 2, calculated: 2.500000, exact: 2.718282
relative error : 0.080301
n: 1, calculated: 2.000000, exact: 2.718282
relative error : 0.264241

```
Less calculated terms, bigger truncation error.
