---
title: Parametry
ms.date: 12/13/2019
description: Naučte se používat parametry SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400454"
---
# <a name="parameters"></a>Parametry

Parametry slouží k ochraně před útoky prostřednictvím injektáže SQL. Namísto zřetězení vstupu uživatele s příkazy SQL použijte parametry pro zajištění, že vstup je někdy považován za hodnotu literálu a nikdy se neprovede. V SQLite jsou parametry obvykle povoleny všude, kde je v příkazech jazyka SQL povolen literál.

Parametry mohou mít předponu buď `:`, `@`nebo. `$`

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Podrobnosti o tom, jak jsou hodnoty .NET mapovány na hodnoty SQLite, naleznete v tématu [datové typy](types.md) .

## <a name="truncation"></a>Zkrácení

Pomocí <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> vlastnosti Zkraťte text a hodnoty objektů BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Alternativní typy

V některých případech může být vhodné použít jiný typ SQLite. Provedete to nastavením <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> vlastnosti.

Lze použít následující alternativní mapování typů. Výchozí mapování najdete v tématu [datové typy](types.md).

| Hodnota          | SqliteType | Poznámky          |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| DateTime       | Skutečné       | Hodnota juliánského dne |
| DateTimeOffset | Skutečné       | Hodnota juliánského dne |
| Identifikátor GUID           | Objekt blob       |                  |
| TimeSpan       | Skutečné       | Ve dnech          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Výstupní parametry

SQLite nepodporuje výstupní parametry. Místo toho se vrátí hodnoty z výsledků dotazu.

## <a name="see-also"></a>Viz také

* [Typy dat](types.md)
