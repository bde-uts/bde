FROM jupyter/pyspark-notebook:0ce64578df46

USER root
# Add essential packages
RUN apt-get update && apt-get install -y build-essential curl git gnupg2 nano apt-transport-https software-properties-common
# Set locale
RUN apt-get update && apt-get install -y locales \
    && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    && locale-gen
# Add config to Jupyter notebook
#COPY jupyter/jupyter_notebook_config.py /home/jovyan/.jupyter/
RUN chmod -R 777 /home/jovyan/
# Spark libraries
RUN wget https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk/1.7.4/aws-java-sdk-1.7.4.jar -P $SPARK_HOME/jars/
RUN wget https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/2.7.3/hadoop-aws-2.7.3.jar -P $SPARK_HOME/jars/

USER $NB_USER

# Install Python requirements
RUN pip install pandas==1.2.2 \
    && pip install s3fs==0.5.2 \
    && pip install pyarrow==2.0.0 \
    && pip install findspark==1.4.2

ENV PYTHONPATH "${PYTHONPATH}:/home/jovyan/work"

RUN echo "export PYTHONPATH=/home/jovyan/work" >> ~/.bashrc

WORKDIR /home/jovyan/work

# Run the notebook
CMD ["/opt/conda/bin/jupyter", "lab", "--allow-root"]





