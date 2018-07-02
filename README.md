Стиль LaTeX для оформления отчетов о НИР, расчётно-пояснительной записки к курсовым и дипломным работам (ГОСТ 7.32-2001 и ГОСТ РВ 15.110-2003).
===========

## Описание
Данный стиль использовался при написании дипломной работы по теме "Разработка интерактивного программного комплекса для изучения методов обеспечения конфиденциальности информации" 4-го курса бакалавриата кафедры "Информационная безопасность" *Научно исследовательского университета Московский институт электронной техники (НИУ МИЭТ)*.

## Почему Lyx?

Использование инструмента Microsoft Office Word сопряжено необходимостью его запуска под виртуальной машиной на ОС Linux и покупной лицензии. А сам по себе объем работ по оформлению просто чудовищен, и зачастую составляет более 70% времени на подготовку текста дипломной работы. Те, кто пытался добавить пару схем в почти готовую работу и получали полностью слетевшее форматирование меня поймут.

В то же время и чисто блокнотно-консольные варианты не добавляют удобства - нужно помнить слишком много синтаксиса tex, который сложно назвать удобочитаемым.

Редакторы вроде Lyx решают обе проблемы - оформление происходит за пользователя кучей разных скриптов, но по большей части они скрыты за интерфейсом, который очень похож на другие текстовые процессоры.

## Отличия от latex-g7-32

Причина, по которой не используется оригинальный репозиторий **latex-g7-32** - некоторые специфические требования кафедры, которые на самом деле не соответствуют ГОСТу 7.32.
Также в исходном репозитории хоть и сделан упор на кросспралформенность и переносимость стиля между приложениями, не всегда очевидно, как заставить его работать. Здесь же все сводится в нескольким простым манипуляциям.

В дополнение:

* Шаблон отдельно от текста.
* Добавлен стиль для альбомной ориентации страницы.
* Добавлены разделы ПРИЛОЖЕНИЕ, СПИСОК УСЛОВНЫХ СОКРАЩЕНИЙ, ИСПОЛНИТЕЛИ.
* Счетчики для вывода числа рисунков, таблиц, разделов и страниц в РЕФЕРАТе (в начале документа).
* Уменьшены отступы слева для перечислений.

## Установка

Установка состоит из нескольких простых шагов.

1. Установка необходимых пакетов:
### Ubuntu

sudo add-apt-repository ppa:lyx-devel/release -y
sudo apt-get update
sudo apt-get install texlive-full texlive-xetex python-pygments lyx fonts-lyx

### Arch

sudo pacman -S texlive-latexextra texlive-bin texlive-lang lyx texlive-fontsextra

2. Запускаем LyX, переходим в *Настроки -> Обработка файлов -> Конверторы -> LaTeX (XeTeX) -> PDF (XeTeX) -> Изменить* и прописываем в строку *Преобразователь*:
```
xelatex -shell-escape $$i
```
После чего нажимаем *Применить -> Сохранить*.

3. Содержимое папки **lyx/layouts** копируем в папку **/home/имя_пользователя/.lyx/layouts**. Папка .lyx показывается, если включить отображение скрытых файлов.
4. Открываем файл vkr.lyx.
5. Переходим в *Документ -> Настройки -> Класс документа -> Локальный формат* и в папке **/home/имя_пользователя/.lyx/layouts** выбираете **g7-32_text.layout** - Применить - Закрыть.
6. Нажимаем меню *Инструменты -> Переконфигурировать*, ждем завершения и переоткрываем приложение.

Данные действия выполняются только один раз при установке. При скачивании изменений с данного репозитория достаточно скопировать папку **lyx/layouts** и выполнить переконфигурирование.

## Экспорт в PDF

Основной файл с материалами - **vkr.lyx**. Из него берутся настройки и из него идет конвертация в pdf. Разделы и приложения лежат в отдельных файлах, при экспорте собираются в один документ.
Для экспорта в PDF выбираем пункт *Файл -> Экспорт -> PDF (XeLaTex)*. Пример можно посмотреть в Релизах.

## Ссылки
(Репозиторий, на котором основан шаблон - **latex-g7-32**)[https://github.com/latex-g7-32/latex-g7-32]
(Приложение, разработка которого описана в материалах - **Cryptonite**)[https://github.com/dolfinus/cryptonite]