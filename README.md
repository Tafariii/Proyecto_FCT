# Proyecto_FCT 
Dacio Alberto Alcalde Leal
## Implementacion Active Directory en un NAS
![Windows active directory](https://thehackerway.files.wordpress.com/2021/10/ad-1.1.png?w=816&h=9999)
### Introduccion del proyecto
En este proyecto se documenta la instalacion, configuracion y uso de un servidor NAS, asi como el despligue de un directorio activo en el mismo.
### Objetivos del proyecto
- Aprender a instalar un servidor NAS
- Aprender a hacer uso de los diferentes RAIDS
- Lograr una mayor compresion del funcionamiento de un servidor NAS
- Aprender a implementar un directorio activo en un servidor NAS
### Medios que se van a utilizar
* 1 Maquina virtual con un NAS, en el cual se instalara el active directory
* 1 Maquinas virtual con Windows 10 que serviran como cliente
* 1 Maquina virtual con un Linux que utilizaremos como atacante
### Fundamentos teóricos y conceptos previos
#### ¿Que es Active Directory?
Active Directory (AD) es una base de datos y un conjunto de servicios que conectan a los usuarios con los recursos de red que necesitan para realizar su trabajo.
La base de datos (o el directorio) contiene información crítica sobre su entorno, incluidos los usuarios y los equipos que hay y quién puede hacer qué. Por ejemplo, la base de datos puede contener una lista de 100 cuentas de usuario con detalles como el puesto de trabajo, el número de teléfono y la contraseña de cada persona. También registrará sus permisos.
#### ¿Cuales son los beneficios de usar Active Directory?
- Configuración y gestión totalmente centralizada de políticas, permisos, etc para todos los usuarios, equipos, grupos y aplicaciones.
- Mayor protección ante pérdidas de datos
- Escalabilidad flexible del dominio.
- Reducción de costes gracias a la centralización de recursos.
