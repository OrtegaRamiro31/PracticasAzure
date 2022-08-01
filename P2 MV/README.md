# Practica 02. Maquinas Virtuales.

Creación y ejecución de dos Máquinas Virtuales en Azure.

## Requisitos

- Cuenta de Azure con suscripción activa.
- Sistema Operativo Windows, Linux o MacOs.
- Conexión estable a internet.

## Procedimiento

1. Ingresamos a [Portal Azure](https://portal.azure.com)
   ![Portal Azure](imagenes/1.png)

2. Seleccionamos o buscamos el recurso **"Máquinas Virtuales"** y accedemos.
   ![Recurso Maquinas Virtuales](imagenes/2.png)

3. Seleccionamos la opción **"Crear"** y seleccionamos **"Máquina virtual de Azure"**.
   ![Crear Maquina Virtual](imagenes/3.png)

4. En esta parte se hace lo siguiente:
   - Se crea un grupo de recursos.
   - Se elige otra región (en caso de que no existan **"Tamaños"** disponibles).
   - Se elige una **imágen**, en este caso es Windows 10 Pro.
   - Se crea un usuario y contraseña para acceder remotamente a la Máquina Virtual.
   - Se confirma que se posee una licencia válida de Windows 10.

- Cualquier otra configuración dependerá del usuario.
  Al finalizar se da click en **"Revisar y crear"**
  ![Ajustes para la Máquina Virtual](imagenes/4.png)

5. Elegimos la opción **"Crear"** si no hay problemas.
   ![Creación de Máquina Virtual](imagenes/5.png)

6. Al finalizar lo anterior, comenzará a implementarse la Máquina Virtual. Mientras pasa lo ya mencionado, se creará otra Máquina Virtual con las mismas características, todo siguiendo exactamente los mismos pasos (desde paso 1).
   ![Implementación en curso de Máquina Virtual](imagenes/6.png)

7. Cuando la implementación de ambas Máquinas Virtuales finalice, aparecerá algo como en la imágen siguiente.
   ![Máquinas Virtuales creadas](imagenes/7.png)

8. En VM1 elegimos la opción **"Conectar"** y **"RDP"**.
   ![IP Pública de VM1](imagenes/8.png)

9. Abrimos **Remote Desktop Connection** en nuestro Windows y colocamos la IP Pública que aparece.
   ![Remote Desktop Connection](imagenes/9.png)

10. Se ingresa el usuario y la contraseña registrados al momento de configurar la Máquina Virtual, posteriormente se da click en OK.
    ![Usuario y contraseña de la Máquina Virtual](imagenes/10.png)

11. Se da click en Yes.
    ![Seleccionar Yes](imagenes/11.png)

12. Después de un momento, la Máquina Virtual habrá cargado completamente y tendremos control sobre ella.
    ![Máquina Virtual 1 cargada](imagenes/12.png)

13. Antes de proseguir debemos verificar la dirección IP Pública de la Máquina Virtual 2 en **Portal Azure**.
    ![IP de la Máquina Virtual 2](imagenes/13.png)

14. Ahora dentro de la Máquina Virtual se abrirá **"Remote Desktop Connection"** y se colocará la IP correspondiente a la otra Máquina Virtual. Posteriormente se ingresa el usuario y la contraseña registrados para esa Máquina Virtual.
    ![Remote Desktop Connection en Máquina Virtual 1](imagenes/14.png)

15. Se da click en Yes.
    ![Seleccionar Yes](imagenes/15.png)

16. Después de un momento la Máquina Virtual 2 aparecerá. En este caso se usó el comando **ipconfig** en el CMD para demostrar que contienen dos IPs distintas.
    ![Ambas Máquinas Virtuales abiertas](imagenes/16.png)
