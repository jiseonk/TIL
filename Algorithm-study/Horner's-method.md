# Horner's-method

```
int main(void)
{
    float a[11], y[11];
    a[0] = 1.0;
    a[1] = 2.0;
    a[2] = 3.0;
    a[3] = -3.0;
    a[4] = -2.0;
    a[5] = -1.0;
 
    int n = 5;

    //1. Input x 
    float x;
    printf("x: ");
    scanf("%f", &x);

    //2. y0=a0
    y[0] = a[0];

    //3. Caculate j=1,2,...,n
    int nt = 0;
    int na = 0;
    int j;
    for (j = 1; j <= n; j++)
    {
        y[j] = y[j - 1] * x + a[j];
        nt++; //Multiplication counter
        na++; //Addition counter
    }
    printf("When use horner's method\n");
    printf("P(%f)= %f \n", x, y[n]);
    printf("Multiplication: %d \n", nt);
    printf("Addition: %d \n", na);

    //If you don't use horner's method

    nt = 0;
    na = 0;
    float xx[11];
    xx[1] = x;
    for (j = 2; j <= n; j++)
    {
        xx[j] = xx[j - 1] * x;
        nt = nt + 1;
    }

    float P = a[n];
    for (j = n - 1; j >= 0; j--)
    {
        P = P + a[j] * xx[n - j];
        nt++;
        na++;
    }

    printf("When do not use horner's method\n");
    printf("P(%f)= %f \n", x, y[n]);
    printf("Multiplication: %d \n", nt);
    printf("Addition: %d \n", na);

    return 0;
}
```
