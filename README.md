Aquí tienes el README.md completo con la estructura del proyecto añadida y mejorado con el formato adecuado:

```markdown
# Confirmación Metrológica

Este proyecto tiene como objetivo implementar y gestionar un sistema de **confirmación metrológica**, respaldado por **machine learning** y procesamiento de datos. El proyecto sigue las mejores prácticas de desarrollo, utilizando Docker para la contenedorización y un entorno de desarrollo administrado con `venv` y Python 3.11+.

## Tabla de Contenidos

- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Uso](#uso)
  - [Scripts](#scripts)
  - [Proceso GitFlow](#proceso-gitflow)
  - [Comenzar a Programar](#comenzar-a-programar)
- [Configuración](#configuración)
- [Mejores Prácticas](#mejores-prácticas)
- [Licencia](#licencia)

## Requisitos

Antes de comenzar, asegúrate de tener instalados los siguientes requisitos:

- [Python 3.11+](https://www.python.org/downloads/)
- [Docker](https://www.docker.com/)
- [Git](https://git-scm.com/)
- [VSCode](https://code.visualstudio.com/) (opcional, pero recomendado)

## Instalación

Sigue estos pasos para configurar el proyecto en tu máquina local.

1. **Clona el repositorio**:
   ```bash
   git clone https://github.com/yourusername/ConfirmacionMetrologica.git
   cd ConfirmacionMetrologica
   ```

2. **Configura el entorno virtual e instala las dependencias**:
   ```bash
   .\scripts.bat startProject
   ```

3. **Configura el archivo `.env`**:
   El archivo `.env` se creará automáticamente mediante el script `scripts.bat`. Puedes modificarlo si lo necesitas.

## Estructura del Proyecto

La estructura del proyecto está organizada de la siguiente manera:

```
ConfirmacionMetrologica/
┣ data/                         # Carpeta para almacenar los datos relacionados con el proyecto.
┃ ┗ raw/                        # Datos sin procesar o datos brutos se almacenan aquí.
┃   ┗ DatosBajoCosto.csv        # Archivo CSV que contiene los datos iniciales sin procesar para el análisis.
┣ docker/                       # Archivos relacionados con la configuración de Docker.
┃ ┣ docker-compose.yml          # Archivo de configuración para definir y ejecutar servicios Docker en múltiples contenedores.
┃ ┗ Dockerfile                  # Definición de la imagen Docker para el entorno de desarrollo/producción.
┣ docs/                         # Carpeta destinada a la documentación del proyecto.
┣ model/                        # Contiene los archivos principales del modelo de machine learning y su configuración.
┃ ┣ configs/                    # Archivos de configuración utilizados para personalizar el modelo.
┃ ┃ ┣ config.example.yaml       # Ejemplo de archivo de configuración para guiar la creación de `config.yaml`.
┃ ┃ ┣ config.py                 # Script Python que maneja la carga y gestión de la configuración.
┃ ┃ ┗ config.yaml               # Archivo YAML que contiene configuraciones ajustables para el modelo.
┃ ┣ controller/                 # Controladores, incluyendo notebooks y scripts, para manejar el flujo de trabajo.
┃ ┃ ┣ notebooks/                # Notebooks de Jupyter utilizados para el procesamiento de datos y análisis.
┃ ┃ ┃ ┗ dataPreprocessing.ipynb # Notebook con el pipeline de preprocesamiento de datos.
┃ ┃ ┗ scripts/                  # Scripts para automatizar tareas de control y procesamiento.
┃ ┣ core/                       # Núcleo del proyecto que contiene las funciones y lógica del modelo.
┃ ┃ ┣ data/                     # Archivos relacionados con la manipulación y preprocesamiento de datos.
┃ ┃ ┃ ┗ DataPreprocess.py       # Script para preprocesar los datos antes del entrenamiento.
┃ ┃ ┗ model/                    # Aquí irían los archivos del modelo de machine learning, como su arquitectura.
┃ ┗ resources/                  # Recursos necesarios para el funcionamiento del proyecto.
┃   ┣ logs/                     # Carpeta para almacenar archivos de registro (logs).
┃   ┗ trainedModels/            # Carpeta destinada a almacenar los modelos entrenados.
┣ tests/                        # Pruebas unitarias y de integración para validar la funcionalidad del código.
┃ ┣ test_data_loader.py         # Prueba unitaria para la carga de datos.
┃ ┗ test_model.py               # Prueba unitaria para verificar la funcionalidad del modelo.
┣ utils/                        # Funciones auxiliares y utilidades comunes que se utilizan en todo el proyecto.
┃ ┗ DataLoader.py               # Script que gestiona la carga y preparación de datos para el modelo.
┣ .env                          # Archivo de entorno que contiene variables sensibles, como claves API y configuraciones.
┣ .env.example                  # Ejemplo del archivo `.env` para configuración.
┣ .gitignore                    # Lista de archivos y carpetas que Git debe ignorar.
┣ README.md                     # Documento que describe el proyecto, su uso, instalación y estructura.
┣ requirements.txt              # Lista de dependencias y bibliotecas necesarias para el proyecto.
┗ scripts.bat                   # Script por lotes para automatizar tareas, como instalación de dependencias y ejecución del proyecto.
```

## Uso

### Scripts

Puedes usar el archivo `scripts.bat` para automatizar tareas comunes:

- **Mostrar ayuda con los comandos disponibles**:
  ```bash
  .\scripts.bat help
  ```

### Proceso GitFlow

Seguimos el flujo de trabajo **GitFlow** para el control de versiones y la gestión de ramas. Aquí tienes un flujo típico para agregar una nueva característica:

1. **Iniciar una nueva característica**:
   ```bash
   git flow feature start mi-nueva-caracteristica
   git add .
   git commit -m "Añadido mejora específica en funcionalidad X"
   git flow feature finish mi-nueva-caracteristica
   git push origin develop
   ```

2. **Iniciar un nuevo lanzamiento**:
   ```bash
   git flow release start 0.1.0
   git flow release finish 0.1.0
   git push origin develop master --tags
   ```

3. **Iniciar un hotfix**:
   ```bash
   git flow hotfix start hotfix-0.1.1
   git flow hotfix finish hotfix-0.1.1
   git push origin develop master --tags
   ```

4. **Solicitar un pull request**:
   ```bash
   # GitFlow automáticamente crea un pull request al finalizar una feature, release o hotfix
   git request-pull master develop
   ```

### Comenzar a Programar

1. **Usar los notebooks en la carpeta `model/controllers/notebooks/`**:
   Sigue el pipeline definido en el notebook `dataPreprocessing.ipynb` y ejecuta las funciones en el orden presentado.

2. **Usar los scripts de la carpeta `model/controllers/scripts/`**:
   Ejecuta en la terminal los scripts disponibles en esta carpeta para automatizar los procesos.

   ```bash
   python script.py
   ```

## Configuración

El archivo de configuración principal se encuentra en la carpeta `configs/`. Puedes modificar la configuración en `config.yaml` según sea necesario. Copia `config.example.yaml` a `config.yaml` para la configuración inicial.

Si es necesario, también puedes sobrescribir configuraciones usando el archivo `.env`.

## Mejores Prácticas

- **Control de Versiones**: Sigue GitFlow para gestionar ramas y lanzamientos de manera eficiente.
- **Documentación**: Mantén tu código bien documentado, usando comentarios significativos y nombres de variables claros.
- **Pruebas Unitarias**: Ejecuta siempre pruebas unitarias antes de hacer commits importantes.
- **Estilo de Código**: Sigue los estándares de PEP 8 para Python. Puedes revisarlos aquí: [PEP 8](https://pep8.org/).
- **Gestión de Dependencias**: Actualiza `requirements.txt` cada vez que agregues o elimines dependencias.
- **Docker**: Usa Docker para garantizar entornos consistentes entre diferentes máquinas y miembros del equipo.

## Licencia

```



