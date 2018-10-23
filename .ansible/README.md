# Ansible for SF4Project
[![Build Status](https://travis-ci.org/DevAndreas/sf4project.svg?branch=master)](https://travis-ci.org/DevAndreas/sf4project)

# Развертывание проекта для разработки

Для развертывания проекта Вам потребуется установить Ubuntu Server 16.04.5 в минимальной установке + OpenBSD Secure Shell Server. [Скачать ubuntu-16.04.5-server-amd64.iso](http://releases.ubuntu.com/16.04/ubuntu-16.04.5-server-amd64.iso)

# Установка Ansible
Для установки ansible запустите следующие команды
```sh
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible
```

# Установка Git
Также Вам понадобится git, установите его
```sh
sudo apt-get install git
```

# Клонируйте проект
На данном этапе Вам понадобится только папка .ansible. Все остальные манипуляции по настройке
нашего окружения разработчика мы будет производить при помощи запуска программы ansible. Выполните следующие команды
```sh
git clone https://github.com/DevAndreas/sf4project
mv sf4project/.ansible ./ansible-sf4project
rm -rf sf4project
```

# Автоматическая настройка проекта
Для автоматической настройки проекта перейдите в папку, где находится конфигурация ansible. В предыдущем примере это была папка ./ansible-sf4project. Затем выполните следующие команды
```sh
cd ./ansible-sf4project
/bin/bash ./start.sh
```

# Полный скрипт настройки сервера для разработки
Данный скрипт также можно запускать при использовании Vagrand
```sh
#!/bin/bash

sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible git

RND=$RANDOM
git clone https://github.com/DevAndreas/sf4project sf4project-$RND
mv sf4project-$RND/.ansible ./ansible-sf4project
rm -rf sf4project-$RND
cd ./ansible-sf4project && bash ./start.sh
```