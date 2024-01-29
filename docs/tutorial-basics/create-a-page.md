---
sidebar_position: 2
---

# Script para Ubuntu 18

### Docker | GitLab | Opción SSL | Opción SSH 

Hemos elaborado un script para uso en instancias Linux con Ubuntu 18 o superior. Este es un archivo que actualiza el sistema, instala las herramientas, sus dependencias y realiza todas las configuraciones previas, dejando el aplicativo listo para probar en menos de 20 minutos (siempre y cuando el dominio ya esté configurado hacia la instancia). Su ejecución es muy sencilla.

### Requisitos previos

1. Tener acceso a su servidor, vps, máquina virtual o local vía SSH. En las instalaciones que realizamos para AWS o Google Cloud, hacemos entrega del usuario, la IP del servidor y la clave ssh que puede ser un archivo .ppk o .pem. Recuerde almacenarlas en su equipo local.
2. Tener instalada una versión de ssh en su máquina para conectarse de manera remota. Puede utilizar putty, filezilla o una consola terminal. Para mayor información sobre el acceso SSH, visite los siguientes manuales:
   - [Guía para acceder con Putty (gestión de servidor)](link_putty)
   - [Guía para acceder con Winscp (gestión de archivos con aplicación de escritorio)](link_winscp)
3. Si es posible, configurar su dominio apuntando a su instancia para que al finalizar la instalación se encuentre disponible el aplicativo. Edite los registros A y CNAME, donde A debe contener su IP y CNAME el valor * (asterisco) para que se tomen los subdominios registrados por la herramienta.

En caso de contar con servicios instalados en su instancia como MySQL, Apache o Nginx, debe detenerlos, ya que estos ocupan los puertos que pasarán a usar el aplicativo con los contenedores de Docker.

### Pasos

1. Acceder a su instancia vía SSH.
2. Loguearse como super usuario: `sudo su`
3. Clonar el snippet de GitLab que contiene el script: `git clone https://gitlab.com/snippets/2079063.git script`
4. Ingresar a la carpeta clonada: `cd script`
5. Dar permisos de ejecución al script: `chmod +x install.sh`
