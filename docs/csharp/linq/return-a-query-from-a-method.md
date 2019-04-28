---
title: Vrácení dotazu z metody
description: Postup vrácení dotazu.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: fe2192a3edb683d7284ffae3b66cb9f70e8854b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659823"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="45067-103">Postupy: Vrácení dotazu z metody (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="45067-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="45067-104">Tento příklad ukazuje, jak jako návratovou hodnotu a vrácení dotazu z metody `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="45067-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="45067-105">Dotaz objekty jsou složení, což znamená, že jste vrácení dotazu z metody.</span><span class="sxs-lookup"><span data-stu-id="45067-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="45067-106">Objekty, které zastupují dotaz neukládejte výsledný kolekce, ale spíše kroky pro vytvoření výsledku v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="45067-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="45067-107">Výhodou vrací objekty dotazu z metody je, že můžou být další skládá nebo upravit.</span><span class="sxs-lookup"><span data-stu-id="45067-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="45067-108">Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí mít také tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="45067-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="45067-109">Pokud bude metoda realizována dotaz do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typ, považuje se vracejí výsledky dotazu namísto samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="45067-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="45067-110">Proměnné dotazu, který je vrácen z metody lze stále skládá nebo upravit.</span><span class="sxs-lookup"><span data-stu-id="45067-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45067-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="45067-111">Example</span></span>  
 <span data-ttu-id="45067-112">V následujícím příkladu první metoda vrací dotaz jako návratovou hodnotu a druhá metoda vrací dotaz jako `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="45067-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="45067-113">Všimněte si, že v obou případech se dotaz, který je vrácen, nejsou výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="45067-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="45067-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45067-114">See also</span></span>

- [<span data-ttu-id="45067-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="45067-115">Language Integrated Query (LINQ)</span></span>](index.md)
