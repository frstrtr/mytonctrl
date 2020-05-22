## HOWTO
This console program is a wrapper over `fift`,` lite-client` and `validator-engine-console`. It was created to facilitate the management of wallets, domains, and validators on the Linux.
Installing the TON validator through the MyTonCtrl console utility.
The instructions and scripts below were verified on Ubuntu 18.04.

![](https://raw.githubusercontent.com/igroman787/mytonctrl/master/screens/mytonctrl-status.png)

## System requirements

To start a validator (full node) in testnet we recommend looking at these system requirements.

| Configuration | CPU (cores) | RAM (GB) | SSD/NVME (GB) | Network (Mbit/s)|
|---|:---|:---|:---|:---|
| Minimal |6|16|256|500|
| Recommended |8|32|480-960|1000|


## Функционал
- [x] Показать статус сети TON
- [x] Управление локальными кошельками
	- [x] Создать локальный кошелек
	- [x] Активировать локальный кошелек
	- [x] Показать локальные кошельки
	- [x] Импортировать кошелек из файла (.pk)
	- [x] Сохранить адрес кошелька в файл (.addr)
	- [x] Удалить локальный кошелек
- [x] Показать статус аккаунта
	- [x] Показать баланс аккаунта
	- [x] Показать историю аккаунта
	- [x] Показать статус аккаунта из закладок
- [x] Перевод средств на кошелек
	- [x] Перевод фиксированной суммы
	- [x] Перевод всей суммы (all)
	- [x] Перевод всей суммы с диактивацией кошелька (alld)
	- [x] Перевод средств на кошелек из закладок
	- [ ] Пропустить средства через миксер
- [x] Управление закладками
	- [x] Добавить аккаунт в закладки
	- [x] Показать закладки
	- [x] Удалить закладку
- [x] Управление предложениями
	- [x] Показать предложения
	- [x] Проголосовать за предложение
	- [x] Автоматическое голосование за ранее проголосованные предложения
- [x] Управление доменами
	- [x] Арендовать новый домен
	- [x] Показать арендованные домены
	- [x] Показать статус домена
	- [x] Удалить домен
	- [ ] Автоматическое продление доменов
- [ ] Автоматическая отправка средств по расписанию
	- [ ] Добавить правило в расписание
	- [ ] Показать правила расписания
	- [ ] Удалить правило из расписания
- [x] Управление валидатором
	- [x] Участвовать в выборах валидатора
	- [x] Возвращать ставку + вознаграждение
	- [ ] Автозапуск валидатора при аварийном завершении
	- [ ] Отправлять статистику валидатора на http://validators.ton

## Список проверенных операционных систем
```
Ubuntu 18.04.2
Debian 10.3
```

## Описание установочных скриптов
- `toninstaller.sh` - Данный скрипт клонирует исходники `TON` и `mytonctrl` в папки `/usr/src/ton` и `/usr/src/mytonctrl`, компилирует программы из исходников и прописывает их в `/usr/bin/`.
- `vpreparation.sh` - Данный скрипт создает пользователя `validator` для работы валидатора и пропишет его в автозагрузку через крон.
- `mytoninstaller.py` - Данный скрипт производит настройку `mytonctrl` и создание ключей для подключения к валидатору.
- `vconfig.sh` - Данный скрипт настроит доступ для подключения к валидатору `lite-client` и `validator-engine-console`.

## Режимы установки
Есть два режима установки: `lite` и `full`. Оба они **компилируют** и устанавливают компоненты `TON`. Однако `lite` версия не настраивает и не запускает валидатор. В данный момент `full` установка сырая/баганутая/недоделанная, поэтому вы можете установить в режиме `lite` и дальше уже руками дописать настройки в конфигурацию `mytonctrl` для взаимодействия с вашим валидатором.

## Установка (Ubuntu)
1. Скачайте и выполните скрипт `install.sh` с нужным вам режимом установки. Мы будем устанавливать в режиме `lite`. В ходе установки у вас будет несколько раз запрошен пароль суперпользователя.
```sh
wget https://raw.githubusercontent.com/igroman787/mytonctrl/master/scripts/install.sh
sudo sh install.sh -m lite
```

2. Готово. Можете пробовать запустить программу `mytonctrl`.
```sh
mytonctrl
```


## Установка (Debian)
1. Скачайте и выполните скрипт `install.sh` с нужным вам режимом установки. Мы будем устанавливать в режиме `lite`. В ходе установки у вас будет несколько раз запрошен пароль суперпользователя.
```sh
wget https://raw.githubusercontent.com/igroman787/mytonctrl/master/scripts/install.sh
su root -c 'sh install.sh -m lite'
```

2. Готово. Можете пробовать запустить программу `mytonctrl`.
```sh
mytonctrl
```
