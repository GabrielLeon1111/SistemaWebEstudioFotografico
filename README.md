# Sistema de Gestión - Estudio Fotográfico

Sistema de gestión para estudios fotográficos desarrollado en GeneXus V18. 
Automatiza la reserva de eventos, asignación de fotógrafos, facturación con 
seña y saldo, y entrega digital de fotos a clientes.

## Capturas
<img width="1440" height="917" alt="image" src="https://github.com/user-attachments/assets/c92f4238-8f48-4024-9e00-d60a4ff590a1" />
<img width="1487" height="912" alt="image" src="https://github.com/user-attachments/assets/5ab30889-c578-479f-bfe5-0145e2f9cc52" />
<img width="1641" height="917" alt="image" src="https://github.com/user-attachments/assets/ae142501-d5a7-4169-a390-87a58f48c28a" />

## Funcionalidades

**Caja**
- Apertura de caja con monto inicial, que habilita el acceso al módulo de agendamiento
- Cierre de caja *(en desarrollo)*

**Recepción y Agendamiento**
- Búsqueda de cliente por cédula con autocompletado; registro manual si es nuevo
- Selección de paquete de servicios disponibles, fecha y horario del evento
- **Asignación automática de fotógrafo** mediante algoritmo propio:
  1. Filtra fotógrafos disponibles según solapamiento de horarios (incluye 3h de margen post-evento)
  2. Selecciona el/los fotógrafo(s) con menor carga de trabajo histórica
  3. Si hay empate, desempata al azar para distribuir el trabajo equitativamente

**Facturación**
- Cálculo automático de seña obligatoria (30% del total)
- Personalización del paquete con servicios adicionales y recálculo de subtotal y seña en tiempo real
- Registro de método de pago, monto y vuelto, con emisión de comprobante
- **Cancelación de saldo pendiente:** la recepcionista (con rol de caja) busca al cliente, visualiza automáticamente los servicios adquiridos y el monto pendiente, y emite un nuevo comprobante al cancelar

**Alta automática de usuario cliente**
- Al confirmar el evento, se crea (o valida si ya existe) un usuario en GeneXus Access Manager (GAM) con rol "Cliente"
- Usuario: email del cliente · Contraseña inicial: número de cédula

**Panel del fotógrafo**
- Listado de eventos asignados con filtros por fecha y estado del evento
- Selección de un evento para gestionar la carga de fotos
- *(parcialmente implementado)*

**Portal del cliente**
- El cliente accede con su usuario y selecciona las fotos correspondientes a su paquete (marcadas con marca de agua)
- El fotógrafo edita en alta calidad las fotos seleccionadas
- Al completar el pago restante, el estado pasa de "parcialmente pagado" a "pagado" y se habilita la descarga

## Stack tecnológico
- **Herramienta:** GeneXus V18
- **Backend:** Java (Apache Tomcat)
- **Base de datos:** SQL Server
- **Seguridad:** GAM

## Estado del proyecto
✅ Apertura de caja, agendamiento, asignación automática de fotógrafo y facturación (seña y saldo) — funcional
🔜 Cierre de caja, panel del fotógrafo, portal de selección/entrega de fotos y edición — en desarrollo
