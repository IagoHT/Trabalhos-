# Trabalhos-
Conhecimentos aplicados em pequenos projetos.
/*Em Sistemas Operacionais o gerenciador de memória é um módulo do SO que gerencia 
a memória principal e a área de memória secundária. Um gerente de memória possui 
algumas funções básicas como controlar as áreas de memória em uso e as disponíveis. 
Para esse gerenciamento existem duas técnicas, a monoprogramação e a 
multiprogramação. Dada essa definição, vimos na disciplina algumas formas de como 
o gerenciador se comporta, ou seja, alguns de seus algoritmos
 Best Fit; o Sistema Buddy você pode utilizar um vetor;
ALUNO: IAGO HENRIQUE THEODORO RA 3508
*/
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>

void BestFit(int memoVet[], int memoria, int processVet[], int processo){
// Identificação incial para os processos e para a memória
    int guarda[processo];
    int ocupado[memoria];
    
// Zera todo lixo de memória
   for(int i = 0; i < processo; i++){
        guarda[i] = -1;
    }
    for(int i = 0; i < memoria; i++){
        ocupado[i] = 0;
    }
// Função que procura o tamanho adequado na memória para o processo
    for (int i = 0; i < processo; i++){
        int armazena = -1;
       	 for (int j = 0; j < memoria; j++) { 
            if (memoVet[j] >=  processVet[i] && !ocupado[j]){ // Função para armazenar na memória o processo de acordo com o tamanho do espaço disponível
                if (armazena == -1)
                    armazena = j;     
// função de verificação entre dois espaços para ver qual cabe melhor o processo na memória
                else if (memoVet[j] < memoVet[armazena])
                    armazena = j;
            }
        }
// Se conseguimos encontrar o bloco com sucesso para o processo
        if (armazena != -1){
           guarda[i] = armazena;            
// identifica o espaço da memória como ocupado
           ocupado[armazena] = 1;
        }
    }
    printf("\n\tNº.do processo\tTamanho do Processo\tNº de ordem da Memoria\n");// Montar a "TABELA", demonstartivo
    for (int i = 0; i < processo; i++){
        printf("\t\t%d \t\t\t %d \t\t\t", i+1,  processVet[i]);
        if (guarda[i] != -1)
            printf("%d\n",guarda[i] + 1);
        else
            printf("Vazio ou espaço de memória insuficiente\n");
    }
}
// Principal
int main(){
	setlocale(LC_ALL, "Portuguese");
		int q,w,e,r,t,y,u;
		int a,s,d,f,g,h,k;
	printf("Digite 7 valores interios para determinar o tamanho do seu processo!\n");
		scanf("%d%d%d%d%d%d%d", &q,&w,&e,&r,&t,&y,&u);
			printf("Digite 7 valores interios para determinar o espaço de memória!\n");
				scanf("%d%d%d%d%d%d%d", &a,&s,&d,&f,&g,&h,&k);
    	int memoVet[] = {a,s,d,f,g,h,k};
    	int  processVet[] ={q,w,e,r,t,y,u};
    	int memoria = sizeof(memoVet)/sizeof(memoVet[0]);// aplicando sizeof
    	int processo = sizeof( processVet)/sizeof( processVet[0]);// aplicando sizeof
    BestFit(memoVet, memoria,processVet, processo);//chama a função principal
 		system("PAUSE");
    return 0 ;
}

