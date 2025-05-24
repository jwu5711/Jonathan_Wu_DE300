FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

RUN apt-get update && apt-get install -y --no-install-recommends \
    default-jdk \
    curl \
    build-essential \
    libsnappy-dev \
    liblz4-tool \
    libbz2-dev \
    libssl-dev \
    libffi-dev \
    && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
ENV PATH="$JAVA_HOME/bin:$PATH"

RUN curl -O https://archive.apache.org/dist/spark/spark-3.4.1/spark-3.4.1-bin-hadoop3.tgz && \
    tar xzf spark-3.4.1-bin-hadoop3.tgz -C /usr/local && \
    rm spark-3.4.1-bin-hadoop3.tgz

ENV SPARK_HOME=/usr/local/spark-3.4.1-bin-hadoop3
ENV PATH="$SPARK_HOME/bin:$PATH"

ENV PYSPARK_SUBMIT_ARGS="--master local[*] pyspark-shell"

RUN pip install --upgrade pip && pip install \
    notebook \
    matplotlib \
    pandas \
    numpy \
    pyspark==3.4.1

WORKDIR /workspace

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=''", "--NotebookApp.password=''"]
