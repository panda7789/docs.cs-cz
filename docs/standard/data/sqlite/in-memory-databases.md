---
title: Databáze v paměti
ms.date: 12/13/2019
description: Naučte se používat databáze SQLite v paměti.
ms.openlocfilehash: 16a9b6536fbfede203c24b757e96e28e7c49dc05
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777417"
---
# <a name="in-memory-databases"></a><span data-ttu-id="7e44e-103">Databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="7e44e-103">In-memory databases</span></span>

<span data-ttu-id="7e44e-104">Databáze v paměti v paměti jsou databáze uložené výhradně v paměti, nikoli na disku.</span><span class="sxs-lookup"><span data-stu-id="7e44e-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="7e44e-105">K vytvoření databáze v paměti použijte `:memory:` speciální název souboru zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="7e44e-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="7e44e-106">Po zavření připojení se databáze odstraní.</span><span class="sxs-lookup"><span data-stu-id="7e44e-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="7e44e-107">Při použití `:memory:`vytvoří každé připojení svou vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="7e44e-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="7e44e-108">Sdílené databáze v paměti</span><span class="sxs-lookup"><span data-stu-id="7e44e-108">Shareable in-memory databases</span></span>

<span data-ttu-id="7e44e-109">Databáze v paměti lze sdílet mezi více připojeními pomocí `Mode=Memory` a `Cache=Shared` v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="7e44e-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="7e44e-110">Klíčové slovo `Data Source` slouží k poskytnutí názvu databáze v paměti.</span><span class="sxs-lookup"><span data-stu-id="7e44e-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="7e44e-111">Připojovací řetězce používající stejný název budou přistupovat ke stejné databázi v paměti.</span><span class="sxs-lookup"><span data-stu-id="7e44e-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="7e44e-112">Databáze zůstane v otevřeném umístění, dokud není otevřeno alespoň jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="7e44e-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="7e44e-113">[Ukázka](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) , která demonstruje tuto hodnotu, je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7e44e-113">A [sample](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
