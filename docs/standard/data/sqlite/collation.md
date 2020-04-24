---
title: Kolace
ms.date: 12/13/2019
description: Naučte se vytvořit vlastní sekvenci seřazení.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242969"
---
# <a name="collation"></a>Kolace

Při porovnávání textových hodnot s určením pořadí a rovnosti používá SQLite sekvence. Můžete určit, kterou kolaci použít při vytváření sloupců nebo operací v dotazech SQL. SQLite obsahuje tři sekvence řazení ve výchozím nastavení.

| Kolace | Popis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje koncovou mezeru.               |
| BEZPŘÍPADU    | Nerozlišuje velká a malá písmena pro znaky ASCII A – Z |
| TVARU    | Rozlišuje velká a malá písmena. Porovná bajty přímo   |

## <a name="custom-collation"></a>Vlastní kolace

Můžete také definovat vlastní pořadí kompletování nebo přepsat předdefinované pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. Následující příklad ukazuje, jak přepsat kolaci případu pro podporu znaků Unicode. [Úplný ukázkový kód](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like – operátor

Operátor LIKE v SQLite nedodržuje kolace. Výchozí implementace má stejnou sémantiku jako řazení v případě případu. Rozlišuje velká a malá písmena pro znaky ASCII A až Z.

Pomocí následujícího příkazu pragma můžete snadno vytvořit rozlišování velkých a malých písmen jako operátor:

```sql
PRAGMA case_sensitive_like = 1
```

Podrobnosti o přepsání implementace operátoru LIKE najdete v tématu [uživatelsky definované funkce](user-defined-functions.md) .

## <a name="see-also"></a>Viz také

* [Uživatelem definované funkce](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
