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
ms.locfileid: "33271211"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="95304-103">Spojení pomocí složených klíčů</span><span class="sxs-lookup"><span data-stu-id="95304-103">Join by using composite keys</span></span>

<span data-ttu-id="95304-104">Tento příklad ukazuje, jak provádět operace spojení, ve kterých chcete použít více než jeden klíč k definování shody.</span><span class="sxs-lookup"><span data-stu-id="95304-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="95304-105">Toho dosahuje pomocí složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="95304-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="95304-106">Vytváření složené klíče jako anonymní typ nebo s názvem typu hodnotami, které chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="95304-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="95304-107">Pokud napříč hranicemi metoda se předá proměnná dotaz, použít pojmenovaného typu, který přepíše <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> klíče.</span><span class="sxs-lookup"><span data-stu-id="95304-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="95304-108">Názvy vlastností a pořadí, ve kterém nastávají, musí být identický každý klíč.</span><span class="sxs-lookup"><span data-stu-id="95304-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95304-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="95304-109">Example</span></span>  
 <span data-ttu-id="95304-110">Následující příklad ukazuje, jak používat složený klíč k připojení dat z tři tabulky:</span><span class="sxs-lookup"><span data-stu-id="95304-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="95304-111">Odvození typu na složené klíče závisí na názvy vlastností v klíče a pořadí, ve kterém nastávají.</span><span class="sxs-lookup"><span data-stu-id="95304-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="95304-112">Pokud vlastnosti v pořadí zdroje nemají stejné názvy, je nutné přiřadit nové názvy v klíče.</span><span class="sxs-lookup"><span data-stu-id="95304-112">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="95304-113">Například pokud `Orders` tabulky a `OrderDetails` tabulku každý použít odlišné názvy pro jejich sloupce, můžete vytvořit složené klíče přiřazením identické názvy v anonymní typy:</span><span class="sxs-lookup"><span data-stu-id="95304-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="95304-114">Složené klíče mohou být také používány `group` klauzule.</span><span class="sxs-lookup"><span data-stu-id="95304-114">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="95304-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="95304-115">See also</span></span>  
 [<span data-ttu-id="95304-116">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="95304-116">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="95304-117">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="95304-117">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="95304-118">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="95304-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
