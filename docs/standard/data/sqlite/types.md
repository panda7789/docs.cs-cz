---
title: Typy dat
ms.date: 12/13/2019
description: Popisuje podporované typy dat a některá omezení, která jsou kolem nich.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389045"
---
# <a name="data-types"></a>Typy dat

SQLite má pouze čtyři primitivní datové typy: INTEGER, REAL, TEXT a BLOB. Rozhraní API, která vracejí hodnoty databáze `object` , se vždy vrátí k jednomu z těchto čtyř typů. Další typy rozhraní .NET jsou podporovány společností Microsoft. data. sqlite, ale hodnoty jsou nakonec přiřazeny mezi tyto typy a jeden ze čtyř primitivních typů.

| .NET           | SQLite  | Poznámky                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Logická hodnota        | CELÉ ČÍSLO | `0` nebo `1`                                                    |
| Byte           | CELÉ ČÍSLO |                                                               |
| Byte []         | PŘÍZNAKY    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | RRRR-MM-DD HH: mm: ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | RRRR-MM-DD HH: mm: ss. FFFFFFFzzz                                |
| Desetinné číslo        | TEXT    | `0.0###########################`formátovat. REAL by byl ztrátou. |
| Double         | REÁLNÉ    |                                                               |
| Identifikátor GUID           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | CELÉ ČÍSLO |                                                               |
| Int32          | CELÉ ČÍSLO |                                                               |
| Int64          | CELÉ ČÍSLO |                                                               |
| SByte          | CELÉ ČÍSLO |                                                               |
| Single         | REÁLNÉ    |                                                               |
| Řetězec         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: ss. fffffff                                            |
| UInt16         | CELÉ ČÍSLO |                                                               |
| UInt32         | CELÉ ČÍSLO |                                                               |
| UInt64         | CELÉ ČÍSLO | Přetečení velkých hodnot                                         |

## <a name="alternative-types"></a>Alternativní typy

Některé typy rozhraní .NET lze číst z alternativních typů SQLite. Parametry lze také nakonfigurovat pro použití těchto alternativních typů. Další informace najdete v tématu [parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Poznámky          |
| -------------- | ------- | ---------------- |
| Char           | CELÉ ČÍSLO | UTF-16           |
| DateTime       | REÁLNÉ    | Hodnota juliánského dne |
| DateTimeOffset | REÁLNÉ    | Hodnota juliánského dne |
| Identifikátor GUID           | PŘÍZNAKY    |                  |
| TimeSpan       | REÁLNÉ    | Ve dnech          |

Například následující dotaz přečte hodnotu TimeSpan z REÁLNÉho sloupce v sadě výsledků dotazu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy sloupců

SQLite používá dynamický typ systému, kde je typ hodnoty spojen s vlastní hodnotou a nikoli sloupcem, kde je uložen. Můžete použít libovolný název typu sloupce, který chcete. Microsoft. data. sqlite nepoužije pro tyto názvy žádnou další sémantiku.

Název typu sloupce má vliv na [spřažení typů](https://www.sqlite.org/datatype3.html#type_affinity). Jednou z běžných gotcha je, že použití typu sloupce STRING se pokusí převést hodnoty na celé číslo nebo reálné, což může vést k neočekávaným výsledkům. Doporučujeme použít pouze čtyři primitivní názvy typů SQLite: INTEGER, REAL, TEXT a BLOB.

SQLite umožňuje zadat omezující vlastnosti typu, jako je délka, přesnost a škálování, ale databázový stroj je neuplatňuje. Vaše aplikace zodpovídá za vynucování těchto.

## <a name="see-also"></a>Viz také

- [DataTypes v SQLite](https://www.sqlite.org/datatype3.html)
