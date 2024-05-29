#Solucion de Guía para Crear y Responder Consultas sobre una Base de Datos de una Licorería Grande

##Paso 1: Creación de la Base de Datos y las Tablas
 
 ###-- Crear la Base de Datos
CREATE DATABASE LicoreriaGrande;
USE LicoreriaGrande;

###-- Crear las Tablas
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

##Paso 2: Inserción de Datos de Ejemplo

###-- Insertar Datos en Proveedores
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

###-- Insertar Datos en Productos
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

###-- Insertar Datos en Clientes
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

###-- Insertar Datos en Empleados
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

###-- Insertar Datos en Ventas
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

###-- Insertar Datos en Detalles_Venta
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


Paso 3: Consultas SQL
# Consultas SQL












