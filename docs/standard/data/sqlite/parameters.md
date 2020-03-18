---
title: Parametry
ms.date: 12/13/2019
description: Přečtěte si, jak používat parametry SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400454"
---
# <a name="parameters"></a>Parametry

Parametry se používají k ochraně proti útokům injektáže SQL. Místo zřetězení vstupu uživatele s příkazy SQL použijte parametry, abyste zajistili, že vstup je vždy považován pouze za literálovou hodnotu a nikdy nebyl proveden. V SQLite parametry jsou obvykle povoleny kdekoli literál je povoleno v příkazech SQL.

Parametry mohou být předponou buď `:`, `@`nebo `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Podrobnosti o tom, jak jsou hodnoty .NET mapovány na hodnoty SQLite, najdete v tématu [Datové typy.](types.md)

## <a name="truncation"></a>Zkrácení

Pomocí <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> vlastnosti můžete zkrátit hodnoty TEXT a BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Alternativní typy

Někdy můžete chtít použít alternativní typ SQLite. To provést nastavením vlastnosti. <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>

Lze použít následující mapování alternativního typu. Výchozí mapování naleznete v tématu [Datové typy](types.md).

| Hodnota          | SqliteTyp | Poznámky          |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| DateTime       | Skutečné       | Hodnota juliánského dne |
| DateTimeOffset | Skutečné       | Hodnota juliánského dne |
| Identifikátor GUID           | Objekt blob       |                  |
| TimeSpan       | Skutečné       | Ve dnech          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Výstupní parametry

SQLite nepodporuje výstupní parametry. Místo toho vrátí tezauje hodnoty ve výsledcích dotazu.

## <a name="see-also"></a>Viz také

* [Datové typy](types.md)
