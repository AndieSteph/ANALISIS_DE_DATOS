#Utiliza ubuntu 20.04
FROM ubuntu:20.04

ENV DEBIAN_FRONTED=noninteractive

#Actualiza e instala dependencias 
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    build-esssential \
    wget \
    && apt-get clean

# Instalamos Jupyter
RUN pip3 install --upgrade pip

# crear directorio de trabajo
WORKDIR /workspace

# crear el directorio de Jupyter
RUN mkdir -p /root/.Jupyter

#agregar configuraciones de jupyter

RUN echo "c.NotebookApp.token = """ >> / root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.password = """ >> / root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >> / root/.jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = True" >> / root/.jupyter_notebook_config.py && 

# Expone el puerto para Jupyter notebook
EXPOSE 8888

# Comando para inicializar jupyter notebook
CMD ["jupyter", "notebook","--ip=0.0.0.0","--port=8888","--no-browser","allow"]