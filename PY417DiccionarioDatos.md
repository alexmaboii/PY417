# DICCIONARIO DE DATOS PY417

### Tabla de Vehículo

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **matricula** | VARCHAR (7) | PK | Matrícula del vehículo. |
| **marca** | VARCHAR (64) | | Nombre de la marca del vehículo. |
| **modelo** | VARCHAR (64) | | Modelo del vehículo. |
| **tipo** | VARCHAR (64) | | Tipo de vehículo. |
| **año** | INT | | Año de matriculación del vehículo. |

### Tabla de Departamento

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **id** | INT | PK | Identificador del departamento. |
| **nombre** | VARCHAR (128) | | Nombre del departamento. |
| **telefono** | INT | | Número de teléfono del departamento. |
| **direccion** | VARCHAR (128) | | Dirección del departamento. |

### Tabla de Agente

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **numPlaca** | INT | PK | Número de la placa del agente. |
| **nombre** | VARCHAR (128) | | Nombre del agente. |
| **fnac** | DATE | | Fecha de nacimiento del agente. |
| **teléfono** | INT | | Número de teléfono del agente. |
| **rango** | VARCHAR (64) | | Rango / Puesto del agente. |
| **matriculaVehiculo** | VARCHAR (7) | FK | Matrícula del vehículo del agente, proviene de la tabla VEHICULO. |
| **idDepartamento** | INT | FK, VNN | ID del departamento al que el agente pertenece, proviene de DEPARTAMENTO. |

### Tabla de Caso

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **numCaso** | INT | PK | Número identificador del caso. |
| **descripcionCaso** | VARCHAR (1024) | | Descripción del caso. |
| **tipoCaso** | VARCHAR (64) | | Tipo de caso. |
| **fApertura** | DATE | | Fecha de apertura del caso. |
| **estadoCaso** | VARCHAR (32) | | Estado actual del caso. |

### Tabla de Investigar (Relación)

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **numPlaca** | INT | PK, FK | Número de placa del agente que está investigando el caso, proviene de la tabla de AGENTE. |
| **numCaso** | INT | PK, FK | Número del caso que está siendo investigado por ninguno o muchos agentes, proviene de la tabla CASO. |

### Tabla de Ciudadano

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **dni** | VARCHAR (9) | PK | DNI del ciudadano. |
| **nombre** | VARCHAR (128) | | Nombre del ciudadano. |
| **dirección** | VARCHAR (128) | | Dirección del ciudadano. |
| **teléfono** | INT | | Número de teléfono del ciudadano. |

### Tabla de Testigo

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **dni** | VARCHAR (9) | PK, FK | DNI del testigo, proviene de CIUDADANO. |
| **declaracion** | VARCHAR (512) | | Declaración del testigo. |
| **numCaso** | INT | FK | Número del caso al que el testigo pertenece. Proviene de CASO. |

### Tabla de Víctima

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **dni** | VARCHAR (9) | PK, FK | DNI de la víctima, proviene de CIUDADANO. |
| **testimonio** | VARCHAR (512) | | Testimonio de la víctima. |
| **numCaso** | INT | FK | Número del caso al que la víctima pertenece. Proviene de CASO. |

### Tabla de Sospechoso

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **dni** | VARCHAR (9) | PK, FK | DNI del sospechoso, proviene de CIUDADANO. |
| **antecedentes (O)**| VARCHAR (512) | | Antecedentes del sospechoso (si tiene). |
| **numCaso** | INT | FK | Número del caso al que el sospechoso pertenece. Proviene de CASO. |

### Tabla de Evidencia

| Columna | Tipo de dato | Restricción | Descripción |
| :--- | :--- | :--- | :--- |
| **id** | INT | PK | Número identificador de la evidencia. |
| **numCaso** | INT | PK, FK | Número de caso al que pertenece la evidencia. Proviene de la tabla CASO. |
| **descripción** | VARCHAR (512) | | Descripción de la evidencia. |
| **tipo** | VARCHAR (64) | | Tipo de evidencia. |