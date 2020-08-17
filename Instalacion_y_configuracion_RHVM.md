# Instalación y configuración de Red Hat Virtualization Manager

## Requisitos de hardware

### Hardware Minimo

* CPU = Dual core
* Memoria libre = 4 GB
* Disco = 25 GB
* NIC = Ancho de banda de al menos 1 Gbps

### Hardware Recomendado

* CPU = Quad core
* Memoria libre = 16 GB
* Disco = 50 GB
* NIC = Ancho de banda de al menos 1 Gbps


Los requisitos reales dependen, como siempre, del tamaño previsto de su implementación. También varían en función de consideraciones tales como si está utilizando servidores de base de datos internos o externos o funciones como la consola web, que dirige grandes cantidades de tráfico a través de RHV-M.

## Software Requirements
Red Hat® Virtualization Manager (RHV-M) requiere Red Hat Enterprise Linux® (RHEL) Server

Instalación básica del sistema operativo para instalar RHV-MRHV-M 

### requires subscriptions to both: 
* Canales necesarios para RHEL
* Canales adicionales

### Required channels:
* Disponible en Red Hat Subscription Management o en Red Hat Satellite Server local.
* Recupere los paquetes de instalación inicial y las actualizaciones a medida que estén disponibles.



## requerimientos generales
### DNS
* DNS crucial para que el entorno funcione correctamente y como se esperaba
* RHV se basa en DNS para Red Hat Virtualization Host (RHV-H), Red Hat Enterprise Linux Host (RHEL-H) y resolución de nombres RHV-M
* Antes de comenzar la instalación, asegúrese de que la infraestructura DNS esté configurada correctamente
