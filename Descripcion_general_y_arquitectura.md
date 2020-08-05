# Implementación de Red Hat Virtualization 4

## Descripción general y arquitectura

### oVirt
Al igual que el resto de la cartera de productos de Red Hat, RHV es de código abierto y se basa en un proyecto ascendente. En este caso, el proyecto ascendente es oVirt, un sistema abierto de gestión de virtualización.

Red Hat luego toma el código de la comunidad y realiza una serie de pasos de integración y garantía de calidad para crear un producto compatible a partir del código ascendente. Este proceso comienza con la selección de versiones de los componentes que funcionan bien juntos y proporcionan un conjunto de características confiable. También incluye pruebas de integración, pruebas de compatibilidad, mejoras de rendimiento y seguridad, y otras actividades de garantía de calidad. Además, Red Hat crea documentación, establece acuerdos de soporte de proveedores cruzados y, de lo contrario, garantiza que el producto sea compatible tanto organizativamente como técnicamente.

El resultado de este proceso es un sistema de gestión de virtualización de código abierto de nivel empresarial conocido como Red Hat Virtualization.

## Componentes del hipervisor
En el nivel más bajo se encuentra el hardware, que proporciona el cálculo, la memoria, el almacenamiento y el acceso a la red, y otros recursos utilizados por las máquinas virtuales. Este hardware es administrado por el kernel de Linux. Al aprovechar las características existentes del kernel de Linux para el acceso al dispositivo, la seguridad, la administración de memoria y otras características en común con un sistema operativo, KVM evita la necesidad de volver a implementar estas características directamente. En cambio, aprovecha la madurez y el tamaño de la comunidad de desarrollo de Linux para obtener esos servicios a través de Linux. Por lo tanto, los módulos KVM pueden proporcionar un conjunto compacto y enfocado de características que son específicas de la virtualización.

En el espacio de usuario, cada VM se representa como un proceso QEMU. QEMU aprovecha las características de virtualización que ofrece KVM para crear máquinas virtuales que aprovechan los recursos de las capas subyacentes. QEMU también implementa hardware virtual, que se presenta al sistema operativo invitado, para permitir el acceso a los recursos físicos. Una pieza de hardware virtual particularmente interesante es la consola SPICE, que aparece como una tarjeta de video dentro del invitado y se implementa como un servidor que ofrece acceso al protocolo SPICE a los clientes.

El sistema operativo invitado también suele ejecutar un agente invitado para informar información a nivel del sistema operativo, como usuarios conectados y procesos en ejecución. También suele utilizar controladores de dispositivos paravirtualizados, como un controlador SPICE dedicado, para aprovechar al máximo el hardware virtualizado. Estos componentes son opcionales pero se recomiendan para un rendimiento óptimo del huésped.

QEMU y KVM son administrados por la libvirt capa de abstracción de virtualización, bajo la dirección del agente host de virtualización VDSM. VDSM proporciona comunicación con RHV-M para informar el estado del host y de la máquina virtual, así como para recibir comandos del Administrador.

Finalmente, en cada centro de datos, un host a la vez ejecuta el rol de administrador de agrupación de almacenamiento, o SPM, que coordina el acceso al almacenamiento compartido.

## KVM
* Módulo de kernel cargable que proporciona virtualización completa a través de extensiones de hardware Intel VT o AMD-V
* Se ejecuta en el espacio del kernel como módulo del kernel
* Los invitados que se ejecutan en KVM se ejecutan como procesos QEMU individuales en el espacio de usuario
* KVM permite que el host ponga su hardware físico a disposición de las máquinas virtuales

## QEMU
* Emulador multiplataforma utilizado para proporcionar una emulación completa del sistema
* Emula el sistema completo, por ejemplo, PC, incluidos uno o más procesadores y periféricos
* En combinación con KVM y el procesador con extensiones de virtualización apropiadas, puede proporcionar una virtualización completa asistida por hardware

## VDSM
* Inicia acciones en máquinas virtuales y almacenamiento
* También facilita la comunicación entre hosts
* Supervisa recursos de host como memoria, almacenamiento, redes
* Gestiona tareas como la creación de máquinas virtuales, la acumulación de estadísticas, la recopilación de registros
* La instancia de VDSM se ejecuta en cada host, recibe comandos de administración de RHV-M utilizando el puerto 54321
* Usos vdsm-regpara registrar cada host con RHV-M
* vdsm-reg proporciona información sobre sí mismo y su host utilizando el puerto 80 o 443

## libvirt
* Facilita la gestión de máquinas virtuales y dispositivos virtuales asociados.
* Cuando RHV-M inicia los comandos del ciclo de vida de la VM, VDSM invoca libvirten las máquinas host relevantes para ejecutarlos
* Comandos de ejemplo: iniciar, detener, reiniciar, migrar

## Storage Pool Manager
* Rol de SPM asignado a un host en el centro de datos
* Tiene la autoridad exclusiva para realizar todos los cambios de metadatos de la estructura del dominio de almacenamiento para el centro de datos
* Ejemplos: creación, eliminación, manipulación de imágenes de disco virtual, instantáneas, plantillas
* SPM se puede migrar a cualquier host en el centro de datos
* Por lo tanto, todos los hosts en el centro de datos deben tener acceso a todos los dominios de almacenamiento definidos en el centro de datos
* RHV-M asegura que SPM esté siempre disponible
* En caso de errores de conectividad de almacenamiento, RHV-M reasigna la función de SPM a otro host

## Redes: redes lógicas
* VM network
* Storage network
* Migration network
* Display network
* Red Hat Gluster Storage network

