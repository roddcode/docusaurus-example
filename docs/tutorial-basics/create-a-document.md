---
sidebar_position: 4
---

# Facturador

### Docker | Linux | SSL Externo

## Pasos

1. Para instalar debe ejecutar el script evitando instalar el SSL, le será consultado en el proceso y deberá ingresar "n".

2. Finalizada la instalación debe dirigirse a la ruta de instalación:
   ```bash
    cd /root/facturadorpro31/
    ```

3. Debe editar el archivo .env:
   ```nano .env```
   Dentro del editor, ubique los parámetros y cámbielos:
   - Antes:
     ```bash
     APP_URL=http://${APP_URL_BASE}
     ```
     ```bash
     FORCE_HTTPS=false
     ```
   - Después:
     ```bash
     APP_URL=https://${APP_URL_BASE}
     ```
     ```bash
     FORCE_HTTPS=true
     ```
   Una vez finalizado, guarde y salga del editor.

4. Ejecute los siguientes comandos para eliminar la caché de la aplicación:
   ```php artisan config:Cache```
   Con eso habrá completado el lado de la herramienta. En ese momento, hasta no tener un SSL configurado no podrá acceder a la herramienta.

### Importante

Recuerde habilitar el puerto 443 para poder tener acceso a la herramienta.
