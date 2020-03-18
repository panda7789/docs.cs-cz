---
title: Základní operace dotazů LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635935"
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma poskytuje stručný úvod do výrazy dotazu LINQ a některé typické druhy operací, které provádíte v dotazu. Podrobnější informace naleznete v následujících tématech:  
  
 [Výrazy dotazu LINQ](../../../linq/index.md)  
  
 [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)  
  
 [Návod: Psaní dotazů v C #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Pokud již znáte dotazovací jazyk, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit. Přečtěte si`from` o "klauzuli" v další části se dozvíte o pořadí klauzulí ve výrazech dotazu LINQ.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 V dotazu LINQ je prvním krokem určení zdroje dat. V jazyce C# jako ve většině programovacích jazyků musí být proměnná deklarována před použitím. V dotazu LINQ `from` je klauzule na prvním místě, aby bylo možné zavést zdroj dat (`customers`) a *proměnnou rozsahu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Proměnná rozsahu je jako iterace proměnné ve smyčce s tím rozdílem, `foreach` že žádná skutečná iterace dochází ve výrazu dotazu. Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz `customers`na každý následující prvek v aplikaci . Vzhledem k tomu, že `cust`kompilátor můžete odvodit typ , není nutné zadat explicitně. Další proměnné rozsahu mohou být `let` zavedeny klauzulí. Další informace naleznete v tématu [let klauzule](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> Pro neobecné zdroje dat, jako <xref:System.Collections.ArrayList>je například proměnná rozsahu, musí být explicitně zadána. Další informace naleznete v [tématu Jak dotaz ArrayList s LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) a [z klauzule](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Pravděpodobně nejběžnější operace dotazu je použít filtr ve formě logického výrazu. Filtr způsobí, že dotaz vrátí pouze ty prvky, pro které je výraz pravdivý. Výsledek je vytvořen pomocí `where` klauzule. Filtr v platnost určuje, které prvky vyloučit ze zdrojové sekvence. V následujícím příkladu `customers` jsou vráceny pouze ty, kteří mají adresu v Londýně.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Můžete použít známé C# `AND` `OR` logické a operátory použít tolik výrazy filtru podle potřeby v klauzuli. `where` Chcete-li například vrátit pouze `AND` zákazníky z "Londýna", jehož název je "Devon", napíšete následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Chcete-li vrátit zákazníkům z Londýna nebo Paříže, napište následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Další informace naleznete v tématu [where clause](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodné seřadit vrácená data. Klauzule `orderby` způsobí, že prvky ve vrácené sekvenci budou seřazeny podle výchozího porovnávání pro typ, který je seřazen. Například následující dotaz lze rozšířit seřadit výsledky `Name` na základě vlastnosti. Protože `Name` je řetězec, výchozí porovnávání provádí abecední řazení od A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Chcete-li výsledky seřadit v opačném pořadí `orderby…descending` od Z do A, použijte klauzuli.  
  
 Další informace naleznete v [tématu orderby klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 Klauzule `group` umožňuje seskupit výsledky na základě zadaného klíče. Můžete například určit, že výsledky by `City` měly být seskupeny tak, aby všichni zákazníci z Londýna nebo Paříže byli v jednotlivých skupinách. V tomto `cust.City` případě je klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Když dotaz ukončíte `group` klauzulí, budou mít výsledky podobu seznamu seznamů. Každý prvek v seznamu je objekt, který má `Key` člen a seznam prvků, které jsou seskupeny pod tímto klíčem. Při itetu přes dotaz, který vytváří posloupnost skupin, `foreach` je nutné použít vnořené smyčky. Vnější smyčka iterát přes každou skupinu a vnitřní smyčka iterates nad členy každé skupiny.  
  
 Pokud je nutné odkazovat na výsledky operace skupiny, můžete použít `into` klíčové slovo k vytvoření identifikátoru, který lze dále dotazovat. Následující dotaz vrátí pouze ty skupiny, které obsahují více než dva zákazníky:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Další informace naleznete v tématu [group clause](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Připojení  
 Operace spojení vytvářejí přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat. Můžete například provést spojení a najít všechny zákazníky a distributory, kteří mají stejné umístění. V LINQ `join` klauzule vždy pracuje proti kolekce objektů namísto tabulky databáze přímo.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 V LINQ není třeba používat `join` tak často jako v SQL, protože cizí klíče v LINQ jsou reprezentovány v objektovém modelu jako vlastnosti, které drží kolekci položek. Například `Customer` objekt obsahuje kolekci `Order` objektů. Místo provedení spojení přistupujete k příkazům pomocí tečkového zápisu:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Další informace naleznete v tématu [join clause](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 Klauzule `select` vytváří výsledky dotazu a určuje "tvar" nebo typ každého vráceného prvku. Můžete například určit, zda se výsledky `Customer` budou skládat z úplných objektů, pouze jednoho člena, podmnožiny členů nebo zcela jiného typu výsledku na základě výpočtu nebo vytvoření nového objektu. Když `select` klauzule vytvoří něco jiného než kopii zdrojového prvku, operace se nazývá *projekce*. Použití projekce k transformaci dat je výkonné schopnosti výrazů dotazu LINQ. Další informace naleznete [v tématu transformace dat s LINQ (C#)](./data-transformations-with-linq.md) a [select klauzule](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také

- [Výrazy dotazu LINQ](../../../linq/index.md)
- [Návod: Psaní dotazů v C #](./walkthrough-writing-queries-linq.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
