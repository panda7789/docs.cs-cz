---
title: Spojení pomocí složených klíčů (LINQ v C#)
description: Naučte se, jak se připojit pomocí složených klíčů v LINQ.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659875"
---
# <a name="join-by-using-composite-keys"></a>Spojení pomocí složených klíčů

Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody. Toho lze dosáhnout pomocí složeného klíče. Složený klíč vytvoříte jako anonymní typ nebo s názvem s hodnotami, které chcete porovnat. Pokud proměnná dotazu bude předána přes hranice metody, použijte pojmenovaný typ, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> pro klíč. Názvy vlastností a pořadí, ve kterém se vyskytují, musí být v každém klíči identické.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak pomocí složeného klíče spojit data ze tří tabulek:

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

Odvození typu na složené klíče závisí na názvy vlastností v klíčích a pořadí, ve kterém k nim dochází. Pokud vlastnosti ve zdrojových sekvencích nemají stejné názvy, je nutné přiřadit nové názvy v klíčích. Pokud například `Orders` tabulka `OrderDetails` a tabulka používají pro své sloupce různé názvy, můžete vytvořit složené klíče přiřazením stejných názvů v anonymních typech:

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Složené klíče lze také `group` použít v klauzuli.

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
- [spojit klauzuli](../language-reference/keywords/join-clause.md)
- [group – klauzule](../language-reference/keywords/group-clause.md)
