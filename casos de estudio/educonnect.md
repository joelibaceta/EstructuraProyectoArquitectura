# **Caso de Estudio: Transformación Digital de EduConnect**

EduConnect es una plataforma de gestión educativa que conecta a estudiantes, profesores, y administradores escolares en tiempo real. Su propósito inicial fue centralizar la gestión académica y administrativa, pero con el aumento del número de usuarios y funciones, el sistema actual se ha vuelto insostenible, afectando la experiencia de los usuarios y limitando la capacidad de expansión.

---

## **Contexto Operativo**

EduConnect opera en **500 escuelas** y **200 institutos técnicos** a nivel nacional, con más de **1 millón de estudiantes activos** y **50,000 profesores registrados**. La plataforma permite gestionar tareas como la inscripción, programación de clases, evaluaciones, calificaciones y notificaciones entre estudiantes, padres y profesores.

### **Estadísticas Operativas:**
- **Usuarios activos mensuales:** 1 millón (crecimiento del 10% anual).
- **Calificaciones registradas mensualmente:** 5 millones.
- **Notificaciones enviadas diariamente:** 1 millón.
- **Usuarios simultáneos en horas pico:** 20,000.
- **Tiempo promedio de respuesta en la app web:** 7 segundos (debería ser <3 segundos).

---

## **Procesos Actuales**

#### **1. Inscripción de Estudiantes**
Cada ciclo escolar, las escuelas y los institutos deben registrar a todos los estudiantes en EduConnect:
1. Los administradores escolares cargan archivos CSV con los datos de los estudiantes.
2. El sistema valida los datos y registra a los estudiantes en la base de datos central.
3. Se generan credenciales para los nuevos estudiantes y se envían correos electrónicos de bienvenida.

**Problemas Identificados:**
- El sistema no escala adecuadamente durante los periodos pico de inscripción, generando fallos frecuentes.
- La validación de datos es lenta y bloquea otros procesos en el sistema.

> **Caso Real:**  
> En el inicio del ciclo escolar 2024, una escuela con 5,000 estudiantes intentó cargar sus datos. El proceso falló varias veces debido a la sobrecarga del servidor, causando retrasos en el inicio de clases.

---

#### **2. Gestión de Evaluaciones**
Los profesores utilizan EduConnect para publicar evaluaciones y registrar calificaciones:
1. Los profesores suben cuestionarios y asignan fechas de disponibilidad.
2. Los estudiantes acceden a las evaluaciones a través de la app.
3. Las respuestas se registran y procesan automáticamente para generar las calificaciones.

**Problemas Identificados:**
- Durante los periodos de evaluaciones masivas, el sistema no soporta la carga de miles de estudiantes accediendo simultáneamente.
- Los retrasos en el procesamiento generan frustración entre los estudiantes y los profesores.

> **Caso Real:**  
> En una evaluación final de matemáticas, 2,000 estudiantes intentaron acceder simultáneamente. El sistema colapsó y las calificaciones se retrasaron dos semanas.

---

#### **3. Notificaciones a Usuarios**
EduConnect envía notificaciones automáticas sobre eventos como cambios en horarios, calificaciones publicadas, o recordatorios de tareas:
1. Las notificaciones se generan a partir de eventos en el sistema.
2. Se envían a través de correos electrónicos, notificaciones push y SMS.

**Problemas Identificados:**
- Las notificaciones no se entregan en tiempo real durante las horas pico.
- Fallos en la generación de eventos bloquean la entrega de notificaciones críticas.

> **Caso Real:**  
> En un instituto técnico, los estudiantes no recibieron notificaciones sobre un cambio de horario, lo que resultó en aulas vacías y profesores esperando.

---

#### **4. Reportes Académicos**
Los administradores escolares utilizan EduConnect para generar reportes sobre:
- Desempeño académico de los estudiantes.
- Asistencia mensual.
- Actividad de los profesores.

**Problemas Identificados:**
- La generación de reportes es manual y requiere largos tiempos de procesamiento.
- Los reportes a menudo contienen datos incompletos o inconsistentes.

> **Caso Real:**  
> En una escuela de Lima, los administradores reportaron que el sistema generó un informe con un error en las estadísticas de asistencia, lo que afectó la planificación de recursos.

---

## **Estructura del Sistema Actual**

### **Arquitectura Monolítica**
EduConnect utiliza un sistema monolítico, donde todas las funcionalidades están acopladas en un único servidor centralizado.

#### **Lenguaje y Herramientas:**
- **Lenguaje:** Java 8 (sin soporte oficial desde 2020).
- **Framework:** Spring Framework 4.x.
- **Base de Datos:** PostgreSQL 9.5, alojada en un único servidor.

#### **Componentes Clave:**
1. **Módulo de Inscripciones:** Maneja el registro de estudiantes y validación de datos.
2. **Módulo de Evaluaciones:** Publica cuestionarios y procesa respuestas.
3. **Módulo de Notificaciones:** Genera y envía notificaciones a los usuarios.
4. **Módulo de Reportes:** Genera estadísticas para administradores escolares.

---

### **Narrativa desde los Actores**

- **CEO:**  
  “EduConnect está creciendo, pero nuestro sistema no está preparado para manejar este volumen. Si no escalamos adecuadamente, perderemos clientes.”

- **Gerente de Tecnología:**  
  “El monolito es el mayor obstáculo. Necesitamos dividir las funcionalidades críticas en microservicios independientes para garantizar la disponibilidad.”

- **Administradores Escolares:**  
  - *"Los retrasos en los reportes afectan nuestras decisiones académicas y administrativas."*  
  - *"El sistema falla cada inicio de ciclo escolar, lo que genera caos entre los estudiantes y profesores."*

- **Profesores:**  
  - *"Las evaluaciones tardan demasiado en procesarse, lo que nos impide dar retroalimentación a tiempo."*  
  - *"Las notificaciones no llegan a tiempo y los estudiantes no cumplen con las fechas."*

- **Estudiantes:**  
  - *"El sistema es lento durante las evaluaciones. A veces ni siquiera puedo acceder a mis calificaciones."*  
  - *"Es frustrante no recibir notificaciones a tiempo sobre cambios importantes."*

---

## **Restricciones y Retos**

- **Tecnología:**  
  El sistema debe ser capaz de manejar picos de tráfico durante periodos clave como inscripciones y evaluaciones.
- **Presupuesto:**  
  $250,000 USD para rediseñar la arquitectura y mejorar la infraestructura.
- **Tiempo:**  
  12 meses para implementar un MVP funcional.

---

## **Métricas Clave**

- **Usuarios activos mensuales:** 1 millón.
- **Calificaciones registradas mensualmente:** 5 millones.
- **Notificaciones enviadas diariamente:** 1 millón.
- **Errores en procesamiento de evaluaciones:** 5% de las pruebas.
- **Tiempo promedio de respuesta:** 7 segundos (objetivo: <3 segundos).
- **Errores en reportes:** 10% de los casos.

---
