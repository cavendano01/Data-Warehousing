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

### Categoría: 
Un nombre, una descripción y un logo
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| categoria_id | INT |  | UNIQUE NOT NULL |
| Nombre_categoria | VARCHAR | 50 | |
| Descripcion | VARCHAR | 255 | |
| logo |   |   |   |


### Detalles del pedido: 
Tabla puente
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
|  orden_id | INT |  | UNIQUE NOT NULL |   
| producto_id | INT |  | UNIQUE NOT NULL |
| precio_unitario | FLOAT | | |
| cantidad | INT | | |
| descuento | FLOAT | | |

### ordenes: 
fechas de cuándo se ordenó, cuándo se requiere y fecha de envío, método de envío, costo de flete, dirección, ciudad, nombre, región, código postal, país
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
|  orden_id | INT |  | UNIQUE NOT NULL |   
| cliente_id | INT |  | UNIQUE NOT NULL |
| empleado_id | INT |  | UNIQUE NOT NULL |
| fecha_orden | DATE | | |
| fecha_requerido | DATE | | |
| fecha_envio | DATE | | |
| remitente | VARCHAR | 50 | |
| freight_id | INT |  | UNIQUE NOT NULL  |   |   |   |
| remitente_nombre | VARCHAR | 50 | |
| remitente_dieccion | VARCHAR | 50 | |
| remitente_ciudad | VARCHAR | 50 | |
| remitente_region | VARCHAR | 50 | |
| remitente_codigo_postal| VARCHAR | 50 | |
| remitente_pais| VARCHAR | 50 | |

##Remitentes (Ship_via): 
Nombre de la empresa y teléfono
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| freight_id | INT |  | UNIQUE NOT NULL  |   |   |   |
| nombre_enpresa | VARCHAR | 50 | | 
| telefono | VARCHAR | 50 | |

### Clientes: 
es una persona de contacto específica dentro de una empresa específica, esa persona tiene un título y necesitamos la dirección, ciudad, región, código postal, país, teléfono y fax de la empresa.
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| cliente_id | INT |  | UNIQUE NOT NULL |   |   |   |
| nombre_empresa | VARCHAR | 50 | Not Null |
| nombre_contacto | VARCHAR | 50 | Not Null | 
| titulo_contacto | VARCHAR | 50 | Not Null | 
| direccion |  VARCHAR | 250 | Not Null | 
| ciudad | VARCHAR | 20 | Not Null | 
| region | VARCHAR | 20 | Not Null | 
| codigo_postal | INT | | |
| pais  | INT | | |
| telefono | VARCHAR | 50 | |
| fax | VARCHAR | 50 | |

### Datos demográficos de los clientes: 
Descripción
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
|  cliente_id | INT |  | UNIQUE NOT NULL |   |   |   |
| tipo_cliente_id | INT |  | UNIQUE NOT NULL |


### Cliente Demografía del cliente (puente)
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| tipo_cliente_id | INT |  | UNIQUE NOT NULL |
| tipo_cliente_desc | VARCHAR | 50 | Not Null |

### Empleados 
Apellido y nombre, título, título de cortesía, fecha de nacimiento, fecha de contratación, dirección, ciudad, región, postal, teléfono particular del país, extensión, foto, notas, informes_a, ruta_foto
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| empleado_id | INT |  | UNIQUE NOT NULL |
| apellido | VARCHAR | 50 | |
| nombre | VARCHAR | 50 | |
| titulo | VARCHAR | 50 | |
| titulo_cortesia | VARCHAR | 50 | |
| fecha_nacimiento  | DATE | | |
| fecha_contratado  | DATE | | |
| direccion |  VARCHAR | 250 | Not Null | 
| ciudad | VARCHAR | 20 | Not Null | 
| region | VARCHAR | 20 | Not Null | 
| codigo_postal | INT | | |
| pais  | INT | | |
| telefono_casa  | VARCHAR | 20 | Not Null |
|  extension  | VARCHAR | 20 | Not Null |
| foto |bytea | | |
| notas | VARCHAR | 50 | |
| reporta_a | VARCHAR | 50 | |
| ubicacion_foto | VARCHAR | 255 |

### Territorios de empleados (puente)
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| empleado_id | INT |  | UNIQUE NOT NULL |
| territorio_id | INT |  | UNIQUE NOT NULL |

### Territorios: 
Descripción del territorio
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| territorio_id | INT |  | UNIQUE NOT NULL |
| region_id | INT |  | UNIQUE NOT NULL |

### Región: 
Descripción
| Nombre del Campo | Tipo de Datos | longitud | restricciones |
|---|---|---|---|
| region_id | INT |  | UNIQUE NOT NULL |
| region_desc | VARCHAR | 250  | UNIQUE NOT NULL |

## Diagrama Entidad- Relación


## Data Definition Language 


## Data
Los datos de la base de datos serán importados de las bases de datos de muestra de [YugabyteDB](https://docs.yugabyte.com/preview/sample-data/northwind/)
Para mayor información, [wiki university]( https://en.wikiversity.org/wiki/Database_Examples/Northwind) tiene un repositorio detallado de la base de datos. 


