# Implementacion Active Directory en un NAS
## Tabla de contenidos
1. [Introducción](https://github.com/Tafariii/Proyecto_FCT#introduccion-del-proyecto)
2. [Objetivos del proyecto](https://github.com/Tafariii/Proyecto_FCT#objetivos-del-proyecto)
3. [Fundamentos teóricos y conceptos previos](https://github.com/Tafariii/Proyecto_FCT#fundamentos-te%C3%B3ricos-y-conceptos-previos)
    - [Active Directory](https://github.com/Tafariii/Proyecto_FCT#active-directory)
    - [NAS](https://github.com/Tafariii/Proyecto_FCT#servidor-nas)
    - [RAID](https://github.com/Tafariii/Proyecto_FCT#raid)
5. [Desarrollo del proyecto](https://github.com/Tafariii/Proyecto_FCT#desarrollo-del-proyecto)
6. [Conclusión](https://github.com/Tafariii/Proyecto_FCT/blob/main/README.md#conclusion)
7. [Bibliografia](https://github.com/Tafariii/Proyecto_FCT#bibliograf%C3%ADa)

## Introduccion del proyecto
En este proyecto se documenta la instalacion, configuracion y uso de un servidor NAS, asi como el despliegue de un directorio activo en el mismo.
## Objetivos del proyecto
- Aprender a instalar un servidor NAS
- Aprender a hacer uso de los diferentes RAIDS
- Lograr una mayor compresion del funcionamiento de un servidor NAS
- Aprender a implementar un directorio activo en un servidor NAS
## Fundamentos teóricos y conceptos previos
### Active Directory
Active Directory (AD) es una base de datos y un conjunto de servicios que conectan a los usuarios con los recursos de red que necesitan para realizar su trabajo.
La base de datos (o el directorio) contiene información crítica sobre su entorno, incluidos los usuarios y los equipos que hay y quién puede hacer qué. Por ejemplo, la base de datos puede contener una lista de 100 cuentas de usuario con detalles como el puesto de trabajo, el número de teléfono y la contraseña de cada persona. También registrará sus permisos.

![Windows active directory](https://thehackerway.files.wordpress.com/2021/10/ad-1.1.png?w=816&h=9999)

#### ¿Cuales son los beneficios de usar Active Directory?
- Configuración y gestión totalmente centralizada de políticas, permisos, etc para todos los usuarios, equipos, grupos y aplicaciones.
- Mayor protección ante pérdidas de datos
- Escalabilidad flexible del dominio.
- Reducción de costes gracias a la centralización de recursos.
#### ¿Y las desventajas?
- **Active Directory puede ser muy costoso** dependiendo de cuántos sistemas administre Active Directory y qué tipo de volumen se requiera de Active Directory.
- **Active Directory requiere una conexión a Internet** siempre activa para que los usuarios de Active Directory puedan autenticar las contraseñas de Active Directory.
- **Active Directory tiene altos costos** de mantenimiento para administrar.
- **Active Directory puede causar problemas de rendimiento** cuando se usa con redes más grandes o más DC de los recomendados por Microsoft.
### Servidor NAS
Un servidor NAS es un dispositivo de almacenamiento conectado a la red. Su función es la de hacer copias de seguridad de los archivos que tú le indiques en la configuración, aunque también tiene muchas otras funcionalidades, es decir, a efectos prácticos la función principal de estos dispositivos es la de actuar como unidad de almacenamiento, haciendo las veces de disco duro externo o permitiéndote crear tu propio almacenamiento en la nube.
Hemos de tener en cuenta que un NAS cuenta con su propio sistema operativo el cual esta adaptado para funcionar durante todo el dia, y en temas de hardware se compone de su memoria RAM, su procesador y los disco duros que se pueden añadir en la ranuras expresamente diseñadas para ello.
Los servidores NAS tambien pueden ser usados para crear una red virtual privada(VPN) e incluso como servidor FTP resultando tremendamente útil para las empresas.

![NAS](https://www.zonagadget.com/wp-content/uploads/2008/04/rhd4_uxe2_0_1.jpg)
#### Beneficios de usar un servidor NAS
- **Crear un entorno propio para trabajar en la nube**.
- **Te permite acceder a la información en remoto**.
- **Sincroniza los archivos**.
- **Apto para copias de seguridad**.
#### Desventajas de usar un servidor NAS
- **Depende del caso puede conllevar un gran aporte de capital**.
- **El espacio fisico que el servidor puede ocupar**.
- **La fiabilidad de un servidor NAS** depende en gran medida del hardware utilizado, y pueden ser propensos a fallos si no se realiza un mantenimiento adecuado.
### RAID
RAID (Redundant Array of Independent Disks) es una tecnología que combina varios discos duros independientes para que funcionen como una unidad. Gracias a los diversos tipos de RAID, esta tecnología proporciona ventajas tales como aumentar la fiabilidad de datos, mejora del rendimiento de entrada/salida, elevación de la tolerancia a fallos, etc.
#### Tipos de RAID mas comunes 
- RAID 0

Un RAID 0 (también llamado conjunto dividido, volumen dividido, volumen seccionado) distribuye los datos equitativamente entre dos o más discos (usualmente se ocupa el mismo espacio en dos o más discos) sin información de paridad que proporcione redundancia. El RAID 0 se usa habitualmente para proporcionar un alto rendimiento de escritura ya que los datos se escriben en dos o más discos de forma paralela, aunque un mismo fichero solo está presente una vez en el conjunto.


![RAID0](https://user-images.githubusercontent.com/113986006/235619208-3a3e3973-5357-44ea-9c57-bd78c48a66cc.png)
- RAID 1

Un RAID 1 crea una copia exacta (o espejo) de un conjunto de datos en dos o más discos. Esto resulta útil cuando queremos tener más seguridad desaprovechando capacidad, ya que si perdemos un disco, tenemos el otro con la misma información. Un conjunto RAID 1 solo puede ser tan grande como el más pequeño de sus discos. 
Un RAID 1 clásico consiste en dos discos en espejo, lo que incrementa exponencialmente la fiabilidad respecto a un solo disco; es decir, la probabilidad de fallo del conjunto es igual al producto de las probabilidades de fallo de cada uno de los discos (pues para que el conjunto falle es necesario que lo hagan todos sus discos).


![RAID1](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Raid1.png/184px-Raid1.png)
- RAID 5

Un RAID 5 (también llamado distribuido con paridad) es una división de datos a nivel de bloques que distribuye la información de paridad entre todos los discos miembros del conjunto. El RAID 5 ha logrado popularidad gracias a su bajo coste de redundancia. Generalmente, el RAID 5 se implementa con soporte hardware para el cálculo de la paridad. RAID 5 necesitará un mínimo de 3 discos para ser implementado.


![RAID5](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Raid5.png/320px-Raid5.png)


En el gráfico de ejemplo anterior, una petición de lectura del bloque «A1» sería servida por el disco 0. Una petición de lectura simultánea del bloque «B1» tendría que esperar, pero una petición de lectura de «B2» podría atenderse concurrentemente ya que sería servida por el disco 1.


## Desarrollo del proyecto
En este apartado describiremos el proceso de instalacion del servidor NAS para posteriormente implementar en este nuestro directorio activo.
OpenVPN
## Conclusión
## Bibliografía
- Xataka (https://www.xataka.com/basics/que-nas-como-configurarlo)
- Synology (https://kb.synology.com/es-mx/DSM/tutorial/How_to_create_and_manage_RAID_volumes_on_the_DiskStation)
- Wikipedia (https://es.wikipedia.org/wiki/RAID)
