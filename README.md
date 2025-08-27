# Tarea-28-08-2025
# Sistema de Validación de Entrada y Notificaciones (SOLID)

Este proyecto demuestra la aplicación de principios **SOLID** en Python a través de dos componentes principales:

1. **Intake & Validation**: lectura de una cadena `edad,nombre`, parseo, validación y decisión.
2. **Sistema de Notificaciones**: envío de mensajes por **Email**, **SMS** y **Push** mediante abstracciones e inversión de dependencias.

> **Objetivo didáctico**: arquitectura limpia, fácil de extender y de probar, con responsabilidades separadas.

---

## 🗂️ Contenido del repositorio
─ README.md # Este documento
─ Clase_codigo.py # Script ejecutable (CLI) con Intake & Validation; integra notificaciones
─ Clase_codigo.ipynb # Notebook Jupyter con ejemplos explicados y pruebas manuales

## 🧱 Arquitectura (resumen)

- **Dominio / Validación**
  - `UserInput` (dataclass): entrada validada (edad:int, name:str).
  - `CSVParser`: parsea `"edad,nombre"` → `(int,str)`, maneja `ParseError`.
  - `BasicValidator`: reglas de negocio; lanza `ValidationError`.
  - `DecisionPolicy`: punto de extensión de reglas (por defecto, acepta tras validación).
  - `InputProcessor`: orquesta parseo → validación → decisión (depende de **Protocol**, no de concretos).

- **Notificaciones**
  - `NotificationSender` (ABC): contrato.
  - `EmailNotification`, `SMSNotification`, `PushNotification`: una responsabilidad cada una (SRP).
  - `NotificationService`: valida y envía.
  - `SenderFactory`: crea el canal por nombre; permite registrar nuevos (OCP).

> **SOLID aplicado**:  
> - **SRP**: cada clase hace solo una cosa.  
> - **OCP**: agregue canales o políticas sin modificar servicios.  
> - **DIP**: los servicios dependen de **interfaces** (Protocol/ABC), no de implementaciones.

---

## ✅ Requisitos

- **Python 3.10+** (recomendado 3.12).
- Sin dependencias externas para el script base.  
- Para el notebook: **Jupyter**.

# Instalar jupyter si no lo tiene
- pip install notebook

#Abrir el Colab
- ejecutar el libro
