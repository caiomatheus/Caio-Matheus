#include <stdio.h>
#include <stdlib.h>

typedef int elem_fila;

typedef struct {
	int cabeca;
	int cauda;
	elem_fila *elementos;
	int tam_max;

} Fila;

void construirFila(Fila *f, int tam_max){
	f->elementos = (int*) malloc(sizeof(int)*tam_max);
	f->cabeca = (-1);
	f->cauda = (-1);
	f->tam_max = tam_max;
}
void destruirFila(Fila *f){
	free(f->elementos);
	free(f);
}
void enfileirar(elem_fila elem, Fila *f){
    if(f->cauda == (f->tam_max)-1){
        printf("A fila esta cheia\n");
    }
    else{
        f->cauda += 1;
        f->cabeca = 0;
        f->elementos[f->cauda+1] = elem;
    }
}
elem_fila desenfileirar(Fila *f ){
    f->cabeca++;
    return (f->elementos[f->cabeca]);
}
int estahVazio(Fila *f){
	if (f->cabeca < 0){
		return 0;
	}
	else
		return 1;
}
elem_fila cabeca(Fila *f){
	return (f->elementos[f->cabeca]);
}
elem_fila cauda(Fila *f){
	return (f->elementos[f->cauda]);
}

int main(){
	int tam = 6;
	int x, y, c, a, b, d, e, f;
	
	Fila *fila = (Fila *)malloc(sizeof(Fila)*tam);
	
	construirFila(fila, tam);
	
	enfileirar(2, fila);
	enfileirar(3, fila);
	enfileirar(4, fila);
	enfileirar(5, fila);
	enfileirar(6, fila);
	enfileirar(7, fila);
	
	
	x = desenfileirar(fila);
    y = desenfileirar(fila);
    c = desenfileirar(fila);
    a = desenfileirar(fila);
    b = desenfileirar(fila);
    d = desenfileirar(fila);
    
    enfileirar(8, fila);
    e = desenfileirar(fila);
    printf("%d\n%d\n%d\n%d\n%d\n%d\n%d\n", x, y, c, a, b, d, e);
	
	
	
	return 0;
}


