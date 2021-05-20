# Atividade-Pilha

Main.C:
#include <stdio.h>
#include <stdlib.h>
#include "pilha.h"

int main(void) {

  empilhar(1);
  empilhar(2);
  empilhar(3);
  
  exibir();

  printf("Desempilhando:\n\n");
  printf("%i\n", desempilhar());
  printf("%i\n", desempilhar());
  printf("%i\n", desempilhar());

  printf("\n\n");

  exibir();

  return 0;
}

Pilha.C:
#include <stdio.h>
#include <stdlib.h>
#include "pilha.h"

#define TAM_PILHA 3

int pilha[TAM_PILHA], topo=0;

void empilhar(int valor){

  if(cheia()){

    printf("Pilha cheia!");

  }
  else{

    pilha[topo] = valor;
    topo++;

  }

}

int desempilhar(){
  
  int itemRetirado = 0;

  if(vazia()){

    printf("Pilha vazia!");

  }
  else{

    itemRetirado = pilha[0];

    //Fazer a pilha andar
    for(int i=0; i < topo-1; i++){
      pilha[i] = pilha[i+1];
    }

    topo--;

  }

  return itemRetirado;

}

int vazia(){

  if(topo == 0){
    return 1;
  }
  else{
    return 0;
  }

}

int cheia(){

  if(topo == TAM_PILHA){
    return 1;
  }
  else{
    return 0;
  }

}

void exibir(){

  if(vazia()){

    printf("Pilha vazia!");

  }
  else{

    for(int i=0; i<topo; i++){
      printf("%i\n", pilha[i]);
    }

  }

}

void esvaziar(){

  // Enquanto a pilha não estiver vazia
  while(!vazia()){
    desempilhar();
  }

}

Pilha.H:
void empilhar(int valor);

int  desempilhar();

int vazia();

int cheia();

void exibir();

void esvaziar();


