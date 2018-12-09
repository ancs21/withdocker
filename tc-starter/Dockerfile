FROM "ubuntu:bionic"
RUN apt-get update && yes | apt-get upgrade

RUN apt-get install -y libblas3 liblapack3 libstdc++6 python-setuptools python-pip
RUN apt-get install -y curl unzip
RUN pip install --upgrade pip

RUN pip install turicreate
RUN pip install Cython
RUN pip install contextlib2
RUN pip install pillow
RUN pip install lxml
RUN pip install jupyter
RUN pip install matplotlib

RUN mkdir -p /turicreate/data
WORKDIR /turicreate/data

RUN jupyter notebook --generate-config --allow-root
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /root/.jupyter/jupyter_notebook_config.py

EXPOSE 8888

CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/turicreate/data", "--ip=0.0.0.0", "--port=8888", "--no-browser"]
