Stable Diffusion Local integration with Telegram Bot API.

Бот предназначен для управления локальной версией Stable Diffusion на примере AUTOMATIC1111,
через Telegram.\
Бот использует API AUTOMATIC для взаимодействия с SD и асинхронную библиотеку Aiogram, Aiohttp и многопоточность
для взаимодействия с Telegram.

Фишки!!! : 
- **Реализована независимая работа с несколькими видеокартами и интерфейсами, таким образом, что пользователи становятся в очередь на генерацию(отслеживая свею позицию в прогресс баре), после чего, когда их картинка начала генерироваться, они также видят другой интерактивный прогресс бар с процентами.**
- **Очереди по принципу LILO, полностью ассихронная реализация логики программы, многопоточность для прогресс баров**
- **История генераций для каждого пользователя хранится в БД SQLite, пользователь имеет к ней доступ и может перегенерировать изображение даже после перезапуска программы**
- **Систему можно масштабировать, добавив больше данных (настройки соединения с SD/веб-интерфейсом) для независимых обработчиков, работающих с пользователями в очереди**




Функционал:
- Добавление и удаление пользователей и админов в файле .env (контроль за пользователями и наделение их правами администратора)
- В папке data в файле sd_config можно изменить стандартные настройки генерации, они используются при добавлении новых пользователей и админов, и при нажатии на кнопку Сброс настроек
- Возможность переключения моделей, а так же выбора нескольких стилей
- Настройки генерации сохраняются для каждого пользователя в базе данных
- Настройки, которые можно изменить: Negative prompt, Model, Styles, CFG Scale, Batch Size, Sampler, Hires Fix
- Вывод текущих настроек
- Сброс настроек на стандартные, заданные в файле sd_config в папке settings
- Включение и отключение сохранения фото на ПК, в файле sd_config в папке settings, изменить значение переменной save_files на True чтобы включить и False выключить. В переменной output_folder можно указать свой путь для сохранения изображений.
- Запуск SD при старте бота. Можно включить и отключить в файле bot_config.
- Перезапуск SD с кнопки в меню Settings. Кнопка доступна только админам бота.

  
Установка:
1. Создать папку в любом месте на диске
2. В этой папке в адресной строке написать cmd и нажать Enter
3. Клонировать репозиторий
4. или скачать Zip архив и распаковать
5. Следовать инструкции по запуску

Инструкция по запуску:
1. В файле "webui-user.bat", в строке set COMMANDLINE_ARGS добавить --api (set COMMANDLINE_ARGS=--args)
2. Запустить SD
3. В файл .env положить токен от бота
4. Запустить файл "start_bot.bat"

Часть кода взята отсюда, за что благодарность автору
https://github.com/odintsovkos/SDTelegramBot.git
