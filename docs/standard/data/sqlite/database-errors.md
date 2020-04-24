---
title: Chyby databáze
ms.date: 12/13/2019
description: Popisuje způsob zpracování chyb databáze a jejich řešení v knihovně.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447270"
---
# <a name="database-errors"></a>Chyby databáze

<xref:Microsoft.Data.Sqlite.SqliteException>je vyvolána, když dojde k chybě SQLite. Zprávu poskytuje SQLite. Vlastnosti `SqliteErrorCode` a `SqliteExtendedErrorCode` obsahují [kód výsledku](https://www.sqlite.org/rescode.html) SQLite chyby.

Může dojít k chybám pokaždé, když Microsoft. data. sqlite komunikuje s nativní knihovnou SQLite. V následujícím seznamu jsou uvedeny běžné scénáře, kdy může dojít k chybám:

* Otevírá se připojení.
* Zahájení transakce.
* Spouští se příkaz.
* Volání <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.

Pečlivě zvažte, jak vaše aplikace tyto chyby zpracovává.

## <a name="locking-retries-and-timeouts"></a>Uzamykání, opakování a vypršení časových limitů

SQLite je agresivní, když přichází na uzamykání tabulek a databázových souborů. Pokud vaše aplikace povolí jakýkoli souběžný přístup k databázi, pravděpodobně dojde k chybám při zaneprázdnění a uzamčení. Můžete zmírnit mnoho chyb pomocí [sdílené mezipaměti](connection-strings.md#cache) a [protokolování proti zápisu](async.md).

Kdykoli dojde k chybě typu zaneprázdněn nebo uzamčená chyba Microsoft. data. sqlite, bude se automaticky opakovat, dokud nebude úspěšná nebo dokud nebude dosaženo časového limitu příkazu.

Časový limit příkazu můžete zvýšit nastavením <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>. Výchozí časový limit je 30 sekund. Hodnota `0` znamená, že nevypršel časový limit.

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

Microsoft. data. sqlite někdy potřebuje vytvořit objekt implicitního příkazu. Například během BeginTransaction. Chcete-li nastavit časový limit pro tyto příkazy <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>, použijte.

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a>Viz také

* [Kódy chyb SQLite](https://www.sqlite.org/rescode.html)
* [Uzamykání souborů v SQLite](https://www.sqlite.org/lockingv3.html)
* [Režim sdílené mezipaměti](https://www.sqlite.org/sharedcache.html)
* [Protokolování před zápisem](https://www.sqlite.org/wal.html)
