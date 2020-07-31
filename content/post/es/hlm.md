+++
author = "Roberto Cantón"
title = "Hybrid Linked Mode en VMware Cloud on AWS"
date = "2019-06-30"
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
thumbnail = "images/blog/hlm.png"
+++

Hybrid Linked Mode es una tecnología que ofrece VMware exclusivamente para clientes de VMware Cloud on AWS.

Hybrid Linked Mode permite vincular la instancia de vCenter Server de VMware Cloud on AWS con un dominio de vCenter Single Sign-On local. 

Si se vincula la instancia de vCenter Server en la nube a un dominio que contiene varias instancias de vCenter Server vinculadas con Enhanced Linked Mode, todas esas instancias se vinculan al SDDC en la nube.  Para más información sobre Enhanced Linked Mode, haga click aquí.

El uso de Hybrid Linked Mode permite:

- Ver y administrar los inventarios de los centros de datos de VMware Cloud on AWS y locales desde la misma interfaz de vSphere Client, a la que se accede con credenciales locales. 
- Migrar cargas de trabajo entre el centro de datos local y el SDDC de nube. Ciertos prerequisitos aplican.
- Compartir etiquetas y categorías de etiquetas de la instancia de vCenter Server al SDDC de nube.

Existen dos opciones para configurar Hybrid Linked Mode. Solo se puede utilizar una de estas opciones a la vez.

- Puede instalar el Dispositivo de Cloud Gateway de vCenter y utilizarlo para establecer un vínculo entre el centro de datos local y  el SDDC de nube. En este caso, se asignan grupos de Active Directory del entorno local a la nube. No es necesario agregar Active Directory  como un origen de identidad en la instancia de vCenter Server en la nube. 
- Puede  establecer un vínculo entre el SDDC de nube y el centro de datos local.  En este caso, debe agregar Active Directory como un origen de identidad  en la instancia de vCenter Server en la nube.

![Hybrid Linked Mode](../../../images/blog/hlm-vmc.png)

Cómo pueden observar, la tecnología de Hybrid Linked Mode disponible para el servicio de VMware Cloud on AWS nos permite administrar desde la misma interfaz, los dos ambientes al mismo tiempo. Lo que significa que actividades como apagar, encender, reiniciar, remover, ó crear una máquina virtual, ya sea de nuestro vCenter on premises, ó nuestro vCenter en VMware Cloud on AWS se puede lograr desde la misma ventanilla ó pestaña de nuestro navegador.

Toda la información adicional sobre Hybrid Linked Mode la puede obtener aquí.

Gracias por leer éste blog, saludos y un fuerte abrazo.

---