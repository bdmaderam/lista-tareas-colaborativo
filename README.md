Descripción del Proyecto
Una aplicación web de lista de tareas desarrollada colaborativamente entre dos personas, implementando metodologías ágiles con GitHub Projects y desplegada en AWS EC2.

Características principales:

Agregar nuevas tareas

Marcar tareas como completadas

Eliminar tareas

Filtrar tareas (Todas, Pendientes, Completadas)

Persistencia de datos en Local Storage

Diseño responsive

Interfaz moderna y intuitiva

Tecnologías Utilizadas
Frontend: HTML5, CSS3, JavaScript (ES6+)

Control de Versiones: Git & GitHub

Gestión de Proyecto: GitHub Projects

Hosting: AWS EC2 con Nginx

Sistema Operativo: Amazon Linux 2023

Metodología de Trabajo Colaborativo
GitHub Projects Implementation
Configuración del Project Board:
text
Backlog -> To Do -> In Progress -> Review -> Done
Flujo de trabajo implementado:
Creación de Issues con templates específicos

Asignación de tareas por áreas (Frontend/Backend)

Branch protection rules con revisión obligatoria

Pull Requests con revisión de código

Merge después de aprobación

Issues trabajados:
#1 - Estructura HTML básica (Frontend)

#2 - Lógica JavaScript principal (Backend)

#3 - Estilos CSS y responsive design (Frontend)

#4 - Sistema de filtros y contadores (Backend)

#5 - Persistencia con Local Storage (Backend)

División de responsabilidades:
Compañero A (Frontend): HTML, CSS, diseño responsive

Compañero B (Backend): JavaScript, funcionalidades, lógica de negocio

Proceso de Desarrollo
Fase 1: Planificación & Setup
Definición de requisitos

Creación del repositorio GitHub

Configuración de GitHub Projects

Establecimiento de branch protection rules

Configuración de CODEOWNERS

Fase 2: Desarrollo Iterativo
Implementación por features en ramas separadas

Revisión de código mediante Pull Requests

Testing continuo y corrección de bugs

Comunicación constante entre el equipo

Fase 3: Deployment & CI/CD
Configuración del servidor EC2

Instalación y configuración de Nginx

Deployment automatizado mediante scripts

Verificación y testing en producción

Deployment en AWS EC2
Configuración del Servidor:
Instancia: t2.micro (Free Tier)

SO: Amazon Linux 2023

Servidor Web: Nginx

Puertos: HTTP (80) abierto al público

Proceso de Deployment:
bash
# 1. Configuración inicial del servidor
sudo dnf update -y
sudo dnf install nginx git -y
sudo systemctl start nginx
sudo systemctl enable nginx

# 2. Clonación del proyecto
cd /usr/share/nginx/html
sudo git clone https://github.com/[usuario]/lista-tareas-colaborativo.git .

# 3. Configuración de permisos
sudo chown -R nginx:nginx /usr/share/nginx/html/
sudo chmod -R 755 /usr/share/nginx/html/

# 4. Reinicio del servicio
sudo systemctl restart nginx
Problemas y Soluciones Encontradas
1. Configuración de GitHub Projects
Problema: No se podían asignar reviewers inicialmente
Solución: El colaborador necesitaba aceptar la invitación al repositorio primero

2. Ramas idénticas en PR
Problema: "There isn't anything to compare" al crear PR
Solución: Asegurarse de hacer commits antes de crear el PR

3. Deployment en EC2 - Directorio incorrecto
Problema: Se mostraba página por defecto de Nginx
Solución: Los archivos estaban en subcarpeta, se movieron a la raíz:

bash
sudo mv lista-tareas-colaborativo/* .
sudo mv lista-tareas-colaborativo/.* . 2>/dev/null || true
4. Permisos de archivos
Problema: Nginx no podía servir los archivos
Solución: Configurar permisos correctos:

bash
sudo chown -R nginx:nginx /usr/share/nginx/html/
Lecciones Aprendidas
Trabajo Colaborativo:
La comunicación constante es esencial

Las revisiones de código mejoran la calidad

GitHub Projects facilita el seguimiento del progreso

Technical:
La protección de ramas previene errores

Los PR pequeños son más fáciles de revisar

La automatización de deployment ahorra tiempo

DevOps:
La configuración inicial de servidores requiere atención a detalles

Los scripts de deployment son indispensables

El monitoreo continuo es crucial

Características de la Aplicación
Funcionalidades Implementadas:
Agregar tareas con validación de input vacío

Marcar como completadas con efecto visual

Eliminar tareas individualmente

Filtros dinámicos (Todas/Pendientes/Completadas)

Contador en tiempo real de tareas pendientes

Persistencia automática en Local Storage

Diseño responsive para móviles y desktop

Interfaz de Usuario:
Diseño moderno con gradientes y sombras

Animaciones suaves en interacciones

Feedback visual inmediato

Iconos intuitivos

Paleta de colores consistente

Scripts de Mantenimiento
Actualización automática:
bash
#!/bin/bash
cd /usr/share/nginx/html
sudo git pull origin main
sudo systemctl restart nginx
echo "Aplicación actualizada"
Backup de datos:
bash
#!/bin/bash
cp /usr/share/nginx/html/data.json /home/ec2-user/backup/
echo "Backup completado"
Acceso a la Aplicación
URL de producción: http://[IP_PUBLICA_EC2]

Métricas de Éxito
100% de issues completados

0 conflictos de merge

Todas las revisiones de código aprobadas

Despliegue exitoso en producción

Tiempo de desarrollo: 1 semana

Contribuidores
[Nombre Compañero A] - Frontend & Design

[Nombre Compañero B] - Backend & Deployment

Próximas Mejoras
Implementar edición in-place de tareas

Añadir categorías y etiquetas

Implementar modo oscuro

Añadir sincronización con cloud

Implementar PWA capabilities

Fecha de finalización: Octubre 2023
Estado del proyecto: Completado y en producción
Calificación del equipo: Excelente colaboración y aprendizaje
