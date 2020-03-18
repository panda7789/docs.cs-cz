---
title: Vrácení dotazu z metody
description: Jak vrátit dotaz.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972512"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="f30a4-103">Jak vrátit dotaz z metody (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="f30a4-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="f30a4-104">Tento příklad ukazuje, jak vrátit dotaz z metody jako `out` vrácená hodnota a jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f30a4-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="f30a4-105">Objekty dotazu jsou kompozitelné, což znamená, že můžete vrátit dotaz z metody.</span><span class="sxs-lookup"><span data-stu-id="f30a4-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="f30a4-106">Objekty, které představují dotazy neukládají výsledné kolekce, ale spíše kroky k vytvoření výsledků v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="f30a4-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="f30a4-107">Výhodou vrácení objektů dotazu z metod je, že mohou být dále složeny nebo změněny.</span><span class="sxs-lookup"><span data-stu-id="f30a4-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="f30a4-108">Proto všechny vrácené hodnoty nebo `out` parametr metody, která vrací dotaz musí mít také tento typ.</span><span class="sxs-lookup"><span data-stu-id="f30a4-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="f30a4-109">Pokud metoda zhmotní dotaz do <xref:System.Collections.Generic.List%601> konkrétní <xref:System.Array> nebo typ, je považován za vrácení výsledků dotazu namísto samotného dotazu.</span><span class="sxs-lookup"><span data-stu-id="f30a4-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="f30a4-110">Proměnná dotazu, která je vrácena z metody, může být stále složena nebo změněna.</span><span class="sxs-lookup"><span data-stu-id="f30a4-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f30a4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f30a4-111">Example</span></span>  
 <span data-ttu-id="f30a4-112">V následujícím příkladu první metoda vrátí dotaz jako vrácenou hodnotu a `out` druhá metoda vrátí dotaz jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f30a4-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="f30a4-113">Všimněte si, že v obou případech se jedná o dotaz, který je vrácen, nikoli výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="f30a4-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="f30a4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f30a4-114">See also</span></span>

- [<span data-ttu-id="f30a4-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="f30a4-115">Language Integrated Query (LINQ)</span></span>](index.md)
