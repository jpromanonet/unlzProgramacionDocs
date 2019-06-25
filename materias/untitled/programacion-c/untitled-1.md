# Parciales\|Finales

## 1° Parcial

## TP Final

{% hint style="info" %}
El trabajo practico final, es un ABM\(Altas, Bajas, Modificaciones\) que guarda empleados, clientes, presupuestos, proveedores, facturas, etc en archivos de formato .dat, más abajo de link voy a dejar el codigo quoteado.
{% endhint %}

### Link ABM

{% embed url="https://raw.githubusercontent.com/jpromanonet/facultadClasesYProyectos/master/C%26C%2B%2B/tpFinal/ABM.c" %}

### Codigo Fuente

```c
//*********************************************************
//Fecha: 27/06/2019                                       *
//Autor: Juan P. Romano                                   *
//Mail: programming@jpromano.net                          *
//--------------------------------------------------------*
//Materia: Programacion C                                 *
//Universidad Nacional de Lomas de Zamora                 *
//--------------------------------------------------------*
//Consigna: ABM de Empleados(agregue extras)              *
//que guarde los datos en un archivo y los lea            *
//cuando sea solicitado, utilizando matrices, vectores    *
//y todo lo visto en clase, asi como los manuales de C    *
//*********************************************************
/*----------------------------------------------------------------------------------------------------------*/
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>

// Funcion principal de Menu
void menu();

// Punteros

//// Defino estructura de Empleado
typedef struct{
    char nombre[250];
    char apellido[250];
    int  dni;
    int  diaAlta;
    int  mesAlta;
    int  anioAlta;
    char email[250];
    int  telefono;
    int  sueldo;
    char obraSocial[50];
    int  nroEmpleado;
    char direccion[250];
    int  direccionNumero;
}Empleados;

//// Defino estructura de Presupuestos
typedef struct{
	int  codigoPresupuesto;
	char razonSocial[250];
	int  diaPresupuesto;
	int  mesPresupuesto;
	int  anioPresupuesto;
	int  precioPresupuesto;
	char moneda[100];
	char descripcion[250];
	char emailPresu[250];
}Presupuesto;

//// Defino estructura de Productos
typedef struct{
	int  codigoProducto;
	char nombreProducto[250];
	int  stock;
	int  precio;
	char moneda[3];
}Producto;

//// Defino estructura de Proveedor
typedef struct{
    char razonSocial[250];
    int  cuit;
    int  diaAlta;
    int  mesAlta;
    int  anioAlta;
    char email[250];
    int  telefono;
    char direccion[250];
    int  direccionNumero;
    char rubro[250];
}Proveedor;

//// Defino estructura de Cliente
typedef struct{
    char nombre[250];
    char apellido[250];
    int  dni;
    int  diaAlta;
    int  mesAlta;
    int  anioAlta;
    char email[250];
    int  telefono;
    int  nroCliente;
    char direccion[250];
    int  direccionNumero;
}Cliente;

// Funciones relacionales a las estructuras previamente definidas

//// Funciones de Empleados
void altaEmpleados();
void bajaEmpleados();
void modifEmpleados();
void listadoEmpleados();

//// Funciones de Presupuestos
void altaPresupuesto();
void bajaPresupuesto();
void modifPresupuesto();
void listadoPresupuesto();

//// Funciones de Productos
void altaProducto();
void bajaProducto();
void modifProducto();
void listadoProducto();

//// Funciones de Proveedores
void altaProveedor();
void bajaProveedor();
void modifProveedor();
void listadoProveedor();

//// Funciones de Cliente
void altaCliente();
void bajaCliente();
void modifCliente();
void listadoCliente();

//// Funciones Extras
void manual();
void licencia();

/*----------------------------------------------------------------------------------------------------------*/

// Funcion principal que llama al Menu
int main(){
    menu();
    return 0;
}

/*----------------------------------------------------------------------------------------------------------*/

// Menu y submenues

void menu(){
	// Color pantalla
	system("color 0a");
	
	// Variables de opciones de menues y sub-menues
    int opcion;
	int opcion2;
    do{
        // Menu Principal
    	printf("********************************************************\n");
    	printf("**                 ABM - TP FINAL - UNLZ              **\n");
    	printf("********************************************************\n");
    	printf("**                    MENU PRINCIPAL                  **\n");
    	printf("********************************************************\n");
        printf("--------------------------------------------------------\n");
        printf("||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
        printf("--------------------------------------------------------\n");
        printf("                          1) Empleados                 |\n");
        printf("========================================================\n");
        printf("                          2) Presupuestos              |\n");
        printf("                          3) Productos                 |\n");
        printf("                          4) Proveedores               |\n");
        printf("                          5) Clientes                  |\n");
        printf("========================================================\n");
        printf("                          6) Manuales                  |\n");
        printf("========================================================\n");
        printf("                          7) Licencia                  |\n");
        printf("========================================================\n");
        printf("                          8) Salir                     |\n");
        printf("--------------------------------------------------------\n");
        printf("Seleccione una opcion: ");
        scanf("%d",&opcion);
        system("cls");

        // Submenu ABM
        printf("--------------------------------------------------------\n");
        printf("--------------------------------------------------------\n");
        printf("                          1) Alta                      |\n");
        printf("                          2) Baja                      |\n");
        printf("                          3) Modificacion              |\n");
        printf("                          4) Listado                   |\n");
        printf("                          5) Menu                      |\n");
        printf("--------------------------------------------------------\n");
        printf("   Para ver Manual, Licencia o Salir, presiona (5)     |\n");
        printf("--------------------------------------------------------\n");
        printf("--------------------------------------------------------\n");
        printf("Seleccione una opcion: ");
		scanf("%d",&opcion2);
        system("cls");
            switch (opcion){
            	case 1:
                        switch(opcion2){
                            case 1:
                                altaEmpleados();
                                break;
							case 2:
                                bajaEmpleados();
                                break;
                            case 3:
                                modifEmpleados();
                                break;
                            case 4:
                                listadoEmpleados();
                                break;
							case 5:
                                menu();
                                break;
                        }
                    break;
                
				case 2:
                        switch(opcion2){
                            case 1:
                                altaPresupuesto();
                                break;
							case 2:
                                bajaPresupuesto();
                                break;
                            case 3:
                                modifPresupuesto();
                                break;
                            case 4:
                                listadoPresupuesto();
                                break;
							case 5:
                                menu();
                                break;
                        }
                    break;
                case 3:
                        switch(opcion2){
                            case 1:
                                altaProducto();
                                break;
                            case 2:
                                bajaProducto();
                                break;
                            case 3:
                                modifProducto();
                                break;
                            case 4:
                                listadoProducto();
                                break;
                            case 5:
                                menu();
                                break;
                        }
                    break;
                case 4:
                        switch(opcion2){
                            case 1:
                                altaProveedor();
                                break;
							case 2:
                                bajaProveedor();
                                break;
                            case 3:
                                modifProveedor();
                                break;
                            case 4:
                                listadoProveedor();
                                break;
                            case 5:
                                menu();
                                break;
                        }
                    break;
                case 5:
                        switch(opcion2){
                            case 1:
                                altaCliente();
                                break;
                            case 2:
                                bajaCliente();
                                break;
                            case 3:
                                modifCliente();
                                break;
                            case 4:
                                listadoCliente();
                                break;
                            case 5:
                                menu();
                                break;
                        }
                    break;
                case 6:
                	manual();
                	break;
                case 7:
                	licencia();
                	break;
                case 8:
                	exit(0);
                    break;

            }
    }while (opcion!=8);
}

/*----------------------------------------------------------------------------------------------------------*/

// ABM Empleados

//// Alta de empleados que se guardan en listaEmpleados.dat
void altaEmpleados(){
    FILE *pf;
    Empleados empleado;
    pf = fopen("listaEmpleados.dat","ab");
    printf("Ingrese nombre: ");
    scanf("%s", empleado.nombre);
    printf("Ingrese Apellido: ");
    scanf("%s", empleado.apellido);
    printf("Ingrese DNI: ");
    scanf("%d", &empleado.dni);
    printf("------------------------------------\n");
    printf("Ingrese dia de Alta: ");
    scanf("%d", &empleado.diaAlta);
    printf("Ingrese mes de Alta: ");
    scanf("%d", &empleado.mesAlta);
    printf("Ingrese anio de Alta: ");
    scanf("%d", &empleado.anioAlta);
    printf("------------------------------------\n");
    printf("Ingrese E-mail: ");
    scanf("%s", empleado.email);
    printf("Ingrese Telefono: ");
    scanf("%d", &empleado.telefono);
	printf("Ingrese Calle: ");
    scanf("%s", empleado.direccion);
	printf("Altura de calle: ");
    scanf("%d", &empleado.direccionNumero);
    printf("------------------------------------\n");  
    printf("Ingrese Sueldo a percibir: ");
    scanf("%d", &empleado.sueldo);
    printf("Ingrese Obra Social: ");
    scanf("%s", empleado.obraSocial);
    printf("------------------------------------\n");
    printf("Ingrese Nro de Empleado: ");
    scanf("%d", &empleado.nroEmpleado);
    fseek(pf,0L,SEEK_END);
    fwrite(&empleado,sizeof(Empleados),1,pf);
    fclose(pf);
    
    // Mensaje de exito
    printf("\n");
    printf("***********************************\n");
    printf("EMPLEADO CARGADO CON EXITO!\n");
    printf("***********************************\n");
    printf("\n");
	        
    // Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Baja de empleados guardados en listaEmpleados.dat por DNI
void bajaEmpleados(){
    FILE *pf,*pfaux;
    Empleados empleado;
    int documentoBaja;
    pf = fopen("listaEmpleados.dat","rb");
    pfaux = fopen("listaEmpleadosAux.dat","ab");
    printf("Ingrese DNI \n");
    scanf("%d",&documentoBaja);
    fread(&empleado,sizeof(Empleados),1,pf);
        while (!feof(pf)){
                if (empleado.dni != documentoBaja){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&empleado,sizeof(Empleados),1,pfaux);
                }
            fread(&empleado,sizeof(Empleados),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaEmpleados.dat");
    rename("listaEmpleadosAux.dat","listaEmpleados.dat");
    
    // Mensaje de baja
    printf("\n");
    printf("***********************************\n");
    printf("EMPLEADO DADO DE BAJA\n");
    printf("***********************************\n");
    printf("\n");
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Lista de empleados guardados en listaEmpleados.dat, listado general.
void listadoEmpleados(){
    FILE *pf;
    Empleados empleado;
    pf = fopen("listaEmpleados.dat","rb");
    fread(&empleado,sizeof(Empleados),1,pf);
    while(!feof(pf)){
    	// Ficha de empleado
    	system("color 0a");
    	printf("*************************************\n");
    	printf("Numero de empleado: %d\n", empleado.nroEmpleado);
    	printf("*************************************\n");
    	printf("=========DATOS PERSONALES========\n");
        printf("Nombre: %s\n", empleado.nombre);
        printf("Apellido: %s\n", empleado.apellido);
        printf("DNI: %d\n", empleado.dni);
        printf("=============INGRESO=============\n");
        printf("Fecha de alta: %d", empleado.diaAlta);
		printf("/%d", empleado.mesAlta);  
		printf("/%d\n", empleado.anioAlta); 
		printf("=============CONTACTO============\n");
        printf("Email: %s\n", empleado.email);
        printf("Telefono: %d\n", empleado.telefono);
        printf("Direccion: %s", empleado.direccion);
        printf(" %d\n", empleado.direccionNumero);
        printf("==============SUELDO=============\n");
        printf("Sueldo: %d\n", empleado.sueldo);
        printf("==============BENEFICIOS=========\n");
        printf("Obra Social: %s\n", empleado.obraSocial);
        printf("*************************************\n");
        printf("\n");
        fread(&empleado,sizeof(Empleados),1,pf);
    }
    fclose(pf);
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Modificacion de Empleados guardados en listaEmpleados.dat, por valor, es decir parametro a cambiar.
void modifEmpleados(){
    FILE *pf,*pfaux;
    Empleados empleado;
    int documento;
    int opcionModifica;
    pf = fopen("listaEmpleados.dat","rb");
    pfaux = fopen("listaEmpleadosAux.dat","ab");
    printf("Buscar DNI: ");
    scanf("%d",&documento);
    fread(&empleado,sizeof(Empleados),1,pf);
        while (!feof(pf)){
                if (empleado.dni != documento){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&empleado,sizeof(Empleados),1,pfaux);
                }else{
                	// Sub menu para seleccionar el valor a modificar de la ficha de empleado.
                	printf("*********************************************************\n");
    				printf("**                    MODIFICAR EMPLEADO               **\n");
    				printf("*********************************************************\n");
        			printf("---------------------------------------------------------\n");
        			printf("|||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
                	printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("                          1) Direccion                  |\n");
                    printf("                          2) Sueldo                     |\n");
                    printf("                          3) Obra Social                |\n");
                    printf("                          4) E-mail                     |\n");
                    printf("                          5) Telefono                   |\n");
                    printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("Seleccione una opcion: ");
		            scanf("%d",&opcionModifica);
                        switch (opcionModifica){
                        	case 1:
                        		printf("---------------------------------------------------------\n");
                               	printf("Ingrese Nueva Calle: ");
                                scanf("%s",empleado.direccion);
                                printf("Numero de Calle: ");
                                scanf("%d",&empleado.direccionNumero);
								system("cls");
								break;
							case 2:
								printf("---------------------------------------------------------\n");
								printf("Nuevo Sueldo o Actual: ");
                                scanf("%d",&empleado.sueldo);
								system("cls");
								break;
							case 3:
								printf("---------------------------------------------------------\n");
								printf("Ingrese Nueva Obra Social: ");
                                scanf("%s",empleado.obraSocial);
								system("cls");
								break;
							case 4:
								printf("---------------------------------------------------------\n");
								printf("Ingrese Nuevo E-mail: ");
                                scanf("%s",empleado.email);
								system("cls");
								break;
							case 5:
								printf("---------------------------------------------------------\n");
							 	printf("Ingrese Nuevo Telefono: ");
                                scanf("%d",empleado.telefono);
                                system("cls");
								break;
                        }
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&empleado,sizeof(Empleados),1,pfaux);
                }
            fread(&empleado,sizeof(Empleados),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaEmpleados.dat");
    rename("listaEmpleadosAux.dat","listaEmpleados.dat");
}

/*----------------------------------------------------------------------------------------------------------*/

// ABM Presupuestos

//// Alta de empleados que se guardan en listaEmpleados.dat
void altaPresupuesto(){
    FILE *pf;
    Presupuesto pres;
    pf = fopen("listaPresupuestos.dat","ab");
    printf("Ingrese codigo de presupuesto (Hasta 8 digitos): ");
    scanf("%d", &pres.codigoPresupuesto);
    printf("Ingrese Razon Social: ");
    scanf("%s", pres.razonSocial);
    printf("Ingrese descripcion: ");
    scanf("%s", pres.descripcion);
    printf("------------------------------------\n");
    printf("Ingrese Precio Estimado: ");
    scanf("%d", &pres.precioPresupuesto);
    printf("Ingrese moneda: ");
    scanf("%s", pres.moneda);
    printf("------------------------------------\n");
    printf("Ingrese dia de emision: ");
    scanf("%d", &pres.diaPresupuesto);
    printf("Ingrese mes de emision: ");
    scanf("%d", &pres.mesPresupuesto);
    printf("Ingrese anio de emision: ");
    scanf("%d", &pres.anioPresupuesto);
    printf("------------------------------------\n");
    printf("Ingrese E-mail de contacto: ");
    scanf("%s", pres.emailPresu);
    fseek(pf,0L,SEEK_END);
    fwrite(&pres,sizeof(Presupuesto),1,pf);
    fclose(pf);
    
    // Mensaje de exito
    printf("\n");
    printf("***********************************\n");
    printf("PRESUPUESTO GENERADO CON EXITO!\n");
    printf("***********************************\n");
    printf("\n");
	        
    // Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Baja de presupuestos guardados en listaPresupuestos.dat por Codigo de Presupuesto
void bajaPresupuesto(){
    FILE *pf,*pfaux;
    Presupuesto pres;
    int codigoBaja;
    pf = fopen("listaPresupuestos.dat","rb");
    pfaux = fopen("listaPresupuestosAux.dat","ab");
    printf("Ingrese Codigo de Presupuesto \n");
    scanf("%d",&codigoBaja);
    fread(&pres,sizeof(Presupuesto),1,pf);
        while (!feof(pf)){
                if (pres.codigoPresupuesto != codigoBaja){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&pres,sizeof(Presupuesto),1,pfaux);
                }
            fread(&pres,sizeof(Presupuesto),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaPresupuestos.dat");
    rename("listaPresupuestosAux.dat","listaPresupuestos.dat");
    
    // Mensaje de baja
    printf("\n");
    printf("***********************************\n");
    printf("PRESUPUESTO DADO DE BAJA\n");
    printf("***********************************\n");
    printf("\n");
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Lista de presupuestos guardados en listaPresupuestos.dat, listado general.
void listadoPresupuesto(){
    FILE *pf;
    Presupuesto pres;
    pf = fopen("listaPresupuestos.dat","rb");
    fread(&pres,sizeof(Presupuesto),1,pf);
    while(!feof(pf)){
    	// Ficha de Presupuesto
    	system("color 0a");
    	printf("*************************************\n");
    	printf("Codigo de Presupuesto: %d\n", pres.codigoPresupuesto);
    	printf("*************************************\n");
    	printf("=========DATOS SOLICITANTE========\n");
        printf("Razon Social: %s\n", pres.razonSocial);
        printf("Descripcion: %s\n", pres.descripcion);
        printf("Mail Contacto: %s\n", pres.emailPresu);
        printf("------------------------------------\n");
        printf("Precio: %d", pres.precioPresupuesto);
        printf(" %s\n", pres.moneda);
        printf("===============FECHA==============\n");
        printf("Fecha de emision: %d", pres.diaPresupuesto);
		printf("/%d", pres.mesPresupuesto);  
		printf("/%d\n", pres.anioPresupuesto); 
        printf("*************************************\n");
        printf("\n");
        fread(&pres,sizeof(Presupuesto),1,pf);
    }
    fclose(pf);
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Modificacion de presupuestos guardados en listaPresupuestos.dat, por valor, es decir parametro a cambiar.
void modifPresupuesto(){
    FILE *pf,*pfaux;
    Presupuesto pres;
    int presModifica;
    int opcionModifica;
    pf = fopen("listaPresupuestos.dat","rb");
    pfaux = fopen("listaPresupuestosAux.dat","ab");
    printf("Buscar Codigo Presupuesto: ");
    scanf("%d",&presModifica);
    fread(&pres,sizeof(Presupuesto),1,pf);
        while (!feof(pf)){
                if (pres.codigoPresupuesto != presModifica){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&pres,sizeof(Presupuesto),1,pfaux);
                }else{
                	// Sub menu para seleccionar el valor a modificar de la ficha de presupuestos.
                	printf("*********************************************************\n");
    				printf("**                    MODIFICAR PRESUPUESTO            **\n");
    				printf("*********************************************************\n");
        			printf("---------------------------------------------------------\n");
        			printf("|||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
                	printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("                          1) Valor                      |\n");
                    printf("                          2) Email                      |\n");
                    printf("                          3) Descripcion                |\n");
                    printf("                          4) Razon Social               |\n");
                    printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("Seleccione una opcion: ");
		            scanf("%d",&opcionModifica);
                        switch (opcionModifica){
                        	case 1:
                        		printf("---------------------------------------------------------\n");
                               	printf("Ingrese Nuevo Precio: ");
                                scanf("%d",&pres.precioPresupuesto);
                                printf("Ingrese Moneda: ");
                                scanf("%s",pres.moneda);
								system("cls");
								break;
							case 2:
								printf("---------------------------------------------------------\n");
								printf("Nuevo E-mail: ");
                                scanf("%s",pres.emailPresu);
								system("cls");
								break;
							case 3:
								printf("---------------------------------------------------------\n");
								printf("Ingrese Nueva Descripcion: ");
                                scanf("%s",pres.descripcion);
								system("cls");
								break;
							case 4:
								printf("---------------------------------------------------------\n");
								printf("Ingrese Razon Social: ");
                                scanf("%s",pres.razonSocial);
								system("cls");
								break;
                        }
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&pres,sizeof(Presupuesto),1,pfaux);
                }
            fread(&pres,sizeof(Presupuesto),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaPresupuestos.dat");
    rename("listaPresupuestosAux.dat","listaPresupuestos.dat");
}

/*----------------------------------------------------------------------------------------------------------*/

// ABM Productos

//// Alta de productos que se guardan en listaProductos.dat
void altaProducto(){
    FILE *pf;
    Producto prod;
    pf = fopen("listaProductos.dat","ab");
    printf("Ingrese codigo de nuevo producto (Numero): ");
    scanf("%d", &prod.codigoProducto);
    printf("Ingrese nombre: ");
    scanf("%s", prod.nombreProducto);
    printf("------------------------------------\n");
    printf("Ingrese Precio: ");
    scanf("%d", &prod.precio);
    printf("Ingrese moneda: ");
    scanf("%s", prod.moneda);
    printf("------------------------------------\n");
    printf("Ingrese stock (cantidad): ");
    scanf("%d", &prod.stock);
    fseek(pf,0L,SEEK_END);
    fwrite(&prod,sizeof(Producto),1,pf);
    fclose(pf);
    
    // Mensaje de exito
    printf("\n");
    printf("***********************************\n");
    printf("PRODUCTO GENERADO CON EXITO!\n");
    printf("***********************************\n");
    printf("\n");
	        
    // Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Baja de productos guardados en listaProductos.dat por Codigo de Producto
void bajaProducto(){
    FILE *pf,*pfaux;
    Producto prod;
    int codigoProductoBaja;
    pf = fopen("listaProductos.dat","rb");
    pfaux = fopen("listaProductosAux.dat","ab");
    printf("Ingrese Codigo de Producto: ");
    scanf("%d", &codigoProductoBaja);
    fread(&prod,sizeof(Producto),1,pf);
        while (!feof(pf)){
                if (prod.codigoProducto != codigoProductoBaja){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prod,sizeof(Producto),1,pfaux);
                }
            fread(&prod,sizeof(Producto),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaProductos.dat");
    rename("listaProductosAux.dat","listaProductos.dat");
    
    // Mensaje de baja
    printf("\n");
    printf("***********************************\n");
    printf("PRODUCTO DADO DE BAJA\n");
    printf("***********************************\n");
    printf("\n");
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Lista de productos guardados en listaProductos.dat, listado general.
void listadoProducto(){
    FILE *pf;
    Producto prod;
    pf = fopen("listaProductos.dat","rb");
    fread(&prod,sizeof(Producto),1,pf);
    while(!feof(pf)){
    	// Ficha de Producto
    	system("color 0a");
    	printf("*************************************\n");
    	printf("Codigo de Producto: %d\n", prod.codigoProducto);
    	printf("*************************************\n");
    	printf("=========DESCRIPCION========\n");
        printf("Nombre: %s\n", prod.nombreProducto);
        printf("========PRECIO Y STOCK======\n");
		printf("Precio: %d", prod.precio);
        printf(" %s\n", prod.moneda);
        printf("----------------------------\n");
        printf("Stock: %d\n", prod.stock);
        printf("*************************************\n");
        printf("\n");
        fread(&prod,sizeof(Producto),1,pf);
    }
    fclose(pf);
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Modificacion de productos guardados en listaProductos.dat, por valor, es decir parametro a cambiar.
void modifProducto(){
    FILE *pf,*pfaux;
    Producto prod;
    int prodModifica;
    int opcionValorProd;
    pf = fopen("listaProductos.dat","rb");
    pfaux = fopen("listaProductosAux.dat","ab");
    printf("Buscar Codigo de Producto: ");
    scanf("%d",&prodModifica);
    fread(&prod,sizeof(Producto),1,pf);
        while (!feof(pf)){
                if (prod.codigoProducto != prodModifica){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prod,sizeof(Producto),1,pfaux);
                }else{
                	// Sub menu para seleccionar el valor a modificar de la ficha de producto.
                	printf("*********************************************************\n");
    				printf("**                    MODIFICAR PRODUCTO               **\n");
    				printf("*********************************************************\n");
        			printf("---------------------------------------------------------\n");
        			printf("|||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
                	printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("                          1) Valor                      |\n");
                    printf("                          2) Nombre                     |\n");
                    printf("                          3) Stock                      |\n");
                    printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("Seleccione una opcion: ");
		            scanf("%d",&opcionValorProd);
                        switch (opcionValorProd){
                        	case 1:
                        		printf("---------------------------------------------------------\n");
                               	printf("Ingrese Nuevo Precio: ");
                                scanf("%d",&prod.precio);
                                printf("Ingrese Moneda: ");
                                scanf("%s",prod.moneda);
								system("cls");
								break;
							case 2:
								printf("---------------------------------------------------------\n");
								printf("Nuevo Nombre: ");
                                scanf("%s",prod.nombreProducto);
								system("cls");
								break;
							case 3:
								printf("---------------------------------------------------------\n");
								printf("Ingrese stock: ");
                                scanf("%d", &prod.stock);
								system("cls");
								break;
                        }
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prod,sizeof(Producto),1,pfaux);
                }
            fread(&prod,sizeof(Producto),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaProductos.dat");
    rename("listaProductosAux.dat","listaProductos.dat");
}

/*----------------------------------------------------------------------------------------------------------*/

// ABM Proveedores

//// Alta de proveedores que se guardan en listaProveedores.dat
void altaProveedor(){
    FILE *pf;
    Proveedor prov;
    pf = fopen("listaProveedores.dat","ab");
    printf("Ingrese razon social: ");
    scanf("%s", prov.razonSocial);
    printf("Ingrese Rubro: ");
    scanf("%s", prov.rubro);
    printf("Ingrese CUIT(Junto, sin guiones): ");
    scanf("%d", &prov.cuit);
    printf("------------------------------------\n");
    printf("Ingrese dia de Alta: ");
    scanf("%d", &prov.diaAlta);
    printf("Ingrese mes de Alta: ");
    scanf("%d", &prov.mesAlta);
    printf("Ingrese anio de Alta: ");
    scanf("%d", &prov.anioAlta);
    printf("------------------------------------\n");
    printf("Ingrese E-mail: ");
    scanf("%s", prov.email);
    printf("Ingrese Telefono: ");
    scanf("%d", &prov.telefono);
	printf("Ingrese Calle: ");
    scanf("%s", prov.direccion);
	printf("Altura de calle: ");
    scanf("%d", &prov.direccionNumero);  
    fseek(pf,0L,SEEK_END);
    fwrite(&prov,sizeof(Proveedor),1,pf);
    fclose(pf);
    
    // Mensaje de exito
    printf("\n");
    printf("***********************************\n");
    printf("PROVEEDOR CARGADO CON EXITO!\n");
    printf("***********************************\n");
    printf("\n");
	        
    // Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Baja de proveedor guardados en listaProveedores.dat por CUIT de proveedor
void bajaProveedor(){
    FILE *pf,*pfaux;
    Proveedor prov;
    int cuitProveedor;
    pf = fopen("listaProveedores.dat","rb");
    pfaux = fopen("listaProveedoresAux.dat","ab");
    printf("Ingrese CUIT: ");
    scanf("%d", &cuitProveedor);
    fread(&prov,sizeof(Proveedor),1,pf);
        while (!feof(pf)){
                if (prov.cuit != cuitProveedor){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prov,sizeof(Proveedor),1,pfaux);
                }
            fread(&prov,sizeof(Proveedor),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaProveedores.dat");
    rename("listaProveedoresAux.dat","listaProveedores.dat");
    
    // Mensaje de baja
    printf("\n");
    printf("***********************************\n");
    printf("PROVEEDOR DADO DE BAJA\n");
    printf("***********************************\n");
    printf("\n");
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Lista de proveedores guardados en listaProveedores.dat, listado general.
void listadoProveedor(){
    FILE *pf;
    Proveedor prov;
    pf = fopen("listaProveedores.dat","rb");
    fread(&prov,sizeof(Proveedor),1,pf);
    while(!feof(pf)){
    	// Ficha de Proveedor
    	system("color 0a");
    	printf("*************************************\n");
    	printf("CUIT: %d\n", prov.cuit);
        printf("----------------------------\n");
        printf("Rubro: %s\n", prov.rubro);
    	printf("*************************************\n");
    	printf("=========DATOS CONTACTO========\n");
        printf("Razon Social: %s\n", prov.razonSocial);
        printf("----------------------------\n");
        printf("E-mail: %s\n", prov.email);
        printf("Telefono: %d\n", prov.telefono);
        printf("E-mail: %s", prov.direccion);
        printf(" %d\n", prov.direccionNumero);
        printf("==============FECHA============\n");
		printf("Fecha Alta: %d", prov.diaAlta);
		printf("/%d", prov.mesAlta);
		printf("/%d\n", prov.anioAlta);
        printf("*************************************\n");
        printf("\n");
        fread(&prov,sizeof(Proveedor),1,pf);
    }
    fclose(pf);
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Modificacion de proveedores guardados en listaProveedores.dat, por valor, es decir parametro a cambiar.
void modifProveedor(){
    FILE *pf,*pfaux;
    Proveedor prov;
    int provModifica;
    int opcionValorProv;
    pf = fopen("listaProveedores.dat","rb");
    pfaux = fopen("listaProveedoresAux.dat","ab");
    printf("Buscar por CUIT: ");
    scanf("%d",&provModifica);
    fread(&prov,sizeof(Proveedor),1,pf);
        while (!feof(pf)){
                if (prov.cuit != provModifica){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prov,sizeof(Proveedor),1,pfaux);
                }else{
                	// Sub menu para seleccionar el valor a modificar de la ficha de proveedores.
                	printf("*********************************************************\n");
    				printf("**                    MODIFICAR PROVEEDOR              **\n");
    				printf("*********************************************************\n");
        			printf("---------------------------------------------------------\n");
        			printf("|||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
                	printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("                          1) Razon Social               |\n");
                    printf("                          2) Telefono                   |\n");
                    printf("                          3) E-mail                     |\n");
                    printf("                          4) Direccion                  |\n");
                    printf("                          5) Rubro                      |\n");
                    printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("Seleccione una opcion: ");
		            scanf("%d",&opcionValorProv);
                        switch (opcionValorProv){
                        	case 1:
                        		printf("---------------------------------------------------------\n");
                               	printf("Ingrese Razon Social: ");
                                scanf("%s", prov.razonSocial);
								system("cls");
								break;
							case 2:
								printf("---------------------------------------------------------\n");
								printf("Nuevo Telefono: ");
                                scanf("%d", &prov.telefono);
								system("cls");
								break;
							case 3:
								printf("---------------------------------------------------------\n");
								printf("Nuevo E-mail: ");
                                scanf("%s", prov.email);
								system("cls");
								break;
							case 4:
								printf("---------------------------------------------------------\n");
								printf("Nueva calle: ");
                                scanf("%s", prov.direccion);
                                printf("Altura: ");
                                scanf("%d", &prov.direccionNumero);
								system("cls");
								break;
							case 5:
								printf("---------------------------------------------------------\n");
								printf("Nuevo Rubro: ");
                                scanf("%s", prov.rubro);
								system("cls");
								break;
                        }
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&prov,sizeof(Proveedor),1,pfaux);
                }
            fread(&prov,sizeof(Proveedor),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaProveedores.dat");
    rename("listaProveedoresAux.dat","listaProveedores.dat");
}

/*----------------------------------------------------------------------------------------------------------*/

// ABM Clientes

//// Alta de Cliente que se guardan en listaClientes.dat
void altaCliente(){
    FILE *pf;
    Cliente cl;
    pf = fopen("listaClientes.dat","ab");
    printf("Ingrese nombre: ");
    scanf("%s", cl.nombre);
    printf("Ingrese Apellido: ");
    scanf("%s", cl.apellido);
    printf("Ingrese DNI: ");
    scanf("%d", &cl.dni);
    printf("------------------------------------\n");
    printf("Ingrese dia de Alta: ");
    scanf("%d", &cl.diaAlta);
    printf("Ingrese mes de Alta: ");
    scanf("%d", &cl.mesAlta);
    printf("Ingrese anio de Alta: ");
    scanf("%d", &cl.anioAlta);
    printf("------------------------------------\n");
    printf("Ingrese E-mail: ");
    scanf("%s", cl.email);
    printf("Ingrese Telefono: ");
    scanf("%d", &cl.telefono);
	printf("Ingrese Calle: ");
    scanf("%s", cl.direccion);
	printf("Altura de calle: ");
    scanf("%d", &cl.direccionNumero);
    printf("------------------------------------\n");
    printf("Ingrese Nro de Cliente: ");
    scanf("%d", &cl.nroCliente);
    fseek(pf,0L,SEEK_END);
    fwrite(&cl,sizeof(Cliente),1,pf);
    fclose(pf);
    
    // Mensaje de exito
    printf("\n");
    printf("***********************************\n");
    printf("CLIENTE CARGADO CON EXITO!\n");
    printf("***********************************\n");
    printf("\n");
	        
    // Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Baja de clientes guardados en listaClientes.dat por nroCliente
void bajaCliente(){
    FILE *pf,*pfaux;
    Cliente cl;
    int numeroCliente;
    pf = fopen("listaClientes.dat","rb");
    pfaux = fopen("listaClientesAux.dat","ab");
    printf("Ingrese Nro de Cliente: ");
    scanf("%d", &numeroCliente);
    fread(&cl,sizeof(Cliente),1,pf);
        while (!feof(pf)){
                if (cl.nroCliente != numeroCliente){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&cl,sizeof(Cliente),1,pfaux);
                }
            fread(&cl,sizeof(Cliente),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaClientes.dat");
    rename("listaClientesAux.dat","listaClientes.dat");
    
    // Mensaje de baja
    printf("\n");
    printf("***********************************\n");
    printf("CLIENTE DADO DE BAJA\n");
    printf("***********************************\n");
    printf("\n");
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Lista de clientes guardados en listaClientes.dat, listado general.
void listadoCliente(){
    FILE *pf;
    Cliente cl;
    pf = fopen("listaClientes.dat","rb");
    fread(&cl,sizeof(Cliente),1,pf);
    while(!feof(pf)){
    	// Ficha de Cliente
    	system("color 0a");
    	printf("*************************************\n");
    	printf("Nro Cliente: %d\n", cl.nroCliente);
        printf("----------------------------\n");
        printf("DNI: %d\n", cl.dni);
    	printf("*************************************\n");
    	printf("=========DATOS CONTACTO========\n");
        printf("Nombre: %s", cl.nombre);
        printf(" %s\n", cl.apellido);
        printf("----------------------------\n");
        printf("E-mail: %s\n", cl.email);
        printf("Telefono: %d\n", cl.telefono);
        printf("E-mail: %s", cl.direccion);
        printf(" %d\n", cl.direccionNumero);
        printf("==============FECHA============\n");
		printf("Fecha Alta: %d", cl.diaAlta);
		printf("/%d", cl.mesAlta);
		printf("/%d\n", cl.anioAlta);
        printf("*************************************\n");
        printf("\n");
        fread(&cl,sizeof(Cliente),1,pf);
    }
    fclose(pf);
    
    // Presiona para continuar  
	system("pause"); 
	system("cls");
}

//// Modificacion de clientes guardados en listaClientes.dat, por valor, es decir parametro a cambiar.
void modifCliente(){
    FILE *pf,*pfaux;
    Cliente cl;
    int clienteModifica;
    int opcionValorCliente;
	pf = fopen("listaClientes.dat","rb");
    pfaux = fopen("listaClientesAux.dat","ab");
    printf("Buscar por Nro Cliente: ");
    scanf("%d",&clienteModifica);
    fread(&cl,sizeof(Cliente),1,pf);
        while (!feof(pf)){
                if (cl.nroCliente != clienteModifica){
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&cl,sizeof(Cliente),1,pfaux);
                }else{
                	// Sub menu para seleccionar el valor a modificar de la ficha de clientes.
                	printf("*********************************************************\n");
    				printf("**                    MODIFICAR CLIENTE                **\n");
    				printf("*********************************************************\n");
        			printf("---------------------------------------------------------\n");
        			printf("|||||||||||||||||||||||||||||||||||||||||||||||||||||||||\n");
                	printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("                          1) Telefono                   |\n");
                    printf("                          2) E-mail                     |\n");
                    printf("                          3) Direccion                  |\n");
                    printf("---------------------------------------------------------\n");
                    printf("---------------------------------------------------------\n");
                    printf("Seleccione una opcion: ");
		            scanf("%d",&opcionValorCliente);
                        switch (opcionValorCliente){
							case 1:
								printf("---------------------------------------------------------\n");
								printf("Nuevo Telefono: ");
                                scanf("%d", &cl.telefono);
								system("cls");
								break;
							case 2:
								printf("---------------------------------------------------------\n");
								printf("Nuevo E-mail: ");
                                scanf("%s", cl.email);
								system("cls");
								break;
							case 3:
								printf("---------------------------------------------------------\n");
								printf("Nueva calle: ");
                                scanf("%s", cl.direccion);
                                printf("Altura: ");
                                scanf("%d", &cl.direccionNumero);
								system("cls");
								break;
                        }
                    fseek(pfaux,0l,SEEK_END);
                    fwrite(&cl,sizeof(Cliente),1,pfaux);
                }
            fread(&cl,sizeof(Cliente),1,pf);
        }
    fclose(pf);
    fclose(pfaux);
    remove("listaClientes.dat");
    rename("listaClientesAux.dat","listaClientes.dat");
}

/*----------------------------------------------------------------------------------------------------------*/

// Manual y Licencia

//// Manual de usuario
void manual(){
	printf("******************************************************************************\n");
	printf("******************************** MANUAL DE USO *******************************\n");
	printf("******************************************************************************\n");
	printf("******************************************************************************\n");
	printf("*                                                                            *\n");
	printf("*1. Empleados:                                                               *\n");
	printf("*                                                                            *\n");
	printf("*      Permite cargar, dar de baja, modificar y listar los empleados         *\n");
	printf("*registrados, los valores que maneja son: nombre(Solo un nombre), Apellido(1)*\n");
	printf("*DNI, Telefono, email, direccion(primero la calle, luego la altura), sueldo y*\n");
	printf("*Obra Social, asi como numero de empleado.                                   *\n");
	printf("*                                                                            *\n");
	printf("*      Se da de baja utilizando el DNI, lo elimina del listado y no hay BKP  *\n");
	printf("*                                                                            *\n");
	printf("*      Permite modificar sueldo, direccion, telefono, email, obra social     *\n");
	printf("*                                                                            *\n");
	printf("*      Lista los empleados con una pequenia ficha con sus datos ordenados    *\n");
	printf("*============================================================================*\n");
	printf("*                                                                            *\n");
	printf("*2. Presupuestos:                                                            *\n");
	printf("*                                                                            *\n");
	printf("*      Permite generar presupuestos, asignando un codigo de presupuesto, una *\n");
	printf("*razon social, y fecha de generacion (primero cargar dia, luego mes y anio ) *\n");
	printf("*precio(solo valor numero), moneda(ARS, U$S, etc), descripcion(una palabra)  *\n");
	printf("* y el E-mail del contacto al que se envia el presupuesto.                   *\n");
	printf("*                                                                            *\n");
	printf("*      Los presupuestos se dan de baja, utilizando el codigo de presupuesto  *\n");
	printf("*y no hay BackUp una vez borrado.                                            *\n");
	printf("*                                                                            *\n");
	printf("*      Permite modificar la razon social, el email, la descripcion y el valor*\n");
	printf("*                                                                            *\n");
	printf("*      Lista los presupuestos con una ficha con sus datos ordenados          *\n");
	printf("*============================================================================*\n");
	printf("*                                                                            *\n");
	printf("*3. Productos:                                                               *\n");
	printf("*                                                                            *\n");
	printf("*      Permite dar de alta productos, con codigo de producto, nombre, precio,*\n");
	printf("*moneda(ARS o U$S), y la cantidad de stock disponible                        *\n");
	printf("*                                                                            *\n");
	printf("*      Los productos se dan de baja utilizando el codigo de producto y una   *\n");
	printf("*vez eliminado, no hay BackUp del producto en la lista de productos.         *\n");
	printf("*                                                                            *\n");
	printf("*      Permite modificar el valor, el nombre del producto y el stock disponi_*\n");
	printf("*ble.                                                                        *\n");
	printf("*                                                                            *\n");
	printf("*      Lista los presupuestos con una ficha con sus datos ordenados.         *\n");
	printf("*============================================================================*\n");
	printf("*                                                                            *\n");
	printf("*4. Proveedores:                                                             *\n");
	printf("*                                                                            *\n");
	printf("*      Permite dar de alta proveedores con razon social, rubro, CUIT, fecha  *\n");
	printf("*de alta, E-mail, telefono, direccion(primero calle, luego altura).          *\n");
	printf("*                                                                            *\n");
	printf("*      Los proveedores se dan de baja utilizando el CUIT y una vez dado de   *\n");
	printf("*baja, no puede restaurarse.                                                 *\n");
	printf("*                                                                            *\n");
	printf("*      Permite modificar la razon social, telefono, E-mail, direccion y rubro*\n");
	printf("*                                                                            *\n");
	printf("*      Lista los proveedores con una ficha con sus datos ordenados           *\n");
	printf("*============================================================================*\n");
	printf("*                                                                            *\n");
	printf("*5. Clientes:                                                                *\n");
	printf("*                                                                            *\n");
	printf("*      Permite dar de alta clientes con nombre(1), apellido(1), DNI, fecha de*\n");
	printf("*alta, e-mail, telefono, direccion(primero calle, luego altura), numero de   *\n");
	printf("*cliente.                                                                    *\n");
	printf("*                                                                            *\n");
	printf("*      Los clientes se dan de baja por numero de cliente y no se recuperan.  *\n");
	printf("*                                                                            *\n");
	printf("*      Permite modificar Telefono, E-mail y direccion(calle y luego altura)  *\n");
	printf("*                                                                            *\n");
	printf("*      Lista los clientes con una ficha con sus datos ordenados.             *\n");
	printf("*============================================================================*\n");
	printf("*                                                                            *\n");
	printf("*                                  EXTRAS                                    *\n");
	printf("*                                                                            *\n");
	printf("*Cuando seleccionas ver el manual, la licencia o salir, presiona 5 para      *\n");
	printf("*continuar.                                                                  *\n");
	printf("*============================================================================*\n");
	printf("******************************************************************************\n"); 
	printf("\n");
	// Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

//// Licencia GPLv3
void licencia(){
	printf("Copyright (C) 2019  Juan P. Romano | UNLZ\n");
	printf("\n");
    printf("This program is FREE SOFTWARE: you can redistribute it and/or modify\n");
    printf("it under the terms of the GNU General Public License as published by\n");
    printf("the Free Software Foundation, either version 3 of the License, or\n");
    printf("(at your option) any later version.\n");
	printf("\n");
    printf("This program is distributed in the hope that it will be useful,\n");
    printf("but WITHOUT ANY WARRANTY; without even the implied warranty of\n");
    printf("MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the\n");
    printf("GNU General Public License for more details.\n");
	printf("\n");
    printf("You should have received a copy of the GNU General Public License\n");
    printf("along with this program.  If not, see <https://www.gnu.org/licenses/>.\n");
    printf("\n");
	
	// Presiona para continuar  
	system("pause");
    
    // Limpia pantalla y vuelve al menu
	system("cls");
    menu();
}

```

