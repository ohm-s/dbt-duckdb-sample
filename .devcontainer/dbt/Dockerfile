FROM public.ecr.aws/lambda/python:3.10

# install requirements for devcontainer
RUN yum update -y
RUN yum install -y tar gzip git unzip wget

# install pipx
RUN pip3 install --upgrade pip
RUN pip3 install pipx

# install the sqlfmt binary to /root/.local/bin
RUN pipx install 'shandy-sqlfmt[jinjafmt]' 

# Install duckdb binary to /root/.local/bin
RUN wget "https://github.com/duckdb/duckdb/releases/download/v0.9.2/duckdb_cli-linux-`uname -m`.zip" -O /tmp/duckdb.zip
RUN unzip /tmp/duckdb.zip -d /root/.local/bin
RUN rm /tmp/duckdb.zip

# install dbt requirements 
ADD requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

# Set entrypoint to bash
ENTRYPOINT [ "/bin/bash" ]