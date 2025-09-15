# Bot de Registro de Tarjetas y Placas SUNARP

## Descripción

Bot RPA que automatiza el proceso de registro y consulta de tarjetas de propiedad vehicular y placas a través del sistema SUNARP. Procesa archivos de ventas de vehículos, consulta comprobantes de facturación electrónica y descarga documentos TIVE.

## Características Principales

- Automatización completa del flujo de trabajo
- Procesamiento de archivos Excel masivos
- Integración con sistemas web gubernamentales
- Generación automática de reportes

## Funcionalidades

### Procesamiento de Facturación Electrónica
- Validación de archivos de ventas en formato Excel
- Búsqueda automática de comprobantes en sistemas de facturación
- Descarga de archivos PDF y XML
- Carga de documentos en Smartsheet

### Consulta SUNARP - Síguelo
- Procesamiento de archivos TIVE
- Búsqueda automática de títulos de propiedad
- Descarga de documentos TIVE y O.Giro
- Actualización de registros en Smartsheet

## Requisitos del Sistema

- Acceso a sistemas de facturación electrónica
- Conexión SFTP para transferencia de archivos
- Credenciales para Smartsheet
- Acceso web a SUNARP - Síguelo

## Estructura de Archivos

### Entrada - Facturación
```
Ventas_dd-mm-aaaa.xlsx
Columnas: Región, Código Tienda, Retail, Nombre Tienda, Marca, Modelo, 
         Número Chasis, Número Motor, Fecha Venta, No Factura, 
         No Documento, Nombres y Apellidos
```

### Entrada - SUNARP
```
TIVES_POR_DESCARGAR_dd-mm-aaaa.xlsx
Columnas: Retail, Oficina Registral, Año, Título, Placa, Código
```

## Configuración

### Carpetas SFTP
- **INPUT Facturación**: `/data/valtx/INPUT/TYP/PAPERLESS`
- **INPUT SUNARP**: `/data/valtx/INPUT/TYP/SUNARP`
- **OUTPUT**: `/data/valtx/OUTPUT/TYP/`

### Horarios de Ejecución
- **Proceso Facturación**: Lunes a Viernes, 12:00 - 15:00
- **Proceso SUNARP**: Lunes a Viernes, 16:00 - 20:00

## Flujo de Trabajo

```
1. Carga archivo → 2. Validación datos → 3. Consulta web → 
4. Descarga documentos → 5. Actualiza Smartsheet → 6. Genera reporte
```

### Diagrama del Proceso
*Flujo principal del proceso de automatización*
<img width="865" height="482" alt="Image" src="https://github.com/user-attachments/assets/bf5549c1-d13a-47a3-88b0-35215fe6d889" />

### Interfaz SUNARP - Síguelo
*Pantalla de consulta en el sistema SUNARP*
<img width="707" height="330" alt="Image" src="https://github.com/user-attachments/assets/e3167f70-2c76-4bf9-82ee-d091cfe52a51" />

### Smartsheet Integration
*Carga automática de documentos en Smartsheet*

<img width="298" height="369" alt="Image" src="https://github.com/user-attachments/assets/30514650-e1ba-4b4c-b20f-6ae05a11e709" />

## Manejo de Errores

### Alertas Automáticas
- Archivo no encontrado en SFTP
- Datos obligatorios faltantes
- Errores de conectividad web
- Fallos en descarga de documentos

### Notificaciones
- Email automático al finalizar proceso
- Reporte detallado de errores
- Log de casos no procesados

## Salidas

### Reportes Generados
- `dd-mm-aaaa_Resultado_Paperless.xlsx`
- `dd-mm-aaaa_Resultado_Archivos_SUNARP.xlsx`

### Documentos Descargados
- Archivos PDF y XML de comprobantes
- Documentos TIVE
- Archivos O.Giro

## Volumen de Procesamiento

- **Capacidad**: 100 registros por semana
- **Frecuencia**: Diaria (días laborables)
- **Tiempo estimado**: 3-4 horas por proceso

## Estados del Proceso

- **Exitoso**: Documento encontrado y descargado
- **No encontrado**: Registro sin resultados en sistema
- **Error**: Fallo técnico requiere revisión manual

## Instalación y Uso

1. Configurar credenciales de acceso
2. Establecer conexiones SFTP
3. Programar ejecución automática
4. Monitorear logs y reportes

## Tecnologías

- RPA (Robotic Process Automation)
- Excel/CSV processing
- Web scraping
- SFTP file transfer
- Email notifications

## Mantenimiento

- Verificación semanal de logs
- Actualización de credenciales según políticas
- Monitoreo de cambios en sistemas web
- Respaldo de configuraciones
