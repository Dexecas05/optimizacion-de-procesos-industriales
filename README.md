# Optimización de Procesos Industriales - Análisis 2024

Proyecto de limpieza, anonimización y análisis de datos de producción para identificar oportunidades de mejora en líneas industriales.

## 📌 Objetivo
Transformar datos crudos de eventos de producción en información accionable para:
- Identificar patrones de pérdida de eficiencia
- Reducir tiempos de parada no planificados
- Optimizar la eficiencia global
- Automatizar la detección de patrones críticos

## 🔍 Datos
- **Fuente**: Sistema MES (Manufacturing Execution System)
- **Cobertura**: Datos anonimizados de toda la línea de producción (2024)
- **Muestra**:
  - 222,403 eventos registrados
  - 78% de reducción tras consolidación
  - Variables clave:
    - Tiempos de inicio/fin
    - Tipos de evento (3 niveles jerárquicos)
    - Turnos y operarios codificados

## 🛠️ Procesamiento
### Flujo de trabajo:
1. **Preprocesamiento** (script interno):
   - Anonimización de metadatos sensibles
   - Estandarización de categorías
   - Codificación de turnos/operarios

2. **Limpieza y enriquecimiento** ([2_limpieza-previa-analisis.ipynb](scripts/2_limpieza-dataset-linea-de-produccion-v2.ipynb)):
   - Consolidación de registros consecutivos
   - Detección automática de relaciones temporales
   - Adición de metadatos (día semana, horas equivalentes)

```python
# Ejemplo de relación detectada
df['Comentarios'] = "Pérdida de velocidad previo a Cambio de proceso"
```

## 📊 Resultados Intermedios
- **804 relaciones temporales** identificadas
- **94 eventos** con herencia de categorías
- Dataset listo para:
  - Análisis de series temporales
  - Modelado predictivo (ML)

## 📊 Próximos pasos
- Análisis de series temporales (en desarrollo)
- Modelado predictivo de eventos críticos

## ⚙️ Configuración
### Requisitos:
```bash
pip install -r requirements.txt
```

**Librerías principales**:
| Librería       | Versión | Uso                              |
|----------------|---------|----------------------------------|
| pandas         | >=2.0   | Manipulación de datos            |
| openpyxl       | >=3.1   | Lectura/escritura de Excel       |
| python-dotenv  | >=1.0   | Gestión de variables             |
| SQLAlchemy     | >=2.0   | Conexión a bases de datos        |
| Numpy          | >=1.24  | Operaciones matemáticas avanzadas|
| Matplotlib     | >=3.8.3 | Visualización de datos           |


## 📂 Estructura del Repositorio
```
/optimización-de-procesos-industriales
├── data/
│   ├── anonymized-data/       # Input para limpieza
│   └── cleaned-data/          # Output procesado para análisis
├── scripts/
│   ├── 1_anonimizar-dataset.ipynb  # Script interno
│   └── 2_limpieza-previa-analisis.ipynb  # Notebook principal
├── .gitignore
├── README.md
└── requirements.txt
```

## 🔐 Ética y Privacidad
- Datos originales **no incluidos** (solo versiones anonimizadas)
- Metodología documentada para auditoría
- Estructura reproducible sin acceso a información sensible

---

> ✨ **Tip**: Ejecuta el notebook en orden secuencial y verifica los paths relativos a `data/`
```
