# **Caso de Estudio: Transformación Digital de AgroChain**

AgroChain es una plataforma tecnológica que conecta a agricultores, transportistas y compradores mayoristas. A pesar de su rápido crecimiento, sus procesos actuales están limitados por un sistema centralizado y secuencial que no puede manejar eficientemente el volumen de operaciones en tiempo real. 

---

## **Contexto Operativo**

AgroChain opera en **15 regiones agrícolas**, conectando a más de **5,000 agricultores**, **500 transportistas**, y **200 compradores mayoristas**. Durante las temporadas de cosecha, la plataforma gestiona un promedio de **10,000 órdenes diarias**, con picos de **15,000 órdenes** en días de alta demanda.

### **Estadísticas Operativas:**
- **Órdenes diarias promedio:** 10,000.
- **Duración promedio de una transacción:** 4 horas.
- **Retrasos en notificaciones:** 30% de las órdenes no se notifican a tiempo.
- **Transacciones fallidas:** 15% debido a falta de sincronización entre actores.
- **Retrasos en entregas:** 20% por falta de seguimiento en tiempo real.
- **Ingresos promedio diarios:** $250,000 USD.

---

### **Procesos Actuales**

#### **1. Gestión de Órdenes**
El flujo para gestionar una orden es secuencial:
1. El agricultor publica un lote en la plataforma (por ejemplo, 500 kg de fresas).
2. El sistema registra el lote en una base de datos central y envía notificaciones a los compradores.
3. Los compradores interesados realizan un pedido, que es procesado manualmente por operadores del sistema.
4. Un transportista disponible es asignado para recoger el lote y entregarlo al comprador.

**Problemas Identificados:**
- Si el sistema de notificaciones falla, los compradores no reciben alertas sobre los lotes disponibles.
- La asignación de transportistas no considera factores como proximidad o capacidad de carga.

> **Caso Real:**  
> Un agricultor en Piura publicó un lote de mango a las 8:00 AM. Las notificaciones a los compradores se retrasaron 3 horas debido a un error en la base de datos. Para cuando se concretó la venta, no había transportistas disponibles, y el agricultor perdió el lote.

---

#### **2. Seguimiento de Envíos**
El sistema actual permite a los transportistas actualizar manualmente el estado del envío ("En camino", "Entregado"), pero no tiene rastreo GPS integrado.

**Problemas Identificados:**
- Si un transportista olvida actualizar el estado, los compradores no saben si su pedido está en camino o retrasado.
- Las estimaciones de entrega no consideran factores dinámicos como tráfico o clima.

> **Caso Real:**  
> Un comprador en Lima esperaba un lote de papas que debía llegar a las 6:00 PM. El transportista no actualizó el estado, y el cliente no supo hasta las 9:00 PM que el pedido estaba retrasado debido a un bloqueo en la carretera.

---

#### **3. Reportes de Calidad**
Los compradores evalúan la calidad de los productos al recibirlos, pero esta información no se distribuye de forma inmediata a los agricultores ni a los transportistas.

**Problemas Identificados:**
- Los agricultores no reciben retroalimentación rápida para mejorar sus próximas entregas.
- Los transportistas no tienen visibilidad sobre los lotes con mayor probabilidad de éxito.

> **Caso Real:**  
> Un agricultor en Cusco recibió reportes de baja calidad dos semanas después de entregar un lote de papas. Para entonces, ya había enviado más productos con los mismos problemas, perdiendo credibilidad ante los compradores.

---

## **Estructura del Sistema Actual**

### **Arquitectura Monolítica**
El sistema actual es monolítico, con un servidor centralizado que maneja todas las operaciones:

- **Gestión de Lotes:** Registra productos publicados por los agricultores.
- **Sistema de Notificaciones:** Envía correos electrónicos a los compradores.
- **Módulo de Seguimiento:** Permite actualizaciones manuales del estado de envíos.
- **Reportes:** Genera reportes semanales de calidad y ventas.

#### **Lenguaje y Herramientas:**
- **Lenguaje:** Python 2.7 (obsoleto desde 2020).
- **Framework:** Django 1.8, una versión desactualizada con soporte limitado.
- **Base de Datos:** MySQL 5.5 en un único servidor, sin particionamiento ni replicación.

---
