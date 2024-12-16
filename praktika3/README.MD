**Практическая работа №З 3. WAZUH.**

1) Разверните виртуальные машины (минимум 2 – сервер и агенты)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/1.png)

2) Обеспечить между ними сетевой обмен.

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/2.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/3.png)

3) Развернуть на belovvs ВМ сервер Wazuh скачав установщик и конфигурационный файл.

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/4.png)

4) Настроим конфиг указав IP-адрес серверной машины

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/5.png)

5) Соберем файл wazuh indexer'a и установим manager и dashboard

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/6.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/7.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/8.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/9.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/10.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/11.png)

6) После успешной установки перейдём на wazuh https://192.168.48.251, введём логин admin и сгенерированный пароль.

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/12.png)

Главное окно wazuh 

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/13.png)

7) Установив сервер, установим на 2ой машине агент, указав адрес серверной машины

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/14.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/15.png)

8) Перезапустим и запустим агент

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/16.png)

9) Проверим, видит сервер наш агент 

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/17.png)

Убедившись, что агент установлен, проанализируем обнаруженные
уязвимости с помощью средств wazuh.

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/18.png)

10) Далее настроим агента. Создадим проверку целостности файлов, проведя базовую настройку /var/ossec/etc/ossec.conf 

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/19.png)

11) Настроим выявление уязвимостей (в соответствии с документацией wazuh).

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/20.png)

12) Настроим выявление скрытых процессов. Установите пакеты, необходимые для сборки руткита:

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/21.png)

Далее настроим Wazuh-агент для запуска сканирования rootcheck каждые 2 минуты. В /var/ossec/etc/ossec.confфайле. Установите frequency параметр в <rootcheck>разделе на 120:

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/22.png)

13) Настроим выявление SQL-инъекций, установим apache.

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/23.png)

Разрешим внешний доступ к веб-портам.

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/24.png)

Проверка статуса 

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/25.png)

Добавим следующие строки в /var/ossec/etc/ossec.conf файл агента Wazuh для возможности отслеживать журналы доступа вашего сервера Apache

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/26.png)

14) Настроим выявление web shell attack.

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/27.png)

15) Проверим результат работы настроенных механизмов

[Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika3/images/28.png)
