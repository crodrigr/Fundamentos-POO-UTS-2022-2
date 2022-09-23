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

