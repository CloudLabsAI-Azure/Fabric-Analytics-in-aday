 ![](../Images/lab-04/image.png)

## Content

[Presentación](#presentación)

[Flujo de datos Gen2](#flujo-de-datos-gen2)

 - [Tarea 1: Copiar consultas de Snowflake al flujo de datos](#tarea-1-copiar-consultas-de-snowflake-al-flujo-de-datos)

 - [Tarea 2: Crear una conexión a Snowflake](#tarea-2-crear-una-conexión-a-snowflake)

 - [Tarea 3: Configurar el destino de datos para las consultas de Supplier
y PO](#tarea-3-configurar-el-destino-de-datos-para-las-consultas-de-supplier-y-po)

 - [Tarea 4: Cambiar el nombre y publicar el flujo de datos de Snowflake](#tarea-4-cambiar-el-nombre-y-publicar-el-flujo-de-datos-de-snowflake)

 - [Tarea 5: Copiar consultas de Dataverse al flujo de datos](#tarea-5-copiar-consultas-de-dataverse-al-flujo-de-datos)

 - [Tarea 6: Crear una conexión a Dataverse](#tarea-6-crear-una-conexión-a-dataverse)

 - [Tarea 7: Crear un destino de datos para la consulta Customer](#tarea-7-crear-un-destino-de-datos-para-la-consulta-customer)

 - [Tarea 8: Publicar y cambiar el nombre del flujo de datos de Dataverse](#tarea-8-publicar-y-cambiar-el-nombre-del-flujo-de-datos-de-dataverse)

 - [Tarea 9: Copiar consultas de SharePoint al flujo de datos](#tarea-9-copiar-consultas-de-sharepoint-al-flujo-de-datos)

 - [Tarea 10: Crear una conexión a SharePoint](#tarea-10-crear-una-conexión-a-sharepoint)

 - [Tarea 11: Configurar el destino de datos para la consulta People](#tarea-11-configurar-el-destino-de-datos-para-la-consulta-people)

 - [Tarea 12: Publicar y cambiar el nombre del flujo de datos de SharePoint](#tarea-12-publicar-y-cambiar-el-nombre-del-flujo-de-datos-de-sharepoint)

[Referencias](#referencias)

# Presentación

En nuestro escenario, los datos del proveedor están en Snowflake, los datos del cliente están

en Dataverse y los datos de los empleados están en SharePoint. Todos estos orígenes de datos se actualizan en diferentes momentos. Para minimizar la cantidad de actualizaciones de datos de los flujos de datos, crearemos flujos de datos individuales para cada uno de estos orígenes de datos.

**Nota:** Se admiten varios orígenes de datos en un único flujo de datos. Al final de este laboratorio, habrá aprendido:

-   Cómo conectarse a Snowflake mediante el flujo de datos Gen2 e ingerir datos en lakehouse

-   Cómo conectarse a SharePoint mediante el flujo de datos Gen2 e ingerir datos en lakehouse

-   Cómo conectarse a Dataverse mediante el flujo de datos Gen2 e ingerir datos en lakehouse

# Flujo de datos Gen2

## Tarea 1: Copiar consultas de Snowflake al flujo de datos

1.  Volvamos al área de trabajo de Fabric, **FAIAD\_\<username\**, que creó en el Laboratorio 2, Tarea 9.

2.  En el menú superior, seleccione **Nuevo -\ Flujo de datos Gen2**.

    ![](../Images/lab-04/image006.png)

Se le dirigirá de vuelta a la **página de del flujo de datos**. Ahora que estamos familiarizados con el flujo de datos, sigamos adelante y copiemos las consultas de Power BI Desktop en el flujo de datos.

3.  Si aún no lo ha abierto, abra **FAIAD.pbix**, que se encuentra en la carpeta **C:\\FAIAD\\Reports** del entorno de laboratorio.

4.  En la cinta de opciones, seleccione **Inicio -> Transformar datos**. Se abre la ventana de Power Query. Como habrá notado en la práctica de laboratorio anterior, las consultas en el panel izquierdo están organizadas por orígenes de datos.

5.  Se abre la ventana de Power Query. Desde el panel izquierdo, en la carpeta SnowflakeData

    **Ctrl+Seleccionar** o Mayús+Seleccionar las siguientes consultas:

    a.  SupplierCategories

    b.  Suppliers

    c.  Supplier

    d.  PO

    e.  PO Line Items

6.  **Haga clic derecho** y seleccione **Copiar**.

    ![](../Images/lab-04/image009.png)

7.  Vuelva al **explorador**.

8.  En el **panel del flujo de datos**, seleccione el **panel central**, introduzca **Ctrl+V** (actualmente, hacer clic con el botón derecho en Pegar no es compatible). Si está utilizando un dispositivo MAC,

    utilice Cmd+V para pegar.

**Nota**: Si está trabajando en el entorno de laboratorio, seleccione los puntos suspensivos en la parte superior derecha de la pantalla. Utilice el control deslizante para **habilitar Portapapeles nativo de VM**. Seleccione Aceptar en el cuadro de diálogo. Una vez que haya terminado de pegar las consultas, puede desactivar esta opción.

![](../Images/lab-04/image012.jpg)

## Tarea 2: Crear una conexión a Snowflake

Observe que las cinco consultas están pegadas y ahora tiene el panel Consultas a la izquierda. Como no tenemos una conexión creada para Snowflake, verá un mensaje de advertencia que le solicitará que configure la conexión.

1.  Seleccione **Configurar conexión**.

    ![](../Images/lab-04/image015.jpg)

2.  Se abre el cuadro de diálogo del origen de datos. En el menú desplegable **Conexión**, asegúrese de que **Crear nueva conexión** esté seleccionado.

3.  **El tipo de autenticación** debe ser **Snowflake**.

4.  Introduzca el **Nombre de usuario y contraseña de Snowflake** disponibles en la pestaña Variables de entorno (al lado de la pestaña Guía de laboratorio).

5.  Seleccione **Conectar**.

    ![](../Images/lab-04/image018.png)

Se establece la conexión y puede ver los datos en el panel de versión preliminar. Siéntase libre de navegar por los pasos aplicados de las consultas. Básicamente, la consulta Suppliers tiene los detalles de los proveedores y SupplierCategories, como su nombre indica, tiene categorías de proveedores.

Estas dos tablas se unen para crear la dimensión Supplier, con las columnas que necesitamos. De

manera similar, tenemos PO Line Items combinada con pedidos de compra para crear el dato de PO. Ahora necesitamos incorporar los datos del proveedor y de PO en el lakehouse.

6.  Como se mencionó anteriormente, no vamos a almacenar provisionalmente ninguno de estos datos. Así que **haga clic derecho** en la consulta **Supplier** en el panel Consultas y seleccione

**Habilitar el almacenamiento provisional** para eliminar la marca de verificación.

![](../Images/lab-04/image021.png)

7.  De manera similar, haga clic derecho en la consulta **PO**. Seleccione **Habilitar el almacenamiento provisional** para eliminar la marca de verificación.

**Nota:** No tenemos que deshabilitar el almacenamiento provisional para las otras tres consultas porque Habilitar carga se deshabilitó en Power BI Desktop (desde donde se copiaron estas consultas).

## Tarea 3: Configurar el destino de datos para las consultas de Supplier y PO

1.  Seleccione la consulta de **Supplier**.

2.  En la cinta de opciones, seleccione **Inicio -> Agregar destino de datos -> Lakehouse**.

    ![](../Images/lab-04/image024.jpg)

3.  Se abre el cuadro de diálogo Conectarse al destino de datos. Desde el **menú desplegable de Conexión**, seleccione **Lakehouse (ninguno)**.

4.  Seleccione **Siguiente**.

    ![](../Images/lab-04/image027.png)

5.  Se abre el cuadro de diálogo de Elegir el objetivo de destino. Asegúrese de que el botón de opción **Nueva tabla** esté **seleccionado**, ya que estamos creando una nueva tabla.

6.  Queremos crear la tabla en el lakehouse que creamos anteriormente. En el panel izquierdo, navegue hasta **Lakehouse -> FAIAD\_\<username\.**

7.  Seleccione **lh_FAIAD**.

8.  Deje el nombre de la tabla como **Supplier**.

9.  Seleccione **Siguiente**.

    ![](../Images/lab-04/image030.png)

10. Se abre el cuadro de diálogo de configuración de Elegir la configuración de destino. Esta vez usaremos la configuración automática, ya que esto realizará una actualización completa de los datos. Además, cambiará el nombre de las columnas según sea necesario. Seleccione **Guardar configuración**.

    ![](../Images/lab-04/image033.jpg)

11. Volverá a la **ventana de Power Query**. Observe que en la **esquina inferior derecha, el destino de los datos** está configurado en el **lakehouse**. De manera similar, **configure el destino de datos para la consulta de PO**. Una vez hecho esto, su consulta de PO debe tener **Destino de datos** establecido en **Lakehouse** como se muestra en la siguiente captura de pantalla.

    ![](../Images/lab-04/image036.jpg)

## Tarea 4: Cambiar el nombre y publicar el flujo de datos de Snowflake

1.  En la parte superior de la pantalla, seleccione la **flecha junto a Dataflow 2** para cambiar el nombre.

2.  En el cuadro de diálogo, cambie el nombre a **df_Supplier_Snowflake**.

3.  Haga clic en **Introducir** para guardar el cambio de nombre.

    ![](../Images/lab-04/image039.png)

4.  En la esquina inferior derecha, seleccione **Publicar**.

    ![](../Images/lab-04/image042.jpg)

Se le dirigirá de vuelta al **área de trabajo FAIAD\_\<username\**. Es posible que el flujo de datos tarde unos minutos en publicarse. Ahora creemos un flujo de datos para traer datos de Dataverse.

## Tarea 5: Copiar consultas de Dataverse al flujo de datos

1.  En el menú superior, seleccione **Nuevo -\ Flujo de datos Gen2**.

    ![](../Images/lab-04/image045.png)

Se le dirigirá de vuelta a la **página del flujo de datos**. Ahora que estamos familiarizados con el flujo de datos, sigamos adelante y copiemos las consultas de Power BI Desktop en el flujo de datos.

2.  Si aún no lo ha abierto, abra **FAIAD.pbix**, que se encuentra en la carpeta **C:\\FAIAD\\Reports** del entorno de laboratorio.

3.  En la cinta de opciones, seleccione **Inicio -> Transformar datos**. Se abre la ventana de Power Query. Como habrá notado en la práctica de laboratorio anterior, las consultas en el panel izquierdo están organizadas por orígenes de datos.

4.  Se abre la ventana de Power Query. Desde el panel izquierdo, en la carpeta DataverseData,

    **Ctrl+Seleccionar** las siguientes consultas:

    a.  BabyBoomer

    b.  GenX

    c.  GenY

    d.  GenZ

    e.  Customer

5.  **Haga clic derecho** y seleccione **Copiar**.

    ![](../Images/lab-04/image048.png)

6.  Vuelva a la ventana **Página del flujo de datos** en su explorador.

7.  En el **panel del flujo de datos**, introduzca **Ctrl+V** (actualmente, hacer clic con el botón derecho en Pegar no es compatible). Si está utilizando un dispositivo MAC, utilice Cmd+V para pegar.

**Nota**: Si está trabajando en el entorno de laboratorio, seleccione los puntos suspensivos en la parte superior derecha de la pantalla. Utilice el control deslizante para **habilitar Portapapeles nativo de VM**. Seleccione Aceptar en el cuadro de diálogo. Una vez que haya terminado de pegar las consultas, puede desactivar esta opción.

## Tarea 6: Crear una conexión a Dataverse

Observe que las cinco consultas están pegadas y ahora tiene el panel Consultas a la izquierda. Como no tenemos una conexión creada para Dataverse, verá un mensaje de advertencia que le solicitará que configure la conexión.

1.  Seleccione **Configurar conexión**.

    ![](../Images/lab-04/image051.jpg)

2.  Se abre el cuadro de diálogo del origen de datos. En el **menú desplegable Conexión**, asegúrese de que **Crear nueva conexión** esté **seleccionado**.

3.  **Tipo de autenticación** debería ser **Cuenta de organización**.

4.  Seleccione **Conectar**.

    ![](../Images/lab-04/image054.png)

## Tarea 7: Crear un destino de datos para la consulta Customer

Se establece la conexión y puede ver los datos en el panel de versión preliminar. Siéntase libre

de navegar por los pasos aplicados de las consultas. Los datos de los clientes están disponibles por categoría: BabyBoomer, GenX, GenY y GenZ. Estas cuatro consultas se adjuntan para crear la consulta Customer. Ahora necesitamos incorporar los datos del cliente en el lakehouse.

1.  Como se mencionó anteriormente, no vamos a almacenar provisionalmente ninguno de estos datos. Así que **haga clic derecho** en la consulta **Customer** en el panel Consultas y seleccione **Habilitar el almacenamiento provisional** para eliminar la marca de verificación.

    ![](../Images/lab-04/image057.png)

2.  Seleccione la consulta **Customer**.

3.  En la cinta de opciones, seleccione **Inicio -> Agregar destino de datos -> Lakehouse**.

    ![](../Images/lab-04/image060.jpg)

4.  Se abre el cuadro de diálogo Conectarse al destino de datos. Desde el **menú desplegable de Conexión**, seleccione **Lakehouse (ninguno)**.

5.  Seleccione **Siguiente**.

    ![](../Images/lab-04/image063.png)

6.  Se abre el cuadro de diálogo de Elegir el objetivo de destino. Asegúrese de que el **botón de opción Nueva tabla** esté seleccionado, ya que estamos creando una nueva tabla.

7.  Queremos crear la tabla en el lakehouse que creamos anteriormente. En el panel izquierdo, navegue hasta **Lakehouse -> FAIAD\_\<username\**.

8.  Seleccione **lh_FAIAD**.

9.  Deje el nombre de la tabla como **Customer**.

10. Seleccione **Siguiente**.

    ![](../Images/lab-04/image066.png)

11. Se abre el cuadro de diálogo de Elegir la configuración de destino. Esta vez usaremos la configuración automática, ya que esto realizará una actualización completa de los datos. Además, cambiará el nombre de las columnas según sea necesario. Seleccione **Guardar configuración**.

    ![](../Images/lab-04/image069.png)

## Tarea 8: Publicar y cambiar el nombre del flujo de datos de Dataverse

1.  Volverá a la **ventana de Power Query**. Observe que en la **esquina inferior derecha**, el **destino de los datos** está configurado en el **lakehouse**.

2.  En la esquina inferior derecha, seleccione **Publicar**.

    ![](../Images/lab-04/image072.jpg)

**Nota:** Se le dirigirá de vuelta al área de trabajo **FAIAD\_\<username\**. Es posible que el flujo de datos tarde unos minutos en publicarse.

3.  Estamos trabajando con Dataflow 2. Cambiémosle el nombre antes de continuar. Haga clic en los

    **puntos suspensivos (...)** junto a Dataflow 2. Seleccione**Propiedades**.

    ![](../Images/lab-04/image075.jpg)

4.  Se abre el cuadro de diálogo de propiedades del flujo de datos. Cambie el **Nombre**

    a df_Customer_Dataverse.

5.  En el cuadro de texto **Descripción**, agregue **Dataflow to ingest Customer data from Dataverse to Lakehouse**.

6.  Seleccione **Guardar**.

    ![](../Images/lab-04/image078.png)

Se le dirigirá de vuelta al **área de trabajo FAIAD\_\<username\**. Ahora creemos un flujo de datos para traer datos de SharePoint.

## Tarea 9: Copiar consultas de SharePoint al flujo de datos

1. En el menú superior, seleccione **Nuevo -\ Flujo de datos Gen2**.

    ![](../Images/lab-04/image084.png)

Se le dirigirá de vuelta a la **página de del flujo de datos**. Ahora que estamos familiarizados con el flujo de datos, sigamos adelante y copiemos las consultas de Power BI Desktop en el flujo de datos.

2.  Si aún no lo ha abierto, abra **FAIAD.pbix**, que se encuentra en la carpeta **C:\\FAIAD\\Reports** del entorno de laboratorio.

3.  En la cinta de opciones, seleccione **Inicio -> Transformar datos**. Se abre la ventana de Power Query. Como habrá notado en la práctica de laboratorio anterior, las consultas en el panel izquierdo están organizadas por orígenes de datos.

4.  Se abre la ventana de Power Query. En el panel izquierdo, en la carpeta SharepointData,

    **seleccione** la consulta **People**.

5. **Haga clic derecho** y seleccione **Copiar**.

    ![](../Images/lab-04/image083.png)

6. Vuelva a la **pantalla del flujo de datos** en el explorador.

7. En el **panel del flujo de datos**, introduzca **Ctrl+V** (actualmente, hacer clic con el botón derecho en Pegar no es compatible).

**Nota**: Si está trabajando en el entorno de laboratorio, seleccione los puntos suspensivos en la parte superior derecha de la pantalla. Utilice el control deslizante para **habilitar Portapapeles nativo de VM**. Seleccione Aceptar en el cuadro de diálogo. Una vez que haya terminado de pegar las consultas, puede desactivar esta opción.

Observe la consulta pegada y disponible en el panel izquierdo. Como no tenemos una conexión

creada para SharePoint, verá un mensaje de advertencia que le solicitará que configure la conexión.

## Tarea 10: Crear una conexión a SharePoint

1.  Seleccione **Configurar conexión**.

    ![](../Images/lab-04/image095.jpg)

2.  Se abre el cuadro de diálogo del origen de datos. En el menú desplegable **Conexión**, asegúrese de que **Crear nueva conexión** esté seleccionado.

3.  **Tipo de autenticación** debería ser **Cuenta de organización**.

4.  Seleccione **Conectar**.

    ![](../Images/lab-04/image089.jpg)

## Tarea 11: Configurar el destino de datos para la consulta People

Se establece la conexión y puede ver los datos en el panel de versión preliminar. Siéntase libre de navegar por los pasos aplicados de las consultas. Ahora necesitamos incorporar los datos de las

personas en el lakehouse.

1.  Como se mencionó anteriormente, no vamos a almacenar provisionalmente ninguno de estos datos. Así que **haga clic derecho** en la consulta **People** en el panel Consultas y seleccione

    **Habilitar el almacenamiento provisional** para eliminar la marca de verificación.

    ![](../Images/lab-04/image092.png)

2.  Seleccione la consulta **People**.

3.  En la cinta de opciones, seleccione **Inicio -> Agregar destino de datos -> Lakehouse**.

    ![](../Images/lab-04/image095.jpg)

4.  Se abre el cuadro de diálogo Conectarse al destino de datos. Desde el **menú desplegable de Conexión**, seleccione **Lakehouse (ninguno)**.

5.  Seleccione **Siguiente**.

    ![](../Images/lab-04/image098.png)

6.  Se abre el cuadro de diálogo de Elegir el objetivo de destino. Asegúrese de que el **botón de opción Nueva tabla** esté seleccionado, ya que estamos creando una nueva tabla.

7.  Queremos crear la tabla en el lakehouse que creamos anteriormente. En el panel izquierdo, navegue hasta **Lakehouse -\ FAIAD\_\<username\.**

8.  Seleccione **lh_FAIAD**.

9.  Deje el nombre de la tabla como **People**.

10. Seleccione **Siguiente**.

    ![](../Images/lab-04/image101.png)

11. Esta vez usaremos la configuración automática, ya que esto realizará una actualización completa de los datos. Además, cambiará el nombre de las columnas según sea necesario. Seleccione **Guardar configuración**.

    ![](../Images/lab-04/image104.png)

## Tarea 12: Publicar y cambiar el nombre del flujo de datos de SharePoint

1.  Volverá a la **ventana de Power Query**. Observe que en la **esquina inferior derecha**, el destino de los datos está configurado en el **lakehouse**.

2.  En la esquina inferior derecha, seleccione **Publicar**.

    ![](../Images/lab-04/image107.jpg)

**Nota:** Se le dirigirá de vuelta al área de trabajo **FAIAD\_\<username\**. Es posible que el flujo de datos tarde unos minutos en publicarse.

3.  Estamos trabajando con Dataflow 2. Cambiémosle el nombre antes de continuar. Haga clic en los

    **puntos suspensivos (...)** junto a Dataflow 2. Seleccione **Propiedades**.

    ![](../Images/lab-04/image110.jpg)

4.  Se abre el cuadro de diálogo de propiedades del flujo de datos. Cambie el **nombre**

    a **df_People_SharePoint.**

5.  En el cuadro de texto **Descripción**, agregue **Dataflow to ingest People data from SharePoint to Lakehouse**.

6.  Seleccione **Guardar**.

    ![](../Images/lab-04/image113.png)

Se le dirigirá de vuelta al **área de trabajo FAIAD\_\<username\**. Ahora hemos ingerido todos los datos en el lakehouse. En la próxima práctica de laboratorio, programaremos la actualización del flujo de datos.

# Referencias

Fabric Analyst in a Day (FAIAD) le presenta algunas funciones clave disponibles en Microsoft Fabric. En el menú del servicio, la sección Ayuda (?) tiene vínculos a algunos recursos excelentes.

![](../Images/lab-04/image116.png)

Estos son algunos recursos más que podrán ayudarle a seguir avanzando con Microsoft Fabric.

-   Vea la publicación del blog para leer el [anuncio de disponibilidad general de Microsoft Fabric](https://aka.ms/Fabric-Hero-Blog-Ignite23) completo.

-   Explore Fabric a través de la [Visita guiada](https://aka.ms/Fabric-GuidedTour)

-   Regístrese en la [prueba gratuita de Microsoft Fabric](https://aka.ms/try-fabric)

-   Visite el [sitio web de Microsoft Fabric](https://aka.ms/microsoft-fabric)

-   Adquiera nuevas capacidades mediante la exploración de los [módulos de aprendizaje de Fabric](https://aka.ms/learn-fabric)

-   Explore la [documentación técnica de Fabric](https://aka.ms/fabric-docs)

-   Lea el [libro electrónico gratuito sobre cómo empezar a usar Fabric](https://aka.ms/fabric-get-started-ebook)

-   Únase a la [comunidad de Fabric](https://aka.ms/fabric-community) para publicar sus preguntas, compartir sus comentarios y aprender de otros.

Obtenga más información en los blogs de anuncios de la experiencia Fabric:

-   [Experiencia de Data Factory en el blog de Fabric](https://aka.ms/Fabric-Data-Factory-Blog)

-   [Experiencia de Synapse Data Engineering en el blog de Fabric](https://aka.ms/Fabric-DE-Blog)

-   [Experiencia de Synapse Data Science en el blog de Fabric](https://aka.ms/Fabric-DS-Blog)

-   [Experiencia de Synapse Data Warehousing en el blog de Fabric](https://aka.ms/Fabric-DW-Blog)

-   [Experiencia de Synapse Real-Time Analytics en el blog de Fabric](https://aka.ms/Fabric-RTA-Blog)

-   [Blog de anuncios de Power BI](https://aka.ms/Fabric-PBI-Blog)

-   [Experiencia de Data Activator en el blog de Fabric](https://aka.ms/Fabric-DA-Blog)

-   [Administración y gobernanza en el blog de Fabric](https://aka.ms/Fabric-Admin-Gov-Blog)

-   [OneLake en el blog de Fabric](https://aka.ms/Fabric-OneLake-Blog)

-   [Blog de integración de Dataverse y Microsoft Fabric](https://aka.ms/Dataverse-Fabric-Blog)

 
 
© 2023 Microsoft Corporation. Todos los derechos reservados.

Al participar en esta demostración o laboratorio práctico, acepta las siguientes condiciones:

Microsoft Corporation pone a su disposición la tecnología o funcionalidad descrita en esta demostración/laboratorio práctico con el fin de obtener comentarios por su parte y de facilitarle una experiencia de aprendizaje. Esta demostración/laboratorio práctico solo se puede usar para evaluar las características de tal tecnología o funcionalidad y para proporcionar comentarios a Microsoft. No se puede usar para ningún otro propósito. Ninguna parte de esta demostración/laboratorio práctico se puede modificar, copiar, distribuir, transmitir, mostrar, realizar, reproducir, publicar, licenciar, transferir ni vender, ni tampoco crear trabajos derivados de ella.

LA COPIA O REPRODUCCIÓN DE ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO (O PARTE DE ELLA) EN CUALQUIER OTRO SERVIDOR O UBICACIÓN PARA SU REPRODUCCIÓN O DISTRIBUCIÓN POSTERIOR QUEDA EXPRESAMENTE PROHIBIDA.

ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO PROPORCIONA CIERTAS FUNCIONES Y CARACTERÍSTICAS DE PRODUCTOS O TECNOLOGÍAS DE SOFTWARE (INCLUIDOS POSIBLES NUEVOS CONCEPTOS Y CARACTERÍSTICAS) EN UN ENTORNO SIMULADO SIN INSTALACIÓN O CONFIGURACIÓN COMPLEJA PARA EL PROPÓSITO ARRIBA DESCRITO. LA TECNOLOGÍA/CONCEPTOS DESCRITOS EN ESTA DEMOSTRACIÓN/LABORATORIO PRÁCTICO NO REPRESENTAN LA FUNCIONALIDAD COMPLETA DE LAS CARACTERÍSTICAS Y, EN ESTE SENTIDO, ES POSIBLE QUE NO FUNCIONEN DEL MODO EN QUE LO HARÁN EN UNA VERSIÓN FINAL. ASIMISMO, PUEDE QUE NO SE PUBLIQUE UNA VERSIÓN FINAL DE TALES CARACTERÍSTICAS O CONCEPTOS. DE IGUAL MODO, SU EXPERIENCIA CON EL USO DE ESTAS CARACTERÍSTICAS Y FUNCIONALIDADES EN UN ENTORNO FÍSICO PUEDE SER DIFERENTE.

**COMENTARIOS**. Si envía comentarios a Microsoft sobre las características, funcionalidades

o conceptos de tecnología descritos en esta demostración/laboratorio práctico, acepta otorgar a Microsoft, sin cargo alguno, el derecho a usar, compartir y comercializar sus comentarios de

cualquier modo y para cualquier fin. También concederá a terceros, sin cargo alguno, los derechos de patente necesarios para que sus productos, tecnologías y servicios usen o interactúen con cualquier parte específica de un software o servicio de Microsoft que incluya los comentarios.

No enviará comentarios que estén sujetos a una licencia que obligue a Microsoft a conceder su software o documentación bajo licencia a terceras partes porque incluyamos sus comentarios en ellos. Estos derechos seguirán vigentes después del vencimiento de este acuerdo.

MICROSOFT CORPORATION RENUNCIA POR LA PRESENTE A TODAS LAS GARANTÍAS Y CONDICIONES RELATIVAS A LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO, INCLUIDA CUALQUIER GARANTÍA Y CONDICIÓN DE COMERCIABILIDAD (YA SEA EXPRESA, IMPLÍCITA O ESTATUTARIA), DE IDONEIDAD PARA UN FIN DETERMINADO, DE TITULARIDAD Y DE AUSENCIA DE INFRACCIÓN.

MICROSOFT NO DECLARA NI GARANTIZA LA EXACTITUD DE LOS RESULTADOS, EL RESULTADO DERIVADO DE LA REALIZACIÓN DE LA DEMOSTRACIÓN/LABORATORIO PRÁCTICO NI LA

IDONEIDAD DE LA INFORMACIÓN CONTENIDA EN ELLA CON NINGÚN PROPÓSITO.

### DECLINACIÓN DE RESPONSABILIDADES

Esta demostración/laboratorio práctico contiene solo una parte de las nuevas características y mejoras realizadas en Microsoft Power BI. Puede que algunas de las características cambien en versiones futuras del producto. En esta demostración/laboratorio práctico, conocerá algunas de estas nuevas características, pero no todas.

