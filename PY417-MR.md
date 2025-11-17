### VEHICULO (<u>matricula</u>, marca, modelo, tipo, año)​
- `PK` (matricula)​

### DEPARTAMENTO (<u>id</u>, nombre, teléfono, dirección)​
- `PK` (id)​

### CIUDADANO (<u>dni</u>, nombre, dirección, teléfono)​
- `PK` (dni)​

### CASO (<u>numCaso</u>, descripción, tipo, fApertura, estado)​
- `PK` (numCaso)​

### TESTIGO (<u>dni*</u>, declaración, numCaso*)​
- `PK` (dni)​
- `FK` (dni) → CIUDADANO​
- `FK` (numCaso) → CASO​

### VICTIMA (<u>dni*</u>, testimonio, numCaso*)​
- `PK` (dni)​
- `FK` (dni) → CIUDADANO​
- `FK` (numCaso) → CASO​

### SOSPECHOSO (<u>dni*</u>, antecedentes, numCaso*)​
- `PK` (dni)​
- `FK` (dni) → CIUDADANO​
- `FK` (numCaso) → CASO​

### AGENTE (<u>numPlaca</u>, fnac, teléfono, nombre, rango, matricula* ,idDepartamento*)​
- `PK` (numPlaca)​
- `FK` (idDepartamento) → DEPARTAMENTO​
- `FK` (matricula) → VEHICULO​
- `VNN` (idDepartamento)​

### INVESTIGAR (<u>numPlaca*, numCaso*</u>)​
- `PK` (numPlaca, numCaso)​
- `FK` (numPlaca) → AGENTE​
- `FK` (numCaso) → CASO​

### EVIDENCIA (<u>id, numCaso*</u>, descripción, tipo)​
- `PK` (id, numCaso)​
- `FK` (numCaso) → CASO​