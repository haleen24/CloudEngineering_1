#образ питона
FROM python

#образ юпитер хаба
FROM jupyterhub/jupyterhub

#путь к папке
ARG NOTEBOOKS_FROM=/home

WORKDIR /app

#установка sudo
#RUN apt-get update && \
#      apt-get -y install sudo


# установка нужных для работы компонентов
RUN pip install jupyterhub

RUN pip install --upgrade notebook



#вот эта строчка создает пользователя, для которого можно создать сервер
RUN useradd -m -d /home/admin -s /bin/bash -p $(openssl passwd -1 admin) admin


# копирование из папки, которая передалась аргументом, в папку в volume
COPY ${NOTEBOOKS_FROM} /home/admin


COPY .. /app

EXPOSE 8000

CMD jupyterhub