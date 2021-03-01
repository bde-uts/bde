FROM jupyter/scipy-notebook:0ce64578df46 as build

RUN pip install pandas==1.2.2 \
    && pip install pyarrow==2.0.0 \
    && pip install psycopg2-binary==2.8.5 \
    && pip install pymongo==3.11.3

ENV PYTHONPATH "${PYTHONPATH}:/home/jovyan/work"

RUN echo "export PYTHONPATH=/home/jovyan/work" >> ~/.bashrc

WORKDIR /home/jovyan/work
