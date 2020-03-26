---
title: Kolace
ms.date: 12/13/2019
description: Přečtěte si, jak vytvořit vlastní posloupnost řazení.
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506538"
---
# <a name="collation"></a>Kolace

Kompletování sekvence jsou používány SQLite při porovnávání text hodnoty k určení pořadí a rovnosti. Můžete určit, které řazení se má použít při vytváření sloupců nebo operací v dotazech SQL. SQLite obsahuje ve výchozím nastavení tři kompletační sekvence.

| Kolace | Popis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje koncové prázdné znaky.               |
| ŽÁDNÝ PŘÍPAD    | Necitlivé malá a velká písmena pro znaky ASCII A-Z |
| Binární    | Case-sensitive. Porovnává přímo bajty   |

## <a name="custom-collation"></a>Vlastní řazení

Můžete také definovat vlastní řazení sekvence nebo přepsat vestavěné ty <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>pomocí . Následující příklad ukazuje přepsání nocase řazení pro podporu znaků Unicode. [Úplný ukázkový kód](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) je k dispozici na GitHubu.

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
