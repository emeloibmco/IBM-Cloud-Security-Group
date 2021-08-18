# IBM Cloud - Security Group ☁🔒
*IBM Cloud* le permite usar grupos de seguridad para declarar un conjunto de reglas de filtro de IP que definen cómo manejar el tráfico entrante y saliente a las interfaces públicas y privadas de una instancia de servidor virtual.

En esta guía se muestra la creación de una regla que permita la entrada de tráfico en una máquina cliente en la que se esta probando el comando ```iperf```, tambien se explican las reglas de ```SSH``` y ```ping``` que ya vienen configuradas por defecto en el grupo de seguridad.
<br />

## Índice  📰
1. [Pre-Requisitos](#Pre-Requisitos-bookmark_tabs)
2. [Protocolo ICMP para ping](#Protocolo-ICMP-para-ping-heavy_check_mark)
3. [Protocolo TCP para SSH](#Protocolo-TCP-para-SSH-computer)
4. [Protocolo TCP para Iperf](#Protocolo-TCP-para-Iperf-chart_with_downwards_trend)
5. [Referencias](#Referencias-mag)
6. [Autores](#Autores-black_nib)
<br />

## Pre-Requisitos :bookmark_tabs:
* Contar con una cuenta en <a href="https://cloud.ibm.com/"> IBM Cloud </a>.
* Contar con una *VPC*.
<br />

## Protocolo ICMP para ping :heavy_check_mark:
*Internet Control Message Protocol (ICMP)* es una red de protocolo que es responsable de reportar errores a través de la generación y envío de mensajes a la dirección IP de origen cuando hay problemas de red que son encontrados por el sistema. 

Existen tipos de mensajes en *ICMP*, el campo de tipo identifica el tipo de mensaje enviado por el host o la puerta de enlace. En este caso, el tipo 8 se refiere a Echo Request (Ping Request).

```Ping``` es un comando  de diagnóstico que permite hacer una verificación del estado de una determinada conexión de un host local con al menos un equipo remoto contemplado en una red de tipo TCP/IP. Sirve para determinar si una dirección IP específica o host es accesible desde la red o no.

Esta regla ya viene incluida en el grupo de seguridad por defecto asigando a su VSI y se encuentra especificado en las reglas de entrada.
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/IBM-Cloud-Security-Group/blob/main/Images/ping.png"></p>

<br />

## Protocolo TCP para SSH :computer:
El protocolo *Secure Shell (SSH)* se utiliza para acceder a máquinas remotas a través de una red y manejar por completo el sistema mediante un intérprete de comandos.  Este protocolo facilita las comunicaciones seguras entre dos sistemas usando una arquitectura cliente/servidor y permite a los usuarios conectarse a un host remotamente. A diferencia de otros protocolos de comunicación remota, *SSH* encripta la sesión de conexión impidiendo que se pueda obtener contraseñas no encriptadas.

Cuando se crea una *VPC* en *IBM Cloud*, de forma predeterminada se implementan grupos de seguridad que definen las reglas de ```IP```, permitiendo el tráfico ```TCP``` de entrada solo en el puerto 22 para SSH.

<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/IBM-Cloud-Security-Group/blob/main/Images/ssh.PNG"></p>
<br />

## Protocolo TCP para Iperf :chart_with_downwards_trend:
El comando ```iperf``` es una herramienta de la línea de comandos usada en el diagnóstico de problemas de velocidad de red. Este comando mide la capacidad máxima de procesamiento de red que puede manejar un servidor. Es particularmente útil cuando se experimentan problemas de velocidad en la red, debido a que se puede utilizar para determinar cuál servidor es incapaz de llegar al rendimiento máximo. Actualmente hay dos ramas independientes de ```iperf``` que se desarrollan en paralelo: ```iperf2``` e ```iperf3```. La funcionalidad de estas herramientas es en su mayoría compatible, pero utilizan diferentes puertos de red de forma predeterminada. En ```iperf2``` es 5001, mientras que en ```iperf3``` es 5201.

Este puerto no viene configurado de forma previa en la *VPC*, por tanto, si desea medir el ancho de banda entre un cliente y un servidor ```TCP```, debe configurar en las reglas de entrada del grupo de seguridad, el puerto que desea habilitar según la rama de ```iperf``` que utilizará. Para ello se debe realizar lo siguiente:

<br />

1.	En ```Infraestructura VPC/VPC Infrastructure``` ubique la sección ```Red/Net``` y de click en la opción ```Grupos de seguridad/Security groups```.
<br />

2.	Seleccione la región en donde se encuentra la *VPC* y visualice el grupo de seguridad. El nombre que aparece se crea de forma automática.
<br />

3.	De click sobre el grupo de seguridad y seleccione la pestaña ```Reglas/Rules```.
<br />

4.	Posteriormente, de click en el botón ```Crear``` ➡ seleccione el protocolo ```TPC``` y en el rango de puertos coloque el puerto ```5201``` que corresponde al puerto de escucha del servidor (definido por defecto con ```iperf3```).  Cuando la configuración esté lista de click en el botón ```Guardar```.
<br />

5.	Espero unos segundos mientras se implementa la regla y verifique que se encuentre correctamente.
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/IBM-Cloud-Security-Group/blob/main/Images/Reglas%20iperf3.gif"></p>
<br />

## Referencias :mag:
* <a href="https://cloud.ibm.com/docs/security-groups?topic=security-groups-getting-started">Getting started with IBM security groups</a>.
* <a href="https://cloud.ibm.com/docs/security-groups?topic=security-groups-managing-sg">Managing security groups</a>.
<br />

## Autores :black_nib:
Equipo *IBM Cloud Tech Sales Colombia*.
