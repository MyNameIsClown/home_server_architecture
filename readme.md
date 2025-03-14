# Servidor Multipropósito Casero

Este proyecto tiene como objetivo configurar un servidor multipropósito en casa utilizando **Ubuntu Server** y **Docker**. El servidor está diseñado para alojar tanto servicios públicos como privados mediante contenedores Docker, asegurando la seguridad y eficiencia a través de diversas herramientas y buenas prácticas.

## Arquitectura General

La arquitectura del servidor utiliza principalmente contenedores Docker para aislar los diferentes servicios y garantizar una gestión sencilla y segura. Las conexiones se gestionan mediante un proxy inverso (**Traefik**), autenticación robusta con **Authelia (TOTP)** y un portal de administración centralizado con **Hestia**.

La administración y el acceso remoto seguro al servidor se realizan mediante una VPN basada en **WireGuard**.

## Componentes Principales

### Core
- **Docker, Docker Compose y Portainer**: Gestión y monitoreo sencillo de contenedores.
- **WireGuard**: VPN segura para acceso remoto.
- **Authelia**: Middleware de autenticación de doble factor (TOTP).
- **Traefik**: Proxy inverso para gestionar las solicitudes entrantes.
- **Hestia**: Portal web centralizado para administración del servidor.
- **Dynamic DNS (DDNS)**: Manejo automatizado de DNS dinámicos para servicios.

### Servicios Públicos
Servicios accesibles públicamente sin necesidad de VPN:
- Páginas web estáticas (servidas con contenedor Nginx)
- Aplicaciones web complejas (ejemplo: Django, Node.js)
- Servidor de Minecraft Vanilla
- Servidor de Minecraft Forge con mods

### Servicios Privados
Servicios protegidos con autenticación robusta (mínimo Authelia + TOTP):
- **NextCloud**: Almacenamiento privado en la nube.
- **Plex**: Servidor multimedia.
- **Navidrome**: Servidor privado de música.

Todos estos servicios privados requieren autenticación adicional a través de Authelia.

### Seguridad
- Autenticación SSH protegida con TOTP
- Implementación de **Fail2Ban** para prevención de accesos no autorizados
- Estrategias de backup regulares con herramientas como **rsync** y configuraciones RAID.

## Esquema de Nombres de Dominio

- Servidor base: `miservidor.com`
- Aplicaciones core: `{aplicacion}.miservidor.com` (Ejemplo: `portainer.miservidor.com`)
- Servicios públicos: dominios singulares (Ejemplo: `mipaginaweb.com`, `miserverdeminecraft.mc`)
- Servicios privados: `{servicio}.miservidor.com` (Ejemplo: `plex.miservidor.com`)

## Guía del Proyecto
El proyecto está organizado para guiarte paso a paso a través de capítulos específicos y breves:

- **Capítulos Básicos y Seguridad**: Instalación y configuración inicial.
- **Red y DNS**: Configuración y gestión de dominios.
- **Servicios Core**: Instalación del núcleo de servicios administrativos.
- **Servicios Públicos y Privados**: Despliegue detallado de cada servicio.
- **Mantenimiento y Monitoreo**: Estrategias de respaldo, monitoreo y mantenimiento regular.

## Requisitos
- Sistema operativo: Ubuntu Server
- Docker y Docker Compose
- Conocimientos básicos en administración Linux y redes (se proporcionan explicaciones para principiantes)

## Contribuciones
¡Las contribuciones son bienvenidas! Realiza un fork del proyecto y envía tus pull requests.

## Licencia
Este proyecto está bajo licencia MIT.
