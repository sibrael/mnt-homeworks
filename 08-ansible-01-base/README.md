# Домашнее задание к занятию 1 «Введение в Ansible»

## Подготовка к выполнению

1. Установите Ansible версии 2.10 или выше.
2. Создайте свой публичный репозиторий на GitHub с произвольным именем.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.

## Основная часть

1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте значение, которое имеет факт `some_fact` для указанного хоста при выполнении playbook.
 
 ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-1.png)

2. Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на `all default fact`.
3. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.
4. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.

   ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-2.png)
  
7. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились значения: для `deb` — `deb default fact`, для `el` — `el default fact`.
8.  Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.

    ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-3.png)
   
11. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`.

    ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-4.png)
   
14. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности.

    ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-5.png)
   
17. Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.
18. В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения.
19. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь, что факты `some_fact` для каждого из хостов определены из верных `group_vars`.

    ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-6.png)
   
22. Заполните `README.md` ответами на вопросы. Сделайте `git push` в ветку `master`. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым `playbook` и заполненным `README.md`.

    ![Image alt](https://github.com/sibrael/ter-homeworks/blob/186d52ff7afc4d286b15b041008d489de9446005/08-ansible-01-base/Ansible1-7.png)



