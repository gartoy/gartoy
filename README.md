// Criar 5 vetores contendo 10 valores reais gerados aleatoriamente
// Utilizar uma função recursiva para somar apenas os elementos pares de cada vetor
// Retornar maior elemento do item 2


#include <stdio.h>
#include <stdlib.h>
#define N 10
#include <time.h>



void gerar_dados(int x[]);
void imprimir_dados(int x[]);
int somar_numeros_pares(int x[]);
int somar_numeros_pares_recursivo(int q, int x[]);
int ehPar(int num);


int main () {
  int soma_par;
  int vetor[N];
  gerar_dados(vetor);
  imprimir_dados(vetor);
  //soma_par= somar_numeros_pares(vetor);
  soma_par= somar_numeros_pares_recursivo(N-1, vetor);
  printf("\nA soma dos pares eh: %i\n",soma_par);
  return(0);
}

void imprimir_dados(int x[]){
	int i;
	for(i=0;i<N;i++){
		printf("\nvetor[%i] = %i\n",i,x[i]);
	}
}

void gerar_dados(int x[]){
	int i, n;
  time_t t;
   
   n = 5;
   
   srand((unsigned) time(&t));
   for( i = 0 ; i < N ; i++ ) {
      x[i]= (int)rand() % 10;
   }
}

int somar_numeros_pares(int x[]){
	int i, soma=0;
	for(i=0;i<N;i++){
    if(x[i]%2==0){
     		soma=soma+x[i]; 
    }
	}
	return soma;
}

int ehPar(int num){
  if(num%2==0){
    return 1;
  }
  return 0;
}

int somar_numeros_pares_recursivo(int q, int x[]){
  int r;
	if(q==0){
		return ehPar(x[0])?x[0]:0;
	}
  r = ehPar(x[q])?x[q]:0;
	return r+somar_numeros_pares_recursivo(q-1,x);
}
