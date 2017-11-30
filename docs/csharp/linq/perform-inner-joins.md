---
title: "Provádění vnitřních spojení"
description: "Postup provádění vnitřních spojení."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: fdf75c0b7195742bdce70566ebb3880bb0565f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-inner-joins"></a>Provádění vnitřních spojení

V podmínkách relační databáze *vnitřní spojení* vytváří je sada výsledků dotazu, ve kterém každého prvku první kolekce se zobrazí jednou pro každý odpovídající element v druhé kolekci. Pokud element v první kolekce nemá žádné odpovídající prvky, nezobrazí se v sadě výsledků dotazu. <xref:System.Linq.Enumerable.Join%2A> Metodu, která je volána metodou `join` klauzule v jazyce C#, implementuje vnitřní spojení.  
  
 Toto téma ukazuje, jak provést čtyři variace vnitřní spojení:  
  
-   Jednoduché vnitřní spojení, které koreluje elementy ze dvou zdrojů dat na základě jednoduché klíče.  
  
-   Vnitřní spojení, které koreluje elementy ze dvou zdrojů dat na základě *složené* klíč. Složený klíč, který je klíč, který se skládá z více než jednu hodnotu, umožňuje korelovat prvky založené na více než jednu vlastnost.  
  
-   A *více spojení* v které následných spojení jsou operace přidat k sobě navzájem.  
  
-   Vnitřní spojení, které je implementována pomocí spojení skupiny.  
  
## <a name="example"></a>Příklad  
  
## <a name="simple-key-join-example"></a>Příklad jednoduchého klíče připojení  
 Následující příklad vytvoří dvě kolekce, které obsahují objekty dvou uživatelem definované typy `Person` a `Pet`. Dotaz používá `join` klauzule v jazyce C# tak, aby odpovídaly `Person` objekty s `Pet` objekty, jehož `Owner` je, že `Person`. `select` Klauzule v jazyce C# definuje, jak bude vypadat výsledných objektech. V tomto příkladu jsou výsledných objektech anonymní typy, které se skládají z vlastníka křestní jméno a název pet.  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 Všimněte si, že `Person` objekt, jehož `LastName` je "Huff" v sadě výsledků, protože je nezobrazí žádné `Pet` objekt, který má `Pet.Owner` rovnající se `Person`.  
  
## <a name="example"></a>Příklad  
  
## <a name="composite-key-join-example"></a>Příklad složeného klíče připojení  
 Místo korelace prvky založené na právě jednu vlastnost, můžete porovnat elementy na víc vlastností na základě složený klíč. Chcete-li to provést, zadejte funkci selektoru klíče pro každou kolekci vrátit anonymní typ, který se skládá z vlastnosti, které chcete porovnat. Pokud můžete označit vlastnosti, musí mít stejný popisek v anonymního typu každý klíč. Vlastnosti musí být také ve stejném pořadí.  
  
 Následující příklad používá seznam `Employee` objekty a seznam `Student` objekty, které chcete určit, které zaměstnanci jsou také studenty. Mají obě tyto typy `FirstName` a `LastName` vlastnost typu <xref:System.String>. Vrátí instanci anonymního typu, který se skládá z funkcí, které vytvoří připojení k klíče z každé seznamu elementů `FirstName` a `LastName` vlastnosti každého prvku. Operace spojení porovná tyto složené klíče rovnosti a vrátí páry objektů z každého seznamu tam, kde křestní jméno a příjmení shodují.  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a>Příklad  
  
## <a name="multiple-join-example"></a>Příklad více připojení k  
 Libovolný počet operací spojování můžete připojit k jiné k provedení více připojení. Každý `join` klauzule v jazyce C# korelaci zadaný zdroj dat s výsledky předchozí spojení.  
  
 Následující příklad vytvoří tři kolekce: seznam `Person` objekty, seznam `Cat` objekty a seznam `Dog` objekty.  
  
 První `join` klauzule v jazyce C# odpovídá osoby a na základě kočky `Person` odpovídající objekt `Cat.Owner`. Vrátí posloupnost anonymní typy, které obsahují `Person` objektu a `Cat.Name`.  
  
 Druhý `join` klauzule v jazyce C# korelaci anonymní typy vrácený toto spojení s `Dog` objekty v zadaný seznam psi, podle složený klíč, který se skládá z `Owner` vlastnost typu `Person`a první písmeno názvu zvířat. Vrátí posloupnost anonymní typy, které obsahují `Cat.Name` a `Dog.Name` vlastnosti z každý odpovídající pár. Protože se jedná o vnitřní spojení, se vrátí pouze ty objekty z první zdroj dat se shodnou ve zdroji dat druhý.  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a>Příklad  
  
## <a name="inner-join-by-using-grouped-join-example"></a>Vnitřní spojení pomocí Příklad seskupených spojení  
 Následující příklad ukazuje, jak implementovat vnitřní spojení pomocí spojení skupiny.  
  
 V `query1`, seznam `Person` objekty jsou připojené do skupiny do seznamu `Pet` na základě objektů `Person` odpovídající `Pet.Owner` vlastnost. Skupiny připojení vytvoří kolekci zprostředkujících skupin, kde se skládá z každé skupiny `Person` objekt a pořadí odpovídajících `Pet` objekty.  
  
 Přidáním druhý `from` klauzule do dotazu, toto pořadí pořadí kombinaci (nebo průmětu) do jedné delší sekvence. Typ elementů konečné pořadí je zadána `select` klauzule. V tomto příkladu, že typ je anonymní typ, který se skládá z `Person.FirstName` a `Pet.Name` vlastnosti pro každý odpovídající pár.  
  
 Výsledek `query1` je ekvivalentní sadu výsledků dotazu, který by byl získán pomocí `join` klauzule bez `into` klauzule provést vnitřní spojení. `query2` Proměnná ukazuje tento ekvivalentní dotaz.  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Provádění seskupených spojení](perform-grouped-joins.md)  
 [Provedení levých vnějších spojení](perform-left-outer-joins.md)  
 [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  
 
