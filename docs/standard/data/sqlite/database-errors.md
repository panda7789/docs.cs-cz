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
# <a name="database-errors"></a><span data-ttu-id="7a4cb-103">Chyby databáze</span><span class="sxs-lookup"><span data-stu-id="7a4cb-103">Database errors</span></span>

<span data-ttu-id="7a4cb-104"><xref:Microsoft.Data.Sqlite.SqliteException> je vyvolána, když dojde k chybě SQLite.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="7a4cb-105">Zprávu poskytuje SQLite.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-105">The message is provided by SQLite.</span></span> <span data-ttu-id="7a4cb-106">Vlastnosti `SqliteErrorCode` a `SqliteExtendedErrorCode` obsahují [kód výsledku](https://www.sqlite.org/rescode.html) SQLite chyby.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="7a4cb-107">Může dojít k chybám pokaždé, když Microsoft. data. sqlite komunikuje s nativní knihovnou SQLite.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="7a4cb-108">V následujícím seznamu jsou uvedeny běžné scénáře, kdy může dojít k chybám:</span><span class="sxs-lookup"><span data-stu-id="7a4cb-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="7a4cb-109">Otevírá se připojení.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-109">Opening a connection.</span></span>
* <span data-ttu-id="7a4cb-110">Zahájení transakce.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-110">Beginning a transaction.</span></span>
* <span data-ttu-id="7a4cb-111">Spouští se příkaz.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-111">Executing a command.</span></span>
* <span data-ttu-id="7a4cb-112">Volání <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="7a4cb-113">Pečlivě zvažte, jak vaše aplikace tyto chyby zpracovává.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="7a4cb-114">Uzamykání, opakování a vypršení časových limitů</span><span class="sxs-lookup"><span data-stu-id="7a4cb-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="7a4cb-115">SQLite je agresivní, když přichází na uzamykání tabulek a databázových souborů.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="7a4cb-116">Pokud vaše aplikace povolí jakýkoli souběžný přístup k databázi, pravděpodobně dojde k chybám při zaneprázdnění a uzamčení.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="7a4cb-117">Můžete zmírnit mnoho chyb pomocí [sdílené mezipaměti](connection-strings.md#cache) a [protokolování proti zápisu](async.md).</span><span class="sxs-lookup"><span data-stu-id="7a4cb-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="7a4cb-118">Kdykoli dojde k chybě typu zaneprázdněn nebo uzamčená chyba Microsoft. data. sqlite, bude se automaticky opakovat, dokud nebude úspěšná nebo dokud nebude dosaženo časového limitu příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="7a4cb-119">Časový limit příkazu můžete zvýšit nastavením <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="7a4cb-120">Výchozí časový limit je 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="7a4cb-121">Hodnota `0` znamená žádný časový limit.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="7a4cb-122">Microsoft. data. sqlite někdy potřebuje vytvořit objekt implicitního příkazu.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="7a4cb-123">Například během BeginTransaction.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="7a4cb-124">Chcete-li nastavit časový limit pro tyto příkazy, použijte <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a4cb-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="7a4cb-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a4cb-125">See also</span></span>

* [<span data-ttu-id="7a4cb-126">Kódy chyb SQLite</span><span class="sxs-lookup"><span data-stu-id="7a4cb-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="7a4cb-127">Uzamykání souborů v SQLite</span><span class="sxs-lookup"><span data-stu-id="7a4cb-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="7a4cb-128">Režim sdílené mezipaměti</span><span class="sxs-lookup"><span data-stu-id="7a4cb-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="7a4cb-129">Protokolování před zápisem</span><span class="sxs-lookup"><span data-stu-id="7a4cb-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
