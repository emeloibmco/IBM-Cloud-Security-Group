# IBM Cloud - Security Group ☁🔒
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
<br />

## Protocolo TCP para SSH :computer:
El protocolo *Secure Shell (SSH)* se utiliza para acceder a máquinas remotas

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
* <a href="https://cloud.ibm.com/docs/security-groups?topic=security-groups-managing-sg">Managing security groups</a>.
<br />

## Autores :black_nib:
Equipo *IBM Cloud Tech Sales Colombia*.
