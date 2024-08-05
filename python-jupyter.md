# Jupyter

Jupyter es un ambiente de trabajo interactivo principalmente para analítica, ciencia de datos, computación científica, ingeniería de datos, inteligencia artificial, y machine learning.

Un Jupyter Notebook es un archivo con código, gráficas, texto en formato [Markdown](https://www.markdownguide.org/basic-syntax) (soporta ecuaciones de [LaTeX](https://latex-tutorial.com/tutorials/amsmath)), y otros más.


**Índice:**
* [Destacados](#destacados)
* [Opiniones](#opiniones)
* [Instalar](#instalar)
* [Ejecutar instancia](#ejecutar-instancia)
* [Instalar librerías](#instalar-librerías)
* [Leer archivos de datos](#leer-archivos-de-datos)
* [Referencias y tutoriales](#referencias-y-tutoriales)


## Destacados
* Jupyter es una librería externa de Python que requiere instalación.

* Una instancia de Jupyter es una ejecución de Jupyter como programa, por ejemplo, desde línea de comandos en el equipo local o desde un servicio en la nube como Google Colab (https://colab.research.google.com/).

* Una instancia local de Jupyter se ejecuta en un puerto local accesible desde el navegador web, por defecto en http://localhost:8888

* Un Jupyter Notebook es un archivo con extensión `.ipynb` (archivo de texto plano en formato JSON) que requiere una instancia de Jupyter para trabajar, o un intérprete para leer/visualizar, por ejemplo, GitHub renderiza estos archivos para fácil lectura: https://github.com/armandoordonez/eda_couse/blob/main/1_intro_carga_dataset_csv.ipynb

* El kernel en Jupyter es la ejecución de Python que la instancia de Jupyter corre internamente para evaluar de manera interactiva los códigos del Notebook.
    * Cuando se reinicia el kernel se pierden las variables en memoria.
    * Usualmente la instancia de Jupyter corre con la misma versión de Python del kernel, sin embargo, es posible cambiar el kernel a otra versión de Python disponible en el equipo.

* Jupyter Lab es una versión más avanzada de Jupyter como ambiente de trabajo, que igualmente se basa en Jupyter Notebooks.

* VSCode puede utilizarse con Jupyter Notebooks como ambiente de trabajo equivalente, en caso de preferirlo.

* Jupyter desde Anaconda Navigator crea una instancia de Jupyter desde el directorio de instalación de Anaconda, por lo que se requiere utilizar rutas absolutas o cambiar el directorio de trabajo para [leer archivos de datos](#leer-archivos-de-datos)

* En Windows es posible tener rutas con backslash (\\), por lo que en Python se requiere reemplazar estos caracteres por slash (/) o duplicar cada uno de estos caracteres backslash (\\\\) para [leer archivos de datos](#leer-archivos-de-datos)


## Opiniones

Jupyter funciona muy bien para exploración y análisis de datos, reportes preliminares, soportes de investigación, y desarrollo/prototipado de modelos, pero en ambientes de producción de servicios se deberían implementar flujos de DataOps y MLOps, usualmente por parte de un ingeniero de datos (data engineer) y de un ingeniero de aprendizaje automático (machine learning engineer).

Respecto a seleccionar un ambiente de trabajo:
* Use Jupyter desde Anaconda Navigator si tiene cero conocimiento de terminal o línea de comandos.
* Use Jupyter desde terminal o línea de comandos en el directorio raiz del proyecto para utilizar rutas relativas de archivos, así evita cambiar directorio de trabajo o usar rutas absolutas.
* Use VSCode Notebooks si busca o tiene un perfil profesional más enfocado en DataOps y MLOps, considerando las ventajas de un ambiente de desarrollo. Especialmente, considere utilizar VSCode Jupyter Cells: https://code.visualstudio.com/docs/python/jupyter-support-py


## Instalar

Notas iniciales:
* Jupyter está incluido en la instalación de Anaconda. En caso que haya instalado Anaconda, entonces continuar con la siguiente sección: [ejecutar instancia](#ejecutar-instancia)
* `ipykernel` se utiliza para VSCode en caso de preferirlo.
* Se puede instalar `jupyter`, `jupyterlab`, o `ipykernel` en la distribución principal de Python, sin embargo, se recomienda utilizar un ambiente virtual para un proyecto en particular (ver [python-venv.md](./python-venv.md)).

Instalar UNO de los siguientes según preferencia:
- En macOS/Linux:
   ```shell
   pip3 install jupyterlab

   pip3 install jupyter

   pip3 install ipykernel
   ```

- En Windows con Git Bash o Command Prompt:
   ```
   pip install jupyterlab

   pip install jupyter

   pip install ipykernel
   ```

Verificar instalación de Jupyter (no disponible si instaló `ipykernel`):
- En macOS/Linux o Windows con Git Bash:
   ```shell
   which jupyter
   jupyter --version
   ```

- En Windows con Command Prompt:
   ```cmd
   where jupyter
   jupyter --version
   ```

En VSCode se requiere instalar las extensiones de Python y Jupyter:
- https://marketplace.visualstudio.com/items?itemName=ms-python.python
- https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter


## Ejecutar instancia

Jupyter desde Anaconda Navigator crea una instancia de Jupyter desde el directorio de instalación de Anaconda, por lo que se requiere utilizar rutas absolutas o cambiar el directorio de trabajo para [leer archivos de datos](#leer-archivos-de-datos). En Anaconda Navigator están disponibles tanto Jupyter Lab como la interfaz simple de Jupyter Notebook.

Jupyter desde VSCode corre una instancia del kernel por cada notebook (ver [#tutoriales](#referencias-y-tutoriales))

Jupyter desde línea de comandos o terminal:
- Ubicarse en el directorio raiz del proyecto:
   ```
   cd /directorio-del-proyecto
   ```

- Ejecutar UNA de las siguientes instancias:
   - Jupyter Lab:
      - Ejecución por defecto en http://localhost:8888
         ```
         jupyter lab
         ```
      - Ejecución en otro puerto: http://localhost:9090
         ```
         jupyter lab --port 9090
         ```
      - Ejecución desde una máquina virtual local, por ejemplo, WSL (Windows Subsystem for Linux):
         ```
         jupyter lab --port 9090 --ip 0.0.0.0
         ```

   - Jupyter (interfaz simple):
      ```
      jupyter notebook
      ```


## Instalar librerías

Puede instalar librerías directamente en una celda de Jupyter Notebook, por ejemplo:
```
!pip install plotly
```

Igualmente, puede abrir una nueva instancia de terminal o línea de comandos, activar el ambiente virtual si lo está utilizando, instalar la librería de interés (ejemplo, `pip install ploty`), y reiniciar el kernel (se pierden las variables en memoria).


## Leer archivos de datos

Los notebooks tienen como directorio de trabajo por defecto el directorio donde se inició la instancia de Jupyter, de tal manera que las rutas relativas de archivos dependen de dicho directorio.

Idealmente el directorio de trabajo es el directorio raiz del proyecto buscando utilizar rutas relativas de archivos:
```python
import pandas as pd

df = pd.read_csv("datos/archivo.csv")
```

Puede verificar y/o cambiar el directorio de trabajo:
```python
import os

# directorio de trabajo actual
print(os.getcwd())

# definir directorio HOME del equipo como directorio de trabajo 
home_dir = os.environ.get("HOME")
os.chdir(home_dir)
print(os.getcwd())
```

Jupyter desde Anaconda Navigator crea una instancia de Jupyter desde el directorio de instalación de Anaconda, por lo que se requiere utilizar rutas absolutas o cambiar el directorio de trabajo.

En Windows es posible tener rutas con backslash (\\), por lo que en Python se requiere reemplazar estos caracteres por slash (/) o duplicar cada uno de estos caracteres backslash (\\\\):
- Ruta: `C:\ruta-directorio\archivo.csv`
- Ruta en Python: `C:/ruta-directorio/archivo.csv`
- Ruta en Python: `C:\\ruta-directorio\\archivo.csv`

Por ejemplo:
```python
import pandas as pd

df = pd.read_csv("C:/ruta-directorio/archivo.csv")
df = pd.read_csv("C:\\ruta-directorio\\archivo.csv")
```

De lo contrario, puede obtener el error `SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes`.


## Referencias y tutoriales

Jupyter:
- Installing Jupyter Notebooks/Anaconda | Alex The Analyst: https://www.youtube.com/watch?v=WUeBzT43JyY
- Jupyter Tips and Tricks | Google Cloud Tech: https://www.youtube.com/watch?v=2eCHD6f_phE + https://towardsdatascience.com/interactive-data-science-with-jupyter-notebooks-457ab4928b08
- https://www.dataquest.io/blog/jupyter-notebook-tutorial/
- Jupyter Notebook Tutorial: Introduction, Setup, and Walkthrough | Corey Schafer: https://www.youtube.com/watch?v=HW29067qVWk

Jupyter Lab:
- Documentación oficial de Jupyter Lab: https://jupyterlab.readthedocs.io/en/stable/
- Jupyter Lab is AWESOME For Data Science | NeuralNine: https://www.youtube.com/watch?v=7wf1HhYQiDg
- Jupyter Lab desde Cero con Python | Garaje de ideas | Tech: https://www.youtube.com/watch?v=VFp2UIeji2Q

Jupyter en VSCode:
- Jupyter Notebooks in VS Code Walkthrough | Visual Studio Code: https://www.youtube.com/watch?v=DA6ZAHBPF1U
- https://code.visualstudio.com/docs/datascience/data-science-tutorial
- https://code.visualstudio.com/docs/datascience/jupyter-notebooks
