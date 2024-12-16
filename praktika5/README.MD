**Практическая работа №5. Threat Hunting.**

Для работы будем использовать развёрнутый стенд Wazuh из 3 практики.

Виртуальные машины с Wazuh

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/1.png)

Сетевой обмен между машинами

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/2.png)

Логин и пароль от admin с 3 работы

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/3.png)

Интерфейс Wazuh c подключенным агентом

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/5.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/4.png)

Установим suricata на агент 

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/6.png)

Загрузим правила

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/7.png)

Теперь настраиваем конфиг suricata

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/8.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/9.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/10.png)

После настройки suricata внесем пути логов в /var/ossec/etc/ossec.conf Wazuh'ы

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/11.png)

Проверка suricata

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/12.png)

Запускаем apache, установленный на практической работе #3

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/13.png)

Установка сканера nikto и язык программирования perl

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/14.png)

Результат сканирования 

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/15.png)

Установим threat hunting tools Yara

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/16.png)

Загрузчик не находит библиотеку libyara, был добавлен путь /usr/local/lib в файл конфигурации загрузчика /etc/ld.so.conf, чтобы решить эту проблему

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/17.png)

Теперь создаём конфиг yara.sh и добавим правила в Wazuh

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/18.png)

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/19.png)

Далее создаём скрипт malware_downloader.sh е для загрузки образцов вредоносного ПО

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/20.png)

Полученные логи на сервере Wazuh

![Image alt](https://github.com/V0vochka/SSSL/blob/main/praktika5/images/21.png)

В результате работы мы развернули полноценную SIEM, добавили IDS/IPS анализатор трафика,  настроили анализатор YARA-правил и с помощью него обнаружили вредоносные файлы.
