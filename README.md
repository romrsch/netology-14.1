## Домашнее задание к занятию "14.1 Создание и использование секретов"
### Задача 1: Работа с секретами через утилиту kubectl в установленном minikube
Выполните приведённые ниже команды в консоли, получите вывод команд. Сохраните задачу 1 как справочный материал.

### Как создать секрет?
```
openssl genrsa -out cert.key 4096
openssl req -x509 -new -key cert.key -days 3650 -out cert.crt \
-subj '/C=RU/ST=Moscow/L=Moscow/CN=server.local'
kubectl create secret tls domain-cert --cert=certs/cert.crt --key=certs/cert.key
```
***Ответ:***
```sh
 openssl genrsa -out cert.key 4096
 openssl req -x509 -new -key cert.key -days 3650 -out cert.crt -subj '/C=RU/ST=Novosibirsk/L=Novosibirsk/CN=server.local'
 ```
 ![Alt text](https://i.ibb.co/fdmPHkL/Screenshot-1.jpg)
 
### Как просмотреть список секретов?
```
kubectl get secrets
kubectl get secret
```
### Как просмотреть секрет?
```
kubectl get secret domain-cert
kubectl describe secret domain-cert
```
***Ответ:***

![Alt text](https://i.ibb.co/cDq5B5p/Screenshot-2.jpg)

![Alt text](https://i.ibb.co/XDKvPvW/Screenshot-3.jpg)

### Как получить информацию в формате YAML и/или JSON?
```
kubectl get secret domain-cert -o yaml
kubectl get secret domain-cert -o json
```
***Ответ:***
в формате YAML
![Alt text](https://i.ibb.co/2M9jhKX/Screenshot-4.jpg)
в формате JSON
![Alt text](https://i.ibb.co/WW056R8/Screenshot-5.jpg)

### Как выгрузить секрет и сохранить его в файл?
```
kubectl get secrets -o json > secrets.json
kubectl get secret domain-cert -o yaml > domain-cert.yml
```
***Ответ:***

![Alt text](https://i.ibb.co/F6S0tHV/Screenshot-6.jpg)

### Как удалить секрет?
```
kubectl delete secret domain-cert
```
***Ответ:***

![Alt text](https://i.ibb.co/z4GH8y6/Screenshot-7.jpg)

### Как загрузить секрет из файла?
```
kubectl apply -f domain-cert.yml
```
***Ответ:***

![Alt text](https://i.ibb.co/3Cd3qvH/Screenshot-8.jpg)


### Задача 2 (*): Работа с секретами внутри модуля
Выберите любимый образ контейнера, подключите секреты и проверьте их доступность как в виде переменных окружения, так и в
виде примонтированного тома.
