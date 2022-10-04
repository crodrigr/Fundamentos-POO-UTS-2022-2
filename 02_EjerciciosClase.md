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
