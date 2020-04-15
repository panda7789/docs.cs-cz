---
title: Typy dat
ms.date: 12/13/2019
description: Popisuje podporované datové typy a některá omezení kolem nich.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389045"
---
# <a name="data-types"></a>Typy dat

SQLite má pouze čtyři primitivní datové typy: INTEGER, REAL, TEXT a BLOB. Api, které vracejí databázové hodnoty jako `object` vždy vrátí pouze jeden z těchto čtyř typů. Další typy .NET jsou podporovány Microsoft.Data.Sqlite, ale hodnoty jsou nakonec vykonaný mezi těmito typy a jeden ze čtyř primitivních typů.

| .NET           | SQLite  | Poznámky                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Logická hodnota        | CELÉ ČÍSLO | `0` nebo `1`                                                    |
| Byte           | CELÉ ČÍSLO |                                                               |
| Bajt[]         | Blob    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFFzzz                                |
| Desetinné číslo        | TEXT    | `0.0###########################`Formát. REAL by byl ztrátový. |
| Double         | REÁLNÉ    |                                                               |
| Identifikátor GUID           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | CELÉ ČÍSLO |                                                               |
| Int32          | CELÉ ČÍSLO |                                                               |
| Int64          | CELÉ ČÍSLO |                                                               |
| SByte          | CELÉ ČÍSLO |                                                               |
| Single         | REÁLNÉ    |                                                               |
| Řetězec         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d.hh:mm:ss.fffffff                                            |
| UInt16         | CELÉ ČÍSLO |                                                               |
| UInt32         | CELÉ ČÍSLO |                                                               |
| UInt64         | CELÉ ČÍSLO | Přetečení velkých hodnot                                         |

## <a name="alternative-types"></a>Alternativní typy

Některé typy .NET lze číst z alternativních typů SQLite. Parametry lze také nakonfigurovat pro použití těchto alternativních typů. Další informace naleznete v tématu [Parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Poznámky          |
| -------------- | ------- | ---------------- |
| Char           | CELÉ ČÍSLO | UTF-16           |
| DateTime       | REÁLNÉ    | Hodnota juliánského dne |
| DateTimeOffset | REÁLNÉ    | Hodnota juliánského dne |
| Identifikátor GUID           | Blob    |                  |
| TimeSpan       | REÁLNÉ    | Ve dnech          |

Například následující dotaz přečte hodnotu TimeSpan ze sloupce REAL v sadě výsledků.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy sloupců

SQLite používá systém dynamického typu, kde je typ hodnoty spojen se samotnou hodnotou a nikoli se sloupcem, kde je uložena. Můžete použít jakýkoli název typu sloupce, který chcete. Microsoft.Data.Sqlite nebude používat žádné další sémantiku na tyto názvy.

Název typu sloupce má vliv na [spřažení typu](https://www.sqlite.org/datatype3.html#type_affinity). Jeden společný gotcha je, že pomocí typu sloupce STRING se pokusí převést hodnoty na INTEGER nebo REAL, což může vést k neočekávaným výsledkům. Doporučujeme používat pouze čtyři primitivní názvy typů SQLite: INTEGER, REAL, TEXT a BLOB.

SQLite umožňuje zadat omezující podmínky typu jako délka, přesnost a měřítko, ale nejsou vynuceny databázovým strojem. Vaše aplikace je zodpovědná za jejich vynucení.

## <a name="see-also"></a>Viz také

- [Datové typy v SQLite](https://www.sqlite.org/datatype3.html)
