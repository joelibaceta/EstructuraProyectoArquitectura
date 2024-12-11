# **Caso de Estudio: Resiliencia y Escalabilidad de StreamArena**

StreamArena es una plataforma de transmisión en vivo dedicada a los esports, que conecta a jugadores profesionales, organizadores de torneos y millones de fanáticos en todo el mundo. Su objetivo principal es proporcionar una experiencia de visualización en tiempo real, pero el crecimiento exponencial de usuarios y eventos ha expuesto serias limitaciones en la infraestructura tecnológica actual.

---

## **Contexto Operativo**

StreamArena transmite torneos en vivo y ofrece funcionalidades como:
- **Streams en Tiempo Real:** Transmisión de partidas en vivo con comentarios profesionales.
- **Interacción con Fans:** Chats en vivo y encuestas en tiempo real para la audiencia.
- **Estadísticas Dinámicas:** Datos de las partidas mostrados en tiempo real.

### **Estadísticas Operativas:**
- **Eventos diarios transmitidos:** 500.
- **Usuarios activos simultáneos en horas pico:** 1 millón.
- **Tasa de aumento anual de usuarios:** 20%.
- **Tiempo de retraso aceptable en streams:** <2 segundos.
- **Chats enviados durante torneos:** 100 millones diarios.

---

## **Procesos Actuales**

#### **1. Transmisión de Video**
Los torneos son transmitidos desde múltiples servidores, que capturan las partidas en vivo y las distribuyen a los usuarios:
1. La señal de video es capturada por los organizadores y enviada al servidor principal.
2. Los servidores realizan la codificación y distribución a los usuarios finales.

**Problemas Identificados:**
- Los streams sufren retrasos significativos durante los eventos masivos.
- La calidad de video se reduce automáticamente en horas pico debido a la saturación del sistema.

> **Caso Real:**  
> Durante la final de un torneo internacional, los espectadores reportaron retrasos de hasta 10 segundos en la transmisión, arruinando la experiencia en tiempo real.

---

#### **2. Gestión de Chats**
La funcionalidad de chat permite a los espectadores interactuar en tiempo real:
1. Los mensajes enviados se procesan en un único servidor central.
2. El servidor redistribuye los mensajes a todos los usuarios conectados al stream.

**Problemas Identificados:**
- Los chats presentan retrasos de hasta 5 segundos durante los eventos principales.
- Algunos mensajes se pierden debido a la sobrecarga del sistema.

> **Caso Real:**  
> Durante un torneo, los espectadores se quejaron de que los chats aparecían fuera de orden o no se mostraban en absoluto, lo que generó una experiencia frustrante.

---

#### **3. Estadísticas en Tiempo Real**
StreamArena muestra datos como el puntaje, las estadísticas de jugadores y eventos destacados durante las partidas:
1. Los datos son capturados desde las plataformas de juego y procesados en el servidor central.
2. Las estadísticas se actualizan en el overlay del stream cada 5 segundos.

**Problemas Identificados:**
- Las estadísticas a menudo se retrasan respecto al juego en vivo.
- Los datos incompletos o erróneos afectan la precisión de las actualizaciones.

> **Caso Real:**  
> En una partida clave, las estadísticas mostraron un puntaje incorrecto durante varios minutos, causando confusión entre los espectadores.

---

#### **4. Alertas y Notificaciones**
StreamArena envía notificaciones para:
- Informar a los usuarios sobre torneos en curso.
- Alertar sobre cambios en horarios o equipos.

**Problemas Identificados:**
- Las notificaciones a menudo se retrasan o no llegan a los usuarios durante eventos masivos.
- No hay priorización entre notificaciones críticas y generales.

> **Caso Real:**  
> Durante un torneo regional, las notificaciones de inicio llegaron con 15 minutos de retraso, resultando en una pérdida significativa de espectadores.

---

## **Estructura del Sistema Actual**

### **Arquitectura Monolítica**
StreamArena opera con un sistema monolítico que integra todas las funcionalidades, desde la captura de video hasta la interacción de los usuarios.

#### **Lenguaje y Herramientas:**
- **Lenguaje:** JavaScript (Node.js).
- **Base de Datos:** MongoDB para almacenar mensajes de chat, estadísticas y configuraciones de eventos.
- **Transmisión de Video:** Codificación HLS (HTTP Live Streaming) gestionada por servidores centralizados.

#### **Componentes Clave:**
1. **Servidor de Transmisión:** Maneja la captura y distribución de video.
2. **Servidor de Mensajes:** Procesa los chats en tiempo real.
3. **Módulo de Estadísticas:** Calcula y actualiza las estadísticas dinámicas.
4. **Módulo de Notificaciones:** Envía alertas a los usuarios registrados.

---

### **Narrativa desde los Actores**

- **CEO:**  
  “Nuestra plataforma está en riesgo. Si seguimos perdiendo usuarios debido a retrasos y caídas durante los eventos importantes, nuestros patrocinadores también se irán.”

- **Gerente de Tecnología:**  
  “El monolito no soporta el tráfico actual. Necesitamos rediseñar todo para manejar cargas masivas sin comprometer el tiempo real.”

- **Espectadores:**  
  - *"El retraso en los streams y chats me quita la emoción del momento."*  
  - *"Las estadísticas están mal sincronizadas y no reflejan lo que ocurre en el juego."*

- **Organizadores de Torneos:**  
  - *"Las fallas en la transmisión afectan la confianza de nuestros patrocinadores y espectadores."*  
  - *"Necesitamos estadísticas precisas para los comentaristas en tiempo real."*

---

## **Restricciones y Retos**

- **Escalabilidad:**  
  La plataforma debe manejar eventos masivos con 1 millón de usuarios simultáneos sin afectar el tiempo de respuesta.
- **Tiempo Real:**  
  La latencia aceptable para streams y estadísticas es <2 segundos.
- **Presupuesto:**  
  $500,000 USD para rediseñar la infraestructura.
- **Tiempo:**  
  18 meses para implementar una solución completa.

---

## **Métricas Clave**

- **Usuarios activos simultáneos en horas pico:** 1 millón.
- **Eventos diarios transmitidos:** 500.
- **Chats enviados durante torneos:** 100 millones diarios.
- **Tasa de errores en estadísticas:** 5% de las actualizaciones.
- **Retrasos en notificaciones críticas:** 15 minutos en eventos principales.
- **Tiempo de retraso aceptable en streams:** <2 segundos.

---
