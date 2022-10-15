FROM python:3-slim-bullseye
ARG USERNAME=butra
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN apt update && apt install -y sudo
RUN pip install  pipenv
RUN pipenv install alpaca_trade_api

RUN groupadd --gid $USER_GID $USERNAME \
&& useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
&& echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
&& chmod 0440 /etc/sudoers.d/$USERNAME 
USER ${USERNAME}

CMD ["python3"]