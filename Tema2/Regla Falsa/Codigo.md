

import java.util.function.Function;

public class Ejercicio {
        public static double funcion(double x) {
        return Math.pow(x, 6) - 2;
    }

    public static double reglaFalsa(double a, double b, Function<Double, Double> f, double errorTolerado) {
        double c = 0;
        double fa = f.apply(a);
        double fb = f.apply(b);
        double fc = 0; 
        double error = 0; 
  
        if (fa * fb > 0) { 
            System.out.println("No hay cambio de signo en el intervalo dado.");
            return Double.NaN;
        } 

        
        do {
            c = (a * fb - b * fa) / (fb - fa);
            fc = f.apply(c);

            if (fa * fc < 0) {
                b = c;
                fb = fc;
            } else {
                a = c;
                fa = fc;
            }
            error = Math.abs(fc);
        } while (error >= errorTolerado);

        return c; 
    }

    public static void main(String[] args) {
        double a = 1; //izquierdo
        double b = 3; // derecho
        double errorTolerado = 0.0001; 

        
        double raiz = reglaFalsa(a, b, Ejercicio2::funcion, errorTolerado);
        if (!Double.isNaN(raiz)) {
            System.out.println("Aproximación de la raíz: " + raiz); 
        }
    }
    }

