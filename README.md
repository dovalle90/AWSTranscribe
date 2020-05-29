# AWSTranscribe
Cliente para utilizar el servicio de Amazon Transcribe

# AWS Transcribe Streaming Aplocacion de Java maven

Aplicacion de Java usando AWS SDK creando trasncripciones via streaming utilizando AWS Transcribe

## Setup

Esta aplicacion asume que tus credenciales estan definidas en la misma forma que [Default Credential Provider Chain](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html#credentials-default)
requiere.

Para eso se pueden exportar las credenciales en las variables de entorno o lo mas recomendable es instalar y configurar previamente la Amazon CLI con la cuenta que tiene acceso a los servicios de Transcribe.

## Descripcion

Esta aplicacion se utiliza como straming API de AWS Transcribe utilizando una interfaz grafica para el usuario. 
El codigo que hace el llamdo a la API Transcribe se encuentra en "TranscribeStreamingClientWrapper.java, en el metodo 
"startTranscription".

En esta API se toma ventaja de la flexibilidad de Java para el manejo de eventos. Se definen difrentes tipos de compartamientos y se considenran las posibles exepciones que se puedan dar.

## Clases

|Clase|Descripcion|
|---|---|
| `TranscribeStreamingDemoApp` | Metodo Main que lanza la aplicacion, inicializa `WindowController` |
| `WindowController` | Elemtos del GUI de la aplicacion. Tambien define el comportamiento para las respuestas de la Stream API |
| `TranscribeStreamingClientWrapper` | Cliente del AWS SDK Transcribe |
| `AudioStreamPublisher` | Utilizado para eventos de streaming al servicio |
| `ByteToAudioEventSubscription` | Convierte bytes de audio introducidos en los AudioEvents que se ennvian al servicio AWS Transcribe |
| `TranscribeStreamingRetryClient` | Logica alrededor del AWS Transcribe SDK, incluyer resumir sesiones en caso de perder coneccion |
| `StreamTranscriptionBehavior` | Clase requerida por `TranscribeStreamingRetryClient` para determinar el manejo de la respuesta |
| `TranscribeStreamingSynchronousClient` | Clase que provee el asynchronismo a las event-stream API | 

## Documentacion de AWS
https://docs.aws.amazon.com/transcribe/latest/dg/streaming.html
