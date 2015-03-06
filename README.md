#include <stdio.h>
#include <stdlib.h>
/* Estructura de la lista del nodo */
struct ListaNode {
char data; /* Datos del nodo */
struct ListaNode *nextPtr; /* Puntero al siguiente nodo */
  }; /* Final de la estructura de la lista del nodo */
 typedef struct ListaNode ListaNode;
typedef ListaNode *ListaNodePtr;
 /* Prototipos de funciones */
 ListaNodePtr reverseList( ListaNodePtr currentPtr );
 void insert( ListaNodePtr *sPtr, char value );
void printList( ListaNodePtr currentPtr );
 void push( ListaNodePtr *topPtr, char info );

 int main()
 {
 ListaNodePtr listatr = NULL; /* Lista de punteros */
 char i; /* Contador del bucle */

 /* Construccion de lista de caracteres de A a J */
 for ( i = 'A'; i <= 'J'; i++ ) {
 insert( &listPtr, i );
 } /* Terminacion del for */

 printf( "la lista es:\n" );
 printList( listPtr );

 /* Revertir la lista y visualización de resultados */
 printf( "la lista en reverso es:\n" );
 printList( reverseList( listaPtr ) );

 return 0; /* Indicacion de terminacion exitosa */

 } /* Final principal */

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
