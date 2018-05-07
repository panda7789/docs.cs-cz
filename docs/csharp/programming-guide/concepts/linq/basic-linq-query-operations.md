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
ms.openlocfilehash: 2825b79c9638fff050522da43184a8d95a3fe02f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma poskytuje stručný úvod do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy a některé typické druhy operace, které můžete provádět v dotazu. Podrobnější informace jsou v následujících tématech:  
  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Návod: Zápis dotazů v C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Pokud jste již obeznámeni s dotazovací jazyk, jako je například SQL nebo XQuery, můžete přeskočit většinu tohoto tématu. Přečtěte si informace o "`from` klauzule" v části Další informace o pořadí klauzule v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, prvním krokem je určit zdroj dat. Proměnné v jazyce C# stejně jako většinu programovacích jazyků musí být deklarován před použitím. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, `from` klauzule dodává nejdřív za účelem předložení zdroje dat (`customers`) a *proměnnou rozsahu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 Proměnná rozsahu je jako proměnné iterace ve `foreach` cykly s tím rozdílem, že dojde k žádné skutečné iterace ve výrazu dotazu. Po provedení dotazu proměnnou rozsahu bude sloužit jako odkaz na všechny následné prvky v `customers`. Protože kompilátor lze odvodit typ `cust`, není nutné explicitně zadat. Další rozsah proměnné mohou být způsobeny `let` klauzule. Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Pro data neobecné zdroje, jako <xref:System.Collections.ArrayList>, proměnnou rozsahu musí být explicitně zadán. Další informace najdete v tématu [postup: dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) a [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Nejběžnější operace dotazů je pravděpodobně použít filtr ve formě logický výraz. Filtr způsobí, že dotaz vrátil jenom elementy, pro které je výraz hodnotu true. Výsledkem je vytvořena pomocí `where` klauzule. Filtr platí určuje prvky, které chcete vyloučit ze zdrojové sekvence. V následujícím příkladu, pouze ty `customers` kdo mají adresu v Londýně jsou vráceny.  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Můžete použít známé jazyka C# logické `AND` a `OR` operátory použít jako mnoho filtrovat výrazy v případě potřeby v `where` klauzule. Chcete-li například vrátit pouze zákazníky z "Praha" `AND` jehož jméno je "Devon" by zápisu následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Vracení zákazníky z Londýna nebo Paříž, by zápisu následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodnější seřaďte vrácená data. `orderby` Klauzule způsobí, že elementy vrácený postupně, který se má seřadit podle výchozí porovnávače pro typ řazen. Například následující dotaz lze rozšířit pro řazení výsledků na základě `Name` vlastnost. Protože `Name` je řetězec, porovnávače výchozí provede abecedním řazení z A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Chcete-li v obráceném pořadí řazení výsledků z Z až A, použijte `orderby…descending` klauzule.  
  
 Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 `group` Klauzule umožňují seskupit výsledky podle klíče, který zadáte. Například můžete zadat, že výsledky by měly být seskupené podle `City` tak, aby všechny zákazníky z Londýna nebo Paříž jsou v jednotlivých skupinách. V takovém případě `cust.City` je klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Při ukončení dotaz s `group` klauzuli výsledky mít formu seznam seznamů. Každý prvek v seznamu je objekt, který má `Key` člen a seznam prvky, které jsou seskupené v rámci tohoto klíče. Pokud jste iterace v dotazu, který produkuje pořadí skupin, je nutné použít vnořený `foreach` smyčky. Vnější smyčky iteruje nad každou skupinu a vnitřní smyčky iteruje nad členy každé skupiny.  
  
 Pokud musí odkazovat na výsledky operace skupiny, můžete použít `into` – klíčové slovo vytvořit identifikátor, který může být dotazován na další. Následující dotaz vrátí jenom skupiny, které obsahují více než dva zákazníkům:  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Spojování  
 Operace spojení vytvořit přidružení mezi pořadí, která nejsou explicitně modelován v datových zdrojů. Například můžete provést připojení k vyhledání zákazníků a distributorů, kteří mají stejné umístění. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` klauzule vždy funguje s kolekcí objektů místo databázových tabulek přímo.  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nemusíte používat `join` často uděláte v systému SQL, protože cizí klíče v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jsou vyjádřené v modelu objektu vlastnosti, které mají kolekce položek. Například `Customer` objektu obsahuje kolekci `Order` objekty. Místo provedení spojení, máte přístup k objednávky pomocí zápisu s tečkou:  
  
```  
from order in Customer.Orders...  
```  
  
 Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 `select` Klauzule vytváří výsledky dotazu a určuje "tvar" nebo typ každý vrácený element. Například můžete určit, jestli výsledky budou tvořeny dokončení `Customer` objekty, jenom jednoho člena, podmnožinu členů nebo nějaký typ úplně jiné výsledek podle výpočtů nebo vytvoření nového objektu. Když `select` klauzule vytvořil něco jiného než kopii source element, operace se nazývá *projekce*. Použití projekce k transformaci dat je výkonná funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) a [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Návod: Zápis dotazů v C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Klíčová slova dotazu (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
