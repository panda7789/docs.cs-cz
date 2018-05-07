---
title: Spojení pomocí složených klíčů
description: Jak spojení pomocí složených klíčů.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: e40f4d147886c07913c761bb5df83ee34d23eaba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [join – klauzule](../language-reference/keywords/join-clause.md)  
 [group – klauzule](../language-reference/keywords/group-clause.md)
