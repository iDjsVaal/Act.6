
public class GestorInventario {
    private String nombreArticulo;
    private double precioUnitario;
    private int cantidadStock;

    public GestorInventario(String nombreArticulo, double precioUnitario, int cantidadStock) {
        this.nombreArticulo = nombreArticulo;
        this.precioUnitario = precioUnitario;
        this.cantidadStock = cantidadStock;
    }

    public String getNombreArticulo() { return nombreArticulo; }
    public void setNombreArticulo(String nombreArticulo) { this.nombreArticulo = nombreArticulo; }

    public double getPrecioUnitario() { return precioUnitario; }
    public void setPrecioUnitario(double precioUnitario) { this.precioUnitario = precioUnitario; }

    public int getCantidadStock() { return cantidadStock; }
    public void setCantidadStock(int cantidadStock) { this.cantidadStock = cantidadStock; }

    public double calcularSubtotal() {
        return this.cantidadStock * this.precioUnitario;
    }

    public double calcularTotalConDescuento(double porcentajeDescuento) {
        double subtotal = calcularSubtotal();
        return subtotal - (subtotal * (porcentajeDescuento / 100.0));
    }

    public void mostrarResumenInventario(double porcentajeDescuento) {
        double totalFinal = calcularTotalConDescuento(porcentajeDescuento);
        System.out.println("Articulo: " + this.nombreArticulo + " | Stock: " + this.cantidadStock);
        System.out.println("Total inventario valorizado: $" + totalFinal);
    }

    public static void main(String[] args) {
        GestorInventario articulo = new GestorInventario("Laptop Pro", 12500.0, 8);
        articulo.mostrarResumenInventario(10.0);
    }
}
