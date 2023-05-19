# Implementación de Active Directory en un servidor NAS
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

### Instalación Directorio Activo
Primero,configuraremos el nombre del equipo para darle un nombre
descriptivo, tarea muy común en entornos empresariales para permitir identificar los
servicios de manera más rápida. En nuestro caso he decidido llamarlo DC01 


![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/c316a5cc-8561-4a15-89cb-d3c37a95e956)

A continuacion, crearemos el Directorio Activo e instalaremos el servidor DNS el cual sera necesario para nuestro Directorio Activo y para agregar el NAS a nuestro Directorio Activo. Para ello le daremos a agregar roles y caracteristicas.

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/d92b8799-7535-48c9-b8c6-550715d35d04)

La instalacion del Directorio Activo y el servidor DNS no tiene complejidad, debemos seleccionar Instalación basada
en características o en roles.

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/7233c754-3427-4986-9451-394d87936509)

Seleccionaremos el servidor que usamos actualmente e instalaremos Active Directory y el servidor DNS

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/c04fc817-d51a-45b8-a113-2f6f631f3fef)

Las siguientes opciones no hace falta modificarlas solo seguir hacia delante

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/f2ea3b52-bd5c-4661-bbb6-2cb831e39260)

A continuación, asignaremos una ip estatica para que el servidor DHCP no nos de una diferente.

Para poder configurar una dirección estática, nos dirigiremos a Panel de control\Redes
e Internet\Conexiones de red y seleccionaremos la interfaz que queremos modificar, daremos clic derecho y Propiedades
y seleccionaremos Protocolo de Internet versión 4 (TCP/IPv4)

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/1ff68a2c-08a8-47a1-af76-b3c767bd1ee6)

Ahora tendremos que promocionar nuestro servidor a controlador de dominio. Para ello, lo haremos en el siguiente menu:

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/d0766115-a0b7-413a-8792-dcb3e825d3e8)

Siguiendo con la configuración del controlador de dominio, deberemos crear un nuevo bosque, donde introduciremos el nombre del dominio que vamos a utilizar.
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/f93124ec-e639-4492-8888-c55817a725ee)

Luego nos pedira una contraseña que servira para el modo restauración de servicios de directorio (DSRM), el cual permitira un arranque en modo seguro para poder recuperar o reparar una base de datos que se encuentre en nuestro Directorio Activo.
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/88d106ba-17ed-42c9-ba0f-09a1480102a4)

Vamos a crear un usuario, el cual utilizaremos luego en el NAS
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/96228e77-4bac-4ee1-aafe-6317e7d9258c)
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/5afaef95-3a50-4f9a-946b-caa1e8e38a20)



### Instalación servidor NAS.

Debido a que TrueNAS está diseñado y se proporciona como un archivo iso, funciona en todas
las soluciones de máquinas virtuales (VMware, VirtualBox, etc.). Nosotros
realizaremos la instalación con VMware Workstation Pro en Windows.

**Archivo de imagen del disco instalador**: https://www.truenas.com/download-truenas-core/

CUIDADO: Error UEFI de FreeBSD con ESXi
Productos VMWare y modo de inicio EFI: un error de terceros afecta actualmente el inicio EFI
(UEFI) en productos VMWare. TrueNAS debe instalarse en modo BIOS hasta que esto se
resuelva. Consulte el artículo de VMware https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.esxi.install.doc/GUID-D1BD27AB-C432-454D-9B2B-DC04E7BA9979.html

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/c2eaeddf-4b6e-4063-a142-74f4caae4525)
Procesador
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/28b992bd-a9cb-4d66-9ec9-7a5958c0003d)
Memoria RAM
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/5aa59e90-c58f-49a8-bf16-c6bc2a2481e7)
Tipo de disco
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/d1c873be-bdbe-47b8-a487-0503f335ada1)
Espacio disco instalacion truenas
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/fb3dc67f-b14f-42c9-9d2a-9de1236497ee)
Añadimos dos disco duros de 1TB cada uno
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/c09e6b9a-7375-4e2e-9ff0-ed2581d111e2)

Pantalla de inicio del NAS
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/eae0bc17-3032-406e-a47e-b41868829379)

Opcion instalar TrueNAS

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/8429c9a5-646e-400a-97b8-d7dbf33d9d97)

Eleccion disco duro donde instalar TrueNAS

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/8d7188ba-f046-41df-8e4a-c43309f62005)

Contraseña root

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/85036a2d-711c-42fc-8398-4e7840f170b0)

Modo BIOS
![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/4f9d2f68-952b-433b-a595-2e2018b5ed38)

Una vez reinicada la maquina nos saldran estas opciones, pero nosotros entraremos con la ip mediante el navegador

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/6d241a29-3478-4c35-88c1-5ccb1919b7b8)


![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/97ed352b-f5e3-4c2e-ab7d-f2f05c38d001)


Lo primero que deberemos hacer para configurar nuestro NAS, es añadir los discos duros que vamos a utilizar de almacenamiento

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/cfb7de59-c121-4135-93d1-9d253fe3b667)

Añadiremos los discos como un volumen de datos y utilizaremos la opcion RAID-Z2 que no es mas que un RAID 6

![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/c46f61db-82c2-4fb3-a046-d27c1af5b9ea)


![image](https://github.com/Tafariii/Proyecto_FCT/assets/113986006/d107cfca-d8cd-400c-a7a8-1bcea1cc9fdc)

### Añadir nuestro NAS a un Active Directory
### Snapshot
### Cloud Sync
### SSH
### OpenVPN
### Acceso recursos
#### Windows
#### Linux
### Docker
### MV
### FTP
## Conclusión
## Bibliografía
- Xataka (https://www.xataka.com/basics/que-nas-como-configurarlo)
- Synology (https://kb.synology.com/es-mx/DSM/tutorial/How_to_create_and_manage_RAID_volumes_on_the_DiskStation)
- Wikipedia (https://es.wikipedia.org/wiki/RAID)
- Flopy (https://www.flopy.es/tutorial-de-truenas-parte-3-como-anadir-truenas-a-un-dominio/)
- Youtube (https://www.youtube.com/watch?v=cY4xouP6CAw)
