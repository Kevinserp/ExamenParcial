# Documentación de Errores en Docker y Configuración de Contenedores

## Concepto de IIS (Internet Information Services)

IIS (Internet Information Services) es un servidor web y de aplicaciones desarrollado por Microsoft para sistemas operativos Windows. Su función principal es alojar y administrar sitios web, servicios HTTP y aplicaciones basadas en tecnologías como ASP.NET. En el contexto de Docker, IIS puede ser utilizado en contenedores Windows para ejecutar aplicaciones web en un entorno aislado y escalable.

## Problema Encontrado

Al intentar ejecutar Docker en un entorno con máquinas frizadas, se presentó el siguiente error:

- Docker no está habilitado para trabajar con contenedores de Windows, solo de Linux.
- Al iniciar Docker, aparece un mensaje solicitando reiniciar la PC.
- Debido a que las máquinas están frizadas, no es posible realizar cambios persistentes en la configuración del sistema.

## Verificación de la Versión de Docker

Para comprobar la versión instalada de Docker, se ejecutó el siguiente comando en la terminal:

```sh
docker version
```

El resultado mostró que Docker está operando en modo Linux, lo que confirma la incompatibilidad con contenedores de Windows en la configuración actual.

## Posibles Soluciones

1. Configurar Docker para ejecutar contenedores de Windows en lugar de Linux.
2. Solicitar permisos administrativos para realizar cambios en la configuración del sistema y deshabilitar el frizado temporalmente.
3. Utilizar una máquina virtual con Windows y Docker configurado adecuadamente.

---

Esta documentación es parte del registro de errores encontrados y las verificaciones realizadas durante la configuración de Docker en el entorno de trabajo.
