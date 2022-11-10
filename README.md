# ExamenFinal_Didactica_carlos_ortiz_200917231
![image](https://user-images.githubusercontent.com/80730391/201008508-823a67c3-5063-4fde-bf4b-64dfb131bd65.png)
 --------PROBLEMA--------------
 NOS SOLICITAN UNA AGENDA TELEFONICA DIGITAL.
 -------- SOLUCION ------------
 #{} []
import os
class DATOS:
    print ("************************")
    print ("* Carlos Ortiz Serrano  *")
    print ("* Carnet 200917231      *")
    print ("* Lic. en Informatica   *")
    print ("*************************" )
    print ("*   EXAMEN FINAL        *\n")
#clase agenda
class AGENDA(DATOS):    
     #metodos
     #menu principal
        def menu_1():
            print("          - - - - -          " )
            print("***** AGENDA PERSONAL ********")

            print("** 1.- Ingreso de Datos    ***")
            print("** 2.- Busqueda de Datos   ***")
            print("** 3.- Modificar Datos     ***")
            print("** 4.- Mostrar Datos       ***")
            print("** 5.- Salir               ***")
            print("          - - - - -          " )
            print()
         
        def menu_2():
            print("a.- Buscar registro por Nombre")
            print("b.- Buscar Registro por Telefono")
            
         
        def menu_3():
            print("Editar Contactos")
            print("a.- Eliminar un contacto")
            print("b.- Editar un contacto")
            
    #atributos
        #lista
        agenda = []

        telefonos = {}
        nombres = {}
        direcciones = {}
        correo = {}
        opcion_menu = 0
        menu_1()
        
    #se utiliza un ciclo mientras para evaluar la opcion por el usuario
        while opcion_menu != 5:
            opcion_menu = int(input("ELIJA UNA OPCION :"))
                 
#opcion 1 - ingreso datos
     #se utilizo una condicionante if  para seleccionar una opcion del metodo principal Menu_1
            if opcion_menu == 1:
                print("Agregar:  Nombre, telefono, direccion y Correo")
                nombre = input("Nombre: ")
                telefono = input("Telefono: ")
                direccion = input("Direccion: ")
                correo = input("Correo:")
                telefonos[nombre] = telefono
                nombres[telefono] = nombre
                direcciones[direccion] = nombre
    #postetior solicitar los datos pricipales se procede a guardar en lista agenda declarada al inicio
                agenda.append([nombre, telefono, direccion, correo])
    #el programa retoma el menu principal 
                menu_1()
                
#opcion 2 - busqueda de datos
                #si el usuario ingresa 2 se utiliza metodo menu_2
            elif opcion_menu == 2:
                print("Busqueda de Datos\n ")    
                menu_2()
                opcion_menu_2 = input("Inserta una letra para elegir una opcion:\n ")
            #mandar a llamar el metodo 2 para desidir con una condisioante la opcion de busqueda por NOMBRE o TELEFONO
                if opcion_menu_2=="a":
                    nombre = input("Nombre:\n ")
                    if nombre in telefonos:
                        print("El telefono es ", telefonos[nombre])
                        menu_1()
                    else:
                        print(nombre, "no se encuentra\n ")
                        menu_1()
         
                if opcion_menu_2=="b":
                    telefono = input("Telefono: ")
                    if telefono in nombres:
                        print("\n El Nombre es ", nombres[telefono])
                        menu_1()
                    else:
                        print(telefono, "no se encuentra\n ")
                        menu_1()
                #al finalizar regresemaos al menu principal
                         
#opcion 3- Modificar Datos
            elif opcion_menu == 3:
    #par ello se manda a llamar al metodo menu_3
                menu_3()
                opcion_menu_3 = input("Inserta un numero para elegir una opcion: ")
    #si se ingresa opcion a==eliminar datos, basados en el nombre
                if opcion_menu_3=="a":
                    nombre = input("Nombre: ")
                    index = None
    #donde se recorre la lista en busca dela considencia de la variable nombre
    #al encontrarla la elimina colocando un valor vacio en  todas las posisiones iniciando por 0
                    for i in range(len(agenda)):
                        if agenda[i][0] == nombre:
                            index = i
                            break
                    if index != None:
                        del agenda[index]
                        print("Registro Borrado")
                        menu_1()
                    else:
                        print(nombre, "Registro No encontrado")
                        menu_1()
    #si es opcion b==modificar
                elif opcion_menu_3=="b":
                    nombre = input("Nombre a Buscar: ")             
                    index = None
    #donde se recorre la lista en busca dela considencia de la variable nombre
                    for i in range(len(agenda)):
                        if agenda[i][0] == nombre:
                            index = i
                            break
                    if index != None:
    #donde si encuentra en valor buscado solicita los nuevos datos
                        print("Ingrese los nuevos Datos: ")
                        nombre = input("Nuevo Nombre: ")
                        telefono = input("Nuevo Telefono: ")
                        direccion = input("Nueva Dirección: ")
                        correo = input("Nuevo Correo: ")
                        agenda[index] = [
    #donde ingresara cada valor nuevo basandose en su indice.
                                nombre if len(nombre) > 0 else agenda[index][0],
                                telefono if len(telefono) > 0 else agenda[index][1],
                                direccion if len(direccion) > 0 else agenda[index][2],
                                correo if len(correo) > 0 else agenda[index][3]
                        ]
                        print("!! Registros Modificados !!")
                        menu_1()
                    else:
                        print("No se encuentran registros")
                        menu_1()

#opcion 4 - mostrar datos    
            elif opcion_menu == 4:
                indice=0
                print ("AGENDA TELEFONICA:\n  Nombre -   Telefono -  Direccion -  Correo")
    #se genero un ciclo mientras encuentre valores en los index  y mostrando uno por uno en pantalla.
                while indice<len(agenda):
                    print (agenda[indice])
                    indice= indice+1
                print ("Numero de Registros:", indice)
                menu_1()                                            
            elif opcion_menu == 5:
                exit()
                                                
#mandar a llamar a la clase
objeto=AGENDA(DATOS)

 
