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
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="d7a29-103">Spojení pomocí složených klíčů</span><span class="sxs-lookup"><span data-stu-id="d7a29-103">Join by using composite keys</span></span>

<span data-ttu-id="d7a29-104">Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody.</span><span class="sxs-lookup"><span data-stu-id="d7a29-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="d7a29-105">To se provádí pomocí složený klíč.</span><span class="sxs-lookup"><span data-stu-id="d7a29-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="d7a29-106">Vytvoření složeného klíče jako anonymního typu nebo s názvem typu hodnotami, které chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="d7a29-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="d7a29-107">Pokud proměnná dotazu se předají přes hranice metody, pomocí pojmenovaného typu, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> klíče.</span><span class="sxs-lookup"><span data-stu-id="d7a29-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="d7a29-108">Názvy vlastností a pořadí, ve kterém k nim dojde, musí být identické v každý klíč.</span><span class="sxs-lookup"><span data-stu-id="d7a29-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="d7a29-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7a29-109">Example</span></span>

<span data-ttu-id="d7a29-110">Následující příklad ukazuje, jak používat složený klíč k připojení dat ze třech tabulkách:</span><span class="sxs-lookup"><span data-stu-id="d7a29-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="d7a29-111">Odvození typu na složených klíčích závisí na názvy vlastností v klíči a pořadí, ve kterém k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="d7a29-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="d7a29-112">Pokud vlastnosti ve zdrojových posloupností nemají stejné názvy, je nutné přiřadit nové názvy v klíčích.</span><span class="sxs-lookup"><span data-stu-id="d7a29-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="d7a29-113">Například pokud `Orders` tabulky a `OrderDetails` tabulka každá používá jiné názvy pro jejich sloupců, můžete vytvořit složených klíčů tak, že přiřadíte stejné názvy v anonymních typů:</span><span class="sxs-lookup"><span data-stu-id="d7a29-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="d7a29-114">Složené klíče můžete také použít v `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d7a29-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7a29-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7a29-115">See also</span></span>

- [<span data-ttu-id="d7a29-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d7a29-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d7a29-117">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="d7a29-117">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="d7a29-118">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="d7a29-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
