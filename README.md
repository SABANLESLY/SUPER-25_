# SUPER-25_
PRACTICA# 1

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.super25;

import java.util.Scanner;

/**
 *
 * @author les_l
 */
public final class SUPER25 {

    

    /* 1. LOGIN EMPLEADO */
    
 public void lOGIN(){
     
            Scanner ingreso = new Scanner (System.in);
            System.out.println("                             ");
            System.out.println("-----------------------------");
            System.out.println("    BIENVENIDO A SUPER-25    ");
            System.out.println("                             ");
            System.out.println("* Ingrese su usuario:        ");
            String usuario = ingreso.nextLine();
            Scanner passw = new Scanner (System.in);
            System.out.println("* Ingrese su contraseña:     ");
            String contraseña = passw.nextLine();
            
            if (usuario.equals("Cajero") && contraseña.equals("admin")){
                System.out.println("Usuario y/o contraseña correcta");  
                    Menu();                      
            }else{
                System.out.println("Usuario y/o contraseña incorrecta, vuelve a intentarlo");
               lOGIN();
            }
        } 
 
 /* 2. Ingreso al Menú */
  
 public void Menu(){
        String eleccion = "";
        Scanner entrada = new Scanner(System.in);
        while(!eleccion.equals("5")){ 
            System.out.println("                                              ");
            System.out.println("                                              ");
            System.out.println("***************  MENÙ INCIAL  ****************");
            System.out.println("            SUPERMERCADO SUPER-25             ");
            System.out.println("                                              ");
            System.out.println("                                              ");
            System.out.println("Seleccione una opción:");
            System.out.println("1. Agregar nuevos productos");
            System.out.println("2. Agregar cupones de descuento");
            System.out.println("3. Realizar ventas");
            System.out.println("4. Reporte de artículos más comprados");
            System.out.println("5. Salir");
            eleccion = entrada.nextLine();
            switch(eleccion){
            case "1":
                Agregar_nuevos_productos();
                break;
            case "2":
                Agregar_nuevos_cupones();
                break;
            case "3":
                Realizar_ventas();
                break;
            case "4":
                Reporte_de_ventas(); 
                break;
            case "5":
                System.out.println(" -----------------------------------");
                System.out.println("|   GRACIAS POR VISITAR SUPER-25,  |");
                System.out.println("| ******************************** |");
                System.out.println("| ¡ Esperamos que vuelvas pronto ! |");
                System.out.println("------------------------------------");
                break;
                
            default:
                System.out.println("          **  ¡ UPS !  **           ");
                System.out.println("------------------------------------");
                System.out.println("Error, la opción ingresada no existe");
                System.out.println("------------------------------------");
                
            }
        }
 }
     
    public void Agregar_nuevos_productos() {
    String[] nombre_prod = new String[10];
    int contador_de_escritura = 0;

        System.out.println("*******************************");
        System.out.println("Ingrese el nombre del prodcuto");
        String nombre_de_mascota = entrada.nextLine(); 
        
        if (contador_de_escritura >= nombre_prod.length){
            System.out.println("Error, ya se ha alcanzado el maximo de productos que se pueden ingresar");
        } else {
            boolean nombre_repetido = false;
            for(int contador = 0; contador < nombre_prod.length; contador++){
                if (nombre_prod[contador] != null){
                    if (nombre_prod[contador].equals(nombre_de_mascota)){ 
                        System.out.println("Error, ya se ha ingresado ese producto: ");
                        nombre_repetido = true;
                    
                    }
                    if(nombre_repetido == true){
                        break;
                    }
                }
            }
            if (nombre_repetido == false){
                nombre_prod[contador_de_escritura] = nombre_de_mascota;
                contador_de_escritura++;
                System.out.println("El nombre ha sido ingresado con exito");
            }
        }
    

        System.out.println("************************");
        System.out.println("prodcuto");
        for(int contador = 0; contador < nombre_prod.length; contador++){
            if (nombre_prod[contador] != null){
                System.out.println("Nombre del prodcuto: " + nombre_prod[contador]);
            }
        }
    }

   

public void Agregar_nuevos_cupones(){
    int cant,opc = 0;
    double precio,pago,total,dev, acumtotal = 0, imp, desc, Subt;
    String  Producto, a, name = null;
    Scanner captu = new Scanner(System.in);
    
    while(opc!=2){
        
        a=captu.nextLine();
        System.out.println("* Ingrese nombre del producto: ");
        Producto = captu.nextLine();
        
        System.out.println("* Ingrese precio del producto: ");
        precio = captu.nextDouble();
        
        System.out.println("* Ingrese la cantidad del producto: ");
        cant = captu.nextInt();
        
        Subt = cant * precio;
        imp = Subt * 0.15;
        
        if(cant >= 0 && cant < 100){
            
            desc = Subt * 0.10;
        }
        else {
             desc = 0;
        }
        total = (Subt +imp) - desc;
       
        acumtotal += total;
    
        System.out.println("----------------------------------------------------------------------");
        System.out.println("                         VENTA SUPER-25                               ");
        System.out.println("\n\n Su impuesto es de:  "+imp+" ");
        System.out.println("\n\n Su descuento es de:  "+desc+" ");
        System.out.println("\n\n Su total por el producto "+Producto+" es de: "+total+" ");
        System.out.println("\n\n ");
        System.out.println("\n\n ¿Desea ingresar otro producto?  1. SI     2. NO");
        opc=captu.nextInt();
    }
        System.out.println("\n\n El total a pagar del cliente es de: "+acumtotal+" ");
        System.out.println("\n\n Cantidad de dinero con el que cliente pagara: ");
        pago = captu.nextDouble();
        
        dev = acumtotal = pago;
        
        if(pago > acumtotal){
            System.out.println("\n\n Tiene una deuda de: "+dev+" ");
            
        }
        else{
        System.out.println("\n\n Su pago es exacto: "+dev+" ¡GRACIAS POR SU COMPRA!");
                }

        }   

public void Realizar_ventas(){
  Agregar_nuevos_cupones();
    String Nombre, NIT,fecha,cajero;
    Scanner captu = new Scanner(System.in);

    System.out.println(" ***************** SISTEMA DE FACTURACIÓN ******************* ");
    System.out.println("                                                              ");
    System.out.println("- Nombre del cajer@:                                          ");
    cajero = captu.nextLine();
    System.out.println("- Ingrese el nombre del cliente:                              ");
    Nombre = captu.nextLine();
    System.out.println("- Ingrese el NIT del cliente:                                 ");
    NIT = captu.nextLine();
    System.out.println("- Ingrese la fecha: ");
    fecha = captu.nextLine();
    System.out.println("");
    System.out.println("                                                              ");
    System.out.println("* A continuación se muestra en detalle la factura generada    ");
    System.out.println("                                                              ");
    System.out.println("_______________________________________________________________");
    System.out.println("|                            FACTURA                          |");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("| SUPER-25                                    NO. FACTURA     |");
    System.out.println("| GUATEMALA,CITY                              FACT-LVXTPU     |");
    System.out.println("| Fecha de emisión: "+fecha+"                                |");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("| Cliente: "+Nombre+"                  NIT:"+NIT+"       |");
    System.out.println("|_____________________________________________________________|");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("| ID PRODUCTO |    DETALLE     | CANTIDAD | P. UNIDAD | TOTAL |");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("|"+id+"      "+Producto+"  "+cant+"  "+unit+" "+acumtotal+"");
    System.out.println("|                                                             |");
    System.out.println("|                                                             |");
    System.out.println("|                                                             |");
    System.out.println("|                                                             |");
    System.out.println("|                                                             |");
    System.out.println("|                                                             |");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("| Subtotal: "+Subt+"                       TOTAL:"+acumtotal+"|");
    System.out.println("|-------------------------------------------------------------|");
    System.out.println("| CAJER@:"+cajero+"                             |");
    System.out.println("|_____________________________________________________________|");   
   
}

 Scanner incio = new Scanner(System.in);
    String[] cofre = new String[10];
    String[][] inventario = new String[10][2];
    int contador_inventario = 0;
  
public void Reporte_de_ventas(){
    
 while(true){
            System.out.println("**************** INVENTARIO ***************************");
            System.out.println("Seleccione el número de PRODUCTOS a consultar: ");
            System.out.println("0. Salir");
            for(int contador = 0; contador  < cofre.length; contador++){
                System.out.println((contador + 1) + ". " + cofre[contador]);
            }
            int id_cofre = incio.nextInt();

            if(id_cofre == 0){
                break;
            }

          
            System.out.println("Ingrese la cantidad de productos a sacar: ");
            int cantidad = incio.nextInt();


            boolean ya_se_ha_escrito = false;
            for(int contador = 0; contador < inventario.length; contador++){
                if(inventario[contador][0] != null){
                    if(inventario[contador][0].equals(cofre[id_cofre - 1])){
                        inventario[contador][1] = Integer.parseInt(inventario[contador][1]) + cantidad + "";                        ya_se_ha_escrito = true;
                        break;
                    }
                }
            }
            if (!ya_se_ha_escrito){  
                inventario[contador_inventario][0] = cofre[id_cofre - 1];
                inventario[contador_inventario][1] = cantidad + ""; 
                contador_inventario++;
            }
        }



        System.out.println("Ahora se mostrará su inventario");
        for(int contador = 0; contador < inventario.length; contador++){
            System.out.println("------------------");
            System.out.println("Nombre: " + inventario[contador][0]);
            System.out.println("Cantidad: " + inventario[contador][1]);
        }
    }

 public void invent_guard(){
    
    guard[0] = "LAPIZ";
    guard[1] = "BORRADOR"; 
    guard[2] = "SACAPUNTAS";
    guard[3] = "ESTUCHE";
    guard[4] = "ENGRAPADORA";
    guard[5] = "CORRECTOR";
    guard[6] = "FOLDER TAMAÑO CARTA";
    guard[7] = "LAPICEROS MARCA BIG";
    guard[8] = "MARCADORES MAPED";
    guard[9] = "HOJAS 120G";
    guard[10] = "REGLA DE 20 CM";
}

 
 public static void main(String[] args) {
        new SUPER25().lOGIN();
}
}





