# IBM Cloud - Security Group ☁🔒
<br />

## Índice  📰
1. [Pre-Requisitos](#Pre-Requisitos-bookmark_tabs)
2. [Protocolo ICMP](#Protocolo-ICMP)
3. [Protocolo TCP para SSH](#Protocolo-TCP-para-SSH)
4. [Protocolo TCP para Iperf](#Protocolo-TCP-para-Iperf)
5. [Referencias](#Referencias-mag)
6. [Autores](#Autores-black_nib)
<br />

## Pre-Requisitos :bookmark_tabs:
* Contar con una cuenta en <a href="https://cloud.ibm.com/"> IBM Cloud </a>.
<br />

## Protocolo ICMP
<br />

## Protocolo TCP para SSH
<br />

## Protocolo TCP para Iperf
Para medir el ancho de banda entre un cliente y un servidor *TCP*, se deben configurar las reglas de entrada en el grupo de seguridad de la *VPC* cuya *VSI* funcionará como servidor. Para ello realice:

<br />

1.	En ```Infraestructura VPC/VPC Infrastructure``` ubique la sección ```Red/Net``` y de click en la opción ```Grupos de seguridad/Security groups```.
<br />

2.	Seleccione la región en donde se encuentra la *VPC* y visualice el grupo se seguridad. El nombre que aparece se crea de forma automática.
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
<br />

## Autores :black_nib:
Equipo *IBM Cloud Tech Sales Colombia*.
