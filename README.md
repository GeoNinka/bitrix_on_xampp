# bitrix_on_xampp
Установка пробной версии bitrix 1c на локальном сервере xampp.

## Установка
1. Скачиваем [xampp](https://www.apachefriends.org/ru/index.html).
1. Скачиваем [отсюда](https://www.1c-bitrix.ru/download/cms.php#tab-subsection-2) bitrixsetup.php.
1. Запускаем xampp, жмём Explorer и в папке htdocs создаём папку bitrix, внутрь копируем bitrixsetup.php.
1. В Файле php.ini:
    - Меняем ```short_open_tag=Off``` на ```short_open_tag=On```.
    - Раскомментируем ```extension=gd```.
    - Меняем ```display_errors=On``` на ```display_errors=Off```.
1. В браузере переходим на localhost/bitrix, открываем bitrixsetup.php, и следуем [инструкции из ЛМС](https://online.mospolytech.ru/mod/scorm/view.php?id=438858) до пункта "Начало установки". 
1. В файле ```/bitrix/modules/main/classes/general/main.php``` комментируем 3407 строчку ```$uniq = Main\Security\Random::getString(32);``` и добавляем под ней ```$uniq = md5(uniqid(rand(), true));```.
1. В пункте "Создание базы данных": 
    - пользовтель: root.
    - пароль: оставляем поле пустым.
    - Для админа то же самое.
    - Если будете переделывать этот пунк не забудьте дропнуть БД в localhost/phpmyadmin.
1. Завершаем установку по инструкции.