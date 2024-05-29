# Solucion de Guía para Crear y Responder Consultas sobre una Base de Datos de una Licorería Grande

## Paso 1: Creación de la Base de Datos y las Tablas
 
 ### -- Crear la Base de Datos
```sql
CREATE DATABASE LicoreriaGrande;
USE LicoreriaGrande;
```

### -- Crear las Tablas
```sql
CREATE TABLE Proveedores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    direccion VARCHAR(255),
    telefono VARCHAR(20)
);

CREATE TABLE Productos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    tipo VARCHAR(50),
    precio DECIMAL(10, 2) NOT NULL,
    stock INT NOT NULL,
    proveedor_id INT,
    FOREIGN KEY (proveedor_id) REFERENCES Proveedores(id)
);

CREATE TABLE Clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    direccion VARCHAR(255),
    telefono VARCHAR(20)
);

CREATE TABLE Empleados (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    puesto VARCHAR(100),
    salario DECIMAL(10, 2)
);

CREATE TABLE Ventas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT,
    empleado_id INT,
    fecha DATE NOT NULL,
    total DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES Clientes(id),
    FOREIGN KEY (empleado_id) REFERENCES Empleados(id)
);

CREATE TABLE Detalles_Venta (
    id INT AUTO_INCREMENT PRIMARY KEY,
    venta_id INT,
    producto_id INT,
    cantidad INT NOT NULL,
    precio_unitario DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (venta_id) REFERENCES Ventas(id),
    FOREIGN KEY (producto_id) REFERENCES Productos(id)
);
```
## Paso 2: Inserción de Datos de Ejemplo

### -- Insertar Datos en Proveedores
```sql
INSERT INTO Proveedores (nombre, direccion, telefono) VALUES
('Bodegas Torres', 'Calle del Vino 10', '123-4567'),
('Diageo', 'Avenida del Whisky 20', '234-5678'),
('Bacardi Limited', 'Boulevard del Ron 30', '345-6789'),
('Pernod Ricard', 'Calle del Licor 40', '456-7890'),
('Heineken', 'Avenida de la Cerveza 50', '567-8901'),
('Constellation Brands', 'Boulevard de los Spirits 60', '678-9012'),
('Brown-Forman', 'Calle del Bourbon 70', '789-0123'),
('Campari Group', 'Avenida del Vermut 80', '890-1234'),
('Asahi Group', 'Boulevard de la Cerveza 90', '901-2345'),
('Molson Coors', 'Calle del Hops 100', '012-3456'),
('Kirin Holdings', 'Avenida de la Malta 110', '123-4568'),
('Suntory Holdings', 'Boulevard del Sake 120', '234-5679'),
('Miller Brewing', 'Calle del Lager 130', '345-6780'),
('Anheuser-Busch', 'Avenida de la Lager 140', '456-7891'),
('Carlsberg', 'Boulevard de la Pilsner 150', '567-8902'),
('AB InBev', 'Calle de la Cerveza 160', '678-9013'),
('Diageo', 'Avenida del Gin 170', '789-0124'),
('Moët Hennessy', 'Boulevard del Champagne 180', '890-1235'),
('Remy Cointreau', 'Calle del Cognac 190', '901-2346'),
('Grupo Cuervo', 'Avenida del Tequila 200', '012-3457');
```
### -- Insertar Datos en Productos
```sql
INSERT INTO Productos (nombre, tipo, precio, stock, proveedor_id) VALUES 
('Whisky Johnnie Walker', 'Whisky', 120.00, 50, 2),
('Vodka Smirnoff', 'Vodka', 80.00, 70, 2),
('Ron Bacardi', 'Ron', 90.00, 30, 3),
('Cerveza Heineken', 'Cerveza', 30.00, 100, 5),
('Tequila José Cuervo', 'Tequila', 110.00, 40, 20),
('Champagne Moët', 'Champagne', 200.00, 20, 18),
('Ginebra Tanqueray', 'Gin', 85.00, 60, 17),
('Bourbon Jack Daniel\'s', 'Bourbon', 130.00, 45, 7),
('Vino Tinto Torres', 'Vino', 50.00, 75, 1),
('Vermut Campari', 'Vermut', 70.00, 55, 8),
('Sake Hakutsuru', 'Sake', 95.00, 25, 12),
('Cerveza Corona', 'Cerveza', 35.00, 95, 15),
('Brandy Fundador', 'Brandy', 105.00, 30, 4),
('Cognac Hennessy', 'Cognac', 180.00, 15, 18),
('Sidra Strongbow', 'Sidra', 40.00, 50, 10),
('Vodka Absolut', 'Vodka', 75.00, 80, 2),
('Ron Captain Morgan', 'Ron', 85.00, 35, 3),
('Whisky Chivas Regal', 'Whisky', 125.00, 25, 2),
('Cerveza Asahi', 'Cerveza', 33.00, 70, 9),
('Lager Miller', 'Cerveza', 28.00, 90, 13);
```
### -- Insertar Datos en Clientes
```sql
INSERT INTO Clientes (nombre, direccion, telefono) VALUES 
('Juan Pérez', 'Calle 123', '555-1234'),
('Maria Lopez', 'Avenida 456', '555-5678'),
('Pedro Gonzalez', 'Boulevard 789', '555-9876'),
('Lucia Fernandez', 'Calle 101', '555-3456'),
('Carlos Martinez', 'Avenida 202', '555-7890'),
('Laura Sanchez', 'Boulevard 303', '555-6789'),
('Ana Torres', 'Calle 404', '555-4321'),
('Jose Rodriguez', 'Avenida 505', '555-8765'),
('Marta Gomez', 'Boulevard 606', '555-7654'),
('Luis Ramirez', 'Calle 707', '555-6543'),
('Elena Diaz', 'Avenida 808', '555-5432'),
('Jorge Alvarez', 'Boulevard 909', '555-4321'),
('Patricia Ruiz', 'Calle 1001', '555-3210'),
('Rafael Navarro', 'Avenida 1102', '555-2109'),
('Isabel Morales', 'Boulevard 1203', '555-1098'),
('Ricardo Paredes', 'Calle 1304', '555-0987'),
('Veronica Salas', 'Avenida 1405', '555-9870'),
('Miguel Chavez', 'Boulevard 1506', '555-8760'),
('Sandra Herrera', 'Calle 1607', '555-7650'),
('Antonio Vega', 'Avenida 1708', '555-6540');
```
### -- Insertar Datos en Empleados
```sql
INSERT INTO Empleados (nombre, puesto, salario) VALUES 
('Carlos Ruiz', 'Cajero', 1500.00),
('Ana Torres', 'Gerente', 3000.00),
('Luis Fernandez', 'Vendedor', 1800.00),
('Sofia Ramos', 'Cajero', 1550.00),
('Miguel Sanchez', 'Vendedor', 1700.00),
('Laura Gutierrez', 'Gerente', 3100.00),
('Pedro Diaz', 'Cajero', 1600.00),
('Julia Perez', 'Vendedor', 1750.00),
('Ramon Lopez', 'Cajero', 1500.00),
('Adriana Jimenez', 'Vendedor', 1800.00),
('Hugo Martinez', 'Gerente', 3200.00),
('Eva Morales', 'Cajero', 1550.00),
('Julian Garcia', 'Vendedor', 1750.00),
('Carolina Suarez', 'Cajero', 1600.00),
('Nicolas Herrera', 'Vendedor', 1700.00),
('Gabriel Flores', 'Gerente', 3300.00),
('Natalia Torres', 'Cajero', 1550.00),
('Diego Alvarez', 'Vendedor', 1750.00),
('Beatriz Rivas', 'Cajero', 1600.00),
('Raul Castro', 'Vendedor', 1700.00);
```
### -- Insertar Datos en Ventas
```sql
INSERT INTO Ventas (cliente_id, empleado_id, fecha, total) VALUES 
(1, 1, '2023-05-01', 240.00),
(2, 2, '2023-05-02', 350.00),
(3, 3, '2023-05-03', 180.00),
(4, 4, '2023-05-04', 120.00),
(5, 5, '2023-05-05', 250.00),
(6, 6, '2023-05-06', 210.00),
(7, 7, '2023-05-07', 300.00),
(8, 8, '2023-05-08', 400.00),
(9, 9, '2023-05-09', 150.00),
(10, 10, '2023-05-10', 500.00),
(11, 11, '2023-05-11', 220.00),
(12, 12, '2023-05-12', 330.00),
(13, 13, '2023-05-13', 275.00),
(14, 14, '2023-05-14', 190.00),
(15, 15, '2023-05-15', 310.00),
(16, 16, '2023-05-16', 360.00),
(17, 17, '2023-05-17', 215.00),
(18, 18, '2023-05-18', 420.00),
(19, 19, '2023-05-19', 185.00),
(20, 20, '2023-05-20', 300.00);
```
### -- Insertar Datos en Detalles_Venta
```sql
INSERT INTO Detalles_Venta (venta_id, producto_id, cantidad, precio_unitario) VALUES 
(1, 1, 2, 120.00),
(2, 2, 3, 80.00),
(3, 3, 2, 90.00),
(4, 4, 4, 30.00),
(5, 5, 5, 110.00),
(6, 6, 6, 200.00),
(7, 7, 7, 85.00),
(8, 8, 8, 130.00),
(9, 9, 9, 50.00),
(10, 10, 10, 70.00),
(11, 11, 11, 95.00),
(12, 12, 12, 35.00),
(13, 13, 13, 105.00),
(14, 14, 14, 180.00),
(15, 15, 15, 40.00),
(16, 16, 16, 75.00),
(17, 17, 17, 85.00),
(18, 18, 18, 125.00),
(19, 19, 19, 33.00),
(20, 20, 20, 28.00);

```
## Paso 3: Consultas SQL

### Consultas SQL

#### 1. Obtener todos los productos disponibles

```sql
SELECT * FROM Productos;
```

#### 2. Obtener el nombre y el precio de los productos cuyo stock es menor a 50

```sql
SELECT nombre, precio FROM Productos WHERE stock < 50;
```

#### 3. Listar las ventas realizadas por un empleado específico

```sql
SELECT * FROM Ventas WHERE empleado_id = 1;
```

#### 4. Calcular el total de ventas realizadas en un mes específico

```sql
SELECT SUM(total) AS total_ventas FROM Ventas WHERE MONTH(fecha) = 5 AND YEAR(fecha) = 2023;
```

#### 5. Obtener el nombre del cliente y el total de cada venta

```sql
SELECT Clientes.nombre, Ventas.total FROM Ventas
JOIN Clientes ON Ventas.cliente_id = Clientes.id;
```

#### 6. Listar los productos vendidos en una venta específica

```sql
SELECT Productos.nombre FROM Detalles_Venta
JOIN Productos ON Detalles_Venta.producto_id = Productos.id
WHERE Detalles_Venta.venta_id = 1;
```

#### 7. Calcular el stock total de productos por tipo

```sql
SELECT tipo, SUM(stock) AS total_stock FROM Productos GROUP BY tipo;
```

#### 8. Obtener el nombre y el salario de los empleados que ganan más de 2000

```sql
SELECT nombre, salario FROM Empleados WHERE salario > 2000;
```

#### 9. Listar los proveedores y la cantidad total de productos que suministran

```sql
SELECT Proveedores.nombre, COUNT(Productos.id) AS total_productos FROM Proveedores
JOIN Productos ON Proveedores.id = Productos.proveedor_id
GROUP BY Proveedores.nombre;
```

#### 10. Obtener el historial de ventas de un cliente específico

```sql
SELECT * FROM Ventas WHERE cliente_id = 1;
```

#### 11. Listar los empleados y el total de ventas que han realizado

```sql
SELECT Empleados.nombre, SUM(Ventas.total) AS total_ventas FROM Ventas
JOIN Empleados ON Ventas.empleado_id = Empleados.id
GROUP BY Empleados.nombre;
```

#### 12. Obtener el precio promedio de los productos

```sql
SELECT AVG(precio) AS precio_promedio FROM Productos;
```

#### 13. Listar las ventas realizadas entre dos fechas específicas

```sql
SELECT * FROM Ventas WHERE fecha BETWEEN '2023-05-01' AND '2023-05-05';
```

#### 14. Obtener el nombre del cliente que ha realizado la compra más grande

```sql
SELECT Clientes.nombre FROM Ventas
JOIN Clientes ON Ventas.cliente_id = Clientes.id
ORDER BY Ventas.total DESC LIMIT 1;
```

#### 15. Calcular el total de productos vendidos por tipo en un mes específico

```sql
SELECT Productos.tipo, SUM(Detalles_Venta.cantidad) AS total_vendidos FROM Detalles_Venta
JOIN Productos ON Detalles_Venta.producto_id = Productos.id
JOIN Ventas ON Detalles_Venta.venta_id = Ventas.id
WHERE MONTH(Ventas.fecha) = 5 AND YEAR(Ventas.fecha) = 2023
GROUP BY Productos.tipo;
```

#### 16. Obtener la dirección y el teléfono de los proveedores que suministran un producto específico

```sql
SELECT Proveedores.direccion, Proveedores.telefono FROM Proveedores
JOIN Productos ON Proveedores.id = Productos.proveedor_id
WHERE Productos.nombre = 'Whisky Johnnie Walker';
```

#### 17. Listar los productos que no han sido vendidos

```sql
SELECT * FROM Productos WHERE id NOT IN (SELECT producto_id FROM Detalles_Venta);
```

#### 18. Calcular el total de ingresos por día

```sql
SELECT fecha, SUM(total) AS ingresos_diarios FROM Ventas GROUP BY fecha;
```

#### 19. Obtener el nombre y la dirección de los clientes que han comprado un producto específico

```sql
SELECT Clientes.nombre, Clientes.direccion FROM Clientes
JOIN Ventas ON Clientes.id = Ventas.cliente_id
JOIN Detalles_Venta ON Ventas.id = Detalles_Venta.venta_id
WHERE Detalles_Venta.producto_id = 1;
```

#### 20. Listar los productos cuyo nombre contiene la palabra 'Tequila'

```sql
SELECT * FROM Productos WHERE nombre LIKE '%Tequila%';
```

#### 21. Obtener el total de ventas y la cantidad de productos vendidos por cada proveedor

```sql
SELECT Proveedores.nombre, SUM(Ventas.total) AS total_ventas, SUM(Detalles_Venta.cantidad) AS total_productos_vendidos FROM Proveedores
JOIN Productos ON Proveedores.id = Productos.proveedor_id
JOIN Detalles_Venta ON Productos.id = Detalles_Venta.producto_id
JOIN Ventas ON Detalles_Venta.venta_id = Ventas.id
GROUP BY Proveedores.nombre;
```

#### 22. Calcular el promedio de ventas diarias en un mes específico

```sql
SELECT AVG(total) AS promedio_ventas_diarias FROM Ventas
WHERE MONTH(fecha) = 5 AND YEAR(fecha) = 2023
GROUP BY fecha;
```

#### 23. Obtener la cantidad de clientes que han realizado compras en un rango de fechas

```sql
SELECT COUNT(DISTINCT cliente_id) AS total_clientes FROM Ventas
WHERE fecha BETWEEN '2023-05-01' AND '2023-05-31';
```

#### 24. Listar los empleados que no han realizado ninguna venta

```sql
SELECT nombre FROM Empleados
WHERE id NOT IN (SELECT DISTINCT empleado_id FROM Ventas);
```

#### 25. Obtener el total de productos en stock por proveedor

```sql
SELECT Proveedores.nombre, SUM(Productos.stock) AS total_stock FROM Proveedores
JOIN Productos ON Proveedores.id = Productos.proveedor_id
GROUP BY Proveedores.nombre;
```










