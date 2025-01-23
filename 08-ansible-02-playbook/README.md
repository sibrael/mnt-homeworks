# Домашнее задание к занятию 2 «Работа с Playbook»

## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.
4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`.
   Для экономии средств в качестве сервера выполнения был выбран localhost
2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev). Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по [ссылке](https://www.dmosk.ru/instruktions.php?object=ansible-nginx-install). не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!
3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.
4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
   ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/2fc3423d486f0023ac81719fff95588b701e934e/08-ansible-02-playbook/Ansible2-1.png)
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
   ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/2fc3423d486f0023ac81719fff95588b701e934e/08-ansible-02-playbook/Ansible2-2.png)
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
   ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/2fc3423d486f0023ac81719fff95588b701e934e/08-ansible-02-playbook/Ansible2-3.png)
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
    ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/2fc3423d486f0023ac81719fff95588b701e934e/08-ansible-02-playbook/Ansible2-4.png)
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по [ссылке](https://github.com/opensearch-project/ansible-playbook). Так же приложите скриншоты выполнения заданий №5-8
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

# netology-ansible/clickhouse-vector-app
## Инфраструктура
* Сервер clickhouse и vector развернуты на localhost, в случае необходимости путём корректировки файла prod.yml место равертывания меняется;
  > https://clickhouse.com/docs/ru
  > https://vector.dev/docs/setup/installation/

## Playbook
Playbook производит установку и приложений на серверах. По развертывание приложения предусмотрено для rpm-based образов clickhouse (в соответствии с предоставленным примером). Для развертывания приложения vector используются образы deb

В playbook используются следующие модули:
 * ansible.builtin.get_url,
 * ansible.builtin.template,
 * ansible.builtin.yum,
 * ansible.builtin.apt
 * ansible.builtin.meta
 * ansible.builtin.service
 * ansible.builtin.command
  
### Clickhouse
* установка clickhouse
* создание базы данных и таблицы в ней

### Vector
* установка vector
* изменение конфигов приложения
  
### Variables
В каталоге group_vars задаются следующие переменные.

|vars|value|
|-|--------|
|clickhouse_version|версия clickhouse|
|vector_version|версия vector|
|vector_config|директория конфига vector|

## Install Clickhouse
1. Скачивание rpm-пакетов
2. Установка Clickhouse
3. Создание базы данных logs.

Через group_vars можно задать следующие параметры:
* clickhouse_version - версия clickhouse

## Install Vector

1. Скачивание rpm-пакетов
2. Установка Clickhouse
3. Создание базы данных logs.

Через group_vars можно задать следующие параметры:
* vector_version - версия vector
* vector_config - директория конфига vector

## Установка и развертывание
* Для установки приложений:
  ```
  ansible-playbook -i inventory/prod.yml site.yml
  ```
* Для проверки конфигурации:
  ```
  ansible-playbook -i inventory/prod.yml site.yml --check
  ```
  ```
  ansible-playbook -i inventory/prod.yml site.yml --diff
  ```
-----
10. Готовый README.md размещаю в личном репозитории github.



---
