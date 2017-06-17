# Carrera
package carrera;

import java.util.Scanner;

public class carrera {
    
    private int tramos;
    
    public void setTramos(){
        
        Scanner entrada = new Scanner (System.in);
        System.out.println("Ingrese el numero de tramos: ");
        this.tramos= entrada.nextInt();
    }
    public int getTramos(){
    return this.tramos;
    
    }
    
    public static int []variarVelocidad(int [] velocidades){
        Vehiculo auto1 = new Vehiculo((int)(Math.random()*4+1));
        Vehiculo auto2 = new Vehiculo((int)(Math.random()*4+1));
        Vehiculo auto3 = new Vehiculo((int)(Math.random()*4+1));
        Vehiculo auto4 = new Vehiculo((int)(Math.random()*4+1));
        
        velocidades [0]= auto1.getVelocidad();
        velocidades [1]= auto2.getVelocidad();
        velocidades [2]= auto3.getVelocidad();
        velocidades [3]= auto4.getVelocidad();
        return velocidades;
    }
    public int [][] generarcarrera (){
        int velocidades [][]= new int [4][tramos];
        int velocidad[]= new int [4];
        for (int j = 0; j < tramos; j++) {
            velocidad =variarVelocidad(velocidad);
            for (int i = 0; i < 4; j++) {
                velocidades [i][j]= velocidad [i];
            }
            
        }
    return velocidades;
    }
    public void imprimirmatriz(int [][]m){
        for (int i = 0; i < 4; i++) {
            for (int j = 0; j < 4; j++) {
                System.out.print(m[i][j]+"");
            }
            System.out.println();
        }
    }
   
    public int [] calcularTiempo(int[][] velocidades){
        
        int []tiempos = new int [4];
        int suma;
        
        for (int i =0; i<4; i++){
            suma=0;
            for(int j=0;j<getTramos();j++){
                suma= suma + velocidades[i][j];
            }
            tiempos [i]=suma;
        }
        return tiempos;
    }  
    public String imprimir (int [] tiempos){
        int tiempodelganador=tiempos[0];
        String nombreganador = " El conductor numero 1";
        
            for (int i = 0; i < 4; i++) {
                if (tiempos [i]>tiempodelganador){
                    tiempodelganador=tiempos[i];
                    switch(i){
                        case 1:
                            nombreganador= "El conductor numero 2";
                            break;
                        case 2:
                            nombreganador= "El conductor numero 3";
                            break;
                       default:
                            nombreganador= "El conductor numero 4";
                            break;
                    }
                }
            }   
            return nombreganador;
    }
}
---------------------------------------------------------------------------------------------------------------------
package carrera;

public class Vehiculo {
    
    private int velocidad;

    public Vehiculo(int velocidad) {
        this.velocidad =velocidad;
    }
    public int getVelocidad() {
        return velocidad;
    }

}
---------------------------------------------------------------------------------------------------------------

package carrera;

public class main extends carrera {
    
    
    public static void main(String[] args) {
        carrera carreras= new carrera();
        carreras.setTramos();
        
        int [][] datos = new int [4] [carreras.getTramos()];
        int [] tiempos = new int [4];
        
        datos = carreras.generarcarrera();
        carreras.imprimirmatriz(datos);
        tiempos = carreras.calcularTiempo(datos);
        System.out.println("El ganador es "+carreras.imprimir(tiempos));
        
    }
    
}
