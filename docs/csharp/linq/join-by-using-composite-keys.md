---
title: Spojení pomocí složených klíčů (LINQ v JAZYKU C#)
description: Zjistěte, jak spojení pomocí složených klíčů v technologii LINQ.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 742338c01746966170551693e8c6b00b964446b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668610"
---
# <a name="join-by-using-composite-keys"></a>Spojení pomocí složených klíčů

Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody. To se provádí pomocí složený klíč. Vytvoření složeného klíče jako anonymního typu nebo s názvem typu hodnotami, které chcete porovnat. Pokud proměnná dotazu se předají přes hranice metody, pomocí pojmenovaného typu, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> klíče. Názvy vlastností a pořadí, ve kterém k nim dojde, musí být identické v každý klíč.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat složený klíč k připojení dat ze třech tabulkách:

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

Odvození typu na složených klíčích závisí na názvy vlastností v klíči a pořadí, ve kterém k nim dojde. Pokud vlastnosti ve zdrojových posloupností nemají stejné názvy, je nutné přiřadit nové názvy v klíčích. Například pokud `Orders` tabulky a `OrderDetails` tabulka každá používá jiné názvy pro jejich sloupců, můžete vytvořit složených klíčů tak, že přiřadíte stejné názvy v anonymních typů:

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Složené klíče můžete také použít v `group` klauzuli.

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
- [join – klauzule](../language-reference/keywords/join-clause.md)
- [group – klauzule](../language-reference/keywords/group-clause.md)
