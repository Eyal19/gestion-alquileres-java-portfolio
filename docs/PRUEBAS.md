# Pruebas · versión 1.2.3

**Verificación del 3 de octubre de 2026: 185 comprobaciones satisfactorias** en la copia privada limpia.
Suite de aceptación propia: un ejecutable Java, sin JUnit. El total corresponde a comprobaciones
ejecutadas, no a 185 métodos JUnit ni a un porcentaje de cobertura.

| Área | Casos cubiertos |
| --- | --- |
| Inicialización | Nueve espacios vacíos, sin datos personales; conservar configuración al reabrir |
| Cálculos | Decimales, redondeo, lectura faltante/cero, medidor, conceptos recurrentes o únicos |
| Cobros y pagos | Duplicados, pago completo, corrección de importes y estado |
| Documentos | Aviso/recibo/liquidación, identificación y conservación de versiones |
| Inquilinos y garantías | Estancias, baja recuperable, reparaciones, aplicación y devolución |
| Auditoría | Motivo, antes/después legibles, recuperación del último cambio |
| Persistencia | Lectura cifrada, detección de alteración, bloqueo, respaldo y restauración |
| Interfaz | Pantallas Swing, calendarios, campos, distribución y pendientes |
| WhatsApp | Normalización y enlaces, mensaje, preparación y confirmación manual sin enviar |

## Ejecución

En el repositorio privado, con JDK 21, Maven y una sesión gráfica:

```shell
mvn clean
mvn test
mvn package
```

La fase test ejecuta la suite en una JVM separada mediante exec-maven-plugin.
Las evidencias se generan bajo target/qa y se excluyen de Git; no se usan datos operativos.
El repositorio público es documental y no incluye los archivos necesarios para ejecutar esas órdenes.

## Límites de la evidencia

La suite pasó en Windows 11 con Temurin 21.0.6 y Maven 3.9.16. Requiere entorno gráfico;
no se probó ejecución headless, instalación en el equipo final ni envío real por WhatsApp.
No se midió cobertura porcentual y no se realizó una auditoría criptográfica independiente.
La traza histórica incluida en el original también decía 185; el resultado aquí se volvió a ejecutar.

El entorno de verificación requirió resolver certificados HTTPS de Maven con un puente local
que valida HTTPS mediante Python, y ejecutar Java fuera del sandbox debido a AccessDeniedException.
No se deshabilitó TLS ni se incorporó esa configuración temporal al proyecto.
Las órdenes se verificaron con opciones de entorno para caché y resolución, descritas en el reporte de entrega.
