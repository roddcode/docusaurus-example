---
sidebar_position: 1
---

# Script para Linux
### Docker + GitLab + SSL

**Descripción:**
Hemos elaborado un script para uso en instancias Linux, este es un archivo .sh que actualiza el sistema, instala las herramientas, sus dependencias, configura un certificado SSL renovable cada 90 días que debe ser confirmado en el proceso con su dominio y realiza todas las configuraciones previas, dejando el aplicativo listo para probar en menos de 20 minutos, su ejecución es muy sencilla.

**Requisitos previos:**
- Tener acceso a su servidor, vps, máquina virtual o local via SSH, en las instalaciones que realizamos para AWS o Google Cloud, hacemos entrega del usuario, la IP del servidor y la clave ssh que puede ser un archivo .ppk o .pem.
- Tener instalado una versión de ssh en su máquina para conectarse de manera remota, puede utilizar putty, filezilla o una consola terminal.
- Es importante configurar su dominio apuntando a la IP de su instancia para que durante la ejecución del script se valide el certificado SSL y al finalizar la ejecución no tenga errores y todo esté listo para realizar pruebas. Edite los récords A y CNAME donde A debe contener su IP y CNAME el valor * (asterisco) para que se tomen los subdominios registrados por la herramienta.

**Pasos:**
1. Acceder a su instancia vía SSH.
2. Loguearse como super usuario `sudo su`.
3. Ubicarse en la carpeta del usuario, por ejemplo `cd /home/ubuntu/`.
4. Crear el archivo `install.sh` ejecutando `touch install.sh`.
5. Editar el archivo con su editor preferido ejecutando `nano install.sh`. En el archivo debe agregar el contenido del siguiente enlace: [GitLab Snippet](https://gitlab.com/snippets/1852652). Para salir del editor y guardar, presionar "ctrl + x", confirmar con "y" y luego "enter".
6. Darle permisos de ejecución al archivo ejecutando `chmod +x install.sh`.
7. El comando a utilizar requiere de dos parámetros principalmente: `./install.sh [repositorio] [dominio]`. Por ejemplo: `./install.sh https://gitlab.com/rash07/facturadorpro2 elfacturador.com`. Una vez ejecutado el comando, se iniciará un proceso donde debe ir aceptando las preguntas y que le mostrará en pantalla los valores que debe añadir en los 2 récords tipo TXT de su dominio con nombre `_acme-challenge.example.com` y `_acme-challenge` (casos como godday y puntope).
8. Editados los récords en su dominio, deberá aceptar para continuar y que el proceso verifique que sea exitoso. De ser exitoso, obtendrá una pantalla similar a la siguiente.


9. Continuará el proceso de actualización del sistema. Se le solicitará el usuario y contraseña de GitLab para que se pueda clonar/descargar el proyecto en su instancia. Luego culminará y tendrá los accesos listos en su dominio:

Correo: admin@gmail.com
Contraseña: 123456

10. Una vez finalizado, puede proseguir con el manual de pruebas o demás documentación de cada proyecto. Las URLs son:

   - PRO1: [GitLab PRO1](https://gitlab.com/rash07/facturadorpro1)
   - PRO2: [GitLab PRO2](https://gitlab.com/rash07/facturadorpro2)

**Recomendaciones:**
- Luego de instalar el facturador, puede cambiar algunos parámetros en el archivo `.env` como:
  - La dirección de envío de correos que utiliza el facturador para enviar los archivos pdf, xml y cdr a sus clientes.
  - Cambiar algunas configuraciones de plantillas de los pdf, entre otros.
- Recuerde que siempre que se edita el archivo `.env`, debe utilizar el comando `php artisan config:cache` dentro del contenedor de fpm1. Para más detalles, puede observar el manual de actualización [aquí](ruta/manual-actualizacion).
- La ruta donde ejecute el script será donde se clone el repositorio. Debe verificar que los usuarios del servidor tengan permisos a dicha ruta si desea acceder desde ftp o scp.
