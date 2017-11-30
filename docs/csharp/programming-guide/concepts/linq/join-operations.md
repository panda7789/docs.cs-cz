---
title: "Připojení k operace (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 158d035985dae0d1c1daf0f276a9df7b913f2263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-c"></a>Připojení k operace (C#)
A *spojení* dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v jiného zdroje dat.  
  
 Připojení je důležité operace v dotazech, které cílí zdroje dat, jejichž vzájemné vztahy nelze přejít přímo. V objektově orientované programování to může znamenat korelace mezi objekty, které není modelován, jako zpětně směr jednosměrný vztah. Je například jednosměrný vztah zákazníků třídy, která má vlastnost typu města, ale třída města nemá vlastnost, která je kolekce objektů zákazníka. Pokud máte seznam objektů města a chcete najít všechny zákazníky v každé město, můžete je najít použít operace spojení.  
  
 Připojení k metody uvedené v rámci LINQ <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provedení equijoins nebo spojení, které odpovídají dvou zdrojů dat podle rovnosti jejich klíče. (Pro porovnání, Transact-SQL podporuje připojení operátory než "je rovno", například "je menší než" operátor.) V podmínkách relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení ve které se vrátí pouze ty objekty, které mají odpovídající v datové sadě. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda má ekvivalent v podmínkách relační databázi, ale implementuje nadmnožinou vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, která vrací každý prvek první zdroje dat (levém), i když nemá žádné korelační elementy v datovém zdroji.  
  
 Následující obrázek znázorňuje koncepční zobrazení dvě sady a elementů v rámci těchto sad, které jsou součástí vnitřní spojení a levé vnější spojení.  
  
 ![Dvě překrývající se kruhy zobrazující vnitřní &#47; vnější. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Spojí dva pořadí podle funkce selektoru klíče a extrahuje dvojice hodnot.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dva pořadí na základě funkce selektoru klíče a skupin výsledné shody pro jednotlivé elementy.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Formulovali spojení a dotazy smíšený produkt](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [JOIN – klauzule](../../../../csharp/language-reference/keywords/join-clause.md)  
 [Postupy: spojení pomocí složených klíčů](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Postupy: spojení obsahu z Nepodobných souborů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Postupy: řazení výsledků Klauzule Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Postupy: provádění vlastních operací spojování](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
 [Postupy: provádění seskupených spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Postupy: provádění vnitřních spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Postup: provedení levých vnějších spojení](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Postupy: vyplňování kolekcí objektů z více zdrojů (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
