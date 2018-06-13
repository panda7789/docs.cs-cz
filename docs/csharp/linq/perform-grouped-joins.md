---
title: Provádění seskupených spojení
description: Postup provádění seskupených spojení.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288174"
---
# <a name="perform-grouped-joins"></a>Provádění seskupených spojení

Připojení skupiny jsou užitečné pro vytváření hierarchické datové struktury. Je to dvojice každý prvek z první kolekce sadu korelační elementy z druhé kolekci.  
  
 Například třídu nebo tabulku relační databáze s názvem `Student` může obsahovat dvě pole: `Id` a `Name`. Tabulku druhé třídy nebo relační databáze s názvem `Course` může obsahovat dvě pole: `StudentId` a `CourseTitle`. Skupiny připojení z těchto dvou zdrojů dat, na základě shody `Student.Id` a `Course.StudentId`, by skupiny každý `Student` s kolekcí `Course` objekty (které mohou být prázdné).  
  
> [!NOTE]
>  Každý prvek první kolekce se zobrazí v sadě výsledků dotazu spojení skupiny bez ohledu na to, jestli se nacházejí korelační elementy v druhé kolekci. V případě, kde nebyly nalezeny žádné korelační elementy je prázdný pořadí elementů korelační pro daný element. Selektor výsledek proto má přístup k každý element první kolekce. To se liší od výsledku selektoru v mimo skupinu spojení, které nelze získat přístup elementy z první kolekci, které mají žádná shoda v druhé kolekci.  
  
 V prvním příkladu v tomto tématu se dozvíte, jak provést připojení k skupiny. V druhém příkladu se dozvíte, jak vytvořit elementů XML pomocí spojení skupiny.  
  
## <a name="example"></a>Příklad  
  
### <a name="group-join-example"></a>Příklad spojení skupiny  
 Následující příklad spojí skupinu objektů typu `Person` a `Pet` na základě `Person` odpovídající `Pet.Owner` vlastnost. Na rozdíl od jiných skupiny spojení, které byste mohli vytvořit pár elementů pro každý shodu, vytvoří spojení skupiny pouze jeden výsledný objekt pro každý prvek první kolekce, která v tomto příkladu je `Person` objektu. Odpovídající elementy z druhé kolekci, které v tomto příkladu jsou `Pet` objekty, jsou seskupeny do kolekce. Nakonec funkce selektor výsledek vytvoří anonymní typ pro každý shodu, která se skládá z `Person.FirstName` a kolekce `Pet` objekty.  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>Příklad  
  
### <a name="group-join-to-create-xml-example"></a>Připojení skupiny pro vytvoření ukázkový kód XML  
 Group JOIN – klauzule jsou ideální pro vytvoření XML s použitím technologie LINQ to XML. V následujícím příkladu je podobně jako v předchozím příkladu s tím rozdílem, že místo vytvoření anonymní typy, vytvoří funkce selektor výsledek elementů XML, které představují připojených objektů.  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Provádění vnitřních spojení](perform-inner-joins.md)  
 [Provedení levých vnějších spojení](perform-left-outer-joins.md)  
 [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  
 
