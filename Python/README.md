# Reto 3 - Sistema de Gestión de Inventario

Sistema de gestión de inventario para una empresa de automoción desarrollado en Python como parte del Reto 3 del curso 1DM3.

## 📋 Descripción

Este programa permite gestionar el inventario de componentes de automoción que llegan a la empresa. El sistema automatiza el registro de recepciones diarias, controla el stock de componentes, identifica piezas defectuosas y genera reportes exportables.

### Funcionalidades principales

- **Gestión de recepciones**: Importa automáticamente los datos de entrada diaria desde archivos JSON (`entradaYYYY-MM-DD.json`)
- **Control de stock**: Mantiene un registro actualizado del inventario de componentes con su código, descripción, cantidad y última entrada
- **Registro de defectos**: Identifica y almacena componentes defectuosos con su tipo de defecto y cantidad
- **Búsqueda de componentes**: Permite consultar componentes específicos y visualizar sus defectos acumulados
- **Exportación de datos**: Genera archivos CSV con el inventario completo para análisis externo
- **Gestión de salidas**: Reduce el stock mediante entrada manual o carga masiva desde JSON (`salidaYYYY-MM-DD.json`)

### Estructura de la base de datos

El sistema utiliza SQLite con tres tablas principales:

1. **componentes**: Almacena el inventario actual (código, descripción, stock, última entrada)
2. **recepciones**: Registra todas las entradas de componentes con detalles de proveedor, lote y estado
3. **defectuosos**: Mantiene un registro de componentes defectuosos vinculados a recepciones específicas

## 🔧 Requisitos

- Python 3.8 o superior
- SQLite3 (incluido en Python)

### Dependencias

```
pandas
```

## 📥 Instalación

1. Clona el repositorio:
```bash
git clone https://github.com/Joseba19/Reto3.git
cd Reto3/Python
```

2. Instala las dependencias necesarias:
```bash
pip install pandas
```

3. Crea la carpeta `Archivos` en el directorio principal:
```bash
mkdir Archivos
```

4. Coloca los archivos JSON de entrada en la carpeta `Archivos` con el formato:
   - `entradaYYYY-MM-DD.json` para recepciones
   - `salidaYYYY-MM-DD.json` para salidas (opcional)

## 💻 Uso

Ejecuta el programa principal:

```bash
python main.py
```

### Menú de opciones

1. **Insertar nueva entrada**: Procesa el archivo JSON del día actual e inserta los datos en la base de datos
2. **Visualizar componentes y stock**: Muestra todos los componentes con su stock actual
3. **Buscar componentes defectuosos**: Consulta defectos por código de componente
4. **Exportar componentes en formato CSV**: Genera un archivo CSV con el inventario
5. **Eliminar stock**: Reduce el stock manualmente o mediante JSON
6. **Eliminar la base de datos**: Resetea las tablas (usar con precaución)
7. **Salir**: Cierra el programa

### Formato de archivos JSON

**Archivo de entrada** (`entradaYYYY-MM-DD.json`):
```json
{
  "recepciones": [
    {
      "fecha": "2025-01-29",
      "codigo": "COMP-001",
      "descripcion": "Filtro de aceite",
      "cantidad": 100,
      "proveedor": "Proveedor S.A.",
      "lote": "L2025-01",
      "estado": "Aceptado",
      "cantidad_defectuosas": 5,
      "observaciones": "Embalaje dañado en 5 unidades"
    }
  ]
}
```

**Archivo de salida** (`salidaYYYY-MM-DD.json`):
```json
{
  "salidas": [
    {
      "codigo": "COMP-001",
      "cantidad": 50
    }
  ]
}
```

## 🛠️ Tecnologías

- **Python**: Lenguaje de programación principal
- **SQLite**: Base de datos relacional integrada
- **JSON**: Formato de intercambio de datos
- **Pandas**: Librería para exportación de datos a CSV

## ✒️ Autor

**Joseba19** - [GitHub](https://github.com/Joseba19)

---

Proyecto desarrollado para el curso 1DM3 - Reto 3