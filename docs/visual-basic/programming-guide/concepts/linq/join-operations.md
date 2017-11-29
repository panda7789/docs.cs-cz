---
title: "Připojení k operací (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ff2c466db223720edf00be91c3516c641762ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-visual-basic"></a>Připojení k operací (Visual Basic)
A *spojení* dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v jiného zdroje dat.  
  
 Připojení je důležité operace v dotazech, které cílí zdroje dat, jejichž vzájemné vztahy nelze přejít přímo. V objektově orientované programování to může znamenat korelace mezi objekty, které není modelován, jako zpětně směr jednosměrný vztah. Je například jednosměrný vztah zákazníků třídy, která má vlastnost typu města, ale třída města nemá vlastnost, která je kolekce objektů zákazníka. Pokud máte seznam objektů města a chcete najít všechny zákazníky v každé město, můžete je najít použít operace spojení.  
  
 Připojení k metody uvedené v rámci LINQ <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provedení equijoins nebo spojení, které odpovídají dvou zdrojů dat podle rovnosti jejich klíče. (Pro porovnání, Transact-SQL podporuje připojení operátory než "je rovno", například "je menší než" operátor.) V podmínkách relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení ve které se vrátí pouze ty objekty, které mají odpovídající v datové sadě. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda má ekvivalent v podmínkách relační databázi, ale implementuje nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, která vrací každý prvek první zdroje dat (levém), i když nemá žádné korelační elementy v datovém zdroji.  
  
 Následující obrázek znázorňuje koncepční zobrazení dvě sady a elementů v rámci těchto sad, které jsou součástí vnitřní spojení a levé vnější spojení.  
  
 ![Dvě překrývající se kruhy zobrazující vnitřní &#47; vnější. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|Spojí dva pořadí podle funkce selektoru klíče a extrahuje dvojice hodnot.|`From x In …, y In … Where x.a = y.a`<br /><br /> -nebo-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dva pořadí na základě funkce selektoru klíče a skupin výsledné shody pro jednotlivé elementy.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Formulovali spojení a dotazy smíšený produkt](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [JOIN – klauzule](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
