---
title: Operace join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 456894dd07f512d7e694ad0056b1e861dc3012c5
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423382"
---
# <a name="join-operations-c"></a>Operace join (C#)
*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 Spojování je důležitou operací v dotazech, které cílí na zdroje dat, u kterých vzájemně vztazích nemůžete přímo následovat. V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace. Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů. Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.  
  
 Metody join poskytované v rozhraní LINQ Framework jsou <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů. (Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V rámci podmínek relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, což je typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.  
  
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
- [Postupy: spojení pomocí složených klíčů](../../../linq/join-by-using-composite-keys.md)
- [Postupy: spojení obsahu z nepodobných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Postupy: řazení výsledků klauzule JOIN](../../../linq/order-the-results-of-a-join-clause.md)
- [Postupy: provádění vlastních operací spojení](../../../linq/perform-custom-join-operations.md)
- [Postupy: provádění seskupených spojení](../../../linq/perform-grouped-joins.md)
- [Postupy: provádění vnitřních spojení](../../../linq/perform-inner-joins.md)
- [Postupy: provedení levých vnějších spojení](../../../linq/perform-left-outer-joins.md)
- [Postupy: naplnění kolekcí objektů z více zdrojů (LINQ)C#()](./how-to-populate-object-collections-from-multiple-sources-linq.md)
