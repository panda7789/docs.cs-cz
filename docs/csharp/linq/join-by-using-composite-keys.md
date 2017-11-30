---
title: "Spojení pomocí složených klíčů"
description: "Jak spojení pomocí složených klíčů."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a>Spojení pomocí složených klíčů

Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody. Toho dosahuje pomocí složeného klíče. Vytváření složené klíče jako anonymní typ nebo s názvem typu hodnotami, které chcete porovnat. Pokud napříč hranicemi metoda se předá proměnná dotaz, použít pojmenovaného typu, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> klíče. Názvy vlastností a pořadí, ve kterém nastávají, musí být identický každý klíč.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat složený klíč k připojení dat z tři tabulky:  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 Odvození typu na složené klíče závisí na názvy vlastností v klíče a pořadí, ve kterém nastávají. Pokud vlastnosti v pořadí zdroje nemají stejné názvy, je nutné přiřadit nové názvy v klíče. Například pokud `Orders` tabulky a `OrderDetails` tabulku každý použít odlišné názvy pro jejich sloupce, můžete vytvořit složené klíče přiřazením identické názvy v anonymní typy:  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 Složené klíče mohou být také používány `group` klauzule.  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [JOIN – klauzule](../language-reference/keywords/join-clause.md)  
 [Group – klauzule](../language-reference/keywords/group-clause.md)
