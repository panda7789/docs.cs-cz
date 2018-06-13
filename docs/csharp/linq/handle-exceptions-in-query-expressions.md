---
title: Zpracování výjimek ve výrazech dotazů
description: 'Postupy: zpracování výjimek ve výrazech dotazů.'
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 691373fabeb3934ecc454cbc3b36a5f7bf477bee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284846"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="dbcfd-103">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="dbcfd-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="dbcfd-104">Je možné volat jakékoli metody v kontextu výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-104">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="dbcfd-105">Doporučujeme však vyhnout voláním jakékoli metody ve výrazu dotazu, který může vytvářet vedlejším účinkem například změně obsahu zdroj dat nebo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="dbcfd-106">Tento příklad ukazuje, jak se vyhnout vyvolání výjimky při volání metody ve výrazu dotazu bez narušení obecné pokyny rozhraní .NET Framework na zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="dbcfd-107">Tyto pokyny stavu, který se dá zachycení určité výjimky, když je pochopit, proč bude vyvolána v daném kontextu.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-107">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="dbcfd-108">Další informace najdete v tématu [osvědčené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="dbcfd-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="dbcfd-109">Poslední příklad ukazuje, jak zpracování těchto případech, pokud musíte vyvolat výjimku během provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbcfd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbcfd-110">Example</span></span>  

 <span data-ttu-id="dbcfd-111">Následující příklad ukazuje, jak přesunout kódu mimo výraz dotazu pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="dbcfd-112">To je možné pouze, pokud metoda nezávisí na žádné proměnné, které jsou místní pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-112">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="dbcfd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbcfd-113">Example</span></span> 

 <span data-ttu-id="dbcfd-114">V některých případech může být okamžitě zabránit spuštění dotazu nejlepší odpověď na výjimku, která je vyvolána od v dotazu.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="dbcfd-115">Následující příklad ukazuje, jak zpracování výjimek, které mohou být vyvolány z uvnitř text dotazu.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="dbcfd-116">Předpokládáme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu zastavit.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="dbcfd-117">Všimněte si, že `try` uzavře bloku `foreach` smyčky a není dotaz.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="dbcfd-118">Důvodem je, že `foreach` smyčka je bod, ve kterém je ve skutečnosti spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="dbcfd-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="dbcfd-119">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="dbcfd-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="dbcfd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbcfd-120">See Also</span></span>  
 [<span data-ttu-id="dbcfd-121">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="dbcfd-121">LINQ query expressions</span></span>](index.md)
