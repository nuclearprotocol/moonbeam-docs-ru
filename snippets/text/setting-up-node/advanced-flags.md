С выходом Moonbase Alpha v7 ноды также предоставляют доступ к некоторым нестандартным методам RPC, которые позволяют разработчикам проверять и отлаживать транзакции во время выполнения. В настоящее время доступны две функции:

 - Geth debug API: более подробно, метод `debug_traceTransaction`. Он попытается запустить транзакцию в том же виде, в котором она была выполнена. Подробнее об этом методе RPC можно прочитать по [этой ссылке](https://geth.ethereum.org/docs/rpc/ns-debug#debug_tracetransaction).
 - Модуль трассировки OpenEthereum: более подробно о методе `trace_filter`. Он возвращает трассировку, соответствующую определенному фильтру, предоставленному в качестве входных данных для вызова RPC. Подробнее об этом методе RPC можно прочитать по [этой ссылке](https://openethereum.github.io/JSONRPC-trace-module#trace_filter).

Перечисленные выше возможности могут быть активированы с помощью следующих флагов:

 - `--ethapi=debug`: enables the Geth debug API for the `debug_traceTransaction` RPC call
 - `--ethapi=trace`: enables the OpenEthereum trace module for the `trace_filter` RPC call

!!! примечание
    Функции отладки/отслеживания все еще активно разрабатываются. Поскольку эти запросы очень требовательны к процессору, рекомендуется запускать ноду с флагом `--execution=Native`. Это позволит использовать родную среду обработки, включенную в исполняемый файл ноды, вместо бинарного файла Wasm, хранящегося в цепи.

Вы можете совмещать оба флага при запуске ноды. 

По умолчанию максимальное количество записей трассировки, которое может вернуть один запрос `trace_filter`, равно `500`. Запрос, превышающий этот лимит, вернет ошибку. Вы можете установить другой максимальный предел с помощью следующего флага:

 - `--ethapi-trace-max-count <uint>`: устанавливает максимальное количество записей трассировки, возвращаемых нодой

Блоки, обрабатываемые запросами, временно хранятся в кэше в течение определенного времени (по умолчанию `300` секунд), после чего удаляются. Вы можете установить другое время удаления с помощью следующего флага:

 - `-ethapi-trace-cache-duration <uint>`: устанавливает продолжительность (в секундах), после которой кэш `trace_filter,` для данного блока, будет удален
