---
title: Databáze v paměti
ms.date: 12/13/2019
description: Naučte se používat databáze SQLite v paměti.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391205"
---
# <a name="in-memory-databases"></a><span data-ttu-id="2608e-103">Databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="2608e-103">In-memory databases</span></span>

<span data-ttu-id="2608e-104">SQLite v paměti databáze jsou databáze uložené výhradně v paměti, nikoli na disku.</span><span class="sxs-lookup"><span data-stu-id="2608e-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="2608e-105">Použijte název souboru `:memory:` zdroje dat speciální zdroj dat k vytvoření databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="2608e-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="2608e-106">Po zavření připojení je databáze odstraněna.</span><span class="sxs-lookup"><span data-stu-id="2608e-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="2608e-107">Při `:memory:`použití vytvoří každé připojení vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="2608e-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="2608e-108">Sdílet databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="2608e-108">Shareable in-memory databases</span></span>

<span data-ttu-id="2608e-109">Databáze v paměti lze sdílet mezi více `Mode=Memory` `Cache=Shared` připojení pomocí a v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="2608e-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="2608e-110">Klíčové `Data Source` slovo se používá k tomu, aby databáze v paměti pojmenovala.</span><span class="sxs-lookup"><span data-stu-id="2608e-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="2608e-111">Připojovací řetězce se stejným názvem budou mít přístup ke stejné databázi v paměti.</span><span class="sxs-lookup"><span data-stu-id="2608e-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="2608e-112">Databáze zůstane zachována tak dlouho, dokud alespoň jedno připojení k ní zůstane otevřené.</span><span class="sxs-lookup"><span data-stu-id="2608e-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="2608e-113">[Ukázka](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) prokazující to je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2608e-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
