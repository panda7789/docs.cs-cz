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
ms.openlocfilehash: 013e1960e6c5721e0bd7ce6998848ddce15a4e4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924396"
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma poskytuje stručný úvod do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazů dotazů a některé z typických typů operací, které v dotazu provedete. Podrobnější informace najdete v následujících tématech:  
  
 [Výrazy dotazů LINQ](../../linq-query-expressions/index.md)  
  
 [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)  
  
 [Návod: Zápis dotazů vC#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Pokud už jste obeznámeni s dotazovacím jazykem, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit. Přečtěte si o`from` klauzuli v následující části, kde najdete další informace o pořadí klauzulí ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] V dotazu je prvním krokem určení zdroje dat. V C# nástroji as ve většině programovacích jazyků musí být před použitím deklarována proměnná. `cust``customers`V dotazu je klauzule nejprve první, aby zavedla zdroj dat () a proměnnou rozsahu (). `from` [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Proměnná rozsahu je stejná jako proměnná iterace ve `foreach` smyčce s tím rozdílem, že ve výrazu dotazu nedochází k žádným skutečným iteracím. Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz na každý následný prvek v `customers`. Vzhledem k tomu `cust`, že kompilátor může odvodit typ, nemusíte ho explicitně určovat. Další proměnné rozsahu mohou být zavedeny `let` klauzulí. Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> U neobecných zdrojů <xref:System.Collections.ArrayList>dat, jako například, je nutné explicitně zadat proměnnou rozsahu. Další informace najdete v tématu [jak: Dotazujte objekt ArrayList pomocí klauzuleC#LINQ](./how-to-query-an-arraylist-with-linq.md) () a [klauzule FROM](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu. Filtr způsobí, že dotaz vrátí pouze prvky, pro které je výraz pravdivý. Výsledek je vytvořen pomocí `where` klauzule. Filtr v důsledku určuje, které prvky mají být vyloučeny ze zdrojové sekvence. V následujícím příkladu jsou vráceny pouze ty `customers` , kteří mají adresu v Londýně.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Známé C# logické `AND` a `OR` operátory můžete použít k použití tolika výrazů filtru podle potřeby v `where` klauzuli. Pokud například chcete vracet pouze zákazníky z "Londýn" `AND` , jejichž název je "Devon", měli byste napsat následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Pokud chcete vracet zákazníky z Brna nebo Paříž, napište následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodné řazení vrácených dat. `orderby` Klauzule způsobí řazení prvků v vrácené sekvenci podle výchozí porovnávací metody pro typ, který se seřadí. Například následující dotaz lze rozšířit pro řazení výsledků na základě `Name` vlastnosti. Vzhledem `Name` k tomu, že je řetězec, výchozí porovnávání provede abecední řazení z a do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Pro seřazení výsledků v opačném pořadí z z na a použijte `orderby…descending` klauzuli.  
  
 Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 `group` Klauzule umožňuje seskupit výsledky podle zadaného klíče. Můžete například určit, že by měly být výsledky seskupené podle `City` , takže všichni zákazníci z Londýna nebo Paříž jsou v jednotlivých skupinách. V tomto případě `cust.City` je klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Když ukončíte dotaz s `group` klauzulí, výsledky budou mít formu seznamu seznamů. Každý prvek v seznamu je objekt, který má `Key` člena a seznam elementů, které jsou seskupeny pod tímto klíčem. Při iteraci na dotaz, který vytváří sekvenci skupin, je nutné použít vnořenou `foreach` smyčku. Vnější smyčka projde každou skupinu a vnitřní smyčka projde členy každé skupiny.  
  
 Pokud musíte odkazovat na výsledky operace skupiny, můžete pomocí `into` klíčového slova vytvořit identifikátor, který může být dále dotazován. Následující dotaz vrátí pouze skupiny, které obsahují více než dva zákazníky:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.  
  
## <a name="joining"></a>Spojování  
 Operace join vytvořte přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat. Můžete například provést připojení a vyhledat všechny zákazníky a distributory, kteří mají stejné umístění. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]klauzulivždyckyfunguje nakolekcíchobjektůnamístopřímovdatabázovýchtabulkách.`join`  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nemusíte používat `join` tak často, jako v jazyce SQL, protože cizí klíče v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jsou reprezentovány v objektovém modelu jako vlastnosti, které obsahují kolekci položek. Například `Customer` objekt obsahuje `Order` kolekci objektů. Místo toho, abyste mohli provádět spojení, získáte přístup k objednávkám pomocí zápisu teček:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 `select` Klauzule vytvoří výsledky dotazu a určí "tvar" nebo typ každého vráceného elementu. Můžete například určit, jestli se výsledky budou skládat z kompletních `Customer` objektů, jenom jednoho člena, podmnožiny členů nebo některého zcela jiného typu výsledku na základě výpočtu nebo nového objektu. Když klauzule vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce.* `select` Použití projekce k transformaci dat je výkonná funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazů dotazů. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](./data-transformations-with-linq.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazů LINQ](../../linq-query-expressions/index.md)
- [Návod: Zápis dotazů vC#](./walkthrough-writing-queries-linq.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
