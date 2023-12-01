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
}
