
# Bases de datos Pesca

Este proyecto está diseñado para gestionar los datos relacionados con una competencia de pesca. Involucra un conjunto de tablas de bases de datos interconectadas en Oracle APEX, que almacenan y gestionan información sobre los participantes (afiliados), licencias, eventos de pesca, especies de peces y las capturas realizadas por los participantes durante los eventos.
## Requisitos del Sistema
- Base de Datos: Oracle Database
- Entorno de desarrollo: Oracle Application Express (APEX).
## Estructura del proyecto
 1. Afiliados: Detalles de los participantes (información personal, etc.).
2. Licencias: Licencias asignadas a los participantes.
3. Permisos: Asociaciones entre afiliados y licencias.
4. Ríos y Ubicaciones: Información sobre los ríos (causes) y lugares de pesca (lugares).
5. Eventos: Competencias o eventos donde se realiza la pesca.
6. Peces: Especies de peces disponibles para captura.
7. Capturas: Registro de los peces capturados por los participantes en los eventos, incluyendo talla y peso.
8. Participación y Clasificaciones: Resultados y premios otorgados a los participantes según su desempeño
9. Fauna y Reglas del Concurso: Restricciones sobre el tamaño mínimo y la cantidad de peces por evento o ubicación.


## Estructura de la instalación
1. **Configuración de la base de datos**:
- Crear las tablas en una instancia de Oracle Utilizando los scripts SQL proporcionados.
Ejecute las secuencias de comandos SQL en el siguiente orden
- **Crear tablas**:
Afiliados, Licencias,Permisos, Cauces,Lugares, Eventos,peces,CapturasSolas,CapturasEventos,Faunas,Concursos.
- **Insertar datos**:
- Ejecute los escripts de inserción de datos en el orden de las dependencias (por ejemplo,afiliados antes de permisos, etc.).
2. **Ejemplo de Creación de Tablas**:
- **Crear la tabla de Afiliados**:
```bash
CREATE TABLE "AFILIADOS" (
    "FICHA" NUMBER PRIMARY KEY,
    "NOMBRE_AFILIADO" VARCHAR2(100),
    "APELLIDOS_AFILIADO" VARCHAR2(100),
    "DIRECCION_AFILIADO" VARCHAR2(200),
    "TELF_AFILIADO" VARCHAR2(15),
    "SEXO_AFILIADO" CHAR(1),
    "NACIMIENTO_AFILIADO" DATE,
    "OD_AFILIADO" VARCHAR2(50)
);
```
3. **Dependencias entre Tablas**:
- Muchas tablas tienen claves foráneas que dependen de otras. Por ejemplo:
- La tabla Permisos depende de Afiliados y Licencias.
- La tabla Eventos depende de Lugares.
- La tabla Capturas depende de Afiliados, Peces, y Eventos.






## Ejemplos de consultas

Comando de busqueda en las tablas.

```bash
 -- Obtener todos los afiliados
SELECT * FROM Afiliados;

-- Consultar eventos de un lugar específico
SELECT * FROM Eventos
WHERE lugar = 11;

-- Consultar peces capturados en un lugar determinado
SELECT peces.od_pez, capturassolas.peso, capturassolas.talla
FROM Peces
JOIN CapturasSolas ON Peces.pez = CapturasSolas.pez
WHERE lugar = 3;

```


## Estructura de Archivos
Los archivos  están organizados en el siguiente orden:
1. Creación de Tablas: Scripts para la creación de las tablas.
2. Inserción de Datos: Scripts para la inserción de datos.
3. Consultas de Ejemplo: Consultas básicas para interactuar con las tablas.
## Authors
- Sebastian Castillo Chaves.
- Andres Meneses. 
- Jessica Contreras.
- Yishac Riveros.

