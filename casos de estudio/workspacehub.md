# **Caso de Estudio: Transformación Digital de WorkSpaceHub**

WorkSpaceHub, una empresa con más de una década en el negocio de coworking, enfrenta el desafío de modernizar sus operaciones. 
---

## **Contexto Operativo**

WorkSpaceHub gestiona 50 sedes distribuidas en 10 ciudades, con una capacidad total de **200 salas** diseñadas para reuniones, trabajo en equipo y actividades individuales.

Cada sede atiende a una base promedio de **150 clientes regulares** al mes, y cada sala es utilizada aproximadamente **6 horas al día** en jornadas de 10 horas de operación. En total, WorkSpaceHub gestiona más de **36,000 horas de ocupación anual** en sus espacios.

Estos procesos varían según la ciudad y el centro, pero comparten problemas comunes de inconsistencia, duplicidad y falta de escalabilidad.

A pesar de su éxito inicial, los métodos manuales y sistemas obsoletos han limitado su capacidad para crecer y satisfacer las expectativas modernas de los clientes.

Estos procesos varían según la ciudad y el centro, pero comparten problemas comunes de inconsistencia, duplicidad y falta de escalabilidad.

- **Reservas Telefónicas:**  
    María, una asistente en el centro principal, recibe numerosas llamadas al día de clientes interesados en reservar salas de coworking. Para gestionar estas solicitudes, utiliza un archivo Excel compartido que contiene información sobre las reservas de todas las sedes.

    El archivo, que también es editado simultáneamente por otros asistentes, presenta conflictos frecuentes:
    
    - Celdas sobrescritas.
    - Reservas duplicadas.
    - Pérdida de información crítica.


    > *Caso Real:* Un día, Ana llegó a su reunión y descubrió que su sala había sido asignada a otra persona, lo que generó una experiencia negativa y una queja formal.

- **Reservas Presenciales:**  
    Los clientes que llegan directamente a las sedes son atendidos por un recepcionista. Este utiliza un calendario físico semanal para verificar la disponibilidad de salas. Si hay espacio, el cliente puede realizar el pago en efectivo o con tarjeta, que se registra en un sistema POS. Sin embargo, esta información no se sincroniza con el archivo Excel compartido.

    Problema:
	- Reservas realizadas presencialmente no siempre se reflejan en el sistema central.
	- Esto genera conflictos cuando la misma sala es reservada a través de otros canales.

    > *Caso Real:* Un cliente que había pagado y reservado su sala presencialmente tuvo que esperar 20 minutos mientras se resolvía un conflicto con otra reserva ingresada por teléfono.

- **Reservas Web:**  
  En un intento de modernización, WorkSpaceHub lanzó un formulario web en 2020. Este permite a los clientes solicitar reservas, pero las solicitudes no son procesadas automáticamente. Los recepcionistas revisan el formulario una vez al día y transcriben la información al archivo Excel.

  > *Caso real:* Laura, emprendedora y cliente habitual, intentó reservar una sala a través del formulario web para una reunión de última hora. Recibió la confirmación 24 horas después, demasiado tarde para sus necesidades. Frustrada, Laura optó por un coworking competidor.

---

## **Estructura del Sistema Actual**

### **Archivo Excel Compartido**

El archivo Excel compartido es el núcleo del sistema de reservas, pero su diseño y uso presentan múltiples problemas.

#### **Hoja Principal ("Reservas")**
| Fecha       | Hora Inicio | Hora Fin | Sala  | Cliente          | Método de Reserva | Confirmación |
|-------------|-------------|----------|-------|------------------|--------------------|--------------|
| 01/12/2024 | 09:00       | 11:00    | Sala A | Ana López        | Teléfono           | Confirmado   |
| 01/12/2024 | 11:00       | 13:00    | Sala B | Juan Rodríguez   | Presencial         | Confirmado   |
| 02/12/2024 | 10:00       | 12:00    | Sala A | Laura Martínez   | Web                | Pendiente    |

**Problemas:**  
  - Reservas duplicadas cuando varios asistentes editan simultáneamente.  
  - Falta de validación automática para prevenir errores de datos.

#### **Hoja de Reportes Semanales ("Reporte Centro")**
| Centro       | Fecha       | Ingresos Totales | Reservas Completadas | Reservas Fallidas |
|--------------|-------------|------------------|-----------------------|-------------------|
| Lima Central | 01/12/2024 | $1,200           | 25                    | 3                 |
| Arequipa     | 01/12/2024 | $850             | 18                    | 5                 |

**Problemas:**  
  - La consolidación manual toma días.  
  - Los gerentes a menudo entregan datos incompletos o retrasados.

#### **Hoja de Clientes ("Clientes Frecuentes")**
| Nombre          | Email               | Teléfono      | Veces Usado | Última Reserva |
|-----------------|---------------------|---------------|-------------|----------------|
| Ana López       | ana@gmail.com       | 987654321     | 10          | 01/12/2024     |
| Juan Rodríguez  | juan@gmail.com      | 987123456     | 8           | 30/11/2024     |

**Problemas:**  
  - No existe automatización para enviar recordatorios o promociones.  
  - Los datos no están sincronizados con el sistema de reservas.

---

## **Narrativa desde los Actores**

- **CEO:**  
  “Perdemos clientes debido a la lentitud y los errores en nuestras reservas. Estamos dejando que nuestra competencia nos supere porque no hemos invertido en tecnología.”

- **Gerente de Operaciones:**  
  “Generar reportes semanales es una pesadilla. Los datos llegan tarde y, cuando llegan, no son confiables.”

- **Clientes:**  
  - *"Nunca sé si mi reserva fue confirmada hasta que recibo un correo manual, que a veces llega tarde."*  
  - *"No puedo confiar en el sistema; prefiero buscar otro coworking más moderno."*

---


##  Restricciones y Retos

- **Tecnología:** La infraestructura de TI en los centros varía, con conexiones a internet inestables y hardware desactualizado.
- **Presupuesto:** El proyecto debe mantenerse dentro de un límite inicial de $50,000 USD.
- **Tiempo:** Se espera que un MVP funcional esté listo en maximo seis meses.

