public class BisectionMethod {

    public static double function(double x) {
        return x * x - 4; // Función: f(x) = x^2 - 4
    }

    public static double bisection(double a, double b, double tolerance) {
        double fa = function(a);
        double fb = function(b);
        double c = 0;

        while ((b - a) > tolerance) {
            c = (a + b) / 2;
            double fc = function(c);

            if (fc == 0) {
                break;
            } else if (fa * fc < 0) {
                b = c;
                fb = fc;
            } else {
                a = c;
                fa = fc;
            }
        }
        return c;
    }

    public static void main(String[] args) {
        double a = 0;
        double b = 3;
        double tolerance = 0.0001;
        double root = bisection(a, b, tolerance);
        System.out.println("Root: " + root);
    }
}
