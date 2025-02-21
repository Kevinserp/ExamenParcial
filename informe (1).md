# Informe sobre la instalación de IIS con Docker 

Configurar IIS con Docker en Windows permite un entorno de desarrollo eficiente. Sin embargo, Windows 10 Home tiene limitaciones para ejecutar contenedores de Windows debido a la falta de soporte completo para la virtualización.

## Requisitos previos

### Sistema operativo
- Windows 10 Home no es compatible con la funcionalidad de contenedores de Windows, lo que impide realizar la instalación de IIS a través de Docker en esta edición.

### Docker Desktop
Es necesario tener Docker Desktop instalado. Docker proporciona la infraestructura para ejecutar contenedores, pero en versiones de Windows 10 Home, Docker solo puede ejecutar contenedores de Linux, ya que la virtualización para contenedores de Windows no está habilitada.

### Requisitos adicionales
- **WSL2 (Windows Subsystem for Linux 2)**: Para ejecutar contenedores de Linux, WSL2 debe estar habilitado en el sistema.
- **Virtualización**: La virtualización debe estar habilitada en la BIOS del sistema para soportar WSL2 y Docker.

## Pasos para la instalación de IIS con Docker

### 1. Verificar la versión de Docker
Antes de proceder, asegúrate de tener Docker Desktop instalado y ejecutándose. Puedes confirmar su instalación abriendo una terminal y ejecutando el siguiente comando:

```bash
docker --version
```

Este comando mostrará la versión actual de Docker instalada en tu sistema.

### 2. Verificar la instalación de WSL2
WSL2 debe estar habilitado para poder ejecutar contenedores de Linux en Docker Desktop. Para habilitarlo, abre PowerShell como administrador y ejecuta los siguientes comandos:

```powershell
dism.exe /online /enable-feature /all /featurename:Microsoft-Hyper-V-All /featurename:VirtualMachinePlatform
```

Esto activará la virtualización necesaria para Docker. Luego, verifica que WSL2 está correctamente habilitado con el siguiente comando:

```powershell
wsl --list --verbose
```


Este comando debería mostrar los subsistemas de Linux instalados y su estado.

### 3. Instalar IIS sin Docker
Dado que Windows 10 Home no soporta la virtualización necesaria para los contenedores de Windows, no es posible instalar IIS a través de Docker en esta edición. Como alternativa, se puede instalar IIS directamente en el sistema operativo utilizando PowerShell.

#### Instalar IIS
Para habilitar IIS en Windows 10 Home, abre PowerShell como administrador y ejecuta el siguiente comando:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-WebServerRole -All
```

Este comando habilita el rol del servidor web IIS en el sistema.

#### Instalar las herramientas de administración de IIS

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-WebServerManagementTools -All
```

Esto instala las herramientas necesarias para administrar IIS, como el Administrador de IIS.

#### Verificar si IIS está corriendo
Para verificar que el servicio de IIS se está ejecutando correctamente, usa el siguiente comando:

```powershell
Get-Service W3SVC
```

Si IIS está instalado correctamente, el servicio W3SVC debería estar en ejecución.

## Conclusión
La instalación de IIS con Docker en Windows 10 Home presenta limitaciones debido a la falta de soporte para contenedores de Windows en esta versión del sistema operativo. Como alternativa, se recomienda instalar IIS directamente en el sistema operativo utilizando PowerShell.
