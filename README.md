# otuslinuxproff_hw30
dhcp-pxe server

<details>
<summary><h3>Задание</h3></summary>
Настройка PXE сервера для автоматической установки
Цель:

Отрабатываем навыки установки и настройки DHCP, TFTP, PXE загрузчика и автоматической загрузки

Описание/Пошаговая инструкция выполнения домашнего задания:

Для выполнения домашнего задания используйте методичку
https://docs.google.com/document/d/1f5I8vbWAk8ah9IFpAQWN3dcWDHMqXzGb/edit?usp=share_link&ouid=104106368295333385634&rtpof=true&sd=true
Что нужно сделать?

Следуя шагам из документа https://docs.centos.org/en-US/8-docs/advanced-install/assembly_preparing-for-a-network-install установить и настроить загрузку по сети для дистрибутива CentOS8.

В качестве шаблона воспользуйтесь репозиторием https://github.com/nixuser/virtlab/tree/main/centos_pxe.

Поменять установку из репозитория NFS на установку из репозитория HTTP.

Настроить автоматическую установку для созданного kickstart файла (*) Файл загружается по HTTP.
</details>

Для более быстрой демонстрации в задании изменил образ для установки по PXE на ``` Rocky-9.1-x86_64-minimal ``` размером 1,5Gb. 

Так же дополнил Vagrantfile конфигом для видеоадаптера, в Vitualbox не нужно изменять его параметры

### Описание:
Стенд с двумя виртуальными машинами, одна - dhcp/pxe-сервер, вторая - клиент на который по сети будет установлена автоматически операционная система

### Запуск:
``` vagrant up ```

``` screen: ```


![Screenshot_20230324_205944](https://user-images.githubusercontent.com/59445051/227604404-3781ddb9-dc9c-4ef9-b367-e09b8bddb0ad.png)

![Screenshot_20230319_201436](https://user-images.githubusercontent.com/59445051/227600464-ccf8d3e7-039f-471e-bf7e-c9ce10c79812.png)

![Screenshot_20230319_202457](https://user-images.githubusercontent.com/59445051/227600803-55e7633d-af86-42d8-b252-675f9b05236b.png)

