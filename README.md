# csharp

-----------------------------------------------------------------------------
                              practicasdotnet 
-----------------------------------------------------------------------------

1	CONTROLES

1.1	CREAR UN NUEVO PROYECTO  DE TIPO “WEB SITE” LLAMADO “PRACTICASDOTNET” QUE EMPLEE COMO LENGUAJE C#

1.2	AÑADIR LOS SIGUIENTES CONTROLES (STANDART) EN EL FORMULARIO POR DEFECTO

Tipo	Id / Nombre
Label	lbltitulo
TextBox	txtnombre
CheckBoxList	chkcaracteristicas
RadioButtonList	rdbsexo
Image	imgfoto
Calendar	calcalendario
DropDownList	lstcategorias
Button	btnaceptar

 


1.3	EN EL EVENTO PAGE_LOAD DE LA CLASE DEL FORMULARIO REALIZAR LAS SIGUIENTES OPCIONES RELACIONADAS CON LA INICIALIZACIÓN DE LOS CAMPOS CREADOS EN EL EJERCICIO 1.2
Inicialización de campos:

Id / Nombre	Valor/es iniciales
lbltitulo	Site de prácticas de ASP.NET C#
txtnombre	Introduzca el nombre del usuario
chkcaracteristicas	5 opciones  con los valores:
Piscina
Garaje
Sótano
Balcón
Trastero
rdbsexo	2 opciones:
Hombre
Mujer
imgfoto	Imgfoto
Una imágen de 96x96px (la imagen que desee el programador)
calcalendario	-
lstcategorias	3 opciones:
Procesado
Rechazado
En Curso
btnaceptar	Aceptar

 
HTTP://QUICKSTARTS.ASP.NET/QUICKSTARTV20/ASPNET/DOC/CTRLREF/DATA/GRIDVIEW.ASPX
1.4	AÑADIR UN CONTROL “GRIDVIEW” (SOLAPA DATA DE TOOLBOX) CON EL NOMBRE GRVUSUARIOS
Crear una pequeña BBDD en SQL-SERVER 2005 que contenga una tabla llamada “Usuarios” con los campos

Nombre	Tipo
Usuacodi	Int, autonumérico
Usuanom	Texto – 250
Usuaactivo	Boolean
	Los tipos de campos tienen que ser los equivalentes en SQL-SERVER 2005

Introducir 3 registros de prueba.

Rellenar empleando asistentes los datos del gridview “grvUsuarios” con los contenidos de la BBDD y tabla creada, llamada “Usuarios”.

1.5	CREAR UN NUEVO FORMULARIO LLAMADO “LISTADO.ASPX” Y AÑADIR UN GRIDVIEW LLAMADO GRVDATOS
Rellenar los datos de dicho gridview con los de la tabla “usuarios” sin emplear asistentes del Visual Studio.


2.1	CREAR UNA CLASE LLAMADA “USUARIO.CS” (EN MINÚSCULAS) QUE INCLUYA:
•	Constructor de la clase
•	Atributos PUBLICOS para cada uno de los campos de la tabla “usuarios” creada anteriormente. Los nombres de los atributos tienen que ser los mismos que los campos.
•	Crear Método: getUsuario, que reciba como parámetro el código del usuario y que devuelva:
o	Si se encuentra el registro: return(1), y asignación de cada campo a un atributo publico de la clase
o	Si no se encuentra el registro: return(0)

2.2	HACER UNA LLAMADA DE PRUEBA A LA FUNCIÓN DE 2.1 (DESDE EL ONLOAD DE EL FORMULARIO WEB) ENVIANDO COMO PARÁMETRO EL CÓDIGO DE UN USUARIO EXISTENTE. MOSTRAR LOS DATOS OBTENIDOS EN LABELS.

2.3

•	Crear tabla “peticiones” en SQL-Server con equivalencia de campos:
o	peticodi – int PK: código de petición
o	petinom – string 250: título de la petición
o	petidesc – string 2000: descripción de la petición
o	petifecha – date: fecha de la petición
o	petiestado – int: estado de la petición
•	Crear un label en practicasdotnet.aspx cuyo valor inicial sea text = “”
•	Crear una clase “petición” con los atributos equivalentes a la tabla de BBDD peticiones
•	En “petición.cs” crear un método “getpeticion” que devuelva un string en el que se listen todos los registros de la tabla peticiones.
•	Contemplar el tratamiento de errores y tratamiento de excepciones.

NOTA: Concatenar en cada línea: …. + “<br />”;






-----------------------------------------------------------------------------
                              practicasdotnetAct2
-----------------------------------------------------------------------------

1	WebService

1.1	CREAR UNA BASE DE DATOS  CON UNA TABLA “SERVICIOSCOMPLEMENTARIOS”
Crear una BBDD en SQL Server con las siguientes tablas:

Nombre: ServiciosComplementarios
Campos:
•	SERVCODI – int – PK – código del servicio
•	SERVNOM – string(255) – not null – nombre del servicio
•	SERVPRECIO – int – null(0) – precio del servicio
•	SERVACTIVO – int – null (0)- activo(1); inactivo(0)
•	SECACODI – int – FK – null(0) – FK de código de categoría

//Script Postgres
{

CREATE TABLE public.servicioscomplementarios (
	servcodi numeric NOT NULL,
	servnom varchar(255) NOT NULL,
	servprecio numeric NULL,
	servactivo numeric NULL,
	secacodi numeric NOT NULL,
	CONSTRAINT servicioscomplementarios_pk PRIMARY KEY (servcodi),
	CONSTRAINT servicioscomplementarios_fk FOREIGN KEY (secacodi) REFERENCES public.servicioscomplementarioscategoria(secacodi)
);


}

Nombre: ServiciosComplementariosCategoria
Campos:
•	SECACODI – int – PK – código de la categoría de servicio
•	SECANOM – string(255) – nombre de la categoría

//Script Postgres

{

CREATE TABLE public.servicioscomplementarioscategoria (
	secacodi numeric NOT NULL,
	secanom varchar(255) NULL,
	CONSTRAINT servicioscomplementarioscategoria_pk PRIMARY KEY (secacodi)
);

}


Insertar los siguientes datos:

ServiciosComplementariosCategoria:

SECACODI: 1
SECANOM: Infantil

SECACODI: 2
SECANOM: Playa

SECACODI: 3
SECANOM: Tecnología

SECACODI: 4
SECANOM: Merchandising 

SECACODI: 5
SECANOM: Packs

SECACODI: 6
SECANOM: Ropa

ServiciosComplementarios:

SERVCODI: 1
SERVCODISERVNOM: Coche de color rojo
SERVPRECIO: 10,25
SERVACTIVO: 1
SECACODI: 1

SERVCODI: 2
SERVCODISERVNOM: Coche de color arcoiris
SERVPRECIO: 69,25
SERVACTIVO: 0
SECACODI: 1

SERVCODI: 3
SERVCODISERVNOM: Muñeca Barbie flexible
SERVPRECIO: 20
SERVACTIVO: 1
SECACODI: 1

SERVCODI: 4
SERVCODISERVNOM: Chaqueta azul con bolsillos
SERVPRECIO: 40,32
SERVACTIVO: 1
SECACODI: 6

SERVCODI: 5
SERVCODISERVNOM: Gorra extra grande
SERVPRECIO: 8,15
SERVACTIVO: 1
SECACODI: 6

SERVCODI: 6
SERVCODISERVNOM: Albornoz negro
SERVPRECIO: 20
SERVACTIVO: 0
SECACODI: 6

SERVCODI: 7
SERVCODISERVNOM: Chanclas transparentes
SERVPRECIO: 0
SERVACTIVO: 1
SECACODI: 6


1.2	CREAR CONSULTA BBDD
Crear una consulta a base de datos que devuelve:
•	Todos los productos activos, con precio y  ordenados de más baratos a más caros
•	Listar el nombre de la categoría del producto
1.3	CREAR WEBSERVICE
Crear un nuevo Webservice llamado “Products” con un método getProducts que ejecute la consulta del punto anterior.

El método podrá recibir los siguientes parámetros que interferirán en la consulta:
•	Order: servirá para identificar el tipo de ordenación. Posibles valores:
o	0: precio asc
o	1: precio desc
o	2: nombre asc
o	3: nombre desc

•	Category: filtrar por categoría concreta. Valores:
o	0: NO filtrar por categoría.
o	Otro valor: fitrar por esa categoría.


2	Interactuar con WebService

2.1	PROYECTO WEB
Crear solución Web llamada “PruebaAjax” en C# y Framework 4.0.

2.2	HTML
Crear una sencilla maquetación en HTML para listar los productos que tiene la BBDD de Productos complementarios.

El HTML debe tener todos los campos de la consulta creada en el punto 1.2


2.3	AJAX
Llamar mediante jQuery al Webservice del punto 1, y listar los resultados en lo creado en 2.1 y 2.2.

Los parámetros del método del Webservice deberán ser: getProducts(0,0).

2.4	INTERACTIVIDAD  - ORDEN
Añadir un desplegable HTML llamado “Orden” que liste las siguientes opciones:
Precio Menor-mayor
Precio Mayor-menor
Nombre A-Z
Nombre Z-A

Que tengan los values 0…3 respectivamente.

Añadir un botón “Filtrar”, que al pulsarlo, el sistema vuelva a llamar al Webservice, pero enviando en el parámetro “order” el value seleccionado en este mismo desplegable.

2.5	INTERACTIVIDAD  - CATEGORÍA

Crear un nuevo método en el Webservice llamado getCategories que devuelva todas las categorías de BBDD ordenadas por nombre A-Z.


Añadir un desplegable HTML llamado “Categoría” que contenga todas las categorías listadas en el nuevo método del Webservice.


Añadir un botón “Filtrar”, que al pulsarlo, el sistema vuelva a llamar al Webservice, pero enviando en el parámetro “category” el value seleccionado en este mismo desplegable.

Si no hay resultados que mostrar, mostrar un mensaje de aviso en una capa bajo los filtros para informar al usuario.






-----------------------------------------------------------------------------
                              pruebasDaniel
-----------------------------------------------------------------------------

1	Formularios

1.1	NOMENCLATURAS
•	Emplear nombres cortos en inglés.
•	Los campos de formulario deberán estar precedidos por un acrónimo de 3 caracteres del tipo de campo:
o	lbl – labels
o	txt – textboxes
o	rdb – radiobuttons
o	chk – checkbuttons
o	drp – desplegables
o	dgv – datagridview
o	dtp – datatimepicker
o	btn – button

Ejemplo: btnsave (botón guardar).

•	Todas las funciones tendrán nombres en inglés, y breves comentarios describiendo qué hacen. Ejemplo:
o	getUser(int usercodi)  //obtención del registro de un usuario
o	checkForm() //validación del formulario
o	saveUser() //almacenar datos de usuario
o	etc…


1.2	NUEVO PROYECTO
Crear un nuevo proyecto llamado “pruebasNOMBRE”, donde NOMBRE será tu propio nombre con las siguientes características:
•	VISUAL C# - Windows
•	Windows From Application
•	.NET Framework 4

 


1.3	FORMULARIO
1.	Cambia el nombre de la ventana (propiedad Text) al mismo nombre de tu proyecto.
2.	Renombra el nombre del archivo del formulario a mainAPP.cs.
3.	Cambia el tamaño del formulario a 1024x768px (anchoxalto).
4.	Haz que por defecto, el formulario esté centrado por pantalla.
5.	Añade un botón cuyo texto sea “Detalle”
6.	Ejecuta tu proyecto para comprobar los cambios.

 
 

1.4	INTERACTUAR CON FORMULARIO
•	Crea un nuevo formulario llamado detail.cs
•	Al pulsar el botón “Detalle” de “mainAPP.cs”, se deberá abrir (mostrar) “detail.cs”.
•	Realiza los siguientes cambios:

o	RESULTADO ESPERADO: al escribir en el campo de texto de mainAPP y pulsar en “Detalle”, se abrirá el 2º formulario con el valor introducido en el primero. Si no se ha introducido nada, se mostrará un mensaje de error.

o	detail.cs
	Crea un label con texto: “Nombre” y nombre “lblname” 
	Crea un textBox con nombre “txtname”.
	Crea una variable pública de tipo string, nombre “name” e inicializado a string vacío.
	En el evento detail_Load asigna al campo txtname el valor de la variable name.


o	mainAPP.cs:
	Crea un label con texto: “Nombre” y nombre “lblname” 
	Crea un textBox con nombre “txtname”.
	Al pulsar el botón “Detalle”:
•	Validar que el campo “txtname”:
o	No esté vacío
o	Contenga un mínimo de 3 caracteres
o	Que contenga un mínimo de 3 letras (a-z o A-Z).
o	En caso de que no se cumplan estas condiciones, mostrar un mensaje al usuario (MessageBox) indicando al usuario que debe rellenar el campo.
	Sólo mostrará 1 mensaje de error, independientemente de que se incumplan varias condiciones.
	Si no hay errores, abrir la ventana “detail.cs” pero asignando (antes de mostrarla) el valor de txtname a la variable pública de detail.cs llamada name.


1.5	VALIDACIÓN DE CAMPOS

Crear los siguientes campos, siempre acompañados de un label indicando su nombre (en inglés) y las reglas de nomenclatura descritas anteriormente:
•	Apellidos - textbox
•	Fecha de nacimiento – datetimepicker
•	E-mail – textbox
•	Contraseña – maskedtextbox
•	Repetir contraseña - maskedtextbox
•	DNI/Pasaporte – textbox
•	Número de teléfono – textbox
•	Sexo (hombre / mujer) – radiobuttons
•	Botón “Registrar” – button

Realizar una nueva función para validar estos campos al pulsar el nuevo botón “Registrar”. Todos los campos serán obligatorios. Validaciones específicas de cada campo:
1	Apellidos – mínimo 2 caracteres.
2	Fecha de nacimiento – deberán ser mayores de edad.
3	E-mail – el texto deberá tener como mínimo un punto y una arroba y no ser inferior a 7 caracteres.
4	Contraseña – maskedtextbox – mínimo de 8 caracteres. Al menos 1 mayúscula, al menos 1 número, al menos 1 letra (a-z  o A-Z).
5	Repetir contraseña – maskedtextbox – deberá ser igual al anterior.
6	DNI/Pasaporte – textbox – Si está en formato DNI, validar que el DNI sea válido (existen funciones para ello).
7	Número de teléfono – textbox
8	Sexo (hombre / mujer) – radiobuttons – por defecto que marque “hombre”.
9	Botón “Registrar” – button

Sólo mostrará 1 mensaje de error al pulsar el botón.
El mensaje de error podrá de ser de dos tipos:
A) Error específico de un campo, indicando el campo y la causa. Por ejemplo: el correo no está escrito correctamente.
B) Campos pendientes de cumplimentar.

Si no hay errores, mostrar un mensaje informativo de que todo es correcto.

2	Base de Datos

2.1	CREAR UNA BBDD
Crear una BBDD en el SQLEXPRESS local con una tabla “Users” que incluya todos los campos del formulario del ejercicio anterior.

Crear una llave privada para la tabla.

//Script postgres

CREATE TABLE public.users (
	usercodi serial4 NOT NULL,
	usernom varchar(200) NULL,
	userapellidos varchar(200) NULL,
	userdate date NULL,
	usermail varchar(256) NULL,
	userpass varchar(200) NULL,
	usercardid varchar(9) NULL,
	userphone varchar(16) NULL,
	usergender varchar(6) NULL,
	CONSTRAINT users_pk PRIMARY KEY (usercodi)
);

NOTA: dejar un margen razonable para los diferentes campos (por ejemplo, un campo de tipo texto para el campo e-mail  de 256 caracteres y otro de 200 para el nombre).

2.2	CONECTAR CON LA BBDD
Conectar con la BBDD al arrancar el formulario.
Recomendable que el objeto de conexión sea público.

BONUS: crear una clase que gestión e la apertura/cierre de conexión con la BBDD.

2.3	DATOS DE PRUEBA
Crear, manualmente, datos de prueba (por ejemplo, 2 usuarios de prueba).

2.4	MOSTRAR DATOS
Al cargar el formulario, cargar el último registro existente en BBDD en los diferentes campos del formulario.

Crear una clase con todos los datos del objeto Usuario y emplearlo para cargar los datos.

NOTA: Si no existen datos en BBDD, el sistema no fallará.

2.5	MODIFICAR DATOS
Modificar el comportamiento del botón “Registrar”:
•	Renombrar su Text a “Guardar”.
•	Al pulsarlo, si hay registro cargado en el formulario, actualizar el registro en BBDD con los datos del formulario.
•	Mostrar mensaje de éxito tras guardar correctamente los datos en BBDD.
•	Mostrar mensaje de error en caso de que ocurriese tras guardar los datos en BBDD.


2.6	CREAR NUEVOS DATOS
•	Añadir un nuevo botón “Nuevo” al formulario.
•	Al pulsarlo, se borrará el contenido de todos los campos del formulario.
•	Al pulsar el botón “Guardar”, el sistema no modificará ningún registro (ya que es uno nuevo) sino que dará de alta uno nuevo en BBDD.
•	Tras guardar con éxito, el formulario entrará en modo edición, por lo que cualquier cambio en el formulario y pulsar el botón “guardar”, no creará nuevos registros sino que actualizará en BBDD (para realizar esto, tras guardar el nuevo registro, será necesario recoger su PK).
•	Mostrar mensaje de éxito tras guardar correctamente los datos en BBDD.
•	Mostrar mensaje de error en caso de que ocurriese tras guardar los datos en BBDD.

2.7	ELIMINAR DATOS
•	Añadir un nuevo botón “Eliminar”.
•	Sólo estará habilitado si el registro actual está en modo edición de registro (no nuevos registros).
•	El sistema solicitará confirmación para eliminar el registro actual.
•	En caso de aceptación, el sistema eliminará el registro actual, reseteará todos los campos, y cargará el último existente en BBDD (o a su defecto dejará todos los campos vacíos).
2.8	GRIDS
•	Crear una grid que cargue todos los registros de BBDD ordenados por código de registro Z-A (más nuevos arriba).
•	Al hacer doble click sobre un registro, mostrar en un mensaje el nombre y apellidos (concatenado) del usuario.







-----------------------------------------------------------------------------
                              pruebasDaniel2
-----------------------------------------------------------------------------

3	Componentes DevExpress

3.1	CAMPOS DEVEXPRESS
Realizar todos los ejercicios del punto 1 empleando exclusivamente componentes devexpress (si existe equivalencia con los del Framework).

3.2	CAMPOS DEVEXPRESS
Realizar todos los ejercicios del punto 2 empleando exclusivamente componentes devexpress (si existe equivalencia con los del Framework).


-----------------------------------------------------------------------------
                              pruebasDaniel3
-----------------------------------------------------------------------------

4	BONUS

4.1	PARSEAR XML Y MOSTRARLO EN UNA GRID WINFORM
1.	Parsear el fichero XML llamado “prestige.xml” ubicado en el directorio de /RECURSOS/ de la carpeta de formación.

2.	Mostrar sus datos en una GRID adaptada automáticamente al tamaño del formulario (propiedad Dock).

3.	Añadir un desplegable para filtrar los datos de la tabla por el nodo “Hotel”, atributo HotelName, cuyo valor sea “Iberostar Al%”. Es decir, todos los que empiecen por “Iberostar Al” y continúen con cualquier otro valor.




