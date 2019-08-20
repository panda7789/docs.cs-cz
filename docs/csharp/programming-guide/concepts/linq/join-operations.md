---
title: Operace join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 95661e2d0d7f4f0e75c1fa1b10e1f322923189b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592078"
---
# <a name="join-operations-c"></a>Operace join (C#)
*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 Spojování je důležitou operací v dotazech, které cílí na zdroje dat, u kterých vzájemně vztazích nemůžete přímo následovat. V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace. Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů. Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.  
  
 Metody join, které jsou k dispozici v <xref:System.Linq.Enumerable.Join%2A> rozhraní <xref:System.Linq.Enumerable.GroupJoin%2A>LINQ Framework, jsou a. Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů. (Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V terminologii <xref:System.Linq.Enumerable.Join%2A> relačních databází implementuje interní spojení typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat. Tato <xref:System.Linq.Enumerable.GroupJoin%2A> metoda nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.  
  
 Následující ilustrace znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď pomocí vnitřního spojení, nebo levého vnějšího spojení.  
  
 ![Dva překrývající se kružnice ukazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Spojí dvě sekvence na základě funkcí selektoru klíčů a extrahuje páry hodnot.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dvě sekvence na základě funkcí selektoru klíčů a seskupí výsledné shody pro každý prvek.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
- [Formulování spojení a dotazů napříč produkty](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join – klauzule](../../../language-reference/keywords/join-clause.md)
- [Postupy: Připojit pomocí složených klíčů](../../linq-query-expressions/how-to-join-by-using-composite-keys.md)
- [Postupy: Spojení obsahu z nepodobných souborů (LINQ)C#()](./how-to-join-content-from-dissimilar-files-linq.md)
- [Postupy: Seřazení výsledků klauzule JOIN](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Postupy: Provádět vlastní operace spojení](../../linq-query-expressions/how-to-perform-custom-join-operations.md)
- [Postupy: Provedení seskupených spojení](../../linq-query-expressions/how-to-perform-grouped-joins.md)
- [Postupy: Provést vnitřní spojení](../../linq-query-expressions/how-to-perform-inner-joins.md)
- [Postupy: Provést levá vnější spojení](../../linq-query-expressions/how-to-perform-left-outer-joins.md)
- [Postupy: Naplnit kolekce objektů z více zdrojů (LINQ)C#()](./how-to-populate-object-collections-from-multiple-sources-linq.md)
