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
