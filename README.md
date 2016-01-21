# Robot-to-start-with-minimum-energy
Robot to start with minimum energy so that it reaches the destination with out becoming zero. Every time the energy is added or subtracted from the present value. The minimum value of sum is 1 not 0.
#include<stdio.h>

int max(int x,int y)
{
	return (x>y)?x:y;
}
int main()
{
	int arr[10][10],n,i,j;
	printf("Enter n\n");
	scanf("%d",&n);

	printf("Enter the matrix\n");
	for(i=0;i<n;i++)
		for(j=0;j<n;j++)
			scanf("%d",&arr[i][j]);

	for(i=1;i<n;i++)
	arr[0][i]+=arr[0][i-1];

	for(i=1;i<n;i++)
	arr[i][0]+=arr[i-1][0];

	for(i=1;i<n;i++)
	{
		for(j=1;j<n;j++)
		{
			arr[i][j]+=max(arr[i-1][j],arr[i][j-1]);
		}
	}
	printf("\n\n");

	for(i=0;i<n;i++)
	{
		for(j=0;j<n;j++)
			printf("%d ",arr[i][j]);
		printf("\n");
	}
	printf("\n\n");
	
	if(arr[n-1][n-1] > 0)
		printf("power to start with is 1 \n");
	else
		printf("power to start with is %d\n",(arr[n-1][n-1]*(-1))+2);
}
