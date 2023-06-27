FROM ubuntu:20.04
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ="Etc/UTC"
RUN apt-get update
RUN apt-get upgrade -y
RUN apt install -y python3
RUN apt install -y python3-pip
RUN apt install -y python3-venv
RUN python3 -m venv hallasenv
RUN source hallasenv/bin/activate
WORKDIR /app 
COPY requirements.txt /app
RUN pip3 install -r requirements.txt --no-cache-dir
COPY . /app 
# Move below lines to composer file if you wanted to use docker|podman compose
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
