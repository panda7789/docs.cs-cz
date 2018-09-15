---
title: Připojte se k operací (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: 660b6d04e0a807a3072cff51d885999545052018
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45613940"
---
# <a name="join-operations-visual-basic"></a>Připojte se k operací (Visual Basic)
A *spojení* dva zdroje dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 Připojení je důležité operace v dotazech, které se zaměřují zdroje dat, jejichž vztahy mezi sebou nemůže následovat přímo. V objektově orientované programování, to může znamenat korelace mezi objekty, které není modelovat, jako zpětně směr jednosměrná relace. Příklad jednosměrná relace je třída zákazníka, který má vlastnost typu Město, ale třída město nemá vlastnost, která je na kolekci objektů zákazníka. Pokud máte seznam objektů, Město a chcete najít všechny zákazníky v každé město, můžete použít operaci join je vyhledat.  
  
 Jsou metody join k dispozici v rámci LINQ <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provádět equijoins nebo spojení, které odpovídají dvou zdrojů dat založených na rovnost hodnoty jejich klíče. (Pro porovnání, příkazů jazyka Transact-SQL podporuje operátory spojení než "je rovno", například "je menší než" operátor.) Relační databáze řečeno <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení v které se vrátí pouze ty objekty, které mají shoda v datové sadě. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda nemá žádný ekvivalent s přímým přístupem v podmínkách relační databáze, ale implementuje nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že ho v jiném zdroji dat nemá žádné korelační elementy.  
  
 Na následujícím obrázku ukazují konceptuální zobrazení dvou sad a elementů v rámci těchto sad, které jsou součástí vnitřní spojení a levé vnější spojení.  
  
 ![Dvě překrývající se kruhy zobrazující vnitřní&#47;vnější. ](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|Spojení dvou sekvencí založené na funkcích selektoru klíče a extrahuje dvojice hodnot.|`From x In …, y In … Where x.a = y.a`<br /><br /> -nebo-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dva pořadí na základě funkcí selektoru klíče a výsledné shody pro každý prvek skupiny.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Formulování spojení a dotazů napříč produkty](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
- [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md)  
- [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
- [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
