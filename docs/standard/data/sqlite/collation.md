---
title: Kolace
ms.date: 12/13/2019
description: Přečtěte si, jak vytvořit vlastní posloupnost řazení.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242969"
---
# <a name="collation"></a>Kolace

Kompletování sekvence jsou používány SQLite při porovnávání text hodnoty k určení pořadí a rovnosti. Můžete určit, které řazení se má použít při vytváření sloupců nebo operací v dotazech SQL. SQLite obsahuje ve výchozím nastavení tři kompletační sekvence.

| Kolace | Popis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje koncové prázdné znaky.               |
| ŽÁDNÝ PŘÍPAD    | Necitlivé malá a velká písmena pro znaky ASCII A-Z |
| Binární    | Case-sensitive. Porovnává přímo bajty   |

## <a name="custom-collation"></a>Vlastní řazení

Můžete také definovat vlastní řazení sekvence nebo přepsat vestavěné ty <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>pomocí . Následující příklad ukazuje přepsání nocase řazení pro podporu znaků Unicode. [Úplný ukázkový kód](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Stejně jako operátor

Operátor LIKE v SQLite nectí kolace. Výchozí implementace má stejnou sémantiku jako kolace NOCASE. Je pouze malá a velká písmena pro znaky ASCII A až Z.

Můžete snadno provést operátor like rozlišování velkých a malých písmen pomocí následujícího příkazu pragma:

```sql
PRAGMA case_sensitive_like = 1
```

Viz [Uživatelem definované funkce](user-defined-functions.md) podrobnosti o přepsání implementace operátoru LIKE.

## <a name="see-also"></a>Viz také

* [Uživatelsky definované funkce](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
