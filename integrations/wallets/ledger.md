---
title: Ledger
description:  В этом руководстве рассказывается, как использовать аппаратный кошелек Ledger для подписи транзакций в Moonbeam, используя его функции совместимости с Ethereum.
---

# Аппаратный кошелек Ledger

![Intro diagram](/images/ledger/ledger-banner.png)

## Вступление

Аппаратные кошельки обеспечивают более безопасный способ хранения криптовалютных средств, поскольку закрытый ключ (используемый для подписи транзакций) хранится в офлайне. На момент написания статьи компания Ledger предлагает два аппаратных кошелька: Ledger Nano S и Ledger Nano X.

Поскольку Moonbeam полностью совместим с Ethereum, а Ledger теперь поддерживает подписание в различных сетях Chain ID, вы можете использовать свое устройство Ledger для подписи транзакций на Moonbeam!

В этом руководстве рассказывается о том, как начать работу с аппаратным кошельком Ledger на Moonbase Alpha. В руководстве показаны шаги только для устройства Ledger Nano X, но вы можете выполнить их и для Ledger Nano S. Этот же процесс можно применить и к другим сетям экосистемы Moonbeam.


## Проверка необходимых условий

Прежде чем приступить к работе, обновите [Ledger Live](https://www.ledger.com/ledger-live/download) до последней актуальной версии. Также убедитесь, что на вашем аппаратном кошельке Ledger установлена последняя версия прошивки. На сайте поддержки Ledger можно найти руководство по обновлению прошивки устройств [Ledger Nano S](https://support.ledger.com/hc/en-us/articles/360002731113-Update-Ledger-Nano-S-firmware) и [Ledger Nano X](https://support.ledger.com/hc/en-us/articles/360013349800-Update-Ledger-Nano-X-firmware).

После установки последней версии прошивки убедитесь, что вы используете новейшее приложение Ethereum. На сайте поддержки Ledger можно найти руководство [как установить приложение Ethereum](https://support.ledger.com/hc/en-us/articles/360009576554-Ethereum-ETH-).


На момент написания статьи используются следующие версии:

 - Ledger Live 2.29
 - Ledger Nano S firmware v2.0.0
 - Ledger Nano X firmware v1.3.0
 - Ethereum app v1.8.5

Кроме того, вам понадобится MetaMask в качестве посредника между вашим устройством Ledger и Moonbase Alpha. Убедитесь, что ваш MetaMask [подключен к Moonbase Alpha](/integrations/wallets/metamask/). Пользователям Chrome (версия 91) необходимо выполнить несколько дополнительных шагов, которые [подробно описаны в этом руководстве](#chrome-browser). Использование Firefox приведет к гораздо более простому/легкому опыту.

Обратите внимание, что ваше устройство Ledger будет подписывать транзакции в той сети MetaMask, к которой подключено.


## Импорт вашего Ledger аккаунта в MetaMask

Для начала работы необходимо подключить устройство Ledger к компьютеру, разблокировать его, открыть приложение Ethereum. Далее, чтобы импортировать ваш аккаунт Ethereum Ledger в MetaMask, выполните следующие действия:

 1. Нажмите на логотип в правом верхнем углу, чтобы раскрыть меню
 2. Выберите " Connect Hardware Wallet" (Подключить аппаратный кошелек)

![MetaMask Connect Hardware Wallet](/images/ledger/ledger-images1.png)

На следующем экране вам будет предложено выбрать, какой аппаратный кошелек вы хотите использовать в MetaMask. На момент написания статьи поддерживаются только аппаратные кошельки Ledger и Trezor. Далее выполните следующие действия:

 1. Выберите логотип Ledger
 2. Нажмите " Continue" (Продолжить)

![MetaMask Select Ledger Hardware Wallet](/images/ledger/ledger-images2.png)

Если MetaMask удалось успешно подключиться к вашему устройству Ledger, вы должны увидеть список из пяти аккаунтов, привязанных к Ethereum. В противном случае еще раз проверьте, что Ledger Live закрыт, вы подключили устройство Ledger к компьютеру, разблокировали его и открыли приложение Ethereum. Если вы используете Chrome, проверьте эти [дополнительные шаги](#chrome-browser).

Из этого списка пяти аккаунтов Ethereum выполните следующие действия:

 1. Выберите аккаунты, которые Вы хотите импортировать из Ledger.
 2. Нажмите на " Unlock"(Разблокировать)

![MetaMask Select Ethereum Accounts to Import](/images/ledger/ledger-images3.png)

Если Вы успешно импортировали аккаунт Ledger, созданный на основе Ethereum, Вы должны увидеть его на главном экране MetaMask, как показано на следующем изображении:

![MetaMask Successfully Imported Ledger Account](/images/ledger/ledger-images4.png)

Теперь Вы успешно импортировали совместимый с Moonbeam аккаунт с Вашего Ledger и теперь готовы приступить к [подписанию транзакций с использованием аппаратного кошелька](#signing-a-transaction-using-your-ledger).

### Браузер Chrome

Начиная с версии 91 Chrome, пользователи, которые хотят подключить свое устройство Ledger к MetaMask, должны использовать последнюю версию Ledger Live (v2.29 на момент написания статьи). 

Кроме того, в MetaMask необходимо включить поддержку Ledger Live. Для этого выполните следующие действия:

 1. Разверните правое верхнее меню и перейдите в раздел " Settings " (Настройки)
 2. Перейдите к пункту " Advanced" (Дополнительно)
 3. Включите функцию " Use Ledger Live" (Использовать Ledger Live ).

При включении этой функции MetaMask будет открывать Ledger Live при попытке подключения к Вашему Ledger. Подробнее об этом Вы можете прочитать в этой статье [MetaMask blog post](https://metamask.zendesk.com/hc/en-us/articles/360020394612-How-to-connect-a-Trezor-or-Ledger-Hardware-Wallet).

## Подписание транзакции с помощью Ledger

Если Вы успешно [импортировали свой аккаунт Ledger в MetaMask] (#importing-your-ledger-account-to-metamask), Вы готовы к подписанию транзакций на Moonbeam с помощью Вашего устройства Ledger. В этом руководстве мы покажем Вам, как отправить простую транзакцию в тестовой сети Moonbase Alpha, но оно применимо и к другим сетям экосистемы Moonbeam.

Во-первых, убедитесь, что Ваш аккаунт Ledger [пополнен токенами DEV] (/getting-started/moonbase/faucet/). Затем нажмите на кнопку " Send" (Отправить).

![MetaMask Ledger Account Funded](/images/ledger/ledger-images5.png)

Как и при обычной транзакции, укажите адрес получателя, введите количество токенов для отправки, просмотрите детали транзакции и подтвердите ее. Это запустит мастер подписи транзакции в Вашем устройстве Ledger. Здесь выполните следующие действия:

 1. Нажмите кнопку , чтобы перейти к следующему экрану. Ваше устройство Ledger предупредит Вас о необходимости просмотреть транзакцию.
 2. Проверьте количество отправляемых токенов. Обратите внимание, что токен соответствует сети, к которой подключен MetaMask. **В данном случае это токены DEV, а не ETH!** Если все готово, перейдите к следующему экрану.
 3. Проверьте адрес получателя и перейдите к следующему экрану
 4. Проверьте идентификатор сети. Эта информация подтверждает, к какой сети подключен MetaMask. Например, для Moonbase Alpha идентификатор сети 1287, Moonriver 1285 (еще не работает) и Moonbeam 1284 (еще не работает). Когда все готово, перейдите к следующему экрану
 5. Проверьте максимальные комиссии, применимые к данной транзакции. Это цена газа, умноженная на лимит газа, который Вы установили в MetaMask. Когда все готово, перейдите к следующему экрану
 6. Если Вы принимаете все детали транзакции, подтвердите ее. Это подпишет транзакцию и запустит MetaMask для ее отправки. В противном случае перейдите к следующему экрану
 7. Если Вы не согласны со всеми деталями транзакции, отклоните ее. Это приведет к отмене транзакции, и MetaMask пометит ее как неудачную
 
!!! примечание 
    На момент написания статьи имя токена всегда отображается как `ETH`. Обратите внимание, что обрабатываемый токен соответствует сети, к которой подключен MetaMask.

![MetaMask Ledger Transaction Wizard](/images/ledger/ledger-images6.png)

Сразу после того, как вы подтвердили транзакцию, MetaMask отправляет ее в сеть. Как только транзакция будет подтверждена, на главном экране MetaMask появится надпись " Send"(Отправлено).

![MetaMask Ledger Transaction Wizard](/images/ledger/ledger-images7.png)

Вот и все! Вы подписали транзакцию на Moonbase Alpha, используя свой аппаратный кошелек Ledger!

## Взаимодействие с контрактами с помощью Ledger

По умолчанию устройства Ledger не допускают наличия поля `data` в транзакции. Следовательно, пользователи не могут развертывать смарт-контракты или взаимодействовать с ними.

Однако если Вы хотите использовать аппаратный кошелек Ledger для транзакций, связанных со смарт-контрактами, вам необходимо изменить параметр конфигурации в приложении Ethereum. Для этого выполните следующие действия:

 1. Откройте приложение Ledger Ethereum
 2. Перейдите в раздел " Settings" (Настройки)
 3. Найдите страницу " Contract data"(Данные контракта). Внизу должно быть указано "NOT allowed" (НЕ разрешено)
 4. Выберите/проверить опцию, чтобы изменить ее значение на " Allowed"(Разрешено)

!!! примечание 
    Эта опция необходима для использования Вашего устройства Ledger для взаимодействия с контрактами на токены ERC20, которые могут находиться внутри экосистемы Moonbeam.

![MetaMask Ledger Allow Contracts Tx](/images/ledger/ledger-images8.png)