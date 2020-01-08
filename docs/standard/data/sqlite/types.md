---
title: Typy dat
ms.date: 12/13/2019
description: Popisuje podporované typy dat a některá omezení, která jsou kolem nich.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447179"
---
# <a name="data-types"></a>Typy dat

SQLite má pouze čtyři primitivní datové typy: INTEGER, REAL, TEXT a BLOB. Rozhraní API, která vracejí hodnoty databáze jako `object`, se vždy vrátí k jednomu z těchto čtyř typů. Další typy rozhraní .NET jsou podporovány společností Microsoft. data. sqlite, ale hodnoty jsou nakonec přiřazeny mezi tyto typy a jeden ze čtyř primitivních typů.

| .NET           | SQLite  | Poznámky                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` Nebo `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| Datum a čas       | TEXT    | RRRR-MM-DD HH: mm: ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | RRRR-MM-DD HH: mm: ss. FFFFFFFzzz                                |
| Desetinné číslo        | TEXT    | Formát `0.0###########################`. REAL by byl ztrátou. |
| Double         | REÁLNÉ    |                                                               |
| identifikátor GUID           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Jednoduché         | REÁLNÉ    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: ss. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Přetečení velkých hodnot                                         |

## <a name="alternative-types"></a>Alternativní typy

Některé typy rozhraní .NET lze číst z alternativních typů SQLite. Parametry lze také nakonfigurovat pro použití těchto alternativních typů. Další informace najdete v tématu [parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Poznámky          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| Datum a čas       | REÁLNÉ    | Hodnota juliánského dne |
| DateTimeOffset | REÁLNÉ    | Hodnota juliánského dne |
| identifikátor GUID           | BLOB    |                  |
| TimeSpan       | REÁLNÉ    | Ve dnech          |

Například následující dotaz přečte hodnotu TimeSpan z REÁLNÉho sloupce v sadě výsledků dotazu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy sloupců

SQLite používá dynamický typ systému, kde je typ hodnoty spojen s vlastní hodnotou a nikoli sloupcem, kde je uložen. Můžete použít libovolný název typu sloupce, který chcete. Microsoft. data. sqlite nepoužije pro tyto názvy žádnou další sémantiku.

Název typu sloupce má vliv na [spřažení typů](https://www.sqlite.org/datatype3.html#type_affinity). Jednou z běžných gotcha je, že použití typu sloupce STRING se pokusí převést hodnoty na celé číslo nebo reálné, což může vést k neočekávaným výsledkům. Doporučujeme použít pouze čtyři primitivní názvy typů SQLite: INTEGER, REAL, TEXT a BLOB.

SQLite umožňuje zadat omezující vlastnosti typu, jako je délka, přesnost a škálování, ale databázový stroj je neuplatňuje. Vaše aplikace zodpovídá za vynucování těchto.

## <a name="see-also"></a>Viz také:

- [DataTypes v SQLite](https://www.sqlite.org/datatype3.html)
