# Consumer Service 📥

**Autor:** Alejandro Prieto Reyes  
**Curso:** Arquitecturas de Software (ARCN)

## Descripción

Microservicio Spring Boot que actúa como **consumidor de eventos** en una arquitectura orientada a eventos. Escucha mensajes de una cola de RabbitMQ y los procesa automáticamente mediante un `@RabbitListener`.

## Tecnologías

- Java 17
- Spring Boot 4.0.5
- Spring AMQP (RabbitMQ)
- Docker

## Imagen Docker

```bash
docker pull samuelprietor/consumer-service
```

🔗 [Ver en Docker Hub](https://hub.docker.com/repository/docker/samuelprietor/consumer-service/general)

## Funcionamiento

El servicio escucha continuamente la cola `messages.queue`. Cuando el **Producer Service** envía un mensaje, este servicio lo recibe y lo procesa automáticamente:
[Producer] --POST /api/messages/send--> [RabbitMQ] --mensaje--> [Consumer]

### Log esperado al recibir un mensaje
INFO  : Mensaje recibido: 'HolaMundo'



Mensaje Procesado: HolaMundo




## Configuración RabbitMQ

| Propiedad | Valor |
|-----------|-------|
| Queue | `messages.queue` |
| Host | `rabbitmq` (en Docker Compose) |
| Puerto | `5672` |

## Ejecutar con Docker Compose

```bash
git clone https://github.com/AlejandroPrieto82/ARCN_Lab_Consumer
docker-compose up -d

# Verificar mensajes recibidos
docker-compose logs consumer
```

## Estructura del Proyecto
```
consumer/
├── src/main/java/com/eci/arcn/consumer/
│   ├── ConsumerApplication.java
│   ├── config/
│   │   └── RabbitMQConfig.java
│   └── listener/
│       └── MessageListener.java
├── src/main/resources/
│   └── application.properties
├── Dockerfile
└── pom.xml
```