---
title: Základní operace dotazů LINQ (C#)
description: Představte si výrazy LINQ Query a některé z operací, které můžete provádět v dotazu.
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
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105528"
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma poskytuje stručný úvod do výrazů LINQ Query a některé z typických typů operací, které v dotazu provedete. Podrobnější informace najdete v následujících tématech:  
  
 [Výrazy dotazů LINQ](../../../linq/index.md)  
  
 [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)  
  
 [Návod: zápis dotazů v jazyce C #](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Pokud už jste obeznámeni s dotazovacím jazykem, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit. Přečtěte si o `from` klauzuli v následující části, kde najdete další informace o pořadí klauzulí ve výrazech dotazů LINQ.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 V dotazu LINQ je prvním krokem určení zdroje dat. V jazyce C# jako ve většině programovacích jazyků je nutné deklarovat proměnnou předtím, než bude možné ji použít. V dotazu LINQ je `from` klauzule nejprve první, aby zavedla zdroj dat ( `customers` ) a *proměnnou rozsahu* ( `cust` ).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Proměnná rozsahu je stejná jako proměnná iterace ve `foreach` smyčce s tím rozdílem, že ve výrazu dotazu nedochází k žádným skutečným iteracím. Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz na každý následný prvek v `customers` . Vzhledem k tomu, že kompilátor může odvodit typ `cust` , nemusíte ho explicitně určovat. Další proměnné rozsahu mohou být zavedeny `let` klauzulí. Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> U neobecných zdrojů dat, jako například <xref:System.Collections.ArrayList> , je nutné explicitně zadat proměnnou rozsahu. Další informace najdete v tématu [Postup dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) a [klauzule FROM](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu. Filtr způsobí, že dotaz vrátí pouze prvky, pro které je výraz pravdivý. Výsledek je vytvořen pomocí `where` klauzule. Filtr v důsledku určuje, které prvky mají být vyloučeny ze zdrojové sekvence. V následujícím příkladu jsou vráceny pouze ty `customers` , kteří mají adresu v Londýně.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Známé logické a operátory jazyka C# můžete `AND` použít `OR` k použití tolika výrazů filtru podle potřeby v `where` klauzuli. Pokud například chcete vracet pouze zákazníky z "Londýn" `AND` , jejichž název je "Devon", měli byste napsat následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Pokud chcete vracet zákazníky z Brna nebo Paříž, napište následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodné řazení vrácených dat. `orderby`Klauzule způsobí řazení prvků v vrácené sekvenci podle výchozí porovnávací metody pro typ, který se seřadí. Například následující dotaz lze rozšířit pro řazení výsledků na základě `Name` Vlastnosti. Vzhledem k tomu `Name` , že je řetězec, výchozí porovnávání provede abecední řazení z a do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Pro seřazení výsledků v opačném pořadí z Z na A použijte `orderby…descending` klauzuli.  
  
 Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 `group`Klauzule umožňuje seskupit výsledky podle zadaného klíče. Můžete například určit, že by měly být výsledky seskupené podle `City` , takže všichni zákazníci z Londýna nebo Paříž jsou v jednotlivých skupinách. V tomto případě `cust.City` je klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Když ukončíte dotaz s `group` klauzulí, výsledky budou mít formu seznamu seznamů. Každý prvek v seznamu je objekt, který má `Key` člena a seznam elementů, které jsou seskupeny pod tímto klíčem. Při iteraci na dotaz, který vytváří sekvenci skupin, je nutné použít vnořenou `foreach` smyčku. Vnější smyčka projde každou skupinu a vnitřní smyčka projde členy každé skupiny.  
  
 Pokud musíte odkazovat na výsledky operace skupiny, můžete pomocí `into` klíčového slova vytvořit identifikátor, který může být dále dotazován. Následující dotaz vrátí pouze skupiny, které obsahují více než dva zákazníky:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.  
  
## <a name="joining"></a>Připojení  
 Operace join vytvořte přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat. Můžete například provést připojení a vyhledat všechny zákazníky a distributory, kteří mají stejné umístění. Klauzule v jazyce LINQ `join` klauzule vždy funguje na kolekcích objektů namísto přímo v databázových tabulkách.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 V LINQ není nutné používat `join` tak často jako v jazyce SQL, protože cizí klíče v technologii LINQ jsou reprezentovány v objektovém modelu jako vlastnosti, které obsahují kolekci položek. Například `Customer` objekt obsahuje kolekci `Order` objektů. Místo toho, abyste mohli provádět spojení, získáte přístup k objednávkám pomocí zápisu teček:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 `select`Klauzule vytvoří výsledky dotazu a určí "tvar" nebo typ každého vráceného elementu. Můžete například určit, jestli se výsledky budou skládat z kompletních `Customer` objektů, jenom jednoho člena, podmnožiny členů nebo některého zcela jiného typu výsledku na základě výpočtu nebo nového objektu. Když `select` klauzule vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*. Použití projekce k transformaci dat je výkonná schopnost výrazů dotazů LINQ. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](./data-transformations-with-linq.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také

- [Výrazy dotazů LINQ](../../../linq/index.md)
- [Návod: zápis dotazů v jazyce C #](./walkthrough-writing-queries-linq.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
