![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/LogoBytte.png)

# Bytte SDK
    Autor Carlos Garzón.
    Fecha de creación 15 de Noviembre 2023.
    versión Documento  -.-.-

# Documento Integración SDK Nativo IOS
### CONFIDENCIALIDAD

La información contenida en el presente documento es CONFIDENCIAL, hace parte del secreto comercial e industrial de la empresa e implica transmisión de información cuya propiedad corresponde exclusivamente a BYTTE SAS. En consecuencia, la divulgación o el uso inapropiado de la información aquí contenida por parte del receptor de la misma, implicarán la aplicación de las normas legales pertinentes para su debida protección.

## 1. INTRODUCCIÓN

El presente documento tiene como objetivo proporcionar una guía detallada para la instalación paso a paso del (SDK) suministrado por Bytte en una aplicación nativa de iOS desarrollada con el entorno de desarrollo integrado (IDE) Xcode

### 1.2. Factores Limitantes

Los factores limitantes para la integración del SDK son:
* Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada
* Se recomiendan cámaras con resolución mayores o iguales a 8 Mega Pixeles para un óptimo rendimiento
* El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone

## 2. INSTALACIÓN

### 2.1. Pre requisitos

* Para compilación de aplicación en plataforma IOS, se requiere:
    > * XCode 15.0 o Superior con SDK IOS 13 o superior
    > * Deshabilitar BitCode

### 2.2. Librerías

El SDK está compuesto por funcionalidades de captura de documentos, biometría dactilar y facial. Para implementar estas capacidades, es necesario incorporar las librerias correspondientes. 

A continuación, se detallan las librerias requeridas:

  > * BytteLibrarySDKComun.framework

#### 2.2.1 Documentos
  > * BytteLibrarySDKDocumentoV2.framework
  > * BlinkID.framework

#### 2.2.2 Biometria Facial
  > * BytteLibrarySDKFaceID.framework
  > * BytteLibrarySDKFaceIP.framework
  > * IdentyFace.framework
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

Bytte facilita el proceso de activación de las capturas mediante la provisión de licencias. Para la captura de documentos, se suministran licencias en formato base64, mientras que para la captura de biometría dactilar y biometría facial, se proporcionan archivos de licencia correspondientes. 

Estos elementos son esenciales para habilitar la captura dentro de la aplicación.

  > * Captura de Huellas
  > * Captura de Selfie V1
  
Se deben embeber los archivos como recursos.

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/ArchivosLicencia.png)

### 3.3. Captura Documentos:

Para realizar el llamado de captura de documentos es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/Document.png)


### 3.3.1 Configuración Parámetros:

| Parametro | |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| licenseKey             | Licencia provista por Bytte para la captura de los documentos. |                             
| bytteProtect     | Retorna una llave de la imagene capturada (No retorna imagen)  | 
| keyProtect     | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| Keyjoin     | Todas las imagenes estan en un unico archivo.    | 
| imgColor     | Identifica si la imagen está a color o blanco y negro    | 
| pais     | Identifica el pais y el tipo de documento a capturar CO -> Documento colombiano Hologramas COV2 -> Documento colombiano Digital COCET2 ->  Documento colombiano extrangeria   | 
| dataBackDocument     | Extrae información adicional del OCR del documento colombiano (Hologramas)    | 
| timeOut     |    Tiempo de duración de la captura    | 
| tipoCaptura     |Identifica la captura a generarse BACK -> reverso, FRONT -> frontal, QR captura qr    | 
| imageTemplate     | Imagen plantilla documento    | 

### 3.3.2 Respuesta Captura:


### 3.4. Captura Biometria Dactilar:

Para realizar el llamado de captura dactilar es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/Dactilar.png)


### 3.4.1 Configuración Parámetros:

| Parametro | |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             | Url provista por Bytte para la captura dactilar. |   
| bytteProtect     | Retorna una llave de la imagene capturada (No retorna imagen)  | 
| keyProtect     | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| Keyjoin     | Todas las imagenes estan en un unico archivo.    | 
| timeOut     |    Tiempo de duración de la captura    | 
| fingerNumber     | Variable dedo a capturar  ***2*** -> Mano derecha. ***7*** -> Mano Izquierda. | 

### 3.4.2 Respuesta Captura:


### 3.5. Captura Biometria Facial V1:

Para realizar el llamado de captura facial V1 es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/FaceV1.png)


### 3.5.1 Configuración Parámetros:

| Parametro | |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             | Url provista por Bytte para la captura dactilar. |   
| bytteProtect     | Retorna una llave de la imagene capturada (No retorna imagen)  | 
| keyProtect     | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| timeOut     |    Tiempo de duración de la captura    | 
| camera     | Indica sobre que camara inicia el sdk ***Front*** -> Camara Frontal ***Back*** -> Camara Reverso  | 

### 3.5.2 Respuesta Captura:

### 3.6. Captura Biometria Facial V2:

Para realizar el llamado de captura facial V2 es necesario inicializar y agregar variables de captura. A continuación, se presenta un ejemplo:

(Swift)
![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/Documentaci%C3%B3n/Bytte/Facev2.png)


### 3.5.1 Configuración Parámetros:

| Parametro | |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url             | Url provista por Bytte para la captura dactilar. |   
| keyProtect     | Llave de protección para las imagenes. Si lleva un valor diferente a vacío esta retorna la imagen en formato .bytte, el resultado es una imagen cifrada con aes 256 por sesión.    | 
| timeOut     |    Tiempo de duración de la captura    | 
| camera     | Indica sobre que camara inicia el sdk ***Front*** -> Camara Frontal ***Back*** -> Camara Reverso  | 

### 3.5.2 Respuesta Captura:






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

