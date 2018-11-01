FROM python:3.6

ENV AIRFLOW_GPL_UNIDECODE yes

COPY requirements.txt .
RUN pip install -r requirements.txt

ENV AIRFLOW_HOME /usr/local/airflow
RUN useradd -ms /bin/bash -d ${AIRFLOW_HOME} airflow
USER airflow
WORKDIR ${AIRFLOW_HOME}
COPY airflow.cfg ${AIRFLOW_HOME}



RUN airflow initdb && \
    airflow scheduler -D && \
    airflow webserver -D
