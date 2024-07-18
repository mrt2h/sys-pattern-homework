Домашнее задание к занятию "Что такое DevOps. СI/СD" - Хасаншин Марат
Решение 2
1. Создана ВМ на Яндекс облаке с образом диска jenkins на ubuntu. Она же будет использоваться для работы registry и golang. Проведена первоначальная настройка jenkins. http://158.160.129.4:8080/ ![8-02-vmyc-jenki](https://github.com/user-attachments/assets/6d416fe3-bd80-47db-aea5-2bca8cf02d79)
2. Установлен golang из репозитория ubuntu: sudo apt install golang
3. Установлен докер: sudo apt install docker.io Сделаны настройки по добавлению пользователя jenkins в группу docker и разрешение на использование http-репозитория.
4. Из докер-хаба скачан nexus: sudo docker pull sonatype/nexus3, запущен с пробросом порта 8081-8082 и проведена начальная настройка. Запуск командой docker run -d -p 8081:8081 -p :8082:8082 --name nexus -e INSTALL4J_ADD_VM_PARAMS="-Xms512m -Xmx512m -XX:MaxDirectMemorySize=273m" sonatype/nexus3. Создан репозиторий для загрузки образа docker ![4](https://github.com/user-attachments/assets/55887d10-af4e-46c3-9911-1a492c7702b9)


5. Создана задача с приведенными параметрами и запущена сборка, завершившаяся успешно.
![5](https://github.com/user-attachments/assets/b6a3bab4-4206-4003-93c4-41fb7795033a)
![6](https://github.com/user-attachments/assets/10f205eb-19f4-49e7-8db4-d1f60678c91b)
![7](https://github.com/user-attachments/assets/85deda08-e588-407b-b4ea-539e5ea52653)

Решение 2
1. Настройки приведены в вид пайплайна 
![1](https://github.com/user-attachments/assets/19e02822-0d20-4844-9d98-c55181ced905)
2. Запущена сборка
![2](https://github.com/user-attachments/assets/0daa813a-d2dd-4488-9082-55d7ff38d659)


Решение 3
1. Создан raw repo в nexus, переделан пайплайн на сборку на golang вместо docker-образа, и push в репо через curl
![1](https://github.com/user-attachments/assets/13867780-75b3-40a3-8866-819cd1d6158c)
2. Запущена сборка 
![2](https://github.com/user-attachments/assets/8ee2de5b-09a4-48e8-8876-e2b2cba1ac29)
