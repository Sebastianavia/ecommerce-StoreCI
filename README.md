# Plataforma de Comercio Electrónico de InnovaRetail Corp. con Sistema de Gestión Avanzado

 
 ---

### Descripción del Proyecto


InnovaRetail Corp. está lanzando una avanzada plataforma de comercio electrónico diseñada para proporcionar una experiencia de usuario excepcional y optimizar la gestión interna. La plataforma contará con una tienda en línea integrada con un completo Sistema de Gestión de Contenidos (CMS) para gestionar eficientemente múltiples vendedores o tiendas, productos, categorías, imágenes, filtros y anuncios. Este proyecto demostrará prácticas ejemplares de DevOps, incluyendo la automatización de infraestructuras y procesos, estrategias de branching efectivas, gestión segura de secretos y una robusta arquitectura de microservicios.

### Integración Continua (CI) con GitHub Actions

Para garantizar que el proceso de desarrollo sea eficiente y confiable, implementaremos un pipeline de Integración Continua (CI) utilizando GitHub Actions. Este pipeline automatizará los procesos de prueba e integración, permitiendo la entrega rápida y confiable de nuevas funcionalidades y actualizaciones.

### Detalles del Pipeline de CI

- Pruebas Automatizadas: Cada commit desencadenará una serie de pruebas automatizadas para asegurar la calidad y funcionalidad del código.
 
- Integración: Las pruebas exitosas fusionarán los cambios en la rama principal, manteniendo una base de código estable.
  

### Canal de Notificaciones

Estableceremos un canal de notificaciones (Slack) para recibir actualizaciones en tiempo real sobre el estado del pipeline de CI. Esto incluirá:

Notificaciones de éxito o fallo en las compilaciones.
Alertas sobre cualquier problema detectado durante los procesos automatizados.


---


Nuestro pipeline principal llamado build-acr.yml, define un flujo de trabajo automatizado que se ejecuta después de que otro flujo de trabajo específico ha terminado (el cual se encarga de notificar que la actualizació ha iniciado). Su propósito es construir y desplegar una aplicación en un contenedor utilizando GitHub Actions y Azure. Aquí está una explicación general de lo que hace este flujo de trabajo:

### Activación del flujo de trabajo:

Se activa cuando otro flujo de trabajo llamado "cicd-workflow with slack integration" se ha completado.

### Configuración del entorno:

Define un trabajo llamado build que se ejecuta en una máquina virtual con Ubuntu.

### Pasos del trabajo:

Chequeo del código: Descarga el código fuente del repositorio.

Inicio de sesión en Azure Container Registry: Se autentica en el registro de contenedores de Azure usando credenciales almacenadas en secretos.

Construcción y envío de la imagen Docker: Construye una imagen Docker del proyecto ubicado en ./e-commerce-admin y la sube al registro de contenedores de Azure con una etiqueta basada en el número de ejecución del flujo de trabajo.

Cerrar sesión en Azure Container Registry: Cierra la sesión del registro de contenedores de Azure para mayor seguridad.

Chequeo del repositorio de despliegue: Descarga otro repositorio específico para despliegues (Deployment_ToDo_App).

Actualización del archivo de configuración: Modifica un archivo values.yaml en el repositorio de despliegue para usar la nueva etiqueta de imagen Docker, luego realiza un commit y empuja estos cambios de vuelta al repositorio.

Este flujo de trabajo automatiza el proceso de construcción, etiquetado y despliegue de una aplicación basada en contenedores, asegurando que siempre se utilice la versión más reciente de la imagen Docker en los despliegues.





