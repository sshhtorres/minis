# Ambientes virtuales usando `venv`

Los ambientes virtuales en Python permiten aislar las dependencias de proyectos para evitar conflictos entre versiones. Además, facilitan replicar/reproducir el mismo ambiente virtual en otros equipos a través de archivos que describen las dependencias, por ejemplo, archivos `requirements.txt`.


**Índice:**
* [Destacados](#destacados)
* [Resumen de comandos](#resumen-de-comandos)
* [Crear](#crear)
* [Activar](#activar)
* [Instalar dependencias](#instalar-dependencias)
* [Describir dependencias](#describir-dependencias)
* [Desactivar](#desactivar)
* [Replicar](#replicar)
* [Eliminar](#eliminar)
* [Referencias y tutoriales](#referencias-y-tutoriales)

## Destacados
* el módulo `venv` viene incluido en la instalación de Python desde su versión 3.3
* `venv` crea ambientes virtuales accesibles desde el directorio donde se crean, conocidos como ambientes virtuales locales
* el archivo `requirements.txt` se debe incluir en el repositorio de un proyecto para replicar el ambiente virtual
* el directorio con el nombre del ambiente virtual es un directorio local en el equipo y se debe excluir del repositorio de un proyecto (se incluye en el archivo `.gitignore`)


## Resumen de comandos
Resumen de comandos para ambientes virtuales:
<table>
   <thead>
      <tr>
         <th>macOS/Linux</th>
         <th>Windows (Git Bash)</th>
         <th>Windows (Command Prompt)</th>
      </tr>
   </thead>
   <tbody>
      <tr>
<td><code><pre>

\# crear
python3 -m venv venv

\# activar
source venv/bin/activate

\# instalar dependencias
pip install numpy pandas

\# describir dependencias
pip freeze > requirements.txt

\# replicar
pip install -r requirements.txt

\# desactivar
deactivate

\# eliminar
rm -r venv/
</pre></code></td>

<td><code><pre>

\# crear
python -m venv venv

\# activar
source venv/Scripts/activate

\# instalar dependencias
pip install numpy pandas

\# describir dependencias
pip freeze > requirements.txt

\# replicar
pip install -r requirements.txt

\# desactivar
deactivate

\# eliminar
rm -r venv/
</pre></code></td>

<td><code><pre>

:: crear
python -m venv venv

:: activar
venv\Scripts\activate

:: instalar dependencias
pip install numpy pandas

:: describir dependencias
pip freeze > requirements.txt

:: replicar
pip install -r requirements.txt

:: desactivar
deactivate

:: eliminar
rmdir /s /q venv
</pre></code></td>
      </tr>
   </tbody>
</table>


## Crear

Ubicarse en el directorio de raiz del proyecto:
```
cd /directorio-del-proyecto
```

Crear ambiente virtual local "venv" (se puede cambiar el nombre):
- En macOS/Linux:
   ```shell
   python3 -m venv venv
   ```

- En Windows con Git Bash o Command Prompt:
   ```shell
   python -m venv venv
   ```

## Activar

Activar un ambiente virtual:
- En macOS/Linux:
   ```shell
   source venv/bin/activate
   ```

- En Windows con Git Bash:
   ```shell
   source venv/Scripts/activate
   ```

- En Windows con Command Prompt:
   ```cmd
   venv\Scripts\activate
   ```

Ahora los comandos `python`, `python3`, `pip`, y `pip3` apuntan al ambiente virtual. En macOS/Linux, los comandos `python` y `pip` apuntan a `python3` y `pip3` del ambiente virtual.

Opcionalmente para entender mejor la diferencia, se puede desactivar el ambiente virtual y verificar la ruta de Python antes y después de activarlo nuevamente:
- En macOS/Linux:
   ```shell
   deactivate
   which python3
   source venv/bin/activate
   which python3
   ```

- En Windows con Git Bash:
   ```shell
   deactivate
   which python
   source venv/Scripts/activate
   which python
   ```

- En Windows con Command Prompt:
   ```cmd
   deactivate
   where python
   venv\Scripts\activate
   where python
   ```

Es posible activar ambientes virtuales creados con `venv` en cualquier directorio (`/ruta-al-directorio/venv`), sin embargo, usualmente se define el directorio que contiene el ambiente virtual como el directorio de trabajo.

## Instalar dependencias

Instalar dependencias o librerías externas en el ambiente virtual:
```shell
pip install numpy pandas
```

## Describir dependencias
Describir dependencias en un archivo `requirements.txt` (sobreescribe el contenido del archivo):
```shell
pip freeze > requirements.txt
```

## Desactivar
Desactivar el ambiente virtual:
```shell
deactivate
```

## Replicar

1. Crear y activar un nuevo ambiente virtual.

2. Instalar las dependencias de un archivo `requirements.txt`:
   ```
   pip install -r requirements.txt
   ```

## Eliminar

Desactivar y eliminar el directorio con el mismo nombre del ambiente virtual:

- En macOS/Linux o Windows con Git Bash::
   ```shell
   deactivate
   rm -r venv/
   ```

- En Windows con Command Prompt:
   ```cmd
   deactivate
   rmdir /s /q venv
   ```

## Referencias y tutoriales
Documentación oficial:
- https://docs.python.org/3/library/venv.html
- https://docs.python.org/es/3/library/venv.html

Video tutoriales en español:
- Así debes usar Python en tu computadora (Entornos Virtuales) | codigofacilito: https://www.youtube.com/watch?v=RHaoNZFK7Fc
- Entornos Virtuales con Python (Módulo virtualenv) | UskoKruM2010: https://www.youtube.com/watch?v=TNtrAvNNxTY

Videos tutoriales que contienen el mismo contenido paso a paso:
- Python Tutorial: VENV (Mac & Linux) - How to Use Virtual Environments with the Built-In venv Module | Corey Schafer: https://www.youtube.com/watch?v=Kg1Yvry_Ydk
- Python Tutorial: VENV (Windows) - How to Use Virtual Environments with the Built-In venv Module | Corey Schafer: https://www.youtube.com/watch?v=APOPm01BVrk

Alternativas equivalentes a los dos videos anteriores:
- Python Virtual Environments - Full Tutorial for Beginners | Tech With Tim: https://www.youtube.com/watch?v=Y21OR1OPC9A
- The Complete Guide to Python Virtual Environments! | teclado: https://www.youtube.com/watch?v=KxvKCSwlUv8

La siguiente referencia explica varios aspectos con mayor detalle: https://realpython.com/python-virtual-environments-a-primer/
