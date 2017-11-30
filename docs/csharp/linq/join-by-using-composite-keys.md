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
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="c7f1d-104">Spojení pomocí složených klíčů</span><span class="sxs-lookup"><span data-stu-id="c7f1d-104">Join by using composite keys</span></span>

<span data-ttu-id="c7f1d-105">Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="c7f1d-106">Toho dosahuje pomocí složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="c7f1d-107">Vytváření složené klíče jako anonymní typ nebo s názvem typu hodnotami, které chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="c7f1d-108">Pokud napříč hranicemi metoda se předá proměnná dotaz, použít pojmenovaného typu, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> klíče.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="c7f1d-109">Názvy vlastností a pořadí, ve kterém nastávají, musí být identický každý klíč.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7f1d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7f1d-110">Example</span></span>  
 <span data-ttu-id="c7f1d-111">Následující příklad ukazuje, jak používat složený klíč k připojení dat z tři tabulky:</span><span class="sxs-lookup"><span data-stu-id="c7f1d-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="c7f1d-112">Odvození typu na složené klíče závisí na názvy vlastností v klíče a pořadí, ve kterém nastávají.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="c7f1d-113">Pokud vlastnosti v pořadí zdroje nemají stejné názvy, je nutné přiřadit nové názvy v klíče.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="c7f1d-114">Například pokud `Orders` tabulky a `OrderDetails` tabulku každý použít odlišné názvy pro jejich sloupce, můžete vytvořit složené klíče přiřazením identické názvy v anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="c7f1d-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="c7f1d-115">Složené klíče mohou být také používány `group` klauzule.</span><span class="sxs-lookup"><span data-stu-id="c7f1d-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c7f1d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7f1d-116">See also</span></span>  
 [<span data-ttu-id="c7f1d-117">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="c7f1d-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="c7f1d-118">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="c7f1d-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="c7f1d-119">Group – klauzule</span><span class="sxs-lookup"><span data-stu-id="c7f1d-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
