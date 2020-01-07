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
# <a name="async-limitations"></a>Asynchronní omezení

SQLite nepodporuje asynchronní vstupně-výstupní operace. Asynchronní metody ADO.NET se spustí synchronně v Microsoft. data. sqlite. Vyhněte se volání.

Místo toho použijte [protokolování proti zápisu](https://www.sqlite.org/wal.html) za účelem zvýšení výkonu a souběžnosti.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> Protokolování proti zápisu je ve výchozím nastavení povolené v databázích vytvořených pomocí [Entity Framework Core](/ef/core/).
