# Use the Jupyter Data Science Notebook as the base image
FROM jupyter/datascience-notebook

# Install the latest AWS CLI version 2
USER root

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    unzip \
    bzip2 \
    git \
    && rm -rf /var/lib/apt/lists/*

# Install python packages
RUN pip install --no-cache-dir \
    pandas \
    boto3 \
    cassandra-driver \
    cassandra-sigv4 \
    duckdb==1.2.2

# Create an empty DuckDB database file
RUN python -c "import duckdb; duckdb.connect('mimic.db').close()"

USER jovyan
WORKDIR /home/jovyan/work

COPY . /home/jovyan/work

EXPOSE 8888

# Start the Jupyter Notebook server when the container launches
# The base image already configures Jupyter to run on start, but you can customize
# startup options here if needed.
CMD ["start-notebook.sh", "--NotebookApp.token=''", "--NotebookApp.password=''", "--allow-root"]
