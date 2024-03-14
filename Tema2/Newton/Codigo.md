package newton;
import java.util.Scanner;
import java.lang.Math;
import java.text.DecimalFormat;


public class Newton {
    
    public static double f(double x){;
        return Math.exp(3*x)-2*Math.pow(x, 2);
    }
    
    public static double fp(double x){
        return 3*Math.exp(3*x)-4*x;
    }
    
    public static void main(String[] args) {
        DecimalFormat de = new DecimalFormat("#.0000");
        double xi=0,fxi=0,fprima=0,fdivf=0,oo=0,xi2=0,error;
        int aa=0;
      
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Ingresa el punto de partida: ");
        xi = sc.nextDouble();
        
        do{
            oo = xi;
            fdivf=(xi-(f(xi)/fp(xi)));
            error= Math.abs((fdivf-oo)/fdivf);
            xi=fdivf;
        }while(error != 0);
        
        System.out.println("El valor aproximado de la raiz es: "+de.format(fdivf));
       
    }
    }
