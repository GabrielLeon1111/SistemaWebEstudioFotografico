# Estudio Fotográfico · Reservas, fotógrafos y facturación

![GeneXus](https://img.shields.io/badge/GeneXus-V18-00A3E0)
![Java](https://img.shields.io/badge/Java-Tomcat-ED8B00?logo=openjdk&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?logo=microsoftsqlserver&logoColor=white)
![GAM](https://img.shields.io/badge/Seguridad-GAM-5C2D91)
![Web](https://img.shields.io/badge/Plataforma-Web-1F3A63)

Sistema web de gestión para un **estudio fotográfico**, desarrollado en **GeneXus V18**. Automatiza
la **reserva de eventos**, la **asignación de fotógrafos**, la **facturación con seña y saldo** y la
**entrega digital de las fotos** al cliente.

## Capturas

<table>
  <tr>
    <td align="center"><img src="https://github.com/user-attachments/assets/c92f4238-8f48-4024-9e00-d60a4ff590a1" width="420" alt="Reserva del evento"><br><b>Reserva del evento</b><br>Cliente por cédula, fecha, horario y fotógrafo asignado solo</td>
    <td align="center"><img src="https://github.com/user-attachments/assets/5ab30889-c578-479f-bfe5-0145e2f9cc52" width="420" alt="Paquete y cobro"><br><b>Paquete y cobro</b><br>Servicios adicionales, anticipo, saldo y vuelto</td>
  </tr>
  <tr>
    <td align="center"><img src="https://github.com/user-attachments/assets/ae142501-d5a7-4169-a390-87a58f48c28a" width="420" alt="Comprobante"><br><b>Comprobante</b><br>Paquete, servicios incluidos y seña del 30 %</td>
    <td></td>
  </tr>
</table>

---

## Índice

1. [Qué hace](#qué-hace)
2. [Asignación automática de fotógrafo](#asignación-automática-de-fotógrafo)
3. [Roles](#roles)
4. [Tecnologías](#tecnologías)
5. [Estado del proyecto](#estado-del-proyecto)
6. [Autor](#autor)

---

## Qué hace

### Caja
- **Apertura de caja** con monto inicial: habilita el módulo de agendamiento.
- Cierre de caja *(en desarrollo)*.

### Recepción y agendamiento
- Búsqueda del cliente por **cédula con autocompletado**; registro manual si es nuevo.
- Elección del paquete de servicios, la fecha, el horario y el lugar del evento.
- **Fotógrafo asignado automáticamente** (ver más abajo).

### Facturación
- **Seña obligatoria del 30 %** calculada sola.
- Personalización del paquete con **servicios adicionales**, con recálculo del subtotal y la seña en
  tiempo real.
- Método de pago, monto pagado y vuelto, con emisión del **comprobante**.
- **Cancelación del saldo:** la recepción busca al cliente, ve los servicios contratados y lo que
  falta pagar, y emite un nuevo comprobante al cobrar.

### Alta automática del cliente
- Al confirmar el evento se crea (o se valida si ya existe) un usuario en **GeneXus Access Manager**
  con rol *Cliente*: usuario = email del cliente, contraseña inicial = número de cédula.

### Panel del fotógrafo *(parcial)*
- Eventos asignados, con filtros por fecha y estado.
- Selección de un evento para gestionar la carga de fotos.

### Portal del cliente
- El cliente entra con su usuario y elige las fotos de su paquete (con marca de agua).
- El fotógrafo edita en alta calidad las elegidas.
- Al pagar el saldo, el estado pasa de *parcialmente pagado* a *pagado* y se habilita la descarga.

---

## Asignación automática de fotógrafo

Algoritmo propio para repartir el trabajo de forma pareja:

1. **Disponibilidad:** descarta a los fotógrafos con otro evento que se superponga en el horario,
   contando **3 horas de margen** después de cada evento.
2. **Carga de trabajo:** entre los disponibles, elige al que tiene **menos eventos en su historial**.
3. **Desempate al azar:** si hay empate, sortea entre ellos para distribuir el trabajo equitativamente.

---

## Roles

| | Recepción / Caja | Fotógrafo | Cliente |
|---|:---:|:---:|:---:|
| Abrir caja, agendar y facturar | ✅ | | |
| Ver eventos asignados y cargar fotos | | ✅ | |
| Elegir y descargar sus fotos | | | ✅ |

Usuarios, roles y permisos con **GeneXus Access Manager (GAM)**.

---

## Tecnologías

| Parte | Herramienta |
|---|---|
| Desarrollo | GeneXus V18 |
| Backend | Java en Apache Tomcat |
| Base de datos | SQL Server |
| Seguridad | GeneXus Access Manager (GAM) |
| Interfaz | Web (WorkWithPlus) |

---

## Estado del proyecto

| Módulo | Estado |
|---|---|
| Apertura de caja, agendamiento, asignación de fotógrafo y facturación (seña y saldo) | ✅ Funcional |
| Cierre de caja, panel del fotógrafo, portal de fotos y edición | 🔜 En desarrollo |

---

## Autor

Desarrollado por **Gabriel León** ([@GabrielLeon1111](https://github.com/GabrielLeon1111)).

**Lo que muestra este proyecto:**
- Sistema web con GeneXus V18, Java y SQL Server.
- Algoritmo de asignación por disponibilidad, carga de trabajo y desempate aleatorio.
- Alta automática de usuarios y permisos por rol con GAM.
- Facturación con seña y cancelación de saldo.
