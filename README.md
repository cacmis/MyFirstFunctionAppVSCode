># Pasos para replicar el ejemplo
___
>### Son necesarias las siguientes extensionas y herramientas
___
 - [Net 6.0 SDK](https://dotnet.microsoft.com/en-us/download)
 - [Azure Functions Core Tools](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cmacos%2Ccsharp%2Cportal%2Cbash#v2)
 - [Azure CLI version 2.4 o superior](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
 - [C# extension para VSCode](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)
 - [Azure Functions extencion para VSCode](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)

Despues de instalar las herramientas siga los siguientes pasos

1.- Abrir la extensión de Azure function es un icono de A en los iconos de la ezquierda

2.- En el apartado workspace local click en el boton "+" y seleccionar crear Function

3.- Seleccionar crear nuevo projecto 

4.- Seleccionar el lenguaje C#

5.- Runtime .Net 6

6.- Template HttpTrigger

7.- Nombre de la función HttpExample u otro nombre

8.- Namespace My.Function u otro nombre

9.- Nivel de autorización "Anonimous"  

    Level value	Description
        anonymous	No API key is required.
        function	A function-specific API key is required. This is the default value when a level isn't specifically set.
        admin	The master key is required.

10.- Creara la funcion y sus configuraciones necesarias

11.- Precio F5 o ejecute el siguiente comando

        func start
        func start --port numeropuerto // esta opción es por si el puerto esta siendo utilizado por otra functionapp

12.- En la extencion de Azure (icono A) posicionarse en workspace local, 
    click con boton derecho sobre el nombre de la FunctionApp => ejecutar funcion ahor

13.- Porbar la función donde le sea mas comodo
 - Copiando la url en el navegador
 - Postman metodos GET y POST
 - Extension de VSCode Tunder Client GET y POST 
 - Url Function:

        HttpTriggerExameple: [GET,POST] http://localhost:7071/api/HttpTriggerExameple

---
>## Crear Azure Function in AZURE desde VSCode
***
1.- Abrir la paleta de comando de VSCode (menu Terminal => Paleta de comandos)
2.- Escribir Azure: Sign In
 - Se abrira el navegador y solicitara las credenciales de la cuenta de Azure
 - Ingresar las credenciales e inciar sesión
 - Regresar a VSCode

3.- En la paleta de comandos excribir 

    Create Function App in Azure
 - Escribir un nombre para su Function App debe ser unico en todo Azure
 - Selecciones Net 6 como runtime
 - Seleccione una ubicacion cerca de usted (region de Azure: East US, Central US, ...)
 - Enter para aceptar y espere a que termine le proceso de creación le notificara cuando termine

4.- Este proceso creara la funcion el grupo de recurso y demas configruaciones necesarias para poder ejecutar el servicio

___
>## Publicar Functions App creada en VSCode en el servicio de Azure 
___

1.- En las opciones de la extensión de Azure Function icono A, ubiquese en el WROKSPACE local

2.- Click en el icono de Deploy o Publciar segun el idioma y hacer click en Publciar Funcion App (Deploy to Function App)

3.- Le pedira que seleccione el nombre de la Function App donde se va publicar, seleccione la creada en los pasos de crear Function App en Azure

4.- Aceptar deploy y esperar a que termine de publicar en Azure

5.- En la notificacion dar click en la opción View Output
 - Mostrara en los recursos de Function App el nombre de la función ya publicada
 
6.- Ejecutar la funcion y probar
 - Expandir el nombre de la Function App 
 - Expandir Functions y ubicar el nombre de nuestra función
 - Click derecho dobre el nombre de la función y Ejecutar Funcion ahora (Execute Function Now)
 - Le mostrar en la paleta de comandos el request para probar la funcion, precione enter para confirmar ( si lo desea puede cambiar la palabra "azure" por otro valor)

        { "name": "Azure" }.
 - En la notificaciones le mostrara la respuesta (response) de la función 

7.- Borrar los recursos si ya no se van a utilizar para evitar cargos inecesarios

 - Desde el portal de Azure ubique el grupo de recursos de la Function App y opcion borrar
 - Desde VSCode en la paleta de comandos escriba Delete Resource Group y seleccione el grupo de recursos que desea borrar
   - Opcion Ok
   - Le pedira que confirme el nombre del recurso, Ingreselo y de enter para aceptar el borrado
   -  El borrado comenzara y cuando termine le notificara en VSCode
 - Desde Linea de comandos Azure CLI ejecute el siguiente comando

        az group delete --name NombreDelGrupoDeRecursos

## Terminado 