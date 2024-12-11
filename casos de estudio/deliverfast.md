# **Caso de Estudio: Optimización de DeliverFast**

DeliverFast es una startup de logística que se especializa en entregas rápidas en áreas urbanas. Aunque ha ganado popularidad por su promesa de entregas en menos de 30 minutos, el crecimiento exponencial del negocio ha puesto en evidencia serias deficiencias en sus sistemas y procesos. 

---

## **Contexto Operativo**

DeliverFast opera en 5 ciudades principales y cuenta con una flota de **1,000 repartidores**. Sus operaciones diarias incluyen la gestión de un promedio de **50,000 pedidos** en horas pico, con un crecimiento anual del **20%**. Aunque inicialmente dependía de soluciones rápidas y herramientas manuales, la complejidad actual exige una transformación digital integral.

- **Clientes:**  
  Usuarios finales que realizan pedidos de comida, compras rápidas o paquetes pequeños a través de la app móvil de DeliverFast.  
  - **Tiempo de Promesa:** Menos de 30 minutos.  
  - **Satisfacción Actual:** 75% (baja por retrasos en horas pico).  

- **Comercios Asociados:**  
  Más de **10,000 restaurantes y tiendas** que dependen de DeliverFast para incrementar sus ventas.  
  - **Problema Frecuente:** Reportes tardíos sobre ventas y entregas, y falta de visibilidad en tiempo real sobre el estado de los pedidos.

---

## **Procesos Actuales**

### **Gestión de Pedidos**
Cuando un cliente realiza un pedido en la app móvil:
1. El pedido se registra en una base de datos SQL básica.
2. Un algoritmo sencillo asigna al repartidor más cercano.
3. El repartidor recibe una notificación en su app para aceptar o rechazar el pedido.
4. El sistema no toma en cuenta factores como el tráfico o la carga de trabajo del repartidor.

> **Caso Real:**  
> En horas pico, varios pedidos son asignados al mismo repartidor, lo que resulta en retrasos y clientes insatisfechos. Un repartidor en Lima reportó que tuvo que entregar cuatro pedidos simultáneamente en puntos opuestos de la ciudad, lo que le tomó 90 minutos en lugar de 30.

---

### **Seguimiento de Entregas**
El sistema actual no cuenta con una solución robusta para rastrear a los repartidores en tiempo real:
- **App del Cliente:** Muestra una estimación básica basada en la distancia, pero no incluye factores dinámicos como tráfico o clima.
- **App del Repartidor:** Solo permite actualizar manualmente el estado del pedido ("En camino", "Entregado").

> **Problema Frecuente:**  
> En días lluviosos, los repartidores sufren retrasos significativos, pero el sistema sigue mostrando estimaciones irreales a los clientes, generando frustración.

---

### **Reportes para Comercios**
Los comercios asociados reciben reportes semanales por correo electrónico con datos de sus ventas y entregas:
- **Tiempo Promedio de Generación:** 3 días después de cerrar la semana.
- **Problema Frecuente:** Datos incompletos o erróneos, debido a que los reportes son generados manualmente por el equipo de operaciones.

> **Caso Real:**  
> Un restaurante reportó que los datos de ventas enviados por DeliverFast eran inconsistentes, mostrando una diferencia de hasta $1,000 con respecto a su sistema interno.

---

## **Métricas Clave**

- **Pedidos diarios:** 50,000 en promedio, con un 60% concentrado entre las 6 PM y 9 PM.
- **Tiempo promedio de entrega:** 40 minutos (10 minutos por encima de la promesa).
- **Tasa de aceptación de pedidos por repartidores:** 85% (baja durante horas pico).
- **Porcentaje de pedidos retrasados:** 25%.
- **Tasa de insatisfacción del cliente:** 20%, según encuestas de la app.
- **Flota activa:** 1,000 repartidores, con una rotación mensual del 15%.

---

## **Narrativa desde los Actores**

- **CEO:**  
  “Nuestra promesa de entrega en 30 minutos está en juego. Si no solucionamos estos problemas rápidamente, perderemos la confianza de nuestros clientes y comercios asociados.”

- **Gerente de Operaciones:**  
  “El sistema actual simplemente no escala. Necesitamos una solución que pueda manejar más pedidos sin generar caos.”

- **Clientes:**  
  - *"Hice un pedido con la promesa de 30 minutos, pero llegó después de una hora. Ni siquiera podía rastrear dónde estaba mi repartidor."*  
  - *"Entiendo que haya tráfico, pero al menos deberían avisarme si va a haber retrasos."*

- **Repartidores:**  
  - *"En horas pico nos asignan más pedidos de los que podemos manejar. Los clientes se molestan y nosotros quedamos mal."*  
  - *"La app necesita mejorar. A veces ni siquiera funciona el GPS correctamente."*

- **Comercios Asociados:**  
  - *"Los reportes son inútiles si llegan tarde o con errores. Necesito saber mis ventas en tiempo real."*

---

## **Restricciones y Retos**

- **Tecnología:** La infraestructura actual está limitada a un sistema monolítico alojado en un servidor único, lo que dificulta la escalabilidad.
- **Presupuesto:** $100,000 USD para el desarrollo de un nuevo sistema.
- **Tiempo:** Un plazo de 8 meses para implementar un MVP funcional.

---


## **Arquitectura Base Actual**

#### **Tipo de Arquitectura:** Monolítica
La aplicación está diseñada como un sistema monolítico en el que todos los componentes (gestión de pedidos, usuarios, repartidores, reportes y notificaciones) están acoplados en un único código base.

#### **Lenguaje y Frameworks:**
- **Lenguaje principal:** PHP 5.6 (una versión obsoleta que no recibe soporte oficial desde 2019).
- **Framework:** CodeIgniter 2.x, elegido por su simplicidad en el momento, pero que carece de herramientas modernas para escalar.

DeliverFast comenzó como una startup pequeña con un sistema desarrollado rápidamente para probar el modelo de negocio. Aunque la aplicación funcionó bien durante sus primeras etapas, ahora enfrenta serias limitaciones debido a su diseño inicial.

#### **Base de Datos:**

- **Tabla de Pedidos:**
  | PedidoID | ClienteID | ComercioID | RepartidorID | Estado       | Tiempo Creado       |
  |----------|-----------|------------|--------------|--------------|---------------------|
  | 001      | 1001      | 5001       | 3001         | En camino    | 2024-12-11 18:45:00 |
  | 002      | 1002      | 5002       | 3002         | Retrasado    | 2024-12-11 18:50:00 |

---
- **Tipo:** MySQL 5.5, alojada en un único servidor.
- **Problemas:**
  - Carece de índices optimizados, lo que genera consultas lentas.
  - No está configurada para manejo de transacciones complejas.
  - Sin replicas ni particionamiento, lo que afecta la disponibilidad.

#### **Servidor de Aplicaciones:**
- **Tipo:** Servidor Apache corriendo en un VPS básico.
- **Problemas:**
  - Soporte limitado para manejar miles de solicitudes simultáneas.
  - Sin balanceo de carga ni redundancia.

#### **Flujo de Operación en el Sistema Actual:**
1. El cliente realiza un pedido a través de la app móvil.
2. La solicitud llega al servidor central, donde se registra en la base de datos MySQL.
3. Un script interno asigna un repartidor basándose únicamente en la distancia, sin considerar otros factores.
4. La información se devuelve a las apps del cliente y del repartidor.
5. Los reportes se generan a partir de consultas manuales ejecutadas sobre la base de datos.

