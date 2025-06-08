# 🛡️ Auditorías en Active Directory con Windows Server

Este proyecto demuestra cómo implementar políticas de auditoría dentro de un entorno de Active Directory para monitorizar eventos críticos como inicios de sesión, cambios de cuenta, accesos a objetos y uso de permisos.

🔧 Trabajo realizado como parte de mi formación en el Ciclo Superior de Administración de Sistemas Informáticos en Red (ASIR).

---

## 🎯 Objetivo

Aplicar auditorías por unidad organizativa (UO) usando directivas de grupo (GPO) específicas, permitiendo registrar eventos relevantes para el control de seguridad y la trazabilidad en el dominio.

---

## 🧩 Auditorías por UO

| Unidad Organizativa | Auditorías aplicadas |
|---------------------|----------------------|
| **Técnicos**        | Inicios de sesión, cambios de cuenta, cambios en políticas |
| **Marketing**       | Inicios de sesión, accesos a objetos, uso de permisos, eventos de sistema |
| **Administración**  | Inicios de sesión, accesos a objetos, uso de permisos |
| **Clientes**        | Inicios de sesión, accesos a objetos, seguimiento de procesos, cierres de sesión |

---

## 🖥️ Herramientas utilizadas

- Windows Server 2019
- Active Directory
- Group Policy Management
- Event Viewer (`eventvwr.msc`)

---

## 🛠️ Proceso resumido

1. Crear políticas de grupo nuevas para cada UO.
2. Habilitar auditorías específicas en cada una según su perfil.
3. Aplicar la GPO a la UO correspondiente.
4. Generar eventos (ej: cambio de contraseña, acceso a recurso).
5. Visualizar registros en el Visor de eventos.

---

## 🖼️ Capturas de configuración y resultados

### 📌 Configuración de GPO
<img src="img/gpo-configuracion.png" width="600">

### 👥 Usuarios en Active Directory
<img src="img/ad-grupos.png" width="600">

### 📋 Evento registrado tras cambio de contraseña
<img src="img/visor-eventos.png" width="600">

---

## 📁 Estructura del repositorio


