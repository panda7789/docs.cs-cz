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
ms.openlocfilehash: 361101258caca763502f92d897866c75bc8d7da2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418726"
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma poskytuje stručný úvod do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazů dotazů a některé z typických typů operací, které v dotazu provedete. Podrobnější informace najdete v následujících tématech:  
  
 [Výrazy dotazů LINQ](../../../linq/index.md)  
  
 [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)  
  
 [Návod: zápis dotazů vC#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Pokud už jste obeznámeni s dotazovacím jazykem, jako je SQL nebo XQuery, můžete většinu tohoto tématu přeskočit. Přečtěte si o klauzuli`from` v další části, kde se dozvíte o pořadí klauzulí v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazy dotazu.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu je prvním krokem určení zdroje dat. V C# nástroji as ve většině programovacích jazyků musí být před použitím deklarována proměnná. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]m dotazu je klauzule `from` nejprve první, aby bylo možné zavést zdroj dat (`customers`) a *proměnnou rozsahu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Proměnná rozsahu je stejná jako proměnná iterace ve smyčce `foreach`, s tím rozdílem, že ve výrazu dotazu nedochází k žádným skutečným iteracím. Při spuštění dotazu bude proměnná rozsahu sloužit jako odkaz na každý následný prvek v `customers`. Protože kompilátor může odvodit typ `cust`, nemusíte ho explicitně určovat. Další proměnné rozsahu mohou být zavedeny klauzulí `let`. Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> U neobecných zdrojů dat, jako je například <xref:System.Collections.ArrayList>, musí být proměnná rozsahu explicitně typu. Další informace najdete v tématu [Postup: dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) a [klauzule FROM](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu. Filtr způsobí, že dotaz vrátí pouze prvky, pro které je výraz pravdivý. Výsledek je vytvořen pomocí klauzule `where`. Filtr v důsledku určuje, které prvky mají být vyloučeny ze zdrojové sekvence. V následujícím příkladu jsou vráceny pouze `customers`, kteří mají adresu v Londýně.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Pomocí známých C# logických `AND` a operátorů `OR` můžete použít libovolný počet výrazů filtru podle potřeby v klauzuli `where`. Pokud například chcete vracet pouze zákazníky z "Londýn" `AND` jejichž název je "Devon", měli byste napsat následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Pokud chcete vracet zákazníky z Brna nebo Paříž, napište následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodné řazení vrácených dat. Klauzule `orderby` způsobí, že prvky v vrácené sekvenci budou seřazeny podle výchozí porovnávací metody pro typ, který se seřadí. Například následující dotaz lze rozšířit pro řazení výsledků na základě vlastnosti `Name`. Vzhledem k tomu, že `Name` je řetězec, výchozí porovnávání provede abecední řazení z A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Pro seřazení výsledků v opačném pořadí z Z na a použijte klauzuli `orderby…descending`.  
  
 Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 Klauzule `group` umožňuje seskupit výsledky podle zadaného klíče. Můžete například určit, že by měly být výsledky seskupené podle `City` tak, že všichni zákazníci z Londýna nebo Paříž jsou v jednotlivých skupinách. V tomto případě je `cust.City` klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Když ukončíte dotaz s klauzulí `group`, vaše výsledky budou mít formu seznamu seznamů. Každý prvek v seznamu je objekt, který má `Key` člen a seznam elementů, které jsou seskupeny pod tímto klíčem. Při iteraci na dotaz, který vytváří sekvenci skupin, je nutné použít vnořenou smyčku `foreach`. Vnější smyčka projde každou skupinu a vnitřní smyčka projde členy každé skupiny.  
  
 Pokud musíte odkazovat na výsledky operace skupiny, můžete pomocí klíčového slova `into` vytvořit identifikátor, který lze dotazovat dále. Následující dotaz vrátí pouze skupiny, které obsahují více než dva zákazníky:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.  
  
## <a name="joining"></a>Spojování  
 Operace join vytvořte přidružení mezi sekvencemi, které nejsou explicitně modelovány ve zdrojích dat. Můžete například provést připojení a vyhledat všechny zákazníky a distributory, kteří mají stejné umístění. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] klauzule `join` vždy funguje na kolekcích objektů namísto přímo v databázových tabulkách.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nemusíte používat `join` tak často jako v jazyce SQL, protože cizí klíče v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jsou reprezentovány v objektovém modelu jako vlastnosti, které obsahují kolekci položek. Například objekt `Customer` obsahuje kolekci objektů `Order`. Místo toho, abyste mohli provádět spojení, získáte přístup k objednávkám pomocí zápisu teček:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 Klauzule `select` generuje výsledky dotazu a určuje "tvar" nebo typ každého vráceného elementu. Můžete například určit, jestli se výsledky budou skládat z kompletních `Customer` objektů, jenom jednoho člena, podmnožiny členů nebo nějakého jiného typu výsledku založeného na výpočtu nebo vytvoření nového objektu. Když klauzule `select` vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*. Použití projekce k transformaci dat je výkonná schopnost [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazů dotazů. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](./data-transformations-with-linq.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také:

- [Výrazy dotazů LINQ](../../../linq/index.md)
- [Návod: zápis dotazů vC#](./walkthrough-writing-queries-linq.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
