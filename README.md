# Proyecto-MBD-2025
Se encuentra el código sobre el análisis realizado para le comportamiento del usuario financiero.

# Proyecto MBD 2025

Este repositorio contiene el código del proyecto para el curso de **Modelación y Bases de Datos (MBD)** 2025. Aquí encontrarás cómo configurar el entorno, instalar dependencias y ejecutar los scripts para reproducir los resultados del análisis y las consultas realizadas.

## Estructura del repositorio

Proyecto-MBD-2025/
├── data/
│   └── raw/                 # Datos originales
│   └── processed/           # Datos transformados
├── notebooks/              # Notebooks de análisis
├── scripts/                # Scripts Python de procesamiento y carga
│   ├── preprocess.py
│   ├── load_db.py
│   └── queries.sql
└── README.md
```

## Requisitos

- Python 3.8 o superior
- Virtual environment (recomendado)
- Git

### Instalación de dependencias

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Steevencruz903/Proyecto-MBD-2025.git
   cd Proyecto-MBD-2025
   ```

2. Crea y activa un entorno virtual:
   ```bash
   python3 -m venv venv
   source venv/bin/activate        # macOS/Linux
   venv\Scripts\activate           # Windows
   ```

3. Instala las libraries:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
   **requirements.txt** debería incluir:
   ```
   pandas
   sqlalchemy
   psycopg2-binary         # o mysqlclient si usas MySQL
   notebook
   matplotlib               # si hay gráficos
   seaborn                  # si hay visualizaciones
   ```

---

## Ejecución paso a paso

1. **Preprocesamiento:** transforma los datos crudos.
   ```bash
   python scripts/preprocess.py \
       --input data/raw/tu_archivo.csv \
       --output data/processed/cleaned.csv
   ```

2. **Carga a base de datos:** crea tablas y carga datos.
   ```bash
   python scripts/load_db.py \
       --db-url postgresql://usuario:pass@localhost:5432/mi_bd \
       --csv data/processed/cleaned.csv
   ```

3. **Ejecución de consultas SQL:** corre consultas y genera resultados.
   ```bash
   psql postgresql://usuario:pass@localhost:5432/mi_bd \
       -f scripts/queries.sql
   ```

4. **Análisis y visualización:** abre el notebook:
   ```bash
   jupyter notebook notebooks/analisis_proyecto.ipynb
   ```
   Recorre las celdas para ver gráficos y métricas.

---

##  Configuración de la base de datos

Ejemplo usando PostgreSQL:

```sql
CREATE DATABASE mi_bd;
CREATE USER usuario WITH PASSWORD 'pass';
GRANT ALL PRIVILEGES ON DATABASE mi_bd TO usuario;
```

Para MySQL:
```sql
CREATE DATABASE mi_bd;
CREATE USER 'usuario'@'localhost' IDENTIFIED BY 'pass';
GRANT ALL PRIVILEGES ON mi_bd.* TO 'usuario'@'localhost';
```

Asegúrate de actualizar la variable `--db-url` en `load_db.py` y los notebooks si usas distinto sistema o credenciales.

---

## Resultados esperados

Al finalizar deberías:
- Tener la tabla(s) cargada(s) en la base de datos.
- Haber generado archivos gráficos y métricas en `notebooks/`.
- Encontrar salidas de terminal mostrando tiempos de carga y conteos de filas.

---

## Posibles mejoras

- Contenedor Docker para automatizar configuración.
- CI/CD con GitHub Actions.
- Pruebas unitarias para scripts.
- Manejo de errores más robusto y logs.

---

## Contacto

Autor: Steeven Cruz  
Email: steevencruz903@gmail.com 
Proyecto creado como parte del curso MBD 2025.


