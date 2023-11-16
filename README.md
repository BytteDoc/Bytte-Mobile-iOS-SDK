![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/LogoBytte.png)

# Bytte SDK
    Autor Carlos Garzón.
    Fecha de creación 30 de Septiembre 2023.

# Documento Integración SDK Nativo IOS
### CONFIDENCIALIDAD

La información contenida en el presente documento es CONFIDENCIAL, hace parte del secreto comercial e industrial de la empresa e implica transmisión de información cuya propiedad corresponde exclusivamente a BYTTE SAS. En consecuencia, la divulgación o el uso inapropiado de la información aquí contenida por parte del receptor de la misma, implicarán la aplicación de las normas legales pertinentes para su debida protección.

## 1. INTRODUCCIÓN

El presente documento tiene como objetivo proporcionar una guía detallada para la instalación paso a paso del (SDK) suministrado por Bytte en una aplicación nativa de iOS desarrollada con el entorno de desarrollo integrado (IDE) Xcode

### 1.2. Factores Limitantes

Los factores limitantes para la integración del SDK son:
* Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada
* Se recomiendan cámaras con resolución mayores o iguales a 8 Mega Pixeles para un óptimo rendimiento
* El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos iPhone

## 2. INSTALACIÓN

### 2.1. Pre requisitos

* Para compilación de aplicación en plataforma IOS, se requiere:
    > * XCode 15.0 o Superior con SDK IOS 13 o superior
    > * Deshabilitar BitCode

### 2.2. Librerías

El SDK compone de diversas funcionalidades, entre las que se incluyen captura de documentos, biometría dactilar, biometría facial ID y Facial IP. Para habilitar estas capacidades en su aplicación, es esencial integrar las bibliotecas correspondientes de acuerdo con los términos establecidos en el acuerdo comercial.

A continuación, se detallan las librerias requeridas:

  > * BytteLibrarySDKComun.framework

#### 2.2.1 Documentos
  > * BytteLibrarySDKDocumentoV2.framework
  > * BlinkID.framework

#### 2.2.2 Biometria Facial
###### 2.2.2.1 Biometria Facial ID
  > * BytteLibrarySDKFaceID.framework
  > * IdentyFace.framework

###### 2.2.2.2 Biometria Facial IP
  > * BytteLibrarySDKFaceIP.framework
  > * iProov.framework

#### 2.2.3 Biometria Dactilar
  > * BytteLIbrarySDKFingerID.framework
  > * Identy.framework


## 3. USO DE LA LIBRERIA

### 3.1. Importar librerías

A continuación, se listan los import que la librería expone: 

  > * import BytteLIbrarySDKFingerID
  > * import BytteLibrarySDKFaceID
  > * import BytteLibrarySDKDocumentoV2
  > * import BytteLibrarySDKFaceIP

  
### 3.2. Activación de la Licencia de Captura:

La activación de licencias está sujeta a un acuerdo comercial. Bytte proporciona archivos de licencia para habilitar las funciones de captura de biometría dactilar y facial ID, de acuerdo con los términos establecidos en dicho acuerdo.

Los archivos mencionados son fundamentales para activar la captura de biometría dactilar y facial ID dentro de la aplicación. Es necesario incorporar estos archivos como recursos, para garantizar el correcto funcionamiento.
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/ArchivosLicencia.png)

En caso de experimentar problemas con las licencias, comuníquese con nosotros a través del correo electrónico Info@bytte.com.co.




### 3.3. Captura Documentos:

Para realizar el llamado de captura de documentos es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/DocumentV2.png)


### 3.3.1 Configuración Parámetros:

| Parametro | Tipo | Descripción |
| ------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             |String | URL proporcionada por Bytte para la captura de documentos. |
| documentType     |Enum| ***DOCUMENT***  -> Documentos de identidad ***PASPORTDOCUMENT*** -> Pasaporte  ***CREDITCARD*** -> Tarjeta de credito.  | 
| country     |Enum | Identifica el pais y versión del documento ***CO*** -> Documento colombiano Hologramas ***COV2*** -> Documento colombiano Digital ***COCET2*** ->  Documento colombiano extrangeria.   |
| captureType     |Enum | Identifica si debe capturar frente o reverso del documento ***BACK*** -> reverso, ***FRONT*** -> frontal.|
| bytteProtect     |Boolean| Variable por defecto en ***True***. Esta variable retorna un KEY de imagen (No retorna imagenes)   | 
| keyProtect     |String | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| keyJoin     |Boolean | Las imagenes capturadas las retorna en un unico archivo.    | 
| colorImg     |Boolean | Variable por defecto en ***False***. Esta variable permite o no capturar fotocopias de documento.  | 
| timeOut     |Int | Tiempo de duración de la captura.    | 
| imgTemplate     |UIImage | Imagen plantilla documento.    | 


### 3.3.2 Respuesta Captura Documentos:


### 3.4. Captura Biometria Dactilar:

Para realizar el llamado de captura dactilar es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/Dactilar.png)


### 3.4.1 Configuración Parámetros:

| Parametro | Tipo | Descripción |
| ------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             |String | URL proporcionada por Bytte para la captura dactilar. |
| bytteProtect     |Boolean| Variable por defecto en ***True***. Esta variable retorna un KEY de imagen (No retorna imagenes)   | 
| keyProtect     |String | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| keyJoin     |Boolean | Las imagenes capturadas las retorna en un unico archivo.    | 
| timeOut     |Int | Tiempo de duración de la captura.    | 
| fingerNumber |Int | Variable dedo a capturar  ***2*** -> Mano derecha. ***7*** -> Mano Izquierda. | 

### Captura Facial

Bytte proporciona diferentes metodos de captura facial. Para comprender las diferencias entre la captura facial ID y Facial IP, así como para validar el licenciamiento, le invitamos a ponerse en contacto con nosotros a través del correo electrónico Info@bytte.com.co.

### 3.5. Captura Biometria Facial ID:

Para realizar el llamado de captura facial ID es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/FaceV1.png)


### 3.5.1 Configuración Parámetros:

| Parametro | Tipo | Descripción |
| ------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             |String | URL proporcionada por Bytte para la captura dactilar. |
| bytteProtect     |Boolean| Variable por defecto en ***True***. Esta variable retorna un KEY de imagen (No retorna imagenes)   | 
| keyProtect     |String | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| timeOut     |Int | Tiempo de duración de la captura.    | 
| camera |Enum |Indica sobre que camara inicia el sdk ***Front*** -> Camara Frontal ***Back*** -> Camara Reverso | 

### 3.5.2 Respuesta Captura Facial ID:

### 3.6. Captura Biometria Facial IP:

Para realizar el llamado de captura facial V2 es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/Facev2.png)


### 3.5.1 Configuración Parámetros:

| Parametro | Tipo | Descripción |
| ------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             |String | URL proporcionada por Bytte para la captura dactilar. |
| keyProtect     |String | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| timeOut     |Int | Tiempo de duración de la captura.    | 
| camera |Enum |Indica sobre que camara inicia el sdk ***Front*** -> Camara Frontal ***Back*** -> Camara Reverso | 

### 3.5.2 Respuesta Captura Facial IP:






### 4. Códigos Respuesta
#### 4.1. Base Respuesta
Al realizar los llamados correspondientes para todas las capturas se genera una respuesta base donde se controlan variables del proceso de captura.

 > * MensajeOriginal
 > * MensajeRetorno
 > * CodigoOperacion
 > * StatusOperacion
 > * CodigoError

#### 4.2. Time Out
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/TimeOut.png)
#### 4.3. Cancelado por el usuario
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Cancelado.png)
#### 4.4. Captura correcta

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Correcta.png)






| Bytte S.A.S.      |
| ------------------ |
| Av. Calle 26 No. 69 D – 91 Torre 1 Of. 407       |
| [https://www.bytte.com.co](https://www.bytte.com.co)          |
| +(57) 601 744 3800       |
| Info@bytte.com.co               |

