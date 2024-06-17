planes = []
plan = []
id = -1
contador = 0
promedio = 0

def opmenu6 ():
    print ("Estadísticas:")
    global promedio
    print (".- Porcentaje de efectividad promedio: ", promedio)
    promedio = promedio / contador
    print (".- Valor del porcentaje de efectividad más alto: ")
    for x in planes:
        print (x[2])
        print (x[2>x])

def cargando ():
    print ("         cargando...         ")

def redirigiendo ():
    print (".-.-.- redirigiendo al menú -.-.-.")

def menu ():
    print ("1.- Agregar plan")
    print ("2.- Listar planes")
    print ("3.- Eliminar plan por ID")
    print ("4.- Generar bbdd")
    print ("5.- Cargar bbdd")
    print ("6.- Estadísticas")
    print ("0.- Salir.")
    
    
while True:
    menu ()
    opmenu = int (input())
    
    if opmenu == 1:
        print ("escriba el nombre de su plan:")
        plan_0 = (input())
        print ("escriba el porcentaje de efectividad de ", plan_0, "este porcentaje debe ser un número del 1 al 100")
        porcentaje = int (input())
        if porcentaje > 0 and porcentaje < 100: 
            if porcentaje > 0 and porcentaje <=25:
                categoria = "chiste"
            elif porcentaje >= 26 and porcentaje <= 50:
                categoria = "anécdota"
            elif porcentaje >= 51 and porcentaje <= 75:
                categoria = "peligro"
            elif porcentaje >= 76 and porcentaje <= 99:
                categoria = "atención"
            elif porcentaje == 100:
                categoria = "esclavitud mundial"     
            id=id+1
            plan = [id,plan_0,porcentaje,categoria]
            planes.append(plan)
            contador=contador+1
            promedio = promedio + porcentaje
            print ("plan guardado correctamente:")
            print ("id del plan:" , id, ", plan: ", plan, "probabilidades de gobernar el mundo: ", porcentaje, ", categoría:", categoria)
        else:
            print ("porcentaje fuera de parameteros")
        
    elif opmenu == 2:
        print ("Lista de planes:")
        print ("planes ingresados: ", contador)
        for x in planes:
            print ("-.- ,  id:" , x[0], ", plan:", x[1], ", probabilidades: ",x[2])
            
    elif opmenu == 3:
        encontrado = False
        print ("ha seleccionado la opción eliminar plan por ID")
        print ("ingrese el id del plan a eliminar:")
        id_e = int (input())
        for x in planes:
            if id_e == x[0]:
                encontrado = True
                print ("plan coincidente:")
                print ("id del plan:" , id, ", plan: ", plan, "probabilidades de gobernar el mundo: ", porcentaje)
                print ("¿desea confirmar su eliminación?")
                print ("1. sí")
                print ("2. no")
                sino = int (input())
                if sino == 1:
                    planes.remove(x)
                    print ("plan eliminado exitosamente")
                    contador = contador -1
                    redirigiendo ()
                elif sino == 2:
                    print ("de acuerdo, plan no eliminado")
                    redirigiendo ()
                else: 
                    print ("ha seleccionado una opción no válida")
                    redirigiendo ()

            if encontrado == False:
                print ("no hay coincidencia de id en la base de datos")            
                
    elif opmenu == 4:
        print ("generando archivo csv")
        cargando ()
        import csv
        with open ('archivo_csv.csv', 'w', newline = '') as archivo_csv:
            escribir_csv=csv.writer(archivo_csv)
            escribir_csv.writerow(['id','plan','porcentaje'])
            escribir_csv.writerow([planes])
            print ("archivo generado")
            redirigiendo ()
        
    elif opmenu == 5:
        print ("cargando archivos desde la base de datps csv ")
        cargando ()
        import csv
        with open ('archivo_csv.csv', 'r', newline = '') as archivo_csv:
            lector_csv=csv.reader(archivo_csv)
            for fila in lector_csv:
                print (fila)
        planes.pop(0)
        
    elif opmenu == 6:
        opmenu6 ()
        break
                
    elif opmenu == 0:
        print ("saliendo")
        cargando ()
        
# https://github.com/co-pino/prueba_constanzapino_3.git
