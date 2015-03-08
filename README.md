#include <stdio.h>
#include <stdlib.h>



struct ListNode {
int data; 
struct ListNode *nextPtr; 
  }; 
 typedef struct ListNode ListNode;
typedef ListNode *ListNodePtr;

 ListNodePtr reverseList( ListNodePtr currentPtr );
 void insert( ListNodePtr *sPtr, int value );
void printList( ListNodePtr currentPtr );
 void push( ListNodePtr *topPtr, int info );
  int deci;

 int main()
 {
 printf("En este programa un usuario ingresara n cantidad de datos que desee en una lista, tales datos son numeros enteros, el programa almacenara estos e imprimira la lista al revez");
 ListNodePtr listPtr = NULL; 

 int i;
 int can;
 int num;

 	printf("Ingrese la cantida de numeros de la lista\n");
	scanf("%d",&can);
	
 	for(i=1;i<=can;i++)
	{	

	printf("\n\n ingrese el numero   %d ",i);
	scanf("%d",&num);
		insert( &listPtr,num);

	}

 printf( "La lista es:\n" );
 printList( listPtr );

/* Revertir la lista y visualización de resultados */
 printf( "La lista en reversa es:\n" );
 printList( reverseList( listPtr ) );

 return 0; 

 } 
 
 /* Creacion de la lista en el orden inverso de la lista */
 ListNodePtr reverseList( ListNodePtr currentPtr )
 {
 ListNodePtr stack = NULL;/* Puntero de la lista invertida*/

 /*Bucle de la lista currentPtr */
 while ( currentPtr != NULL ) {

 /* Empujar elemento actual en la pila */
 push( &stack, currentPtr->data );
 currentPtr = currentPtr->nextPtr;
 } 

 return stack;/* Volver a lista invertida */
}
void insert( ListNodePtr *sPtr, int value )
 {
 ListNodePtr newPtr; /* nuevo nodo*/
 ListNodePtr previousPtr; /* nodo anterior*/
 ListNodePtr currentPtr; /* nodo*/

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
 } 

 /* Insertar nuevo principio de la lista */
 if ( previousPtr == NULL ) {
 newPtr->nextPtr = *sPtr;
 *sPtr = newPtr;
 } 
 else { /* Insertar nodo entre previousPtr y currentPtr */
 previousPtr->nextPtr = newPtr;
 newPtr->nextPtr = currentPtr;
 } 

 } 
 else {
 printf( "%c no insertado.\n", value );
 } 

 } 

 /* Insertar un nodo en la parte superior de pila */
 void push( ListNodePtr *topPtr, int info )
 {
 ListNodePtr newPtr; /* puntero del nodo temporal */

 /* Asignar memoria */
 newPtr = malloc( sizeof( ListNode ) );

 if ( newPtr ) {
 newPtr->data = info;
 newPtr->nextPtr = *topPtr;
 *topPtr = newPtr;
 } 
 else {
 printf( "%c no insertado.\n", info );
 } 
 } 

/* imprimir la lista*/
 void printList( ListNodePtr currentPtr )
 {
 if ( !currentPtr ) {
 printf( "Lista vacia.\n\n" );
 } /* end if */
 else {

 /*  Bucle while currentPtr no es igual a NULL*/
 while ( currentPtr ) {
 printf( "%d ", currentPtr->data );
 currentPtr = currentPtr->nextPtr;
 } 
