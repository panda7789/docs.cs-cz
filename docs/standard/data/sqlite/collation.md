---
title: Kolace
ms.date: 12/13/2019
description: Naučte se vytvořit vlastní sekvenci seřazení.
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777386"
---
# <a name="collation"></a>Kolace

Při porovnávání textových hodnot s určením pořadí a rovnosti používá SQLite sekvence. Můžete určit, kterou kolaci použít při vytváření sloupců nebo operací v dotazech SQL. SQLite obsahuje tři sekvence řazení ve výchozím nastavení.

| Kolace | Popis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje koncovou mezeru.               |
| BEZPŘÍPADU    | Nerozlišuje velká a malá písmena pro znaky ASCII A – Z |
| TVARU    | Rozlišuje velká a malá písmena. Porovná bajty přímo   |

## <a name="custom-collation"></a>Vlastní kolace

Můžete také definovat vlastní řadicí sekvence nebo přepsat vestavěné objekty pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. Následující příklad ukazuje, jak přepsat kolaci případu pro podporu znaků Unicode. [Úplný ukázkový kód](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like – operátor

Operátor LIKE v SQLite nedodržuje kolace. Výchozí implementace má stejnou sémantiku jako řazení v případě případu. Rozlišuje velká a malá písmena pro znaky ASCII A až Z.

Pomocí následujícího příkazu pragma můžete snadno vytvořit rozlišování velkých a malých písmen jako operátor:

```sql
PRAGMA case_sensitive_like = 0
```

Podrobnosti o přepsání implementace operátoru LIKE najdete v tématu [uživatelsky definované funkce](user-defined-functions.md) .

## <a name="see-also"></a>Viz také:

* [Uživatelsky definované funkce](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
