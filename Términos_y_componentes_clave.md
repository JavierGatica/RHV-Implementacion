# Implementación de Red Hat Virtualization 4

## Términos y componentes clave

*Hypervisor:*
* Software que se ejecuta en un servidor físico que admite virtualización
* Permite la ejecución de máquinas virtuales que proporcionan acceso a los recursos del sistema virtual
* Ejemplos: vCPU, memoria virtual, discos virtuales, redes virtuales
* Estrechamente asociado con el servidor físico
* Hipervisores utilizados indistintamente con hosts

*Host:*
* Máquina física utilizada como hipervisor.
* Consta de máquina física y sistema operativo.

*Guest:*
* VM que se ejecuta en hipervisor

*Client:*
* Sistema físico o dispositivo que accede al entorno virtual
* Proporciona interfaz para VM y entorno de virtualización.

*RHV Manager (RHV-M):*
* Servicio que proporciona GUI y API para administrar recursos en el entorno.

*Hosts:*
* Hosts que proporcionan recursos utilizados para ejecutar máquinas virtuales
* Usar máquina virtual basada en kernel (KVM)
* Hosts compatibles: hosts Red Hat Enterprise Linux Host (RHEL-H) y hosts Red Hat Virtualization Host (RHV-H)

*Shared Storage:*
* Servicio de almacenamiento utilizado para almacenar datos asociados con máquinas virtuales

*Networking:*
* Servicio de red que proporciona una capa de red física para redes virtuales.
* Permite que las máquinas virtuales se comuniquen en un entorno de red definido

*cockpit*
* Interfaz web fácil de usar para administrar servidores
* Utilizado en RHV para:
* Implemente un entorno de motor autohospedado
* Realizar otras tareas de supervisión y administración en el host.

*vdsm*
* Escritorio virtual y administrador del servidor
* Daemon requerido por RHV-M para administrar hosts Linux e invitados KVM VM que se ejecutan en el host
* Administra y monitorea:
* Almacenamiento de host y memoria de host
* Redes
* Creación de VM y otras operaciones
* Tareas de administración de host
* Recopilación de estadísticas y recopilación de registros.
* Facilita la comunicación entre host y se comunica de nuevo a RHV-M a través del puerto 54321

*libvirt*
* Facilita la gestión de máquinas virtuales y dispositivos virtuales asociados.
* vdsm invoca libvirt para ejecutar comandos en la máquina host para administrar máquinas virtuales que se ejecutan en el host

*remote-viewer*
* Aplicación que proporciona una interfaz gráfica para conectarse a máquinas virtuales a través de una conexión de red
* Proporcionado por virt-viewer paquete
* También disponible desde el por al RHV-M en Recursos del cliente de la consola

*qemu*
* Emulador multiplataforma utilizado para proporcionar emulación de sistema completo
* En RHV, se utiliza junto con kvmpara proporcionar una virtualización completa asistida por hardware
* El procesador debe tener las extensiones de virtualización necesarias

*kvm*
* Máquina virtual basada en kernel
* Módulo de kernel cargable que proporciona virtualización completa al aprovechar las extensiones de hardware Intel VT y AMD-V
* Permite al host hacer que el hardware físico esté disponible para su uso en máquinas virtuales

