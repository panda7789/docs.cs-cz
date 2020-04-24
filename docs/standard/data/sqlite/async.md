---
title: Asynchronní omezení
ms.date: 12/13/2019
description: Vysvětluje omezení asynchronních rozhraní API a některé alternativy, které lze použít místo toho.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447081"
---
# <a name="async-limitations"></a><span data-ttu-id="1475f-103">Asynchronní omezení</span><span class="sxs-lookup"><span data-stu-id="1475f-103">Async limitations</span></span>

<span data-ttu-id="1475f-104">SQLite nepodporuje asynchronní vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="1475f-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="1475f-105">Asynchronní metody ADO.NET se spustí synchronně v Microsoft. data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="1475f-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="1475f-106">Vyhněte se volání.</span><span class="sxs-lookup"><span data-stu-id="1475f-106">Avoid calling them.</span></span>

<span data-ttu-id="1475f-107">Místo toho použijte [protokolování proti zápisu](https://www.sqlite.org/wal.html) za účelem zvýšení výkonu a souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="1475f-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="1475f-108">Protokolování proti zápisu je ve výchozím nastavení povolené v databázích vytvořených pomocí [Entity Framework Core](/ef/core/).</span><span class="sxs-lookup"><span data-stu-id="1475f-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
