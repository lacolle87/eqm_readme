# Инструкция по использованию Telegram бота EpicQuoteMaster
Этот бот предназначен для управления автоматическими публикациями в каналы и группы Телеграма. При первом использовании необходимо настроить конфигурацию с помощью команды **/setconfig**.

В **Destination** пишется название канала или группы начиная с **@**.\
В **PostTime** устанавливается время постов в формате **CRON**, попробовать как он работает и сгенерировать время постов можно на этом сайте: https://crontab.guru/ .\
**ResetInterval** время сброса поста для повторного использования, по умолчанию 365 дней.\
В **RandomAscDsc** выбирается порядок в котором будут забираться посты из базы данных.
```
Random - случайный
Asc - от первого к последнему
Dsc - от последнего к первому
```
**IsReusable** Возможность повторного использования цитаты (true или false). Если true, то **RandomAscDsc** == Random.\
**RandomDelay:** Задержка перед публикацией цитаты в минутах. По умолчанию одна минута, максимум 720 минут.

Менять конфиг можно по одному, а можно сразу все пункты.

# Команды бота
### Основные команды
**/start:** Инициализация бота и приветственное сообщение.\
**/help:** Отображает список доступных команд с описанием их использования.
### Управление цитатами
**/getdata:** Получить данные из базы данных в формате JSON.\
**/adddata:** Добавить новые данные в базу данных в формате CSV (разделитель — вертикальная черта |).\
**/deldata:** Удалить данные из базы данных. Позволяет указать ID или диапазоны ID для удаления.\
**/post:** Постит цитату в группу или канал. Можно указать ID цитаты или ввести random для случайной цитаты.\
**/reset:** Сбросить статус цитаты. Можно указать ID цитаты или ввести all для сброса всех цитат.
### Управление конфигурацией
**/getconfig:** Получить текущие настройки конфигурации.\
**/setconfig:** Установить или изменить настройки конфигурации.
### Управление администраторами
**/addadmin:** Добавить нового администратора бота.\
**/getadmin:** Получить список текущих администраторов бота.\
**/deladmin:** Удалить администратора бота.
### Суперпользовательские команды
**/su:** Установить или снять статус суперпользователя для администратора. Доступно только суперпользователям. Обычный администратор не может назначать и удалять админов
#### Пример:
```
/su 12345678
```
# Конфигурация бота
Конфигурация бота задается с помощью команды /setconfig. В качестве параметров конфигурации используются следующие настройки:

**PostTime:** Время публикации цитаты в формате cron.\
**ResetInterval:** Интервал сброса статуса цитаты в днях.\
**RandomAscDsc:** Направление выбора случайной цитаты (Random, Asc или Dsc).\
**IsReusable:** Возможность повторного использования цитаты (true или false).\
**Destination:** Канал или группа для публикации цитат.\
**RandomDelay:** Задержка перед публикацией случайной цитаты в минутах.

#### Пример:
```
PostTime: 1-59 * * * *
ResetInterval: 1
RandomAscDsc: Asc
IsReusable: false
Destination: @group
RandomDelay: 1
```

# Загрузка постов в базу данных

После команды **/adddata** бот попросит ввести посты в формате **pipe delimited CSV**. Каждая запись начинается с новой строки, и записывается в таком виде **Author|Text** . До и после | пробел не ставится.
#### Пример ввода информации:
```
Albert Einstein|Imagination is more important than knowledge.
Winston Churchill|Success is not final, failure is not fatal: It is the courage to continue that counts.
Eleanor Roosevelt|No one can make you feel inferior without your consent.
Nelson Mandela|Education is the most powerful weapon which you can use to change the world.
```
