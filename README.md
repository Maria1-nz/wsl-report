Отчёт по развертыванию окружения WSL
Студент: Кудиярова Мария
Дата: 19.10.2026

1. Проверка виртуализации
Перед установкой была проведена проверка поддержки виртуализации в системе (Диспетчер задач -> Производительность -> ЦП). Виртуализация включена.

https://images/01-virt.png

2. Установка WSL и дистрибутива Ubuntu
Установка производилась через Windows PowerShell, запущенный от имени администратора. Сначала был проверен список доступных дистрибутивов, затем выполнена установка Ubuntu.

powershell
wsl --list --online
wsl --install -d Ubuntu
https://images/02-install.png

3. Запуск Ubuntu и создание пользователя
После перезагрузки системы приложение Ubuntu было найдено через поиск и запущено.

https://images/03-ubuntu-app.png

При первом запуске системы был создан пользователь kudiyarova-m, соответствующий требованиям задания.

https://images/04-username.png

Успешный вход в систему под учетной записью kudiyarova-m.

https://images/05-welcome.png

4. Обновление пакетов
Перед установкой необходимого ПО было выполнено обновление списков пакетов.

bash
sudo apt update
https://images/06-update.png

5. Установка SDK, компилятора и СУБД
Установлены компилятор GCC (пакет build-essential), интерпретатор Python 3 и СУБД PostgreSQL.

bash
sudo apt install -y build-essential python3 python3-pip postgresql postgresql-contrib
https://images/07-install-packages.png

6. Настройка PostgreSQL
Был выполнен запуск сервиса PostgreSQL и вход в консоль под системным пользователем postgres.

bash
sudo service postgresql start
sudo -u postgres psql
https://images/08-postgres-login.png

В консоли PostgreSQL создан новый пользователь (роль) и база данных.

sql
CREATE USER "kudiyarova-m" WITH PASSWORD '1909m';
CREATE DATABASE "kudiyarova_db" OWNER "kudiyarova-m";
https://images/09-create-db.png

7. Проверка версий установленного ПО
Финальная проверка версий компилятора, интерпретатора и СУБД.

bash
gcc --version
python3 --version
psql --version
https://images/10-versions.png

