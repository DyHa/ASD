ASD
===
// Lomuto-Hoare Partition.cpp: główny plik projektu.

#include "stdafx.h"
#include <iostream>
#include "conio.h"
#include "Windows.h"
#include <time.h>
#include <stdio.h>
#include <stdlib.h>

using namespace std;

void Pisz_Tabele(int A[]);
int Lomuto_Partition(int A[], int p, int r);
int Hoare_Partition(int A[], int p, int r);

const int n = 50;
//----------------------------------------
int main()
{
	int p, r;
	int A[] = {42, 55, 33, 97, 13, 70, 79, 76, 50, 3, 68, 43, 16, 53, 39, 50, 6, 80, 71, 28, 76, 80, 42, 16, 19, 82, 66, 64, 31, 17, 95, 73, 73, 28, 71, 87, 99, 50, 63, 50, 54, 32, 93, 70, 85, 33, 21, 92, 13, 93};
	//int A[] = {7, 2, 18, 5, 49, 93, 19, 50, 19, 99, 64, 34, 57, 46, 93, 45, 78, 54, 43, 67, 42, 43, 17, 84, 61, 58, 18, 48, 1, 31, 29, 9, 33, 47, 14, 83, 40, 33, 33, 60, 33, 98, 94, 90, 45, 88, 35, 23, 42, 78};

	Pisz_Tabele(A);
	//cout << "Lomuto Partition: " << Lomuto_Partition(A, 0, 49) << endl;
	cout << "\nHoare Partition: " << Hoare_Partition(A, 0, 49) << endl;

	_getch();
	return 0;
}
//---------------------------------
void Pisz_Tabele(int A[])
{
	int i;
	for (i = 0; i < n; i++)
		cout << "A[" << i << "] = " << A[i] << endl;
	cout << "\n\n";
}
int Lomuto_Partition(int A[], int p, int r)
{
	int x = A[r];
	int i = p-1;
	for(int j = p; p <= r-1; p++){
		if(A[j] <= x){
			i++;
			int tmp = A[i];
			A[i] = A[j];
			A[j] = tmp;
		}
		int tmp = A[i+1];
		A[i+1] = A[r];
		A[r] = tmp;
	}
	return i+1;

}
int Hoare_Partition(int A[], int p, int r){
	int x = A[p];
	int i = p-1;
	int j = r+1;
	while(true){
		do{
			j=j-1;
		}while(A[j] <= x);
		do{
			i=i+1;
		}while(A[i]>=x);

		if(i<j){
			int tmp = A[i];
			A[i] = A[j];
			A[j] = tmp;
		}
		else return j;
	}	
}


