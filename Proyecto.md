# proyecto-final
internal class Pantallas 
{
        public static string[] nom_alm = new string[50];
        public static string[] nom_produc = new string[50];
        public static string[] nom_alamcen = new string[50];
        public static float[] precio = new float[5000];
        public static float[] cantidad = new float[500];
        public static int contador_produc = 0;
        public static int contador_alm = 0;

static void Main(string[] args)
        {
            int opcion;
            do
            {
                opcion = inventario_tienda();
                switch (opcion)
                {
                    case 1:
                        gestionar_productos();
                        break;
                    case 2:
                        gestionar_almacenes();
                        break;
                    case 3:
                        Agregar_Extraer_Productos();
                        break;
                }
            } while (opcion != 4);
        }
public static int inventario_tienda()
    {
        Console.Clear();
        Console.WriteLine("=====================================================");
        Console.WriteLine("||                                                 ||");
        Console.WriteLine("||       Sistema de Inventario Mi Tiendita         ||");
        Console.WriteLine("||                                                 ||");
        Console.WriteLine("=====================================================");
        Console.WriteLine("|| 1. Gestionar Productos                          ||");
        Console.WriteLine("|| 2. Gestionar Almacenes                          ||");
        Console.WriteLine("|| 3. Agregar y Extraer Productos                  ||");
        Console.WriteLine("=====================================================");
        Console.WriteLine("Seleccione una opción y presione Enter");
        return getOpcion();
    }
 public static void gestionar_productos()
    {
        Console.Clear();
        Console.WriteLine("-----------------------------------------------------");
        Console.WriteLine("||       Gestionar Productos - Mi Tiendita         ||");
        Console.WriteLine("-----------------------------------------------------");
        Console.WriteLine("|| 1. Agregar Producto                             ||");
        Console.WriteLine("|| 2. Eliminar Producto                            ||");
        Console.WriteLine("|| 3. Modificar Producto                           ||");
        Console.WriteLine("|| 4. Mostrar Inventario                           ||");
        Console.WriteLine("|| 5. Volver al Menú Principal                     ||");
        Console.WriteLine("-----------------------------------------------------");
        int opcion = Operaciones.getEntero("Ingresa una opción:");

switch (opcion)
        {
 case 1:
                Console.Clear();
                Console.WriteLine("==== Pantalla para Agregar Producto ====");
                Console.WriteLine("----------------------------------------");
                string nombre_producto = Operaciones.getTextoPantalla("Ingrese el nombre del producto:");
                float precio_producto = Operaciones.getDecimal("Ingrese el precio del producto:");
                float cantidad_producto = Operaciones.getDecimal("Ingrese la cantidad del producto:");
                nom_produc[contador_produc] = nombre_producto;
                precio[contador_produc] = precio_producto;
                cantidad[contador_produc] = cantidad_producto;
                contador_produc++;
                Console.WriteLine("----------------------------------------");
                Console.WriteLine("Confirmación: Producto agregado exitosamente.");
                Console.WriteLine("1. Volver al Menú Principal");
                break;

case 2:
                Console.Clear();
                Console.WriteLine("==== Pantalla para Eliminar Producto ====");
                Console.WriteLine("-----------------------------------------");
                string nom_eliminar = Operaciones.getTextoPantalla("Ingrese el producto a eliminar:");
                int indice_eliminar = -1;
                for (int i = 0; i < contador_produc; i++)
                {
                    if (nom_produc[i] == nom_eliminar)
                    {
                        indice_eliminar = i;
                    }
                }
                if (indice_eliminar != -1)
                {
                    Console.WriteLine($"Producto encontrado:{nom_produc[indice_eliminar]} - Precio:{precio[indice_eliminar]} - Cantidad: {cantidad[indice_eliminar]}");
                    for (int i = indice_eliminar; i < contador_produc - 1; i++)
                    {
                        nom_produc[i] = nom_produc[i + 1];
                        precio[i] = precio[i + 1];
                        cantidad[i] = cantidad[i + 1];
                    }
                    contador_produc--;
                    Console.WriteLine("----------------------------------------");
                    Console.WriteLine("Confirmación: Producto eliminado exitosamente.");
                }
                else
                {
                    Console.WriteLine("----------------------------------------");
                    Console.WriteLine("Confirmación: Operación cancelada.");
                }
                Console.WriteLine("Presione Enter para continuar...");
                Console.ReadLine();
                Console.WriteLine("1. Volver al Menú Principal");
                break;

case 3:
   Console.Clear();
   Console.WriteLine("==== Pantalla para Modificar Producto ====");
    Console.WriteLine("------------------------------------------");
                string nombreMoodificar = Operaciones.getTextoPantalla("Ingrese el nombre del producto a modificar:");
                int indiceProducto = -1;
                for (int i = 0; i < contador_produc; i++)
                {
                    if (nom_produc[i] == nombreMoodificar)
                    {
                        indiceProducto = i;
                    }

                }
  if (indiceProducto != -1)
                {
                    Console.WriteLine($"Producto encontrado: {nom_produc[indiceProducto]}-Precio:{precio[indiceProducto]} - Cantidad: {cantidad[indiceProducto]}");
                    Console.WriteLine("Ingrese el nuevo precio: ");
                    float nuevoPrecio = float.Parse(Console.ReadLine());
                    Console.WriteLine("Ingrese la nueva cantidad:");
                    float nuevaCantidad = float.Parse(Console.ReadLine());

 precio[indiceProducto] = nuevoPrecio;
                    cantidad[indiceProducto] = nuevaCantidad;
                    Console.WriteLine("----------------------------------------");
                    Console.WriteLine("Confirmación:Producto agregado exitosamente.");
                    Console.WriteLine("1. Volver al Menú Principal");
                }
  else
                {
                    Console.WriteLine("----------------------------------------");
                    Console.WriteLine("Confirmación: Producto no encontrado.");
                }
                break;

  case 4:
                Console.Clear();
                Console.WriteLine("==== Pantalla para Mostrar Inventario ====");
                Console.WriteLine("------------------------------------------");
                Console.WriteLine("Inventario Actual:");
                for (int i = 0; i < contador_produc; i++)
                {

Console.WriteLine($"Producto {i + 1}: {nom_produc[i]} \t- Precio:$ {precio[i]} -\t  Cantidad: {cantidad[i]}");
               }
              Console.WriteLine("...");
               break;

case 5:
                break;
        }
        Console.ReadLine();
}

public static void gestionar_almacenes()
{
    Console.Clear();
    Console.WriteLine("-----------------------------------------------------");
    Console.WriteLine("||       Gestionar Almacenes - Mi Tiendita         ||");
    Console.WriteLine("-----------------------------------------------------");
    Console.WriteLine("|| 1. Agregar Almacén                              ||");
    Console.WriteLine("|| 2. Eliminar Almacén                             ||");
    Console.WriteLine("|| 3. Mostrar Almacenes                            ||");
    Console.WriteLine("|| 4. Volver al Menú Principal                     ||");
    Console.WriteLine("-----------------------------------------------------");
    int opcion = Operaciones.getEntero("Ingresa una opción:");

    switch (opcion)
    {
        case 1:
            Console.Clear();
            Console.WriteLine("==== Pantalla para Agregar Almacén ====");
            Console.WriteLine("----------------------------------------");
            string nombre_almacen = Operaciones.getTextoPantalla("Ingrese el nombre del nuevo almacén:");
            nom_alamcen[contador_alm] = nombre_almacen;
            contador_alm++;
            Console.WriteLine("----------------------------------------");
            Console.WriteLine("Confirmación: Almacén agregado exitosamente.");
            Console.WriteLine("1. Volver al Menú Principal");
            break;

        case 2:
            Console.Clear();
            Console.WriteLine("==== Pantalla para Eliminar Almacén ====");
            Console.WriteLine("-----------------------------------------");
            string eliminar_almacen = Operaciones.getTextoPantalla("Ingrese el nombre del almacén a eliminar:");
            int indice_eliminar = -1;
            for (int i = 0; i < contador_alm; i++)
            {
                if (nom_alamcen[i] == eliminar_almacen)
                {
                    indice_eliminar = i;
                }
            }
            if (indice_eliminar != -1)
            {
                Console.WriteLine($"Almacén encontrado:{nom_alamcen[indice_eliminar]}");
                for (int i = indice_eliminar; i < contador_alm - 1; i++)
                {
                    nom_alamcen[i] = nom_alamcen[i + 1];
                }
                contador_alm--;
                Console.WriteLine("----------------------------------------");
                Console.WriteLine("Confirmación: Almacén eliminado exitosamente.");
            }
            Console.WriteLine("Presione Enter para continuar...");
            Console.ReadLine();
            Console.WriteLine("1. Volver al Menú Principal");
            break;

        case 3:
            Console.Clear();
            Console.WriteLine("==== Pantalla para Mostrar Almacenes ====");
            Console.WriteLine("------------------------------------------");
            Console.WriteLine("Lista de Almacenes:");
            for (int i = 0; i < contador_alm; i++)
            {
                Console.WriteLine($"Almacén {i + 1}: {nom_alamcen[i]}");
            }
            Console.WriteLine("...");
            break;

        case 4:
            break;
    }
    Console.ReadLine();
}
public static int Agregar_Extraer_Productos()
{
    Console.Clear();
    Console.WriteLine("-----------------------------------------------------");
    Console.WriteLine("    Agregar y Extraer Productos - Mi Tiendita    ");
    Console.WriteLine("-----------------------------------------------------");
    Console.WriteLine(" || 1. Ingresar Producto en Almacén ||               ");
    Console.WriteLine(" || 2. Extraer Producto de Almacén  ||               ");
    Console.WriteLine(" || 3. Ver Stock Actual             ||               ");
    Console.WriteLine(" || 4. Volver al Menú Principal     ||               ");
    Console.WriteLine("-----------------------------------------------------");
    int opcion = Operaciones.getEntero("Ingrese una opción: ");
    switch (opcion)
    {
        case 1:
            Console.Clear();
            Console.WriteLine("==== Pantalla para Ingresar Producto en Almacén ====");
            Console.WriteLine("-----------------------------------------------------");
            Console.WriteLine("Lista de Almacenes:");
            for (int i = 0; i < contador_alm; i++)
            {
                Console.WriteLine($"{i + 1}. {nom_alamcen[i]}");
            }

            Console.WriteLine("-----------------------------------------------------");
            int numeroAlmacen = Operaciones.getEntero("Seleccione el almacén:");
            int indiceAlmacen = numeroAlmacen - 1;
            Console.WriteLine("Lista de Productos:");
            for (int i = 0; i < contador_produc; i++)
            {
                Console.WriteLine($"{i + 1}. {nom_produc[i]}");
            }
            Console.WriteLine("-----------------------------------------------------");
            int numeroProducto = Operaciones.getEntero("Seleccione el producto a ingresar:");
            int indiceProducto = numeroProducto - 1;
            float cantidadIngresar = Operaciones.getDecimal("Ingrese la cantidad a ingresar:");
            cantidad[indiceProducto] -= cantidadIngresar;
            Console.WriteLine("-----------------------------------------------------");
            Console.WriteLine("Confirmación: Producto ingresado en el almacén exitosamente.");
            Console.WriteLine("1. Volver al Menú Principal");
            Console.ReadLine();
            break;


        case 2:
            Console.Clear();
            Console.WriteLine("==== Pantalla para Extraer Producto de Almacén ====");
            Console.WriteLine("----------------------------------------------------");
            Console.WriteLine("Lista de Almacenes:");
            for (int i = 0; i < contador_alm; i++)
            {
                Console.WriteLine($"{i + 1}. {nom_alamcen[i]}");
            }
            Console.WriteLine("-----------------------------------------------------");
            int numeroAlmacen_extraer = Operaciones.getEntero("Seleccione el almacén:");
            int indiceAlmacen_extraer = numeroAlmacen_extraer - 1;
            Console.WriteLine("-----------------------------------------------------");
            Console.WriteLine($"Productos en {nom_alm[indiceAlmacen_extraer]}:");
