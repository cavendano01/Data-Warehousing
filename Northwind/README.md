# Formulación de la base de datos Northwind

## Resumen del proyecto:

El objetivo principal de este proyecto es crear un concepto de almacén de datos utilizando técnicas de modelado dimensional. Identificar las partes interesadas clave y los requisitos comerciales para los mismos. Con base en estos requisitos, desarrollar un esquema de diseño para el almacén de datos. Finalmente cargar los datos de prueba.

## Acerca de la base de datos

La base de datos Northwind es una base de datos de muestra creada originalmente por Microsoft y utilizada como base para sus tutoriales en una variedad de productos de bases de datos durante décadas. La base de datos de Northwind contiene datos de ventas de una empresa ficticia llamada "Northwind Traders", que importa y exporta alimentos especiales de todo el mundo. La base de datos Northwind es un excelente esquema tutorial para un ERP de pequeñas empresas, con clientes, pedidos, inventario, compras, proveedores, envíos, empleados y contabilidad de entrada única. Desde entonces, la base de datos Northwind ha sido trasladada a una variedad de bases de datos que no son de Microsoft, incluido PostgreSQL.
El conjunto de datos de Northwind incluye datos de muestra para lo siguiente.

- Proveedores: Proveedores y vendedores de Northwind
- Clientes: Clientes que compran productos de Northwind
- Empleados: detalles de los empleados de los comerciantes de Northwind.
- Productos: Información del producto
- Transportistas: los detalles de los transportistas que envían los productos desde los comerciantes a los clientes finales.
- Orders y Order_Details: Transacciones de órdenes de venta que tienen lugar entre los clientes y la empresa.

## Convención de Nombre

Todo en minuscula con "_" separando diferentes palabras. Usando abreviaturas
cliente_id
primer_nombre 

## Entidades y Tablas de Hechos

### Proveedores: 

un Proveedor es una persona de contacto específica dentro de una empresa específica, esa persona tiene un título y necesitamos la dirección, ciudad, región, código postal, país, teléfono, fax y página de inicio de la empresa.

| Nombre del Campo | Tipo de Datos | largo | restricciones |
|---| ---|---|---|
| proveedor_id | INT |  | UNIQUE NOT NULL
| nombre_contacto | VARCHAR | 50 | Not Null | 
| nombre_empresa | VARCHAR | 50 | Not Null | 
| titulo_contacto | VARCHAR | 50 | Not Null | 
| direccion |  VARCHAR | 250 | Not Null | 
| ciudad | VARCHAR | 20 | Not Null | 
| region | VARCHAR | 20 | Not Null | 
| codigo_postal | INT | | |

### Productos (FACT): 
Definidos por un nombre, un proveedor, pertenecen a una categoría, Dice cuantos productos vienen por paquete, un precio unitario, una cantidad de unidades en stock y unidades pedidas al proveedor, una definición específica para saber si debe reordenarse según el nivel y una bandera si se descontinua

| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---| ---|---|---|
| producto_id |  INT | |
| nombre | VARCHAR | 50 |
| producto_id | INT | |
| categoria_id | INT |
| items_pkg | INT  | |
| precio_unitario | FLOAT | |
| stock_units | INT | |
| order_unit | INT | |
| reorder_flag | BOOL | |


### Categoria 



## Diagrama Entidad- Relación

## Data Definition Language 



