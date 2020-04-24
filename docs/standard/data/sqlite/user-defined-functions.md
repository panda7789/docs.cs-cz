---
title: Uživatelem definované funkce
ms.date: 12/13/2019
description: Naučte se vytvářet uživatelsky definované skalární a agregační funkce.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447172"
---
# <a name="user-defined-functions"></a>Uživatelem definované funkce

Většina databází obsahuje procedurální dialekt SQL, který můžete použít k definování vlastních funkcí. SQLite se ale v rámci vaší aplikace spouští v procesu. Místo toho, abyste se seznámili s novým dialektem SQL, můžete pouze použít programovací jazyk vaší aplikace.

## <a name="scalar-functions"></a>Skalární funkce

Skalární funkce vrací jednu skalární hodnotu pro každý řádek v dotazu. Definujte nové skalární funkce a přepište vestavěné objekty pomocí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.

Seznam podporovaných parametrů a návratových typů pro `func` argument naleznete v tématu [datové typy](types.md) .

Zadáním `state` argumentu předáte tuto hodnotu do každého vyvolání funkce. Použijte k tomu, abyste se vyhnuli uzávěrům.

Určete `isDeterministic` , zda je funkce deterministické, aby mohl SQLite použít při kompilování dotazů další optimalizace.

Následující příklad ukazuje, jak přidat skalární funkci pro výpočet poloměru válce.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a>Operátory

Následující operátory SQLite jsou implementovány pomocí odpovídajících skalárních funkcí. Definování těchto skalárních funkcí v aplikaci přepíše chování těchto operátorů.

| Operátor          | Funkce      |
| ----------------- | ------------- |
| X GLOB Y          | glob (Y, X)    |
| X JAKO Y          | like (Y, X)    |
| X JAKO Y ESCAPE Z | like (Y, X, Z) |
| × ODPOVÍDÁ Y         | shoda (Y, X)   |
| X REGEXP Y        | RegExp (Y, X)  |

Následující příklad ukazuje, jak definovat funkci RegExp pro povolení odpovídajícího operátoru. SQLite neobsahuje výchozí implementaci funkce RegExp.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a>Agregační funkce

Agregační funkce vrací jednu agregovanou hodnotu pro všechny řádky v dotazu. Definování a přepsání agregačních funkcí <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>pomocí.

`seed` Argument určuje počáteční stav kontextu. Toto použijte, chcete-li se vyhnout uzávěrům také.

`func` Argument je vyvolán jednou na řádek. Pomocí kontextu nashromáždíte konečný výsledek. Vrátí kontext. Tento model umožňuje, aby kontext byl typ hodnoty nebo neměnný.

Pokud `resultSelector` není zadán, použije se jako výsledek konečný stav kontextu. To může zjednodušit definici funkcí, jako je součet a počet, které potřebují pouze zvyšovat počet řádků a vracet je.

Určete `resultSelector` , chcete-li vypočítat konečný výsledek z kontextu po provedení iterace na všech řádcích.

Zobrazení [datových typů](types.md) pro seznam podporovaných typů parametrů pro `func` argument a návratové typy pro. `resultSelector`

Pokud je funkce deterministické, určete `isDeterministic` , aby SQLite mohl použít další optimalizace při kompilování dotazů.

Následující příklad definuje agregační funkci pro výpočet směrodatné odchylky sloupce.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a>chyby

Pokud uživatelsky definovaná funkce vyvolá výjimku, zpráva se vrátí do SQLite. SQLite potom vyvolá chybu a Microsoft. data. sqlite vyvolá výjimku SqliteException. Další informace najdete v tématu [chyby databáze](database-errors.md).

Ve výchozím nastavení se kód chyby SQLite chyby SQLITE_ERROR (nebo 1). Můžete ji však změnit vyvoláním <xref:Microsoft.Data.Sqlite.SqliteException> ve vaší funkci s požadovaným <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> parametrem.

## <a name="debugging"></a>Ladění

SQLite volá vaši implementaci přímo. To umožňuje přidat zarážky, které se aktivují, zatímco SQLite vyhodnocuje dotazy. K dispozici je plné rozhraní .NET pro ladění, které vám může pomáhat při vytváření uživatelem definovaných funkcí.

## <a name="see-also"></a>Viz také

* [Typy dat](types.md)
* [Základní funkce SQLite](https://www.sqlite.org/lang_corefunc.html)
* [Agregační funkce SQLite](https://www.sqlite.org/lang_aggfunc.html)
