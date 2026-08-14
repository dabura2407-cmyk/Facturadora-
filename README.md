# FacturaMX — CFDI 4.0

Prototipo web frontend desarrollado en HTML5, CSS3 y JavaScript.

## Ejecutar
Abre `index.html` en un navegador moderno con conexión a internet (usa librerías vía CDN: jsPDF, jsPDF-AutoTable y QRCode.js).

## Alcance actual
- Captura de emisor y receptor.
- Campos principales de CFDI 4.0 (con claves SAT reales en los selects).
- Conceptos dinámicos con cálculo redondeado a 2 decimales.
- Cálculo de subtotal, IVA y total.
- Validaciones preventivas (RFC, CP, claves SAT de concepto, campos requeridos).
- Vista previa en pantalla.
- Exportación de borrador JSON.
- **Generación de PDF** de la representación de la factura.
- **Código QR** en el PDF con los datos de la factura en texto plano (RFC emisor/receptor, folio, fecha, subtotal, IVA, total).
- **Folio de verificación interno**: hash SHA-256 del contenido de la factura, para detectar si el PDF fue alterado después de emitido.

## Importante — límites fiscales
Esta versión **NO timbra CFDI ante el SAT** y el PDF que genera **no es un CFDI válido fiscalmente**:

- El QR y el folio de verificación son mecanismos propios de esta app, **no** el Sello Digital del SAT ni la Cadena Original del Complemento de Certificación Digital del SAT.
- Esos elementos fiscales reales solo pueden generarse con un Certificado de Sello Digital (CSD) del contribuyente y el timbrado a través de un Proveedor Autorizado de Certificación (PAC).
- Para producción se necesita: backend, manejo seguro del CSD (nunca en el cliente/navegador), generación y sellado del XML conforme al XSD oficial del SAT, y conexión con un PAC.

El diseño se basa en los requisitos generales publicados por el SAT para CFDI 4.0 y debe complementarse con los catálogos, XSD, reglas de validación y casos de uso oficiales antes de considerarse un sistema fiscal de producción.
