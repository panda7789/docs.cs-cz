---
title: Operace sjednocení
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: b09574369185be13664276c2e84697fc4969c6f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353297"
---
# <a name="join-operations-visual-basic"></a>Operace join (Visual Basic)
*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 Spojování je důležitou operací v dotazech, které cílí na zdroje dat, u kterých vzájemně vztazích nemůžete přímo následovat. V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace. Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů. Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.  
  
 Metody join poskytované v rozhraní LINQ Framework jsou <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů. (Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V rámci podmínek relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, což je typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.  
  
 Následující ilustrace znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď pomocí vnitřního spojení, nebo levého vnějšího spojení.  
  
 ![Dva překrývající se kružnice ukazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Visual Basic syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Spojit|Spojí dvě sekvence na základě funkcí selektoru klíčů a extrahuje páry hodnot.|`From x In …, y In … Where x.a = y.a`<br /><br /> -nebo-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dvě sekvence na základě funkcí selektoru klíčů a seskupí výsledné shody pro každý prvek.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Formulování spojení a dotazů napříč produkty](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Postupy: spojení obsahu z nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)
- [Postupy: naplnění kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
