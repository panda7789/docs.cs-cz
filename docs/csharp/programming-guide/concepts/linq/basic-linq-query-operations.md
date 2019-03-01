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
ms.openlocfilehash: b8884f2ae230a92f48e93d9b5408ff241f874f92
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968189"
---
# <a name="basic-linq-query-operations-c"></a>Základní operace dotazů LINQ (C#)
Toto téma nabízí stručný úvod do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů výrazy a některé typické druhy operací, které provedete v dotazu. Podrobnější informace jsou v následujících tématech:  
  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Návod: Zápis dotazů vC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Pokud jste již obeznámeni s dotazovací jazyk, jako je SQL nebo výraz XQuery, můžete přeskočit většinu v tomto tématu. Přečtěte si informace o "`from` klauzule" v další části a informace o pořadí ustanovení [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.  
  
## <a name="obtaining-a-data-source"></a>Získání zdroje dat  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, prvním krokem je určení zdroje dat. V jazyce C# jako většina programovacích jazyků musí být proměnná deklarovaná předtím, než je možné. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, `from` klauzule dodává nejprve za účelem předložení zdroje dat (`customers`) a *proměnnou rozsahu* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 Proměnná rozsahu je jako proměnné iterace ve `foreach` opakovat s tím rozdílem, že dojde k žádné skutečné iterace ve výrazu dotazu. Při spuštění dotazu rozsah proměnné bude sloužit jako odkaz na každý prvek po sobě jdoucích `customers`. Protože kompilátor může odvodit typ `cust`, není potřeba explicitně zadat. Další rozsah proměnné může být zavedené prostřednictvím `let` klauzuli. Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  U neobecných zdrojů dat, jako například <xref:System.Collections.ArrayList>, proměnná rozsahu musí být explicitně určeny typy. Další informace najdete v tématu [jak: Vytvoření dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) a [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtrování  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logický výraz. Filtr způsobí, že se dotaz, který vrací pouze prvky, pro které má výraz hodnotu true. Výsledkem je vytvořen pomocí `where` klauzuli. Filtr v platnosti určuje prvky, které chcete vyloučit ze zdrojové sekvence. V následujícím příkladu, pouze na ty `customers` kdo mít adresu v Londýně se vrátí.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Můžete použít známou jazyka C# logické `AND` a `OR` operátory použít jako řada filtr výrazů podle potřeb `where` klauzuli. Například pro vrácení pouze zákazníci z "Londýn" `AND` jejíž název je "Devon", měli byste napsat následující kód:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Chcete-li vrátit zákazníci z Londýna nebo Paříž, měli byste napsat následující kód:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Řazení  
 Často je vhodné seřaďte vrácená data. `orderby` Klauzule způsobí prvky v vrácená sekvence má být seřazen podle výchozí porovnávací metody pro typ seřazený. Například následující dotaz je možné rozšířit seřadit výsledky podle `Name` vlastnost. Protože `Name` je řetězec, výchozí porovnávací metody provede abecední řazení z A do Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Chcete-li v obráceném pořadí řazení výsledků od Z do A, použijte `orderby…descending` klauzuli.  
  
 Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Seskupování  
 `group` Klauzule umožňují seskupit výsledky na základě klíče, který zadáte. Například můžete zadat, že výsledky by se měly Seskupit podle `City` tak, aby všichni zákazníci z Londýna nebo Paříž v jednotlivých skupinách. V takovém případě `cust.City` je klíč.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Konec dotazu s `group` klauzule, vaše výsledky mít formu seznamů. Každý prvek v seznamu je objekt, který má `Key` člen a seznam prvků, které jsou seskupeny podle klíče. Při iteraci přes dotaz, který generuje sekvenci skupin, je nutné použít vnořený `foreach` smyčky. Vnější smyčka iteruje jednotlivé skupiny a vnitřní smyčku iteruje jednotlivých členů.  
  
 Pokud musíte odkazovat na výsledky operace skupiny, můžete použít `into` – klíčové slovo vytvořit identifikátor, který může být dotázán dále. Následující dotaz vrátí pouze skupiny, které obsahují více než dvěma zákazníkům:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Spojování  
 Operace spojení vytvořte přidružení mezi sekvencí, které nejsou explicitně namodelovanou v datových zdrojů. Například můžete provést připojení k najít všechny zákazníky a distributory, kteří mají stejné umístění. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` klauzule vždy funguje s kolekcí objektů místo databázových tabulek přímo.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] není nutné používat `join` tak často, jak máte v SQL, protože cizí klíče v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jsou reprezentovány v objektovém modelu ve formě vlastnosti, které obsahují kolekci položek. Například `Customer` objekt obsahuje kolekci `Order` objekty. Místo provedení spojení, přistupovat pomocí zápisu s tečkou objednávky:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Další informace najdete v tématu [klauzule join](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Výběr (projekce)  
 `select` Klauzule produkuje výsledky dotazu a určuje "tvar" nebo typ jednotlivých prvků vrácených. Například můžete určit, zda vaše výsledky se skládají z kompletní `Customer` objekty, jenom jeden člen, podmnožinu členů nebo typ úplně jiné výsledky na základě výpočtu nebo vytvoření nového objektu. Když `select` klauzule vytváří něco jiného než kopii zdrojového elementu, operace se nazývá *projekce*. Použití projekce k transformaci dat je vynikající funkcí služby [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) a [klauzule select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [Návod: Zápis dotazů vC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Klíčová slova dotazu (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
- [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
