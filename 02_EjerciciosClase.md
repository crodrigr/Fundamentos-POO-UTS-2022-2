# Ejericios de clase del corte 2.

## 1. Vendedor con POO

![image](https://user-images.githubusercontent.com/31961588/191957065-1af8c33c-8ae5-4b1f-ac2b-1da594b40c3b.png)


**AppVendedor.java**


```Java

package appvendedor;

public class AppVendedor {
   
    public static void main(String[] args) {
      Vendedor v1=new Vendedor("100001",1,200000.0);
      v1.calcularComision();
      
      Vendedor v2=new Vendedor();
      
      v2.setNumeroIdentificacion("3993999");
      v2.setTipoDeVendedor(20);
      v2.setVentasMes(40000.0);
      
      
      
      System.out.println("Vendedor 1 Identificacion:"+ v1.getNumeroIdentificacion() +" "+
                         "Tipo de Vendedor: "+v1.getTipoDeVendedor()+"  "+
                         "Ventas del mes: "+v1.getVentasMes()+" "+
                         "Comisión: "+ v1.getComision() );
      
       System.out.println("Vendedor 2 Identificacion:"+ v2.getNumeroIdentificacion() +" "+
                         "Tipo de Vendedor: "+v2.getTipoDeVendedor()+"  "+
                         "Ventas del mes: "+v2.getVentasMes()+" "+
                         "Comisión: "+ v2.getComision() );
      
    }
    
}


```


**Vendedor.java**


```Java

package appvendedor;

public class Vendedor {
    
    //Atributos
    private String numeroIdentificacion;
    private int    tipoDeVendedor;
    private double ventasMes;
    private double comision;
    
    //Métodos    
    public Vendedor(){
    }
    
    public Vendedor(String _numeroIdentificacion,int _tipoDeVendedor, double _ventasMes){
        this.numeroIdentificacion=_numeroIdentificacion;
        this.tipoDeVendedor=_tipoDeVendedor;
        this.ventasMes=_ventasMes;     
    }

    public String getNumeroIdentificacion() {
        return numeroIdentificacion;
    }

    public void setNumeroIdentificacion(String numeroIdentificacion) {
        this.numeroIdentificacion = numeroIdentificacion;
    }

    public int getTipoDeVendedor() {
        return tipoDeVendedor;
    }

    public void setTipoDeVendedor(int tipoDeVendedor) {
        if(this.tipoDeVendedor==1 || this.tipoDeVendedor==2){
          this.tipoDeVendedor = tipoDeVendedor;
        }else{
          this.tipoDeVendedor=-1;
        }
    }

    public double getVentasMes() {
        return ventasMes;
    }

    public void setVentasMes(double ventasMes) {
        this.ventasMes = ventasMes;
    }

    public double getComision() {
        return comision;
    }

    public void setComision(double comision) {
        this.comision = comision;
    }
          
    public void calcularComision(){
      if(this.tipoDeVendedor!=-1){  
        if(this.tipoDeVendedor==2){
        this.comision=this.ventasMes*0.25;
        }else{
            this.comision=this.ventasMes*0.20;
        }
      }  
        
    
    }
        
    
}


```

## 2. Tipo número en POO

![image](https://user-images.githubusercontent.com/31961588/191957641-c516b692-b516-4175-9205-28f39659298a.png)

**clase1.java**

```Java


```

**clase2.java**

```Java


```


## 3. Vendedores con menu

**AppVendedor.java**

```Java

package appvendedor;

import java.util.Scanner;

public class AppVendedor {    
    //Variables Globales
    static Scanner leer=new Scanner(System.in);
    static int posListVendedor=0;   
    public static void main(String[] args) {
      Vendedor[] listVendedores=new Vendedor[10];      
      int op=0;      
      do{
      op=menu();      
      switch(op){
          case 1:
            crearVendedor(listVendedores);  
          break;
           case 2:
            calcularComsion(listVendedores); 
          break;  
           case 3:
             listarVendedor(listVendedores);  
          break;  
          case 4:
             System.out.println("Ingrese la indentificación a buscar: ");
             String idBuscar=leer.next();
             int posEncontrador=buscarIndentificador(listVendedores,idBuscar);  
             if(posEncontrador!=-1){
                  System.out.println("Identificación: "+listVendedores[posEncontrador].getNumeroIdentificacion()+
                            " Tipo de Vendedor: "+listVendedores[posEncontrador].getTipoDeVendedor()+
                            " Ventas: "+listVendedores[posEncontrador].getVentasMes()+
                            " Comisión: "+listVendedores[posEncontrador].getComision());
             }else{
                System.out.println("No existe");
             }
          break;  
      }
      }while(op>=1 && op<=4);      
    }
    
    public static int menu(){
         System.out.println("___MENU___________________");
         System.out.println("___1.Crear Vendedor_______");
         System.out.println("___2.Calcular comisión____");
         System.out.println("___3.Listar Vendedores____");
         System.out.println("___4.Buscar_______________");
         System.out.println("___5.Salir________________");
         int op=leer.nextInt();
         return op;   
    }
    
    public static void crearVendedor(Vendedor[] list){
        System.out.println("CREAR VENDEDOR");
        System.out.println("Ingrese la identificación: ");
        String identificacion=leer.next();
        System.out.println("Ingrese tipo de vendedor: ");
        int tipoVendedor=leer.nextInt();
        System.out.println("Ingrese ventas del mes: ");
        double ventas=leer.nextDouble();        
        Vendedor vendedor=new Vendedor(identificacion,tipoVendedor,ventas);
        list[posListVendedor]=vendedor;
        posListVendedor++;    
    
    }
    
    public static void listarVendedor(Vendedor[] list){
       System.out.println("LISTADO DE VENDEDORES ");
       for(int i=0;i<posListVendedor;i++){
         System.out.println("Identificación: "+list[i].getNumeroIdentificacion()+
                            " Tipo de Vendedor: "+list[i].getTipoDeVendedor()+
                            " Ventas: "+list[i].getVentasMes()+
                            " Comisión: "+list[i].getComision());
       }
    
    
    }

    public static void calcularComsion(Vendedor[] vendedores){
        System.out.println("Calculando comisión de vendedores!!!");
        double totalComsiones=0;
        for(int i=0;i<posListVendedor;i++){
             vendedores[i].calcularComision();
             totalComsiones+=vendedores[i].getComision();
        }
        System.out.println("Total comisiones de todos los vendedores: "+totalComsiones);
        
         
    }
    
    public static int buscarIndentificador(Vendedor[] vendedores,String id){
       for(int i=0;i<posListVendedor;i++){
             if(vendedores[i].getNumeroIdentificacion().equals(id)){
                   return i;
             }             
        }
       return -1;
    
    }
}


```

**Vendedor.java**

```Java

package appvendedor;

public class Vendedor {
    
    //Atributos
    private String numeroIdentificacion;
    private int    tipoDeVendedor;
    private double ventasMes;
    private double comision;
    
    //Métodos    
    public Vendedor(){
    }
    
    public Vendedor(String _numeroIdentificacion,int _tipoDeVendedor, double _ventasMes){
        this.numeroIdentificacion=_numeroIdentificacion;
        this.tipoDeVendedor=_tipoDeVendedor;
        this.ventasMes=_ventasMes;     
    }

    public String getNumeroIdentificacion() {
        return numeroIdentificacion;
    }

    public void setNumeroIdentificacion(String numeroIdentificacion) {
        this.numeroIdentificacion = numeroIdentificacion;
    }

    public int getTipoDeVendedor() {
        return tipoDeVendedor;
    }

    public void setTipoDeVendedor(int tipoDeVendedor) {
        if(this.tipoDeVendedor==1 || this.tipoDeVendedor==2){
          this.tipoDeVendedor = tipoDeVendedor;
        }else{
          this.tipoDeVendedor=-1;
        }
    }

    public double getVentasMes() {
        return ventasMes;
    }

    public void setVentasMes(double ventasMes) {
        this.ventasMes = ventasMes;
    }

    public double getComision() {
        return comision;
    }

    public void setComision(double comision) {
        this.comision = comision;
    }
          
    public void calcularComision(){
      if(this.tipoDeVendedor!=-1){  
        if(this.tipoDeVendedor==2){
        this.comision=this.ventasMes*0.25;
        }else{
            this.comision=this.ventasMes*0.20;
        }
      }  
        
    
    }
        
    
}


```
# Aplicación de Publicaciones usando herencia


**AppLibrary.java**

```Java

package applibrary;

import java.util.ArrayList;
import java.util.Scanner;


public class AppLibrary {

    static Scanner leer=new Scanner(System.in);
    
    public static void main(String[] args) {
        ArrayList<Publicacion> listPublicaciones=new ArrayList<Publicacion>();        
        Ventas ventas=new Ventas();
        int opcion=0;
        do{
          opcion=menu();
          
          switch(opcion){
              case 1:
                 crearPublicacion(listPublicaciones);
              break;
              case 2:
                venderProducto(listPublicaciones,ventas);
              break;
              case 3:
                  System.out.println("3.Total de las ventas");
              break;
              case 4:
                 ventas.mostrar();
              break;
              case 5:
                  mostrarTodasPublicaciones(listPublicaciones);
              break;
          
          }         
        
        }while(opcion>=1 && opcion<=5);
              
    }
    
    public static int menu(){
        System.out.println("______MENU____");
        System.out.println("1.Crear publicación: libro o disco");
        System.out.println("2.Vender producto");
        System.out.println("3.Total de las ventas");
        System.out.println("4.Listar todas las ventas");
        System.out.println("5.Mostrar todas las publicaciones");
        System.out.println("6.Salir");
        int op=leer.nextInt();
        return op;
    }
    
    public static void crearPublicacion(ArrayList<Publicacion> list){
        Publicacion p=null;
        System.out.println("1.Disco o 2.Libro");
        int tipo=leer.nextInt();
        String titulo;
        float  precio;        
        System.out.println("Ingrese el titulo: ");
        titulo=leer.next();
        System.out.println("Ingrese el precio:");
        precio=leer.nextFloat();
        if(tipo==1){
         float duracion;
         System.out.println("Ingrese la duración: ");
         duracion=leer.nextFloat();
         p=new Disco(duracion,titulo,precio);         
        }else if(tipo==2){
          int añoPublicacion;
          int numPaginas;
          System.out.println("Ingresar año de publicación: ");
          añoPublicacion=leer.nextInt();
          System.out.println("Ingrese el número de paginas: ");
          numPaginas=leer.nextInt();
          p=new Libro(numPaginas,añoPublicacion,titulo,precio);
        }else{
          p=new Publicacion(titulo,precio);
        }
        
        list.add(p);
        
        
    }

    public static void mostrarTodasPublicaciones(ArrayList<Publicacion> list){
        int pos=0;
        for(Publicacion p  : list){
          System.out.println("Id:"+pos);
          p.mostrar();
        }
        
    }

    public static void venderProducto(ArrayList<Publicacion> list, Ventas ventas){
        
         System.out.println("Seleccione el id del producto a vender: ");
         mostrarTodasPublicaciones(list);
         int id=leer.nextInt();
         Publicacion p=list.get(id);
         ventas.addPublicacion(p);
         
    }
    
}

```

**Publicacion.java**
```Java
package applibrary;


public class Publicacion {
    
    private String titulo;
    private float  precio;

    public Publicacion() {
    }

    public Publicacion(String titulo, float precio) {
        this.titulo = titulo;
        this.precio = precio;
    }

    public String getTitulo() {
        return titulo;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public float getPrecio() {
        return precio;
    }

    public void setPrecio(float precio) {
        this.precio = precio;
    }
    
    public void mostrar(){
       System.out.println("DATO DE PUBLICACIÓN");
       System.out.println("Titulo: "+this.titulo);
       System.out.println("Precio: "+this.precio);
    }
    
}

```

**Libro.java**

```Java
package applibrary;



public class Libro extends Publicacion {
    
    private int numPaginas;
    private int añoPublicacion;

    public Libro(int numPaginas, int añoPublicacion, String titulo, float precio) {
        super(titulo, precio);
        this.numPaginas = numPaginas;
        this.añoPublicacion = añoPublicacion;
    }

    public int getNumPaginas() {
        return numPaginas;
    }

    public void setNumPaginas(int numPaginas) {
        this.numPaginas = numPaginas;
    }

    public int getAñoPublicacion() {
        return añoPublicacion;
    }

    public void setAñoPublicacion(int añoPublicacion) {
        this.añoPublicacion = añoPublicacion;
    }
    
    @Override
    public void mostrar(){
      System.out.println("DATOS LIBRO");
      System.out.println("Titulo: "+super.getTitulo());
      System.out.println("Precio: "+super.getPrecio());
      System.out.println("Número paginas: "+this.numPaginas);
      System.out.println("Año de publicación: "+this.añoPublicacion);      
    }
    
    
    
}

```

**Disco.java**
```Java
package applibrary;

public class Disco extends Publicacion {
    
    private float duracion;

    public Disco(float duracion, String titulo, float precio) {
        super(titulo, precio);
        this.duracion = duracion;
    }

    public float getDuracion() {
        return duracion;
    }

    public void setDuracion(float duracion) {
        this.duracion = duracion;
    }
    
    
    @Override
    public void mostrar(){
       System.out.println("DATOS DE DISCO");
       System.out.println("Titulo: "+super.getTitulo());
       System.out.println("Precio: "+super.getPrecio());
       System.out.println("Duración: "+this.duracion);
               
    }
    
    
    
}

```

**Ventas.java**
```Java

package applibrary;

import java.util.ArrayList;


public class Ventas {
    
    public ArrayList<Publicacion> listVentas;
    
    public Ventas(){
       listVentas=new ArrayList<Publicacion>();
    }
    
    public void addPublicacion(Publicacion publicacion){
        listVentas.add(publicacion);
    }
    
    public void mostrar(){
        for(Publicacion p : this.listVentas  ){
            p.mostrar();
        }
    }
    
}

```
