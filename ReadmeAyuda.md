# Has ingresado a la opción AYUDA
# Los autores de la aplicación son:
# Lester Miguel Angel López Duarte | 7690-23-25649 
# Eliezer López Garcia|7690-20-19696
>Presta atención a la siguiente información
 ```
Has presionado el botón de ayuda por eso es por lo que tienes acceso a esta información, aquí puedes ver la licencia de la aplicación y su versión. A continuación podrás leer las funciones que tiene dicha aplicación que estas usando o tienes pensado usar tiene varias funciones, la primera y la más destacable es que puedes buscar un archivo con su nombre y tipo de ruta escribiéndolo en el apartado que se te indica, luego de ahí presionas buscar y se te mostrara el archivo que buscas y si no está la misma aplicación te dirá que el archivo no está, le segunda función es que puedes editar la información y a la vez guardarla, es decir que puedes modificar la información dentro del archivo sin ningún problema, también esta la función donde puedes guardar el documento después de modificarlo pero en un lugar diferente, uno donde tu elijas que se almacene el archivo y la ruta que tu elijas, todo dependerá del gusto de la persona que está manejando el archivo y las necesidades que se le presente con el mismo. También está la función de deshacer, la misma al realizar control + z pero en este caso esta presentado en botón para que la persona que está usando la aplicación pueda deshacer lo que desee al momento de modificar algún archivo y junto a esta función esta la función de rehacer la misma al presionar control + y, porque sabemos que a veces deseamos regresar a algo que hemos realizado cambios, por lo mismo tienes esa facilidad al presionar el botón de rehacer.
  ```
---
---
>Algoritmo en Python | Ejercicio 1
 ```Python
# Función para guardar los datos en un archivo
def guardarDatos(productos):
    with open("productos.txt", "w") as archivo:
        for producto in productos:
            archivo.write(f"{producto['nombre']} {producto['codigo']} {producto['precio']} {producto['proveedor']} {producto['existencia']} {producto['estado']} {producto['descuento']}\n")

# Función para cargar los datos desde un archivo
def cargarDatos():
    try:
        with open("productos.txt", "r") as archivo:
            productos = []
            for linea in archivo:
                datos = linea.strip().split()
                producto = {
                    'nombre': datos[0],
                    'codigo': datos[1],
                    'precio': float(datos[2]),
                    'proveedor': datos[3],
                    'existencia': int(datos[4]),
                    'estado': datos[5],
                    'descuento': float(datos[6])
                }
                productos.append(producto)
            return productos
    except FileNotFoundError:
        print("El archivo de datos no existe o no se puede abrir.")
        return []

# Función para agregar un producto
def agregarProducto(productos):
    producto = {}
    producto['nombre'] = input("Nombre: ")
    producto['codigo'] = input("Código: ")

    # Verificar que el código no se repita
    for p in productos:
        if p['codigo'] == producto['codigo']:
            print("El código de producto ya existe. No se puede agregar.")
            return

    producto['precio'] = float(input("Precio: "))
    producto['proveedor'] = input("Proveedor: ")
    producto['existencia'] = int(input("Existencia: "))
    producto['estado'] = input("Estado (A = Aprobado, R = Reprobado): ")
    producto['descuento'] = float(input("Descuento: "))

    productos.append(producto)
    guardarDatos(productos)
    print("Producto agregado con éxito.")

# Función para buscar un producto por código o nombre
def buscarProducto(productos):
    criterio = input("Ingrese el criterio de búsqueda (código o nombre): ")
    for producto in productos:
        if producto['codigo'] == criterio or criterio in producto['nombre']:
            print("Nombre:", producto['nombre'])
            print("Código:", producto['codigo'])
            print("Precio:", producto['precio'])
            print("Proveedor:", producto['proveedor'])
            print("Existencia:", producto['existencia'])
            print("Estado:", producto['estado'])
            print("Descuento:", producto['descuento'])
            print("---------------------------")

# Función para modificar los datos de un producto
def modificarProducto(productos):
    codigo = input("Ingrese el código del producto que desea modificar: ")
    for producto in productos:
        if producto['codigo'] == codigo:
            producto['precio'] = float(input("Nuevo precio: "))
            producto['proveedor'] = input("Nuevo proveedor: ")
            producto['existencia'] = int(input("Nueva existencia: "))
            producto['estado'] = input("Nuevo estado (A = Aprobado, R = Reprobado): ")
            producto['descuento'] = float(input("Nuevo descuento: "))
            guardarDatos(productos)
            print("Producto modificado con éxito.")
            return

    print("No se encontró ningún producto con el código proporcionado.")

# Función principal
def main():
    productos = cargarDatos()

    while True:
        print("Menú:")
        print("1. Agregar producto")
        print("2. Buscar producto")
        print("3. Modificar datos de un producto")
        print("4. Salir")
        opcion = input("Seleccione una opción: ")

        if opcion == "1":
            agregarProducto(productos)
        elif opcion == "2":
            buscarProducto(productos)
        elif opcion == "3":
            modificarProducto(productos)
        elif opcion == "4":
            return
        else:
            print("Opción no válida.")

if __name__ == "__main__":
    main()
 ```
---
---
