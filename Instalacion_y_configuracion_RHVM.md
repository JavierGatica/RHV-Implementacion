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

Más allá de los requisitos básicos de hardware y software, es importante asegurarse de que el entorno de red sea adecuado para su sistema RHV. Debido a que los diversos componentes del sistema se comunican a través de la red y usan nombres DNS para encontrarse entre sí, asegúrese de que RHV-M, los sistemas host del hipervisor y cualquier directorio externo y servidor de base de datos tengan configurados correctamente la resolución de nombres directa e inversa.

### Ajustes de hora
* Los componentes RHV suelen utilizar SSH para la comunicación
* SSH conocido por ser sensible a las diferencias de reloj
* Asegúrese de sincronizar los servidores centrales mediante:
* Mismo tiempo fuentes
* Diferentes fuentes que presentan al mismo tiempo
* Sincronice la configuración de la hora antes de comenzar la instalación para evitar que los sesgos de tiempo causen problemas

Si está utilizando alguna de las virt-who suscripciones, como licencias VDC o Red Hat Enterprise Linux con Smart Virtualization y Red Hat Smart Management, también es extremadamente importante sincronizar la hora para que los sistemas se puedan conectar correctamente a Satellite y usar virt-whopara autorizar los invitados virtuales y los hipervisores físicos.

## Configuración
### ovirt-provider-ovn
* engine-setup puede configurar ovirt-provider-ovn
* Permite a los usuarios utilizar la red interna RHV-M para VM
* Ayuda a establecer una ovirtmgmtred
          
          Configure ovirt-provider-ovn (Sí, No) [Sí]:

### Proxies opcionales
* engine-setup opcionalmente puede configurar:
*Proxy de E / S de imagen: permite a los usuarios cargar imágenes y archivos ISO en dominios de datos RHV desde la interfaz de usuario web RHV-M

          Configurar Image I / O Proxy en este host (Sí, No) [Sí]:
          
* Servidor proxy Websocket: permite a los usuarios conectarse a máquinas virtuales a través de consolas noVNC o HTML 5

          ¿Configurar WebSocket Proxy en esta máquina? (Sí, No) [Sí]:
          
          
