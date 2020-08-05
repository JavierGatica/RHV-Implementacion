# Implementación de Red Hat Virtualization 4

## Términos y componentes clave

*Hypervisor: *
* Software que se ejecuta en un servidor físico que admite virtualización
* Permite la ejecución de máquinas virtuales que proporcionan acceso a los recursos del sistema virtual
* Ejemplos: vCPU, memoria virtual, discos virtuales, redes virtuales
* Estrechamente asociado con el servidor físico
* Hipervisores utilizados indistintamente con hosts

*Host: *
* Máquina física utilizada como hipervisor.
* Consta de máquina física y sistema operativo.

*Guest: *
* VM que se ejecuta en hipervisor

*Client: *
* Sistema físico o dispositivo que accede al entorno virtual
* Proporciona interfaz para VM y entorno de virtualización.

*RHV Manager (RHV-M):  *
* Servicio que proporciona GUI y API para administrar recursos en el entorno.

*Hosts: *
* Hosts que proporcionan recursos utilizados para ejecutar máquinas virtuales
* Usar máquina virtual basada en kernel (KVM)
* Hosts compatibles: hosts Red Hat Enterprise Linux Host (RHEL-H) y hosts Red Hat Virtualization Host (RHV-H)

*Shared Storage: *
* Servicio de almacenamiento utilizado para almacenar datos asociados con máquinas virtuales

*Networking: *
* Servicio de red que proporciona una capa de red física para redes virtuales.
* Permite que las máquinas virtuales se comuniquen en un entorno de red definido

