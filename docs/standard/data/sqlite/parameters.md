---
title: Parametry
ms.date: 12/13/2019
description: Naučte se používat parametry SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447186"
---
# <a name="parameters"></a>Parametry

Parametry slouží k ochraně před útoky prostřednictvím injektáže SQL. Namísto zřetězení vstupu uživatele s příkazy SQL použijte parametry pro zajištění, že vstup je někdy považován za hodnotu literálu a nikdy se neprovede. V SQLite jsou parametry obvykle povoleny všude, kde je v příkazech jazyka SQL povolen literál.

Parametry mohou být uvozeny buď `:`, `@`nebo `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Podrobnosti o tom, jak jsou hodnoty .NET mapovány na hodnoty SQLite, naleznete v tématu [datové typy](types.md) .

## <a name="truncation"></a>Zkrácení

Pro zkrácení textu a hodnot objektů BLOB použijte vlastnost <xref:Microsoft.Data.Sqlite.SqliteParameter.Size>.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Alternativní typy

V některých případech může být vhodné použít jiný typ SQLite. Provedete to nastavením vlastnosti <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.

Lze použít následující alternativní mapování typů. Výchozí mapování najdete v tématu [datové typy](types.md).

| Hodnota          | SqliteType | Poznámky          |
| -------------- | ---------- | ---------------- |
| Char           | Celé číslo    | UTF-16           |
| Datum a čas       | Skutečné       | Hodnota juliánského dne |
| DateTimeOffset | Skutečné       | Hodnota juliánského dne |
| identifikátor GUID           | Blob       |                  |
| TimeSpan       | Skutečné       | Ve dnech          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Výstupní parametry

SQLite nepodporuje výstupní parametry. Místo toho se vrátí hodnoty z výsledků dotazu.

## <a name="see-also"></a>Viz také:

* [Datové typy](types.md)
