//	Workshop 04.1 _ Fraction Simplifier 
/**
 * @ due 13.02.2022 
 * @author Nguyen Thi Minh Chau _ SE1728 
 */
 
#include<stdio.h>

	//Prototype
void input(int *num, int *den); 
void display(int num, int den); 
void simplify(int *num, int *den);  
	
	//Program
int main(){
	int num, den; 
	char run = 'y'; //initialize initial value of "run"
	while(run == 'y'){
		
		// Input
		printf("1. Input faction \n"); 
		input(&num, &den);
		
		// Output 
		printf("2. Simplify fraction \n"); 
		printf("%d/%d", num, den);
		printf("\n=\n"); 
		display(num, den); 
		
		//Ask the user to continue the program or not?
		printf("\nAnother run <y/n>? ");
		scanf("%c", &run);
		run = getchar(); 
	}
	return 0; 
} 
	// Input numerator (num) and denominator of a fraction (den)
void input(int *num, int *den){
	int n=0;
	printf("\nEnter numerator: ");
	scanf("%d", num);
	while(n==0){
		printf("Enter denominator: ");
		scanf("%d", den);  
		n = *den;
	} 
}

	// Display the fraction
void display(int num, int den){
	if(num%den==0){
		printf("%d", num/den); 
	} else{
		simplify(&num, &den);
		printf("%d/%d", num, den); 
	}
}

	// Simplify the fraction
void simplify(int *num, int *den){
	int i, simp=1; 
	int a = *num;
	int b = *den;	
	if(a<0){
		a*=-1;
	} 
	if(b<0){
		b*=-1;
	} 
	for(i = 1; i <= a || i <= b; i++) {
   		if( a%i == 0 && b%i == 0 )
      		simp = i;
    }
   		*num/=simp;
 		*den/=simp; 
   if(*den<0){
		*num*=-1;
		*den*=-1; 
	}  
}  
	
