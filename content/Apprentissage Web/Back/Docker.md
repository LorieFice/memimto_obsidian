Docker permet de créer des containers qui encapsulent des applications ou serveurs avec les bonnes dépendances.
## Commandes Docker de base

- `docker run <image>` : Crée et démarre un nouveau conteneur à partir d'une image Docker.
- `docker ps` : Affiche tous les conteneurs en cours d'exécution.
- `docker stop <container>` : Arrête un conteneur en cours d'exécution.
- `docker rm <container>` : Supprime un conteneur.
- `docker pull <image>` : Télécharge une image Docker depuis un registre.
- `docker build -t <image_name> .` : Crée une nouvelle image Docker à partir d'un Dockerfile.
- `docker volume create <volume_name>` : Crée un volume Docker pour stocker des données.
- `docker network create <network_name>` : Crée un réseau Docker pour connecter des conteneurs.

Docker.nvidia :
```bash
# This is a sample Dockerfile you can modify to deploy your own app based on face_recognition on the GPU
# In order to run Docker in the GPU you will need to install Nvidia-Docker: https://github.com/NVIDIA/nvidia-docker
FROM nvidia/cuda:12.3.2-cudnn9-devel-ubuntu22.04
ENV DEBIAN_FRONTEND=noninteractive
ENV TZ="Europe/Paris"

RUN ln -fs /usr/share/zoneinfo/Europe/Paris /etc/localtime && apt-get update && apt-get -y install python3 python3-pip git cmake build-essential

RUN git clone https://github.com/davisking/dlib.git\
&&  cd dlib\
&&  mkdir build\
&&  cd build\
&&  cmake .. -DDLIB_USE_CUDA=1 -DUSE_AVX_INSTRUCTIONS=1\
&&  cmake --build .\
&&  cd ..\
&&  python3 setup.py install --set DLIB_USE_CUDA=1

WORKDIR /app

COPY requirements.txt requirements.txt

ENV DEPS="zlib1g-dev libjpeg-dev"

RUN apt-get update \
  && apt-get install ffmpeg libsm6 libxext6  -y \
  && apt-get install -y ${DEPS} --no-install-recommends \
  && pip3 install click==7.1.2\
  && pip3 install -r requirements.txt \
  && rm -rf /var/lib/apt/lists/* \
  && rm -rf /usr/share/doc && rm -rf /usr/share/man \
  && apt-get purge -y --auto-remove ${DEPS} \
  && apt-get clean

COPY . .

RUN python3 setup.py install

EXPOSE 8000

CMD ["gunicorn", "-b", "0.0.0.0", "--log-level=DEBUG", "memimto.__main__:app"]
```

Les containers Docker sont basés sur des systèmes Linux, d'où les commandes que l'on utilise. Le fichier ci-dessus configure et lance les différents serveurs dans le container.