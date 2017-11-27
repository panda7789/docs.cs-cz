---
title: "Provedení levých vnějších spojení"
description: "Postup provedení levých vnějších spojení."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-left-outer-joins"></a>Provedení levých vnějších spojení
Levé vnější spojení je výsledkem spojení v které každý prvek první kolekce se vrátí, bez ohledu na to, jestli má všechny korelační elementy v druhé kolekci. Je možné použít k provedení levé vnější spojení voláním LINQ <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích skupiny spojení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích spojení skupiny účelem levé vnější spojení.  
  
 Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provést vnitřní spojení pomocí spojení skupiny. (Viz [provádění vnitřních spojení](perform-inner-joins.md) vysvětlení tohoto procesu.) V tomto příkladu seznam `Person` objektů je připojený k vnitřní do seznamu `Pet` na základě objektů `Person` objekt, který odpovídá `Pet.Owner`.  
  
 Druhým krokem je zahrnout každý prvek první kolekce (levém) i v případě, že element má žádné odpovídající položky v pravém kolekci sadu výsledků dotazu. To lze provést voláním <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na každé pořadí odpovídajících prvky ze skupiny spojení. V tomto příkladu <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> se volá na každé pořadí odpovídajících `Pet` objekty. Vrátí kolekci, která obsahuje jednu, výchozí hodnotu, pokud metoda pořadí odpovídajících `Pet` je prázdná pro všechny objekty `Person` objekt, a zajistí tak, aby se každý `Person` objekt je znázorněn v kolekci výsledek.  
  
> [!NOTE]
>  Výchozí hodnota pro typ odkaz je `null`; proto v příkladu vyhledává odkaz s hodnotou null před přístupem k každý prvek jednotlivých `Pet` kolekce.  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Provádění vnitřních spojení](perform-inner-joins.md)  
 [Provádění seskupených spojení](perform-grouped-joins.md)  
 [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  
 
