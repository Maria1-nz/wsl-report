# Отчёт по развертыванию окружения WSL

**Студент:** Кудиярова Мария
**Дата:** 19.10.2026

## 1. Проверка виртуализации
Перед установкой была проведена проверка поддержки виртуализации в системе (Диспетчер задач -> Производительность -> ЦП). Виртуализация включена.

![Проверка виртуализации](images/01-virt.png)

## 2. Установка WSL и дистрибутива Ubuntu
Установка производилась через Windows PowerShell, запущенный от имени администратора. Сначала был проверен список доступных дистрибутивов, затем выполнена установка Ubuntu.

```powershell
wsl --list --online
wsl --install -d Ubuntu
```

![Установка WSL](images/02-install.png)

## 3. Запуск Ubuntu и создание пользователя
После перезагрузки системы приложение Ubuntu было найдено через поиск и запущено.

![Запуск приложения](images/03-ubuntu-app.png)

При первом запуске системы был создан пользователь `kudiyarova-m`, соответствующий требованиям задания.

![Создание пользователя](images/04-username.png)

Успешный вход в систему под учетной записью `kudiyarova-m`.

![Успешный вход](images/05-welcome.png)

## 4. Обновление пакетов
Перед установкой необходимого ПО было выполнено обновление списков пакетов.

```bash
sudo apt update
```

![Обновление пакетов](images/06-update.png)

## 5. Установка SDK, компилятора и СУБД
Установлены компилятор GCC (пакет `build-essential`), интерпретатор Python 3 и СУБД PostgreSQL.

```bash
sudo apt install -y build-essential python3 python3-pip postgresql postgresql-contrib
```

![Установка пакетов](images/07-install-packages.png)

## 6. Настройка PostgreSQL
Был выполнен запуск сервиса PostgreSQL и вход в консоль под системным пользователем `postgres`.

```bash
sudo service postgresql start
sudo -u postgres psql
```

![Вход в PostgreSQL](images/08-postgres-login.png)

В консоли PostgreSQL создан новый пользователь (роль) и база данных.

```sql
CREATE USER "kudiyarova-m" WITH PASSWORD '1909m';
CREATE DATABASE "kudiyarova_db" OWNER "kudiyarova-m";
```

![Создание БД](images/09-create-db.png)

## 7. Проверка версий установленного ПО
Финальная проверка версий компилятора, интерпретатора и СУБД.

```bash
gcc --version
python3 --version
psql --version
```

![Проверка версий](images/10-versions.png)
