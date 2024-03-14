package metodo.de.la.secante;
import java.text.DecimalFormat;
import java.util.Scanner;

public class MetodoDeLaSecante {


    public static double f(double x){
        
        return (Math.pow(x,4))+3*(Math.pow(x,3))-2;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        DecimalFormat df = new DecimalFormat("#.0000");
        
        System.out.println("Ingresa un primer valor propuesto:");
        double aa = sc.nextDouble();
        System.out.println("Ingresa un segundo valor propuesto:");
        double bb = sc.nextDouble();
        System.out.println("Ingresa la tolerancia del error:");
        double tol = sc.nextDouble();
        
        tol=tol*100;
        double error=0,xi,xiant;
        int ite=0;
        xi=aa;
        xiant=bb;
        do{
            double fxmu=f(xiant);
            double fxi=f(xi);
            double fxiN=xi-(fxi*(xiant-xi))/(fxmu-fxi);
            
            xiant=xi;
            xi=fxiN;
            if(ite==0){
                error=tol+1;
            }else{
                error=Math.abs((xi-xiant)/xi)*100;
            }
            System.out.println(ite);
            ite+=1;
        }while(error>=tol);
        
        System.out.println("El valor de la raiz aproximado es: " + df.format(xi));
    }
    }
