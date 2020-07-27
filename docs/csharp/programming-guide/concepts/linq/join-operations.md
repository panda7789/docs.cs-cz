---
title: :::no-loc(Join):::Operace (C#)
description: Spojení dvou zdrojů dat přidruží objekty k objektům, které sdílejí atribut napříč zdroji dat. Přečtěte si informace o metodách JOIN v rozhraní LINQ Framework v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165686"
---
# <a name="no-locjoin-operations-c"></a>:::no-loc(Join):::Operace (C#)

*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 :::no-loc(Join):::důležité operace v dotazech, které cílí na zdroje dat, u kterých se vzájemně vzájemně nevztahují, nemůžou následovat přímo. V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace. Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů. Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.  
  
 Metody join, které jsou k dispozici v rozhraní LINQ Framework, jsou <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> a <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> . Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů. (Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V terminologii relačních databází <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implementuje interní spojení typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat. Tato <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> metoda nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.  
  
 Následující ilustrace znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď pomocí vnitřního spojení, nebo levého vnějšího spojení.  
  
 ![Dva překrývající se kružnice ukazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|:::no-loc(Join):::s dvě sekvence na základě funkcí selektoru klíčů a extrahují páry hodnot.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|:::no-loc(Join):::s dvě sekvence založené na funkcích selektoru klíčů a seskupují výsledné shody pro každý prvek.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů
  
### :::no-loc(Join):::  
  
Následující příklad používá `join … in … on … equals …` klauzuli pro spojení dvou sekvencí na základě konkrétní hodnoty:
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

Následující příklad používá `join … in … on … equals … into …` klauzuli pro spojení dvou sekvencí založených na konkrétní hodnotě a seskupení výsledných shod pro každý prvek:
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
- [Formulace :::no-loc(Join)::: s a dotazy na více produktů](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join – klauzule](../../../language-reference/keywords/join-clause.md)
- [:::no-loc(Join):::pomocí složených klíčů](../../../linq/join-by-using-composite-keys.md)
- [Postup připojení obsahu z nepodobných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Řazení výsledků klauzule join](../../../linq/order-the-results-of-a-join-clause.md)
- [Provádění vlastních operací spojování](../../../linq/perform-custom-join-operations.md)
- [Provádění seskupených spojení](../../../linq/perform-grouped-joins.md)
- [Provádění vnitřních spojení](../../../linq/perform-inner-joins.md)
- [Provedení levých vnějších spojení](../../../linq/perform-left-outer-joins.md)
- [Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
