 public class GaussSeidel {
    // Función para imprimir la matriz
    public static void imprimirMatriz(double[][] matriz) {
        int n = matriz.length;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n + 1; j++) {
                System.out.print(matriz[i][j] + "\t");
            }
            System.out.println();
        }
    }

    public static double[] gaussSeidel(double[][] matriz, double tolerancia, int iterMax) {
        int n = matriz.length;
        double[] x = new double[n];
        double[] xAnterior = new double[n];
        int iter = 0;

 
        for (int i = 0; i < n; i++) {
            x[i] = 0;
        }

       
        while (iter < iterMax) {
            
            for (int i = 0; i < n; i++) {
                xAnterior[i] = x[i];
            }

            
            for (int i = 0; i < n; i++) {
                double sum = 0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        sum += matriz[i][j] * x[j];
                    }
                }
                x[i] = (matriz[i][n] - sum) / matriz[i][i];
            }

            
            double error = 0;
            for (int i = 0; i < n; i++) {
                error += Math.abs(x[i] - xAnterior[i]);
            }

            if (error < tolerancia) {
                System.out.println("Convergencia alcanzada en la iteración " + (iter + 1));
                return x;
            }

            iter++;
        }

        System.out.println("Iteraciones máximas alcanzadas sin convergencia.");
        return null;
    }

    public static void main(String[] args) {
        // Ejemplo de sistema de ecuaciones:
        // 3x + y - z = 5
        // x - 4y + z = -7
        // 2x + y - 3z = 3
        double[][] matriz = {
            {3, 1, -1, 5},
            {1, -4, 1, -7},
            {2, 1, -3, 3}
        };

        // Tolerancia y número máximo de iteraciones
        double tolerancia = 0.0001;
        int iterMax = 100;

        // Llamar al método de Gauss-Seidel
        double[] soluciones = gaussSeidel(matriz, tolerancia, iterMax);

        // Imprimir las soluciones
        if (soluciones != null) {
            System.out.println("Soluciones:");
            for (int i = 0; i < soluciones.length; i++) {
                System.out.println("x[" + i + "] = " + soluciones[i]);
            }
        }
    }

    }
