# Azure Functions

Uso de Cognitive Service para escribir mensaje en Teams al identificarse un #IAWizzards en Twitter.

---

## Requisitos

- Cuenta de Azure activa.
- Cuenta de Google activa.
- Archivo de Google Sheets creado en Google Drive.

---

## Pasos

1. Entrar a [Portal Azure](https://portal.azure.com).
   ![Portal Azure](img/1.png)

2. En el buscador escribimos **Aplicación de funciones** o **Logic Apps**. Al entrar damos click en el botón de **Agregar**.
   ![Logic Apps](img/2.png)

3. Llenamos los campos necesarios para crear la Aplicaicón Lógica. Necesitamos obligatoriamente:

   - Una suscripción.
   - Grupo de recursos.
   - Nombre de la aplicación de lógica.
   - Región.
   - Tipo de plan (consumo).

   ![Creación de Logic App](img/3.png)

4. Revisamos las configuraciones anteriores y damos click en **Revisar y crear**.
   ![Revisión de configuración de Logic App](img/4.png)

5. Al finalizar damos click en **Ir al recurso**. Nos aparecerá una nueva ventana.
   ![Logic App](img/5.png)

6. Damos un poco de scroll hacia abajo y seleccionamos **Aplicación lógica en blanco**.
   ![Selección de Aplicación Lógica en Blanco](img/6.png)

7. Al aparecer la ventana de **Diseñador de aplicaciones lógicas**, seleccionamos o buscamos "Twitter, cuando se publica un tweet nuevo". Se mostrarán algunos campos para llenar, primero se pedirá:

   - **Un nombre de la conexión**: Cualquiera.
   - **Authentication Type**: Use default shared application.
     Al finalizar lo anterior deberemos iniciar sesión con nuestra cuenta de Twitter. Seguidamente, se elige lo siguiente:
   - **Texto e búsqueda**: El texto que será buscado y que nos servirá como "trigger" después, en este caso es #iawizzards.
   - **¿Con qué frecuecia quiere comprobar elementos**: Elegir cualquiera opción que el usuario desee.

   Al finalizar lo anterior, damos click en **"Nuevo paso"**.
   ![Llenar campos de twitter cuando se publica un tweet nuevo](img/7.png)

8. En el siguiente paso haremos una búsqueda por "azure cognitive", al seleccionarlo, se desplegará una lista. Seleccionamos "Sentimientos (V3.0)" para detectar el sentimiento con el que se coloca el mensaje con #iawizzards en Twitter.
   ![Búsqueda Cognitive Services](img/8.png)

9. Al terminar la selección anterior, se mostrará una ventana con los siguientes campos:

   - Nombre de la conexión.
   - Tipo de autenticación.
   - Clave de cuenta
   - URL del sitio.

   Para proseguir, es necesario ir al siguiente paso que se muestra a continuación a partir del paso número 10.

   ![Campos para Azure Cognitive Service for Language](img/9.png)

10. Abrimos otra pestaña en el navegador y buscamos en el [Portal Azure](https://portal.azure.com) **Cognitive Services**. Dentro de Cognitive Services buscamos **Servicio de lenguaje** y seleccionamos **Crear**.
    ![Cognitive Services Ventana](img/10.png)

11. En la nueva ventana simplemente se da click en **Continuar con la creación del recurso**.
    ![Características adicionales](img/11.png)

12. Llenamos los campos que son obligatorios con la información necesaria.

    - Una suscripción.
    - Grupo de recursos.
    - Región.
    - Nombre.
    - Plan de tarifa (free).

![Llenado de campos de Cognitive Services](img/12.png)

13. Abrimos otra pestaña en el navegador y buscamos en el [Portal Azure](https://portal.azure.com) **Cognitive Services**. Dentro de Cognitive Services buscamos **Servicio de lenguaje** y seleccionamos **Crear**.
    ![Creacuñon de Servicio Cognitive](img/13.png)

14. Esperamos a que se implemente el servicio y después damos click en **Ir al recurso**.
    ![Implementación del servicio](img/14.png)

15. Nos vamos al apartado de **Claves y puntos de conexión y copiamos la **Clave 1** y **Exremo**. Esto lo pegaremos en la ventana del **diseñador de Logic App\*\*.
    ![Claves del servicio de lenguaje](img/15.png)

16. De esta manera deberían de quedar los campos llenos. Al hacer eso, damos click en crear.
    ![Llenado de campos en el diseñador de aplicaciones lógicas](img/18.png)

17. En la siguiente ventana llenamos lo siguiente:

- **Document Id**: Id de tweet
- **Documents text**: Texto del tweet

Al finaliar damos click en **Nuevo Paso**.
![Llenado de campos de Sentimiento V3](img/19.png)

18. Buscamos **Google Sheets**.
    ![Búsqueda Google Sheets](img/20.png)

19. Seleccionamos la opción de **Insertar Fila**.
    ![Insertar Fila](img/21.png)

20. Pedirá iniciar sesión con la cuenta de Google que deseemos.
    ![Inicio de sesión en Google](img/22.png)

21. Damos click en la carpeta que aparece al lado derecho del campo **Archivo**. Buscamos el archivo Google Sheets creado en Google Drive. En el campo de abajo buscamos la hoja de cálculo a utilizar. **IMPORTANTE si la hoja de cálculo no aparece debe eliminarse el paso actual y volverlo a crear.**
    ![Llenado de cmapos de Google Sheet](img/23.png)

22. Aparecerá un nuevo input (add new parameter) al llenar los inputs del paso anterior. Debemos seleccionarlo y añadir los parámetros que se necesiten. Posteriormente, cada campo se llenará con la información que le corresponda tal y como se muestra en la imágen. En el apartado de **sentimiento** buscamos y seleccionamos **sentiment**. Al finalizar, creamos una acción.
    ![Llenando información a obtener del tweet](img/24.png)

23. Seleccionamos Microsoft Teams **Publicar mensaje en un chat o canal**.
    ![Usando conector para Teams](img/25.png)

24. Al finalizar el paso anterior también pedirá inicio de sesión para Microsoft Teams.
    ![Inicio de sesión en Teams](img/26.png)

25. Llenamos los campos correspondientes. Se necesita:

    - **Publicar Como**: Bot de Flow.
    - **Publicar en**: Canal.
    - **Equipo**: Seleccionar un equipo de Microsoft Teams.
    - **Canal**: Canal del equipo a utilizar.
    - **Mensaje**: Colocamos un mensaje personalizado. Podemos hacer uso de el **"Texto del Tweet"**, **"Twiteado por"**, etc.
      ![Usando conector para Teams](img/27.png)

26. Para hacer una prueba, damos click en **Ejecutar desencadenador**, nos vamos a Twitter y colocamos un nuevo tweet con el # de #iawizzards o el # que configuramos.
    ![Ejecutando desencadenador](img/30.png)

27. Para hacer una prueba, nos vamos a Twitter y colocamos un nuevo tweet con el # de #iawizzards o el # que configuramos.
    ![Esperar mensaje de desencadenador](img/31.png)

28. Por cada tweet con el # configurado se activará el desencadenador.
    ![Esperar mensaje de desencadenador](img/32.png)

29. Si entramos al canal de Teams configurado podrá verse nuestro mensaje.
    ![Esperar mensaje de desencadenador](img/33.png)

30. También en el Google Sheet se guardará la información.
    ![Esperar mensaje de desencadenador](img/34.png)
