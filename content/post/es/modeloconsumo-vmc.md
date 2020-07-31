+++
author = "Roberto Cantón"
title = "Modelos de Consumo de VMware Cloud on AWS"
date = "2019-06-26"
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
thumbnail = "images/blog/vmc-cloud.png"
+++

Muchos clientes preguntan ¿Cómo se consume el servicio?, ¿Cómo se paga?

A continuación trataré de explicar lo más fácil posible como el servicio es consumido, la unidad de consumo, entre otras cosas.

A diferencia de muchas nubes públicas donde clientes pueden pagar por la unidad de consumo de una máquina virtual (Almacenamiento, Cómputos), en VMware Cloud on AWS la unidad de consumo es el nodo (servidor). 

El servicio empezó ofreciendo sólo un tipo de nodo (al momento de esta publicación) que es la instancia i3 metal de AWS. AWS ofrece servidores bare metal a sus clientes. Les describo las características de cada nodo de tipo i3-metal:

- 2 CPUs
- 36 cores (18 por CPU)
- 512 GB RAM
- 10.7 TB de almacenamiento NvME puro presentado como un datastore a través de VSAN

Recientemente VMware también agregó una segunda opción de nodos (R5-metal) la cual tiene las siguientes características:

- 2 CPUs
- 48 cores (24 por CPU)
- 768 GB RAM
- Almacenamiento de Amazon Elastic Block Storage (EBS) entre 15-35 TB por nodo presentado como un datastore a través de VSAN
- Almacenamiento empieza en 15TB y se puede hacer crecer en incrementos de 5TB hasta 35TB por nodo

A la fecha de esta publicación (Junio de 2019) el consumo mínimo para obtener el servicio es de un cluster de 3 nodos. VMware también ofrece la opción de 1-nodo (no puede ser llamado cluster pues para eso necesitaríamos 2 nodos al menos). El modelo de SDDC de 1 nodo tiene unas limitaciones importantes que todos los clientes interesados deben entender:

- Vida útil de 30 días como máximo y no se puede extender.
- No existe alta disponibilidad, si el nodo falla, se pierden todas la máquinas virtuales que corren en el nodo.
- Al final (o antes) de los 30 días el cliente debe crecer el SDDC a un mínimo de 3 nodos ó simplemente destruirlo.

Se preguntarán porque un cliente estaría interesado en un SDDC de 1 nodo? 

Hay muchos clientes que desean hacer una prueba rápida del servicio para probar que les funcionará pero no quieren hacer un contrato a largo tiempo con VMware ó simplemente no hacer un gasto excesivo de 3 nodos para hacer una prueba sencilla. La opción de un SDDC de 1 nodo es una opción muy económica ya que cuesta aproximadamente US$7/hora/nodo lo que equivale a aproximadamente US$5,110 por los 30 días de vida de este SDDC. La ventaja también es que si uno como cliente quiere hacer crecer el ambiente al finalizar las pruebas o los 30 días, no tienen que destruir el trabajo realizado durante las pruebas.

---

## **Opciones de plan de consumo**

Ya que revisamos y entendemos que la unidad de consumo es el nodo físico, y que necesito un mínimo de 3 nodos para correr un cluster de producción, la pregunta ahora es como lo consumo o lo pago. A continuación les explico los modelos:

1. **On Demand** - En este modelo, VMware nos cobra por hora sin necesidad de firmar ningún tipo de contrato. Lo que quiere decir es que yo puedo levantar un cluster de 3 nodos por 10 días y le debo a VMware por 240 horas de uso (24 horas en el día por 10 días).
2. **Contrato de 1 año** - Podemos también firmar un contrato con VMware en el cual nos compremetemos a consumir el servicio por un período mínimo de 1 año, Este modelo tiene un ahorro de aproximadamente 30% sobre el costo On Demand.
3. **Contrato de 3 años** - Otra opción a largo plazo dónde cómo clientes nos comprometemos a consumir el servicio por un período de 3 años. Este modelo tiene un ahorro de aproximadamente 50% sobre el costo On Demand.

## **Costos variables**

![VMC Costs](../../../images/blog/vmc-costs.png)

Les adjunto una gráfica que explica los costos adicionales (además de los nodos) que tiene el servicio de VMware Cloud on AWS.

Platicando con muchos clientes les preocupa mucho los precios variables que tiene no sólo éste servicio pero cualquier servicio de nube pública.

Igual que con otros servicios de nube, no existen cobros adicionales por subir datos a la nube, pero si existen al sacarlos de la nube, ya sea de regreso a nuestro ambiente on-premises ó hacia el internet.

Por suerte, VMware y AWS se han puesto de acuerdo en un precio especial para clientes de VMware Cloud on AWS que es de .05 centavos de dólar por GB que salga del ambiente de VMware Cloud on AWS.

Normalmente es recomendable presupuestar un 5 a 10% del costo de la infraestructura de VMware Cloud on AWS. Por ejemplo, si mi costo es US$100,000, añadir cómo mínimo US$5,000 (5%) al costo para poder tener fondos disponibles para costos de salida de datos. En este ejemplo, US$5,000 equivalen a 100TB de datos que puedo bajar de el servicio.

Para más información sobre precios, calculadora ó para presupuestar aproximadamente el costo de los diferentes modelos, por favor visite el sitio oficial de VMware Cloud on AWS: https://cloud.vmware.com/es/vmc-aws/pricing, ó platique con su agente de ventas de VMware.

Gracias y hasta la próxima. Saludos y un fuerte abrazo.

---