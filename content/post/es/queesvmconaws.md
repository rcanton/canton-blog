+++
author = "Roberto Cantón"
title = "¿Qué es VMware Cloud on AWS?"
date = "2019-06-25"
description = "VMware Cloud on AWS"
featured = true
tags = [
    "VMware",
    "Cloud",
    "AWS",
    "Español"
]
categories = [
    "Cloud",
    "AWS",
    "VMware"
]
series = ["Blog - Español"]
thumbnail = "images/vmc.png"
+++

En el mes de Octubre del año 2016, VMware y Amazon Web Services (AWS) anunciaron en conjunto una alianza estratégica para traer al mercado una solución que fué diseñada en conjunto por ingenieros de las dos empresas llamado VMware Cloud on AWS.

Este anuncio tomó a la industria por sorpresa pues hasta ese momento todos consideraban a ambas empresas competencia de la otra. Pero si evaluamos las razones de ésta alianza, hace mucho sentido:

VMware por un lado es el líder en virtualización y lo ha sido por muchos años, abarcando aproximadamente el 80% del mercado de virtualización y de lo que llamamos la nube privada.

Amazon Web Services (AWS) por el otro lado es el líder de servicios de nube pública y ha logrado mantenerse como el líder en la industria en lo que respecta a servicios de nubes públicas.

A pesar de que estas dos empresas, líderes en sus respectivos mercados, han tenido un nivel de éxito díficil de igualar por otros, no han podido penetrar por sí solos el mercado de el otro. VMware por un lado ha tratado de penetrar el mundo de nubes públicas sin mucho éxito en el pasado, y AWS simplemente no ha tenido presencia dentro de los Centros de Datos privados, aún con todo el éxito que han tenido con sus servicios de nube pública. Esta alianza, cuando se observa desde este punto de vista, hace mucho sentido para las dos empresas.

## **Software Defined Data Center (SDDC) de VMware

{{< figure src="../../../images/blog/sddc.jpg" attr="*VMware SDDC*" height="210" width="337" >}}

VMware tiene una serie de productos para poder virtualizar todos los aspectos de un centro de datos privado:

**vSphere** - El hipervisor que hizo a VMware famoso y que hasta el día de hoy no ha podido ser igualado en el mercado. Este es el producto insignia de VMware y permite virtualizar el área de computos de un centro de datos.

**NSX** - Producto para poder virtualizar la operación e infraestructura de redes adentro de un centro de datos.

**VSAN** - Producto que permite virtualizar la parte de almacenamientos de un centro de datos.

Estos tres productos forman parte de la estrategia que VMware nos ha venido evangelizando por unos años llamada "Software Defined Data Center" (SDDC), o el Centro de Datos Basado en Software. Tecnologías que permiten automatizar las funciones de un centro de datos para poder obtener más agilidad en las áreas de virtualización de computos, redes (y seguridad), y almacenamiento.

VMware Cloud on AWS básicamente es compuesto de éstas tecnologías de VMware (el SDDC de VMware) entregado como un servicio en la nube de AWS.

---

## **¿Qué beneficios nos ofrece VMware Cloud on AWS?**

![VMConAWS](../../../images/blog/vmcaws.png)

***1. Consistencia y familiaridad de tecnologías de VMware.***

La mayoría de clientes que hoy administran un centro de datos privado, están acostumbrados a tecnologías de VMware para administrar sus máquinas virtuales, ya sea a través de vCenter, o de las herramientas de vRealize Suite. Esta familiaridad es importante al momento de evaluar una nube pública pues la manera de operar o administrar un ambiente en un servicio de nube pública no es necesariamente el mismo, y estas diferencias en tecnologías y/o herramientas pueden demorar una migración hacia la nube pública.

***2.   Fácil portabilidad de cargas de trabajo y capacidades híbridas.***

Todas las nubes públicas ofrecen la capacidad de correr una máquina virtual, pero el proceso de migrar una máquina virtual de una nube privada que usualmente corre en el hipervisor de VMware hacia una nube pública, la cual corre un hipervisor diferente, puede ser costoso, dificultoso,  y no siempre funciona bien aún cuando una máquina se migre exitosamente. VMware Cloud on AWS corre el mismo hipervisor de VMware que clientes corren en sus centros de datos privados, lo cual permite la fácil migración de máquinas virtuales sin necesidad de convertir éstas máquinas a otros formatos para que sean compatibles con otro hipervisor al momento de migrarlas. En otro post, les platicaré más a fondo sobre las opciones que tenemos para migrar dichas máquinas y los diferentes métodos disponibles.

Pero migrar hacia la nube, a pesar de todas estas dificultades se puede hacer, pero ¿Cómo migramos éstas máquinas virtuales de regreso a nuestro centro de datos privado en un futuro si es necesario? Aquí es dónde el poder híbrico de VMware Cloud on AWS resalta sobre cualquier otra opción, pues así de simple como se migró una máquina virtual hacia la nube, así de simple podemos migrar dicha máquina de regreso a nuestro centro de datos privado.

***3. Acceso directo al poder de servicios nativos de AWS.***

AWS ofrece alrededor de más de 100 servicios de el lado nativo de sus servicios. No sólo por proximidad pero también por el poder de comunicación entre los dos ambientes. Esto nos permite poder interactuar con casi cualquier servicio de el lado de AWS nativo para poder aprovechar muchas de las capacidades de estos servicios y que puedan interactuar o comunicarse con máquinas virtuales que corren en VMware Cloud on AWS.

---

## **¿Cómo funciona VMware Cloud on AWS?**

![SDDC en VMConAWS](../../../images/blog/sddc-vmc.png)

Podemos observar la gráfica de el lado izquierdo tenemos nuestro centro de datos, ó nuestra nube privada corriendo en tecnologías de VMware. Al centro podemos observar el servicio de VMware Cloud on AWS corriendo encima de infraestructura de AWS, lo cual básicamente significa que la suite de productos de virtualización de VMware corre encima de servidores bare-metal de AWS. Estos son los mismos servidores que AWS utiliza para correr muchos de los servicios nativos que ellos ofrecen como proveedor de nube pública. Al lado derecho también observamos los servicios nativos de AWS corriendo sobre la misma infraestructura que el ambiente de VMware Cloud on AWS lo cual permite a los dos ambientes interactuar y comunicarse entre sí.

### **Hybrid Linked Mode**

Cómo podemos observar, vCenter está expuesto en el servicio para que clientes puedan tener la misma herramienta a la que están acostumbrados en su ambiente on-premises para administrar sus ambientes. Pero también hay una doble flecha que conecta nuestro vCenter on-premises con el vCenter de VMware Cloud on AWS, ¿qué significa esto? se preguntarán.

Hybrid Linked Mode es una nueva tecnología que nació con éste servicio el cual nos permite conectar nuesto vCenter on-premises con el vCenter de VMware Cloud on AWS para poder administrar los dos ambientes desde la misma ventanilla y no tener que estar administrando los dos ambientes desde dos ventanillas o pestañas de navegador. Escribiré en más detalles sobre Hybrid Linked Mode en otro post, así que estén atentos a ese blog.

### **Elastic Network Interface (ENI)**

También podrán observar una doble flecha conectando el ambiente de VMware Cloud on AWS con los servicios nativos de AWS. Esto pasa durante la construcción del ambiente de VMware Cloud on AWS a través de una tecnología disponible de el lado de AWS llamada Elastic Network Interfaces (ENI), la cual pueden leer más información haciendo click [aquí](https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/using-eni.html).

Me gusta comparar este ENI como una tubería de agua que suple los dos ambientes. La tubería está instalada pero para que el agua fluya tanto de un lado como del otro, necesitamos abrir las llaves de cada lado. Esto se hace a través de reglas de Firewall tanto de un lado como del otro para que la información fluya libremente entre los dos ambientes.

---

En otros posts entraré más a fondo sobre otras capacidades de éste servicio cómo los modelos de consumo, cómo el servicio es diferente a un ambiente de VMware on-premises y otros temas importantes para entender las capacidades de este servicio.

Gracias por leer este blog, y estén atentos a otros blogs. Siéntase libre de dejar un comentario, un saludo, o alguna sugerencia de algún tema del cuál le gustaría que escribiera.

Saludos y un fuerte abrazo.

---
