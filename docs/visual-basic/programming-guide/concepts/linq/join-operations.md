---
title: Připojení k operací (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: 4f375946b69eadb885873889b28790730943a3d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="join-operations-visual-basic"></a>Připojení k operací (Visual Basic)
A *spojení* dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v jiného zdroje dat.  
  
 Připojení je důležité operace v dotazech, které cílí zdroje dat, jejichž vzájemné vztahy nelze přejít přímo. V objektově orientované programování to může znamenat korelace mezi objekty, které není modelován, jako zpětně směr jednosměrný vztah. Je například jednosměrný vztah zákazníků třídy, která má vlastnost typu města, ale třída města nemá vlastnost, která je kolekce objektů zákazníka. Pokud máte seznam objektů města a chcete najít všechny zákazníky v každé město, můžete je najít použít operace spojení.  
  
 Připojení k metody uvedené v rámci LINQ <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provedení equijoins nebo spojení, které odpovídají dvou zdrojů dat podle rovnosti jejich klíče. (Pro porovnání, Transact-SQL podporuje připojení operátory než "je rovno", například "je menší než" operátor.) V podmínkách relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení ve které se vrátí pouze ty objekty, které mají odpovídající v datové sadě. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda má ekvivalent v podmínkách relační databázi, ale implementuje nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, která vrací každý prvek první zdroje dat (levém), i když nemá žádné korelační elementy v datovém zdroji.  
  
 Následující obrázek znázorňuje koncepční zobrazení dvě sady a elementů v rámci těchto sad, které jsou součástí vnitřní spojení a levé vnější spojení.  
  
 ![Dvě překrývající se kruhy zobrazující vnitřní&#47;vnější. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|Spojí dva pořadí podle funkce selektoru klíče a extrahuje dvojice hodnot.|`From x In …, y In … Where x.a = y.a`<br /><br /> -nebo-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dva pořadí na základě funkce selektoru klíče a skupin výsledné shody pro jednotlivé elementy.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Formulování spojení a dotazů napříč produkty](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
