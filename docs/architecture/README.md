# Arquitectura · versión 1.2.3

Aplicación monolítica de escritorio, un módulo Maven y un paquete Java `pe.alquileres`.
La separación es por responsabilidad de clase, con dependencias directas; no se presenta como MVC estricto.

```mermaid
flowchart TD
    Main[Inicio y configuración visual] --> UI[Interfaz Swing y FlatLaf]
    UI --> Service[Servicio de alquileres]
    UI --> Tasks[Proyección de pendientes e historial legible]
    Service --> Model[Modelo de datos en memoria]
    Tasks --> Model
    Service --> PDF[Generación de documentos con PDFBox]
    PDF --> Model
    Service --> Store[Almacenamiento local]
    Store --> JSON[Serialización con Gson]
    JSON --> Encrypted[Archivo autenticado con AES-256-GCM]
    Store --> Backup[Respaldos y recuperación]
    UI --> Export[Exportación de PDF legible]
    UI --> WA[Mensaje y enlace de WhatsApp]
    WA --> Manual[Adjuntar y enviar manualmente]
```

El modelo reúne espacios, inquilinos, estancias, cobros, garantías, reparaciones, documentos y auditoría.
Los documentos se conservan junto al estado; la exportación crea un PDF legible fuera del almacenamiento.
No hay servidor de base de datos ni backend web. La integración con WhatsApp abre un enlace;
no utiliza WhatsApp Business API ni verifica entrega o lectura.

El cifrado protege el archivo de estado y el contenido de documentos almacenados. La protección
depende de custodiar el almacenamiento y su material de recuperación. Los PDF exportados requieren
cuidado separado. El diagrama explica responsabilidades; no publica algoritmos ni formatos internos.
