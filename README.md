# 📊 Generación Automatizada de Reporte de Nómina

## 📋 Descripción del Proyecto

Proyecto de automatización RPA desarrollado con UiPath Studio para la **Prueba Técnica de Home Power Colombia** para el puesto de Desarrollador RPA. El sistema procesa archivos de nómina y métricas para generar reportes consolidados automáticamente.

## 🎯 Objetivo del Proyecto

Automatizar la generación de reportes de nómina mediante la lectura, filtrado y consolidación de información de dos archivos Excel (Nomina.xlsx y Metricas.xlsx), generando un informe final con la información procesada y estructurada.

---

## 🔄 Flujo del Proceso

El proceso principal (`Main.xaml`) invoca los siguientes workflows en orden:

1. **Selección formato lectura archivo** (`Seleccion formato lectura archivo.xaml`)

   - Permite al usuario elegir la ubicación de los archivos
   - Opción de buscar carpeta de parámetros o ingresar ruta manual

2. **Encontrar archivos parámetros** (`Encontrar archivos parametros.xaml`)

   - Localiza los archivos Nomina.xlsx y Metricas.xlsx
   - Valida la existencia de los archivos requeridos

3. **Leer nómina** (`Leer_nomina.xaml`)

   - Lee el archivo Nomina.xlsx en memoria
   - Extrae datos de la hoja "Insumo1"

4. **Leer métricas** (`Leer_metricas.xaml`)

   - Lee el archivo Metricas.xlsx en memoria
   - Carga la información de métricas por identificación

5. **Filtrado y construcción de reporte** (`Filtrado y construccion de reporte.xaml`)
   - Filtra NITs únicos de la columna "Nit" en Nomina.xlsx
   - Busca coincidencias en la columna "IDENTIFICACION" de Metricas.xlsx
   - Duplica registros según cantidad de filas en métricas
   - Añade información de CECO y NOMBRE CECO
   - Genera archivo final con nombre del participante

---

## 📁 Estructura del Proyecto

```
Generación Automatizada de Reporte de Nómina/
├── 📂 Dependencies
├── 📂 Entities
├── 📂 Templates
├── 📂 Params
├── 📂 Results
├── 📄 Encontrar archivos parametros.xaml
├── 📄 Filtrado y construccion... (filtrado_construccion)
├── 📄 Leer_metricas.xaml
├── 📄 Leer_nomina.xaml
├── 📄 Main.xaml (Punto de entrada)
├── 📄 project.json
├── 📄 repetir_datatable.xaml (eliminable)
└── 📄 Seleccion formato lectura archivo.xaml
```

---

## 🛠️ Requisitos Técnicos

### Software Necesario

- **UiPath Studio** (versión compatible con las dependencias listadas)
- **Microsoft Excel** (para procesamiento de archivos .xlsx)
- **Windows OS** (dependencias específicas de Windows)

### Paquetes/Dependencias UiPath

| Paquete                              | Versión |
| ------------------------------------ | ------- |
| UiPath.Excel.Activities              | 3.3.1   |
| UiPath.Mail.Activities               | 2.5.10  |
| UiPath.MicrosoftOffice365.Activities | 3.5.10  |
| UiPath.System.Activities             | 25.10.3 |

### Archivos de Entrada Requeridos

1. **Nomina.xlsx**

   - Debe contener hoja "Insumo1"
   - Columna "Nit" con identificaciones (pueden estar repetidos)

2. **Metricas.xlsx**
   - Columna "IDENTIFICACION" para filtrar por NIT
   - Columnas "CECO" y "NOMBRE CECO"

---

## 🚀 Cómo Ejecutar el Proyecto

1. **Abrir el proyecto** en UiPath Studio
2. **Verificar dependencias** instaladas correctamente
3. **Preparar archivos de entrada**:
   - Colocar `Nomina.xlsx` y `Metricas.xlsx` en la carpeta de parámetros
   - O tener la ruta de los archivos disponible
4. **Ejecutar** `Main.xaml`
5. **Seleccionar opción** de ubicación de archivos cuando se solicite
6. El proceso generará automáticamente el archivo de reporte

---

## 📊 Resultado Esperado

El proyecto genera un archivo Excel con el nombre del participante que contiene:

- **Hoja "Reporte"**: Consolidación de información de nómina y métricas
  - Registros de nómina filtrados por NIT
  - Duplicación de registros según cantidad de filas en métricas
  - Información de CECO y NOMBRE CECO añadida
  - Si no hay coincidencias en métricas, se deja una sola repetición

---

## 🔧 Áreas de Mejora

### Funcionalidades Sugeridas

1. **Eliminacion de ventanas emergentes**

   - Durante la ejecucion las ventanas o mensajes flotantes pueden ser insignificantes en varias partes del proceso

1. **Manejo de Errores Robusto**

   - Implementar bloques Try-Catch más específicos
   - Agregar logs detallados para debugging
   - Validación de estructura de archivos de entrada

1. **Configuración Externalizada**

   - Mover rutas y nombres de archivo a archivo de configuración
   - Parametrizar nombres de hojas y columnas
   - Configurar opciones de email desde archivo externo

1. **Validaciones de Datos**

   - Verificar formato de NITs antes de procesar
   - Validar estructura de columnas esperadas
   - Alertar sobre datos duplicados o inconsistentes

1. **Reportería Mejorada**

   - Agregar formato condicional al Excel generado
   - Generar log de ejecución con métricas de proceso

1. **Interfaz de Usuario**

   - Crear formulario UiPath Forms para configuración
   - Agregar barra de progreso visual
   - Implementar notificaciones de finalización

1. **Gestión de Versiones**
   - Implementar versionado de archivos generados
   - Crear backup automático de resultados anteriores
   - Mantener histórico de ejecuciones

---

## 📝 Notas del Desarrollador

- 🎯 Cumplimiento de requisitos: Se logro implementar la mayoria de puntos pero todavia falta rubustecer el proyecto con validaciones de diferentes calibres y manejo profundo de errores además falto la implementacion de envio de correo El proyecto tiene mucho alcance en mejorar como se menciono en la parte superior.

---

## 📄 Licencia

#### Proyecto desarrollado como prueba técnica para Home Power Colombia S.A.S.

**Desarrollado usando UiPath Studio**
