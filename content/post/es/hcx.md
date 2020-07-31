+++
author = "Roberto Cantón"
title = "VMware Hybrid Cloud Extension (HCX)"
date = "2019-08-12"
description = "VMware Cloud on AWS"
featured = true
tags = [
    "VMware",
    "Cloud",
    "AWS",
    "HCX",
    "Español"
]
categories = [
    "Cloud",
    "AWS",
    "VMware"
]
series = ["Blog - Español"]
thumbnail = "images/blog/hcx.png"
+++

VMware Hybrid Cloud Extension (HCX) conecta ambientes on-premises, nubes privadas, VMware Cloud on AWS, infraestructuras de proveedores de nubes basadas en tecnología de VMware, creando un ambiente híbrido y multi-nube para cargas de trabajo de vSphere.

![HCX](../../../images/blog/hcx2.png)

VMware HCX ofrece movilidad de aplicaciones de una forma segura e ininterrumpida, convirtiendo su infraestructura en una nube híbrida de una manera fácil y eficiente y también sin necesidad de actualizar la infraestructura virtual en la que corre pues soporta desde versiones de vSphere 5.0 en adelante.

---

## **Capacidades Técnicas de VMware HCX**

![HCX](../../../images/blog/hcx3.png)

1. Extiende versiones antiguas de vSphere hacia VMware Cloud on AWS, sin necesidad de actualizar la versión local on-premises. Soporta desde versiones 5.1 hacia arriba.
2. No existe requerimiento de un solo dominio SSO.
3. Funciona a través de diferentes tecnologías de redes de vSphere, ambiente on-premises puede ser simplemente vDS (Switch Virtual Distribuido), capacidades adicionales si el ambiente corre NSX.
4. Capacidad de extender redes en capa 2 de ambientes on-premises hacia VMware Cloud on AWS a través del HCX Interconnect encriptado, el cuál puede funcionar a través de una conección regular de internet o línea privada (Direct Connect).
5. Optimizador de WAN incluído con la solución y routing inteligente, hace parecer que el WAN funcione como un LAN lo que dramáticamente reduce los tiempos de migración.
6. L2C (Concentrador de Capa 2) de alto rendimiento, puede alcanzar 6 Gbs por VLAN y escalar a las demandas de red de la empresa.
7. Soporte para multi-sitios, se puede extender múltiples sitios on-premises al mismo ambiente de VMware Cloud on AWS, o extender un ambiente on-premises a varios ambientes de VMware Cloud on AWS.
8. Migración bi-direccional fácil de cargas de trabajo, no hay necesidad de actualizar la aplicación, sistema operativo, dirección IP, MAC, o convertir la VM a otro formato.
9. Provee la capacidad de migrar cientos de máquinas virtuales con Bulk Migration.
10. También se puede ejecutar Cold Migration (máquina apagada), Bulk Migration (interrupción mínima), o en vivo sin interrupción con vMotion.
11. Programación de migración avanzada con flujos de trabajo posteriores a la migración para garantizar que la VM ejecute las últimas herramientas de VM y VM HW.

---

## **Tipos de migraciones soportadas por HCX hacia VMware Cloud on AWS**

### Cold Migration

![Cold Migration](../../../images/blog/hcx4.png)

*Migración en "frío"* - La migración en frío utiliza la misma ruta de red que VMware HCX vMotion para transferir una máquina virtual apagada. Durante una migración en frío, se conservan la dirección IP de la máquina virtual y la dirección MAC. Las migraciones en frío deben satisfacer los requisitos de vMotion.

### HCX vMotion

![vMotion](../../../images/blog/hcx5.png)

*HCX vMotion* - VMware HCX vMotion puede transferir una máquina virtual en vivo desde un servidor vCenter habilitado para VMware HCX a un sitio remoto habilitado para VMware HCX (o desde el sitio de destino habilitado para VMware HCX hacia el sitio local. La transferencia vMotion captura la memoria activa de la máquina virtual, su estado de ejecución, su dirección IP y su dirección MAC. La duración de la migración depende de la conectividad, incluido el ancho de banda disponible y la latencia entre los dos sitios.

### HCX Bulk Migration

![HCX Bulk Migration](../../../images/blog/hcx6.png)

*HCX Bulk Migration* - VMware HCX Bulk Migration utiliza la replicación basada en host (vSphere Replication) para mover una máquina virtual en vivo desde y hacia sitios de nube o centros de datos habilitados para VMware HCX. Para reducir el tiempo de inactividad, la máquina virtual de origen permanece en línea durante la replicación y se reinicia en el host ESX de destino una vez que se completa la replicación. Este último ejercicio (switchover) puede ocurrir de 2 maneras: al momento que la VM esté completamente replicada, o se puede agendar para que haga el switchover en una ventana determinada en el futuro.

### HCX Replication Assisted vMotion

![HCX Replication Assisted vMotion](../../../images/blog/hcx7.png)

*HCX Replication Assisted vMotion* - Esta opción funciona exactamente que Bulk Migration, con la excepción que durante el switchover, en vez de haber interrupción en la máquina virtual, HCX transfiere control de la última parte de la VM al servicio de HCX vMotion para hacer la última sincronización de la máquina virtual y los datos a sincronizar, esto logra que no haya interrupción en la operación de la máquina virtual.

---

## **Componentes de HCX**

### HCX Cloud/HCX Target

![HCX Cloud/HCX Target:left](../../../images/blog/hcx8.png)
\
\
HCX Cloud o HCX Target, es básicamente HCX desplegado en el SDDC de VMware Cloud on AWS. Los mismo componentes que se despliegan on-premises son desplegados del lado del SDDC de VMware Cloud on AWS.  
  
    


    

### HCX Enterprise/HCX Manager

![HCX Enterprise/HCX Manager](../../../images/blog/hcx9.png)

HCX Enterprise, también conocido como HCX Manager es el principal componente de HCX y se instala localmente en el ambiente on-premises en vCenter. Una vez instalado, un plug-in aparece en la herramienta local de vCenter.

### HCX Interconnect Appliance

![HCX Interconnect](../../../images/blog/hcx-ix.png)

El servicio de interconexión proporciona acceso resistente a través de Internet y líneas privadas al sitio de destino, a la vez que proporciona cifrado sólido, ingeniería de tráfico y extiende el centro de datos.

### HCX WAN Optimization Appliance

![HCX WAN Optimization](../../../images/blog/hcx-wo.png)

El HCX WAN Optimization Appliance, optimiza el tráfico de migración al deduplicar y comprimir el tráfico antes que se ejecute la migración, lo que logra hacer que las migraciones se ejecuten de una manera mucho más eficiente.

### HCX Network Extension Appliance

![HCX Network Extension](../../../images/blog/hcx-ne.png)

El Network Extension Appliance de HCX ofrece un servicio de alto rendimiento (4–6 Gbps), puede extender las redes de máquinas virtuales a un sitio remoto habilitado para VMware HCX. Las máquinas virtuales que se migran o crean en el segmento extendido en el sitio remoto son capa 2 junto a las máquinas virtuales ubicadas en la red de origen. Al usar la extensión de red, los recursos de un sitio remoto se pueden consumir rápidamente. Con la Extensión de red, la puerta de enlace predeterminada para la red extendida solo existe en el sitio de origen. El tráfico de máquinas virtuales (en redes remotas extendidas) que debe enrutarse regresa a la puerta de enlace del sitio de origen.

---

![VMware Cloud on AWS](../../../images/blog/hcx-vmc.png)

En otro blog les explicaré como habilitar HCX en su SDDC de VMware Cloud on AWS así cómo también como ejecutar la instalación on-premises de HCX.

Espero ésta información les sea útil e informativa, y acá estoy a la orden con cualquier duda que tengan.

¡Saludos y un abrazo!

---

