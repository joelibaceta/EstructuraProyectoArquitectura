# **Caso de Estudio: Escalabilidad de MedTrack**

MedTrack es una plataforma tecnológica utilizada por hospitales y clínicas para gestionar el seguimiento de pacientes con enfermedades crónicas. A pesar de su impacto positivo inicial, la plataforma enfrenta graves problemas de escalabilidad y coordinación, limitando su capacidad de expansión a nuevas instituciones y afectando la calidad del servicio.

---

## **Contexto Operativo**

MedTrack opera en **20 hospitales** y **50 clínicas privadas**, conectando a más de **1,000 médicos** y **250,000 pacientes crónicos**. Su objetivo principal es centralizar el historial médico, facilitar recordatorios de medicación y coordinar citas de seguimiento para pacientes con enfermedades como diabetes, hipertensión y asma.

### **Estadísticas Operativas**
- **Pacientes registrados:** 250,000 (crecimiento mensual del 5%).
- **Alertas de medicación enviadas diariamente:** 15,000.
- **Citas gestionadas mensualmente:** 50,000.
- **Usuarios activos simultáneos en horas pico:** 3,000.
- **Tiempo promedio de respuesta en la aplicación móvil:** 6 segundos (debería ser <2 segundos).
- **Errores en la sincronización de citas:** 10% de las reservas.

---

### **Procesos Actuales**

#### **1. Registro de Pacientes**
Cuando un nuevo paciente se registra, su historial médico debe ser importado desde sistemas existentes en el hospital:
1. Un asistente médico introduce los datos básicos del paciente en MedTrack.
2. Un script extrae el historial médico del sistema del hospital y lo almacena en la base de datos central.
3. El paciente recibe un correo electrónico de bienvenida con instrucciones para descargar la app móvil.

**Problemas Identificados:**
- Los sistemas de origen en los hospitales varían, lo que genera inconsistencias en la importación de datos.
- El proceso completo puede tomar hasta 24 horas, retrasando el acceso del paciente a la plataforma.

> **Caso Real:**  
> En un hospital de Lima, un paciente con hipertensión grave tuvo que esperar dos días para recibir su primera alerta de medicación porque su historial no fue importado correctamente.

---

#### **2. Alertas de Medicación**
MedTrack envía recordatorios diarios a los pacientes para que tomen sus medicamentos:
1. Cada alerta se programa según la receta registrada por el médico.
2. Los recordatorios se envían a través de notificaciones push, correos electrónicos y SMS.

**Problemas Identificados:**
- Las notificaciones push suelen retrasarse en horas pico debido a la saturación del sistema.
- No hay un mecanismo para confirmar si el paciente recibió o ignoró la alerta.

> **Caso Real:**  
> Una paciente diabética en Cusco no recibió alertas durante tres días consecutivos debido a un error en el servidor, lo que resultó en una hospitalización de emergencia.

---

#### **3. Gestión de Citas**
Los pacientes pueden programar citas de seguimiento a través de la app móvil:
1. El paciente selecciona un médico y un horario disponible.
2. La cita se registra en la base de datos de MedTrack y se sincroniza con el sistema del hospital.

**Problemas Identificados:**
- El sistema no actualiza los horarios en tiempo real, lo que genera conflictos cuando dos pacientes intentan reservar el mismo horario.
- Las citas canceladas no siempre se reflejan en la app móvil.

> **Caso Real:**  
> Un médico reportó que dos pacientes llegaron al mismo horario porque ambos habían recibido confirmación de la cita.

---

#### **4. Reportes para Hospitales**
MedTrack genera reportes mensuales con estadísticas clave para cada hospital, incluyendo:
- Número de pacientes registrados.
- Tasa de cumplimiento de medicación.
- Citas programadas y atendidas.

**Problemas Identificados:**
- La generación de reportes es manual y toma hasta 48 horas.
- Los datos a menudo contienen inconsistencias debido a fallos en la sincronización.

> **Caso Real:**  
> Un hospital en Trujillo recibió un reporte con un error de cálculo que mostraba un cumplimiento del 90% en la medicación, cuando en realidad era del 70%.

---

## **Estructura del Sistema Actual**

### **Arquitectura Monolítica**
El sistema está diseñado como un monolito centralizado, donde todas las operaciones (registro de pacientes, alertas, gestión de citas y generación de reportes) están acopladas en un único servidor.

#### **Lenguaje y Herramientas**
- **Lenguaje:** PHP 5.6 (obsoleto desde 2019).
- **Framework:** Laravel 5.1 (sin soporte oficial).
- **Base de Datos:** MySQL 5.7, alojada en un único servidor.

#### **Componentes Clave**
1. **Módulo de Registro:** Maneja la importación de datos de pacientes desde sistemas hospitalarios.
2. **Módulo de Notificaciones:** Envía alertas de medicación y citas.
3. **Módulo de Citas:** Gestiona la reserva y cancelación de citas.
4. **Módulo de Reportes:** Genera estadísticas mensuales para hospitales.

---

### **Narrativa desde los Actores**

- **CEO:**  
  “MedTrack está creciendo, pero nuestro sistema no está listo para escalar. Si no resolvemos esto, perderemos la confianza de los hospitales.”

- **Gerente de Tecnología:**  
  “El monolito actual no soporta el volumen de operaciones. Necesitamos un sistema distribuido que permita manejar tareas críticas de forma independiente.”

- **Médicos:**  
  - *"Los conflictos en las citas generan frustración tanto para los pacientes como para nosotros."*  
  - *"Necesitamos estadísticas más precisas para medir el impacto del tratamiento."*

- **Pacientes:**  
  - *"Las alertas son útiles, pero a veces no las recibo a tiempo."*  
  - *"Tuve que esperar días para acceder a la plataforma después de registrarme."*

---

## **Restricciones y Retos**

- **Tecnología:**  
  El sistema debe integrarse con múltiples plataformas hospitalarias existentes, cada una con formatos de datos diferentes.
- **Presupuesto:**  
  $200,000 USD para rediseñar la arquitectura y mejorar la infraestructura.
- **Tiempo:**  
  12 meses para implementar un MVP funcional.

---

## **Métricas Clave**

- **Pacientes registrados:** 250,000 (crecimiento mensual del 5%).
- **Alertas enviadas diariamente:** 15,000.
- **Citas gestionadas mensualmente:** 50,000.
- **Usuarios simultáneos en horas pico:** 3,000.
- **Errores en citas:** 10% de las reservas.
- **Tasa de cumplimiento de medicación:** 70% (objetivo: 90%).

---

