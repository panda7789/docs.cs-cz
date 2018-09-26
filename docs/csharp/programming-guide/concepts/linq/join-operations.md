---
title: Připojte se k operace (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: f03d5cf14525a6d23240747c2f377348bf608782
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193054"
---
# <a name="join-operations-c"></a>Připojte se k operace (C#)
A *spojení* dva zdroje dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.  
  
 Připojení je důležité operace v dotazech, které se zaměřují zdroje dat, jejichž vztahy mezi sebou nemůže následovat přímo. V objektově orientované programování, to může znamenat korelace mezi objekty, které není modelovat, jako zpětně směr jednosměrná relace. Příklad jednosměrná relace je třída zákazníka, který má vlastnost typu Město, ale třída město nemá vlastnost, která je na kolekci objektů zákazníka. Pokud máte seznam objektů, Město a chcete najít všechny zákazníky v každé město, můžete použít operaci join je vyhledat.  
  
 Jsou metody join k dispozici v rámci LINQ <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provádět equijoins nebo spojení, které odpovídají dvou zdrojů dat založených na rovnost hodnoty jejich klíče. (Pro porovnání, příkazů jazyka Transact-SQL podporuje operátory spojení než "je rovno", například "je menší než" operátor.) Relační databáze řečeno <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení v které se vrátí pouze ty objekty, které mají shoda v datové sadě. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda nemá žádný ekvivalent s přímým přístupem v podmínkách relační databáze, ale implementuje nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že ho v jiném zdroji dat nemá žádné korelační elementy.  
  
 Na následujícím obrázku ukazují konceptuální zobrazení dvou sad a elementů v rámci těchto sad, které jsou součástí vnitřní spojení a levé vnější spojení.  
  
 ![Dvě překrývající se kruhy zobrazující vnitřní&#47;vnější. ](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Spojení dvou sekvencí založené na funkcích selektoru klíče a extrahuje dvojice hodnot.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dva pořadí na základě funkcí selektoru klíče a výsledné shody pro každý prvek skupiny.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Formulování spojení a dotazů napříč produkty](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
- [join – klauzule](../../../../csharp/language-reference/keywords/join-clause.md)  
- [Postupy: spojení pomocí složených klíčů](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
- [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
- [Postupy: řazení výsledků Klauzule Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
- [Postupy: provádění vlastních operací spojování](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
- [Postupy: provádění seskupených spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
- [Postupy: provádění vnitřních spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
- [Postupy: provedení levých vnějších spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
- [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
