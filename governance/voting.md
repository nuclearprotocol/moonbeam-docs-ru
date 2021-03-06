---
title: Голосование за предложение
description: Как проголосовать за предложение, чтобы оно было принято или отклонено в Moonbeam с помощью функций управления
---

# Предложения

![Governance Moonbeam Banner](/images/governance/governance-voting-banner.png)

## Введение {: #introduction } 

Как только предложение достигнет публичного референдума, держатели токенов могут проголосовать за него, используя свои собственные токены. Два фактора определяли вес голоса: количество заблокированных токенов и продолжительность блокировки (называемая осуждением). Это сделано для того, чтобы обеспечить экономическую поддержку результата, чтобы предотвратить продажу голосов. Следовательно, чем дольше Вы хотите заблокировать свои токены, тем сильнее будет ваш голос. У Вас также есть возможность вообще не блокировать токены, но вес голосования резко снижается.

Референдумы — это простые, инклюзивные схемы голосования на основе стекинга. С каждым референдумом связано предложение, в котором предлагается какое-либо действие. Они имеют фиксированную продолжительность, по истечении которой голоса подсчитываются, и действие вступает в силу, если голосование одобрено.

В Moonbeam пользователи смогут создавать, поддерживать и голосовать за предложения, используя свой адрес H160 и закрытый ключ, то есть свою обычную учетную запись Ethereum!

С выпуском  [Moonbase Alpha v6](https://github.com/PureStake/moonbeam/releases/tag/v0.6.0), пользователи сети теперь могут вносить предложения на публичные референдумы и голосовать за них. В этом руководстве рассказывается, как проголосовать за предложение, вынесенное на общественный референдум. Вы можете найти руководство по подаче предложения  [здесь](/governance/proposals/).

Дополнительную информацию, касающуюся [Управления](https://wiki.polkadot.network/docs/learn-governance) и [Участия в Демократии](https://wiki.polkadot.network/docs/maintain-guides-democracy) можно найти на страницах Wiki Polkadot.

!!! примечание 
    Это руководство было составлено с настроенной версией Moonbeam с короткими периодами запуска / введения в действие только для демонстрационных целей.

## Определения {: #definitions } 

Некоторые из ключевых параметров этого руководства следующие:

 - **Период голосования** — время, в течение которого держатели токенов должны проголосовать за референдум (продолжительность референдума)
 - **Голосование** — инструмент, используемый держателями токенов для одобрения или отклонения предложения. Вес голоса определяется двумя факторами: количеством заблокированных токенов и продолжительностью блокировки (называемой осуждением)
 - **Явка** — общее количество токенов для голосования
 - **Электорат** — общее количество токенов, выпущенных в сети
 - **Максимальное количество голосов** — максимальное количество голосов на учетную запись
 - **Период принятия** — время между утверждением предложения и его введением в действие (принятие закона). Это также минимальный период блокировки при голосовании
 - **Период блокировки** — время (после принятия предложения), в течение которого токены победивших избирателей блокируются. Пользователи по-прежнему могут использовать эти токены для ставок или голосования
 - **Делегирование** — акт передачи вашего права голоса на другую учетную запись до определенного срока

В настоящее время для Moonbase Alpha:

|        Переменная         |     |                                 Значение                                                                           |
| :---------------------: | :-: | :-------------------------------------------------------------------------------------------------------------------: |
|       Период Голосованя       |     |  {{ networks.moonbase.democracy.vote_period.blocks}} blocks ({{ networks.moonbase.democracy.vote_period.days}} days)  |
|      Период Принятия        |     | {{ networks.moonbase.democracy.enact_period.blocks}} blocks ({{ networks.moonbase.democracy.enact_period.days}} days) |
| Максимальное колличество голосов |     |                                      {{ networks.moonbase.democracy.max_votes}}                                       |

## Дорожная карта предложения {: #roadmap-of-a-proposal } 

--8<-- 'text/governance/roadmap.md'

## Голосование на референдуме {: #voting-on-a-referendum } 

В этом разделе рассматривается процесс голосования на референдуме. В руководстве предполагается, что он уже выполняется, в данном случае созданный в  [этом руководстве](/governance/proposals/).

Чтобы проголосовать за предложение в сети, вам необходимо использовать интерфейс PolkadotJS Apps. Для этого вам необходимо сначала импортировать учетную запись в стиле Ethereum (адрес H160), что Вы можете сделать, следуя [этому руководству](/integrations/wallets/polkadotjs/#creating-or-importing-an-h160-account). В этом примере три учетных записи были импортированы и названы супер оригинальными именами: Алиса,Боб и Чарли.

![Accounts in PolkadotJS](/images/governance/governance-proposal-1.png)

Предложение, по которому проводится голосование, установит баланс Боба на `1500` через управление!

### Как проголосовать {: #how-to-vote } 

Голосовать на Moonbeam довольно просто. Все, что связано с управлением, находится на вкладке «Демократия», где (на изображении) Вы можете отметить цифру 1, указывающую на то, что еще не решен один вопрос о демократии (предложения или референдумы). Оказавшись там, Вы можете просмотреть подробную информацию о референдуме, за который хотите проголосовать, щелкнув стрелку рядом с описанием. Число рядом с действием и его описанием называется индексом референдума (в данном случае это 0). Когда будете готовы, нажмите кнопку «Голосовать».

![Vote Button](/images/governance/governance-vote-1.png)

Здесь вам необходимо предоставить следующую информацию:

 1. Выберите учетную запись, за которую Вы хотите проголосовать
 2. ведите количество токенов, которыми Вы хотите проголосовать. Они будут заблокированы на время, указанное на следующем шаге
 3. Установите убежденность голосования, которая определяет его вес (`vote_weight = tokens * conviction_multiplier`). Множитель убеждения связан с количеством периодов вступления в силу, на которые токены будут заблокированы. Следовательно, чем дольше Вы хотите заблокировать свои токены, тем сильнее будет ваш голос. У вас также есть возможность вообще не блокировать токены, но вес голоса резко снижается (токены по-прежнему заблокированы во время референдума)

   | Период Блокировки |     | Множитель Осуждения |
   | :----------: | :-: | :-------------------: |
   |      0       |     |          0.1          |
   |      1       |     |           1           |
   |      2       |     |           2           |
   |      4       |     |           3           |
   |      8       |     |           4           |
   |      16      |     |           5           |
   |      32      |     |           6           |

 4. Нажмите «Голосовать за», чтобы одобрить предложение, или «Голосуйте против», чтобы отклонить предложение, а затем подпишите транзакцию

![Vote Submission](/images/governance/governance-vote-2.png)

!!! примечание 
    Периоды блокировки, показанные на предыдущем изображении, не следует воспринимать как справочные. Это руководство было составлено с настроенной версией Moonbeam с короткими периодами запуска / введения в действие только для демонстрационных целей.

В этом случае Alice решила «Проголосовать за предложение» с убежденностью в 6 раз. С другой стороны, Charley решил «проголосовать против» по предложению, но решил не блокировать никакие токены (его токены блокируются только на время референдума), поэтому его осуждение было 0,1x. При таком распределении голосов частичные результаты можно увидеть на главной вкладке «Демократия».

![Vote Information](/images/governance/governance-vote-3.png)

Благодаря голосования можно сделать несколько важных выводов:

 - Взвешенный голос Алисы составляет 10800 единиц. То есть ее 1800 заблокированных токенов  умножили ее убежденность в 6 раз
 - Взвешенный голос Чарли составляет 80 единиц. То есть его 800 токенов без периода блокировки (только во время референдума) делали его коэффициент убежденности x0.1
 - На экране отображаются как оставшийся период голосования, так и время до принятия предложения (если оно принято).
 - Общая явка (в процентах) составляет всего 0,21%. Это рассчитывается как общее количество токенов для голосования (2600), разделенное на общее количество токенов в сети (в данном случае 1,22 млн)
 - Несмотря на то, что явка довольно низкая, предложение предварительно одобрено из-за одобрения подавляющим большинством. Более подробную информацию можно найти в [этом разделе](/governance/voting/#positive-turnout-bias)
 - Важно записать индекс референдума, так как это необходимо для разблокировки токенов позже, когда истечет период блокировки. В настоящее время нет возможности получить индекс референдума после того, как он был принят

По истечении периода голосования предложение будет отображаться на вкладке «Отправка», если оно будет одобрено. Здесь Вы также можете увидеть время, оставшееся до принятия предложения.

![Proposal Enactment](/images/governance/governance-vote-4.png)

Помните, что в этом примере функция `setBalance` использовалась для установки баланса Боба на 1500 токенов. По истечении срока вступления в силу Вы можете вернуться на вкладку «Учетные записи», чтобы убедиться, что предложение было внесено в закон.

![Proposal Result](/images/governance/governance-vote-5.png)

### Делегирование голосования {: #delegate-voting } 

Держатели токенов могут делегировать свой голос другой учетной записи, мнению которого они доверяют. Делегируемая учетная запись не требует каких-либо действий. Когда они голосуют, вес голоса (то есть количество токенов, умноженное на множитель убежденности, выбранный делегатом) добавляется к его голосу.

Чтобы делегировать свой голос, сначала перейдите в менюe "Extrinsics" на вкладке "Developers".

![Extrinsics Menu](/images/governance/governance-vote-6.png)

Здесь вам необходимо предоставить следующую информацию:

 1. Выберите учетную запись, из которой Вы хотите делегировать свой голос
 2. Выберите pallet с которым хотите взаимодействовать. В данном случае это `democracy`
 3. Выберите внешний метод, который будет использоваться для транзакции. Это определит поля, которые необходимо заполнить в следующих шагах. В этом случае это `delegate`
 4. Выберите учетную запись, на которую Вы хотите передать свой голос
 5. Установите убежденность голосования, которая определяет его весомость (`vote_weight = tokens * conviction_multiplier`). Множитель убеждения связан с количеством периодов вступления в силу, на которые токены будут заблокированы. Следовательно, чем дольше Вы хотите заблокировать свои токены, тем сильнее будет ваш голос. У вас также есть возможность вообще не блокировать токены, но вес голосования резко снижается
 6. Установите количество токенов, которое Вы хотите делегировать в учетную запись, предоставленную ранее
 7. Нажмите кнопку "Submit Transaction" и подпишите транзакцию

![Extrinsics Transaction for Delegation](/images/governance/governance-vote-7.png)

В этом примере Алиса делегировала Чарли общий вес 1000 (1000 токенов с коэффициентом убежденности  x1).

!!! примечание 
    Другой способ делегировать голоса - на вкладке «Учетные записи». Нажмите на три точки учетной записи, с которой Вы хотите делегировать свой голос, и введите информацию, как и раньше.

После того, как учетная запись, на которую Вы делегировали свой голос, была передана голосам, общий вес делегированного голоса будет распределен для варианта, выбранного учетной записью. В этом примере Чарли решил проголосовать за предложение, вынесенное на публичный референдум. Он проголосовал общим весом 800 (800 токенов с коэффициентом убедительности x1). Но поскольку Алиса делегировала ему вес в 1000 голосов, «Да» всего 1800 единиц.

![Total Votes with Delegation](/images/governance/governance-vote-8.png)

Чтобы удалить делегирование, повторите процесс, описанный ранее, но выберите внешнюю функцию без делегирования   `undelegate`  на шаге 3.

Из делегирования голосования можно сделать несколько важных выводов:

 - Если владелец токена удалит делегирование голосов во время публичного референдума, на котором использовались делегированные голоса, они будут удалены из подсчета
 - Держатель токена, который делегировал голоса, по-прежнему имеет экономическую поддержку. Это означает, что если вариант, выбранный делегатом, выиграет, делегированные токены будут заблокированы на количество периодов блокировки
 - Токены, делегированные для голосования, больше не входят в свободный баланс держателя токенов. Чтобы узнать больше о типах балансов, Вы можете посетить этот [сайт](https://wiki.polkadot.network/docs/build-protocol-info#free-vs-reserved-vs-locked-vs-vesting-balance)
 - Держатель токенов, который делегировал их, не может участвовать в публичном референдуме. Во-первых, владелец токена должен отменить делегирование своего голоса.
 - Владелец токенов, который их делегировал, должен вручную разблокировать свои заблокированные токены после истечения периода блокировки. Для этого необходимо знать индекс референдума

### Разблокировка заблокированных токенов {: #unlocking-locked-tokens } 

Когда держатели токенов голосуют, используемые токены блокируются и не могут быть переданы. Вы можете проверить, есть ли у вас заблокированные токены, на вкладке «Учетные записи», развернув данные учетной записи адреса для запроса. Там Вы увидите разные типы балансов (подробнее о каждом из них Вы можете [здесь](https://wiki.polkadot.network/docs/build-protocol-info#free-vs-reserved-vs-locked-vs-vesting-balance)). Если Вы наведете курсор на значок рядом с надписью «демократия», отобразится информационная панель, сообщающая вам текущий статус вашего замка. Различные состояния блокировки включают:
 - Заблокирован из-за продолжающегося референдума, что означает, что Вы использовали свои токенов и должны дождаться завершения референдума, даже если Вы проголосовали с фактором убеждения без блокировки
 - Заблокировано из-за выбранного множителя убежденности, отображается количество блоков и оставшееся время
 - Срок действия блокировки истек, что означает, что теперь Вы можете вернуть свои токены

![Account Lock Status](/images/governance/governance-vote-9.png)

По истечении срока блокировки Вы можете запросить свои токены обратно. Для этого перейдите в меню "Extrinsics" на вкладке "Developers" .

![Extrinsics Menu](/images/governance/governance-vote-10.png)

Здесь необходимо отправить два разных внешних объекта. Во-первых, вам необходимо предоставить следующую информацию:

 1. Выберите учетную запись, из которой Вы хотите восстановить свои токены
 2. Выберите набор модулей, с которым хотите взаимодействовать. В данном случае это набор `democracy`
 3. Выберите внешний метод, который будет использоваться для транзакции. Это определит поля, которые необходимо заполнить в следующих шагах. В данном случае это `removeVote`. Этот шаг необходим для разблокировки токенов. Этот внешний вид также может быть использован для снятия вашего голоса с референдума.
 4. Введите индекс референдума. Это число, которое появилось в левой части вкладки "Democracy". В данном случае это 0
 5. Нажмите кнопку "Submit Transaction" и подпишите транзакцию

![Remove Vote Extrinsics](/images/governance/governance-vote-11.png)

Для следующего внешнего запроса вам необходимо предоставить следующую информацию:

 1. Выберите учетную запись, из которой Вы хотите восстановить свои токены
 2. Выберите набор модулей, с которым хотите взаимодействовать. В данном случае это набор `democracy` 
 3. Выберите внешний метод, который будет использоваться для транзакции. Это определит поля, которые необходимо заполнить в следующих шагах. В данном случае это `unlock` 
 4. Введите целевую учетную запись, которая получит разблокированные токены. В этом случае токены будут возвращены Алисе.
 5. Нажмите кнопку "Submit Transaction" и подпишите транзакцию

![Unlock Extrinsics](/images/governance/governance-vote-12.png)

После завершения транзакции заблокированные токены должны быть разблокированы. Чтобы еще раз проверить, Вы можете вернуться на вкладку "Accounts"и увидеть, что для этого примера Алиса имеет полный баланс как "transferable."

![Check Balance](/images/governance/governance-vote-13.png)

## Положительный сдвиг явки {: #positive-turnout-bias } 

В публичных референдумах используется показатель смещения положительной явки, то есть формула одобрения большинством голосов. Уравнение следующее:

![Positive Turnout Bias](/images/governance/governance-vote-bias.png)

Где:

 - **Одобрить** — количество голосов «За» (с учетом множителя убеждения)
 - **Против** — количество голосов "против" (с учетом множителя убеждения)
 - **Явка** — общее количество токенов для голосования (без учета множителя убеждения)
 - **Электорат** — бщее количество токенов, выпущенных в сети

В предыдущем примере это были следующие числа:

|  Переменная  |     |         Значение         |
| :--------: | :-: | :-------------------: |
|  Одобрить   |     |   10800 (1800 x 6)    |
|  Против   |     |    80 (800 x 0.1)     |
|  Явка   |     |   2600 (1800 + 800)   |
| Єлеторат |     |         1.22M         |
| **Результат** |     | 1.5 < 9.8 (Да Победили!) |

Короче говоря, для одобрения предложения при низкой явке требуется подавляющее большинство голосов «за», но по мере увеличения явки оно становится  большинством.

