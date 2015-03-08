
#include <stdio.h>
#include <stdlib.h>
/* Estructura de la lista del nodo */
struct ListaNode {
int data; /* Datos del nodo */
struct ListaNode *nextPtr; /* Puntero al siguiente nodo */
  }; /* Final de la estructura de la lista del nodo */
 typedef struct ListaNode ListaNode;
typedef ListaNode *ListaNodePtr;
 /* Prototipos de funciones */
 ListaNodePtr reverseList( ListaNodePtr currentPtr );
 void insert( ListaNodePtr *sPtr, int value );
void printList( ListaNodePtr currentPtr );
 void push( ListaNodePtr *topPtr, int info );

 int main()
 {
 ListaNodePtr listatr = NULL; /* Lista de punteros */
 int i; 
 for ( i = 1; i <= 6; i++ ) {
 insert( &listPtr, i );
 } 

 printf( "la lista es:\n" );
 printList( listPtr );

 /* Revertir la lista y visualización de resultados */
 printf( "la lista en reverso es:\n" );
 printList( reverseList( listaPtr ) );

 return 0; } 

 /* Creacion de la lista en el orden inverso de la lista */
 ListaNodePtr reverseList( ListaNodePtr currentPtr )
 {
 ListaNodePtr stack = NULL; /* Puntero de la lista invertida*/

 /*Bucle de la lista currentPtr */
 while ( currentPtr != NULL ) {

 /* Empujar elemento actual en la pila */
 push( &stack, currentPtr->data );
 currentPtr = currentPtr->nextPtr;
 } /* fin del while */

 return stack; /* Volver a lista invertida */
return stack; /* Volver a lista invertida */
}
void insert( ListNodePtr *sPtr, char value )
 {
 ListNodePtr newPtr; /* Nodo nuevo */
 ListNodePtr previousPtr; /* Nodo anterior */
 ListNodePtr currentPtr; /* Nodo actual */

 /* Asignar dinámicamente la memoria */
 newPtr = malloc( sizeof( ListNode ) );

 /* if newPtr no es igual a NULL */
 if ( newPtr ) {
 newPtr->data = value;
 newPtr->nextPtr = NULL;

 previousPtr = NULL;
 currentPtr = *sPtr; /* Establece currentPtr para iniciar la lista */

 /*Bucle para encontrar la ubicación correcta en la lista */
 while ( currentPtr != NULL && value > currentPtr->data ) {
 previousPtr = currentPtr;
 currentPtr = currentPtr->nextPtr;
 } /* Fin del while */

 /* Insertar nuevo principio de la lista */
 if ( previousPtr == NULL ) {
 newPtr->nextPtr = *sPtr;
 *sPtr = newPtr;
 } /* Fin de if */
 else { /* Insertar nodo entre previousPtr y currentPtr */
 previousPtr->nextPtr = newPtr;
 newPtr->nextPtr = currentPtr;
 } /* fin else */

 } /* fin if */
 else {
 printf( "%c No insertado.\n", value );
 } /* fin else */

 } /*  Función de inserción final*/

 /* Insertar un nodo en la parte superior de pila */
 void push( ListNodePtr *topPtr, int info )
 {
 ListNodePtr newPtr; /* puntero del nodo temporal */

 /* Asignar memoria */
 newPtr = malloc( sizeof( ListNode ) );

 /*if si la memoria no se asigno inserte nodo en la parte superior de la lista  */
 if ( newPtr ) {
 newPtr->data = info;
 newPtr->nextPtr = *topPtr;
 *topPtr = newPtr;
 } /* Fin if */
 else {
 printf( "%c No insertado.\n", info );
 } /* Fin else */
 } /* Fin funcion push */

/* Imprimir la lista */
 void printList( ListNodePtr currentPtr )
 {

 /* if si la lista esta vacia */
 if ( !currentPtr ) {
 printf( "Lista vacia.\n\n" );
 } /* Fin if */
 else {

 /*  Bucle while currentPtr no es igual a NULL*/
 while ( currentPtr ) {
 printf( "%c ", currentPtr->data );
 currentPtr = currentPtr->nextPtr;
 } /* Fin while */

 printf( "*\n\n" );
 } /* Fin else */
 } /* Imprimir lista */
