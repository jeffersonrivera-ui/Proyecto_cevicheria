# Cevichería — versión con DAO

Este proyecto mantiene los paquetes y las opciones de menú originales:

- `modelo`
- `controlador`
- `conexion`
- `vista`

Se añadieron `dao` y `dao.impl`. Los controladores solicitan sus conexiones a
través de la interfaz `ConexionDAO`; `ConexionDAOImpl` usa el punto único
`ConexionBD.getConnection()`. Las validaciones, CRUD y transacciones originales
de compras, pagos, ventas, pedidos, detalles, recetas, exclusiones e inventario
se conservaron en los controladores para no alterar su comportamiento.

## Preparación de la base de datos

1. Inicia MySQL o MariaDB.
2. Importa el archivo `cevicheria.sql` incluido en la raíz del proyecto.
3. Revisa `src/conexion/ConexionBD.java` y ajusta `URL`, `USUARIO` y `CLAVE`
   si tu instalación no usa `localhost:3306`, la base `cevicheria`, el usuario
   `root` y contraseña vacía.

## Ejecutar en IntelliJ IDEA

1. Abre la carpeta del proyecto.
2. Configura un JDK (Java 8 o posterior).
3. Añade MySQL Connector/J al classpath. El proyecto original ya contiene una
   referencia de IntelliJ; si no funciona en tu equipo, usa Maven o agrega el
   archivo JAR de Connector/J manualmente.
4. Ejecuta `src/Main.java`.

## Ejecutar con Maven

Con un JDK y Maven instalados:

```bash
mvn compile
mvn exec:java
```

El `pom.xml` descarga `mysql-connector-j` automáticamente. La ejecución requiere
que la base de datos ya esté importada y accesible.

## Nota sobre verificación

Se hizo una revisión estática del código y de la compatibilidad con el esquema
incluido. Esta copia no pudo compilarse ni conectarse a MySQL en el entorno de
entrega porque no había un compilador Java/JDK disponible, por lo que todavía
debes ejecutar las pruebas funcionales en tu equipo con MySQL levantado.
