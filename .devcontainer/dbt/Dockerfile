FROM public.ecr.aws/lambda/python:3.10

# install requirements for devcontainer

RUN yum update -y
RUN yum install -y tar gzip git

# install pipx
RUN pip3 install --upgrade pip
RUN pip3 install pipx

# install the sqlfmt binary to /root/.local/bin
RUN pipx install 'shandy-sqlfmt[jinjafmt]' 

# install dbt requirements to /root/dbt
ADD requirements.txt requirements.txt
RUN pip3 install -r requirements.txt -t /root/libs

# Set entrypoint to bash
ENTRYPOINT [ "/bin/bash" ]