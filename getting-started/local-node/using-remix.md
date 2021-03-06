---
title: Использование Remix
description: В этом руководстве Вы узнаете как использовать один из самых популярных инструментов разработчика Ethereum, Remix IDE, для взаимодействия с локальной нодой Moonbeam.
---

# Взаимодействие с Moonbeam с помощью Remix

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/RT_f1-ga_n4' frameborder='0' allowfullscreen></iframe></div>
<style>.caption { font-family: Open Sans, sans-serif; font-size: 0.9em; color: rgba(170, 170, 170, 1); font-style: italic; letter-spacing: 0px; position: relative;}</style><div class='caption'>
Вы можете найти весь необходимый код касающийся этого руководства в <a href="{{ config.site_url }}resources/code-snippets/">code snippets page</a></div>

## Введение {: #introduction } 

Remix — одна из часто используемых сред разработки для смарт-контрактов на Ethereum. Учитывая особенности совместимости Moonbeam с Ethereum, Remix можно использовать напрямую с нодой Moonbeam.

В этом руководстве рассматривается процесс создания и размещения смарт-контракта на основе Solidity на ноде Moonbeam с использованием [Remix IDE](https://remix.ethereum.org/). 

!!! примечание 
    Это руководство было создано с использованием тега {{ networks.development.build_tag}}, который основан на {{ networks.moonbase.version }} версии [Moonbase Alpha](https://github.com/PureStake/moonbeam/releases/tag/{{ networks.moonbase.version }}). Платформа Moonbeam и компоненты [Frontier](https://github.com/paritytech/frontier), которые используются для совместимости Ethereum на основе Substrate, все еще находятся в стадии активной разработки.

В этом руководстве предполагается, что у Вас уже есть нода Moonbeam, работающая в режиме `--dev` и что у Вас установлен и настроен [MetaMask](https://metamask.io/) для использования с этой нодой. Вы можете найти инструкции по запуску ноды Moonbeam [здесь](/getting-started/local-node/setting-up-a-node/) и инструкции по подключению MetaMask [здесь](/getting-started/local-node/using-metamask/).

## Проверка предварительных условий {: #checking-prerequisites } 

Если Вы следовали приведенным ранее пунктам,то у Вас уже должна быть нода Moonbeam, производящая блоки, которые выглядят следующим образом:

![Локальная нода Moonbeam, производящая блоки](/images/remix/using-remix-1.png)

И у Вас должен быть установлен MetaMask, подключеный к Вашей ноде Moonbeam, по крайней мере, с одной учетной записью, на балансе которой есть средства. Это должно выглядеть примерно так (развернутый вид):

![Установленный MetaMask с балансом](/images/remix/using-remix-2.png)

!!! примечание 
    Убедитесь, что Вы подключены к своей ноде Moonbeam, а не к другой сети!

## Начало работы с Remix {: #getting-started-with-remix } 

Теперь давайте запустим Remix, чтобы использовать продвинутые функции Moonbeam.

Запустите Remix, перейдя на [https://remix.ethereum.org/](https://remix.ethereum.org/). На главном экране, в разделе Environments, выберите Solidity, чтобы настроить Remix для разработки Solidity, а затем перейдите к вкладке File Explorer:

![File explorer](/images/remix/using-remix-3.png)

Мы создадим новый файл для нашего смарт-контракта Solidity. Нажмите кнопку + под File Explorer и введите имя «MyToken.sol» во всплывающем окне:

![Создание нового файла для вашего смарт-контракта Solidity](/images/remix/using-remix-4.png)

Затем давайте вставим следующий смарт-контракт в открывшуюся вкладку редактора:

```solidity
--8<-- 'code/remix-local/contract.md'
```

Это простой контракт ERC-20, основанный на текущем шаблоне Open Zeppelin ERC-20. Этот контракт создает MyToken с символом MYTOK и создает первичное предложение токенов для эмитента контракта.

После того, как Вы вставили контракт в редактор, он должен выглядеть так:

![Вставьте ваш контракт в редактор](/images/remix/using-remix-5.png)

Теперь перейдите к боковой панели компиляции и нажмите кнопку «Compile MyToken.sol»:

![Compile MyToken.sol](/images/remix/using-remix-6.png)

Вы увидите, как Remix загрузит все Open Zeppelin и скомпилирует контракт.

## Размещение контракта на Moonbeam с помощью Remix {: #deploying-a-contract-to-moonbeam-using-remix } 

Теперь мы можем разместить контракт, перейдя к опции Deployment в боковой панели. Вам необходимо изменить верхнее раскрывающееся меню "Environment" с "JavaScript VM" на "Injected Web3". Remix предлагает использовать MetaMask, который будет ссылаться на Вашу ноду Moonbeam. 

Как только Вы выберете это, Вам будет предложено разрешить Remix подключиться к Вашей учетной записи MetaMask.

![Изменить](/images/remix/using-remix-7.png)

Нажмите "Next" в Metamask, чтобы позволить Remix получить доступ к выбранной учетной записи.

Вернувшись к Remix, Вы должны увидеть, что учетная запись, которую Вы хотите использовать для размещения, теперь управляется MetaMask. Рядом с кнопкой Deploy укажите начальный баланс в 8 миллионов токенов. Поскольку в этом контракте по умолчанию используется 18 знаков после запятой, значение для ввода в поле составляет `8000000000000000000000000`.

После того как Вы ввели это значение, выберите "Deploy".

![Внести средства на баланс и разместить контракт](/images/remix/using-remix-8.png)

MetaMask предложит Вам подтвердить транзакцию размещения контракта.

![Подтвердить транзакцию](/images/remix/using-remix-9.png)

!!! примечание 
    Если у Вас возникли проблемы с размещением какого-либо контракта, Вы можете попробовать вручную увеличить лимит газа. Вы можете сделать это в разделе Settings -> Advanced -> Advanced Gas Controls = ON.

После нажатия кнопки подтверждения и завершения размещения Вы увидите транзакцию, указанную в MetaMask. Контракт появится в разделе Deployed Contracts in Remix.

![Подтвержденная транзакция](/images/remix/using-remix-10.png)

После размещения контракта Вы можете взаимодействовать с ним с помощью Remix.

Разверните контракт в разделе "Deployed Contracts". Нажмите на имя,символ и totalSupply, Вам должны вернуться "MyToken", "MYTOK" и "8000000000000000000000000" соответственно. Если Вы скопируете адрес, с которого Вы разместили контракт, и вставите его в поле balanceOf, Вы должны увидеть, что баланс ERC20 полностью принадлежит этому пользователю. Скопируйте адрес контракта, нажав кнопку рядом с названием и адресом контракта.

![Взаимодействие с контрактом с помощью Remix](/images/remix/using-remix-11.png)

## Взаимодействие с ERC-20 на основе Moonbeam c помощью MetaMask {: #interacting-with-a-moonbeam-based-erc-20-from-metamask } 

Теперь откройте MetaMask, чтобы добавить недавно размещенные токены ERC-20. Перед этим убедитесь, что Вы скопировали адрес контракта из Remix. Вернувшись в MetaMask, нажмите "Add Token", как показано ниже. Убедитесь, что Вы находитесь в учетной записи, в которой был размещен контракт токена.

![Add a token](/images/remix/using-remix-12.png)

Вставьте скопированный адрес контракта в поле "Custom Token". Поля "Token Symbol" и "Decimals of Precision" должны заполниться автоматически.

![Вставьте скопированный адрес контракта](/images/remix/using-remix-13.png)

После нажатия на "Next" Вам нужно будет подтвердить, что Вы хотите добавить эти токены в свою учетную запись MetaMask. Нажмите "Add Token" и Вы должны увидеть баланс в 8 миллионов MyTokens в MetaMask:

![Добавьте токены в вашу учетную запись Metamask](/images/remix/using-remix-14.png)

Теперь мы можем отправить некоторые из этих токенов ERC-20 в другую учетную запись, которую мы настроили в MetaMask. Нажмите "Send", чтобы начать передачу 500 MyTokens и выберите учетную запись получателя.

После нажатия "Next" Вас попросят подтвердить отправку (аналогично тому, как показано на рисунке ниже).

![Подтверждение отправки токенов](/images/remix/using-remix-15.png)

Нажмите "Подтвердить" и после завершения транзакции Вы увидите уменьшение баланса учетной записи MyToken со счета отправителя в MetaMask:

![Подтвердить уменьшение баланса отпарвителя](/images/remix/using-remix-16.png)

Если учетная запись, на которую Вы отправили токены, принадлжеит вам, Вы можете добавить актив токена, чтобы убедиться, что перевод получен.


