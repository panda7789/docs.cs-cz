---
title: "Zpracování výjimek ve výrazech dotazů"
description: "Postupy: zpracování výjimek ve výrazech dotazů."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="52289-104">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="52289-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="52289-105">Je možné volat jakékoli metody v kontextu výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="52289-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="52289-106">Doporučujeme však vyhnout voláním jakékoli metody ve výrazu dotazu, který může vytvářet vedlejším účinkem například změně obsahu zdroj dat nebo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="52289-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="52289-107">Tento příklad ukazuje, jak se vyhnout vyvolání výjimky při volání metody ve výrazu dotazu bez narušení obecné pokyny rozhraní .NET Framework na zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="52289-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="52289-108">Tyto pokyny stavu, který se dá zachycení určité výjimky, když je pochopit, proč bude vyvolána v daném kontextu.</span><span class="sxs-lookup"><span data-stu-id="52289-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="52289-109">Další informace najdete v tématu [osvědčené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="52289-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="52289-110">Poslední příklad ukazuje, jak zpracování těchto případech, pokud musíte vyvolat výjimku během provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="52289-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52289-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="52289-111">Example</span></span>  

 <span data-ttu-id="52289-112">Následující příklad ukazuje, jak přesunout kódu mimo výraz dotazu pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="52289-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="52289-113">To je možné pouze, pokud metoda nezávisí na žádné proměnné, které jsou místní pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="52289-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="52289-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="52289-114">Example</span></span> 

 <span data-ttu-id="52289-115">V některých případech může být okamžitě zabránit spuštění dotazu nejlepší odpověď na výjimku, která je vyvolána od v dotazu.</span><span class="sxs-lookup"><span data-stu-id="52289-115">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="52289-116">Následující příklad ukazuje, jak zpracování výjimek, které mohou být vyvolány z uvnitř text dotazu.</span><span class="sxs-lookup"><span data-stu-id="52289-116">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="52289-117">Předpokládáme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu zastavit.</span><span class="sxs-lookup"><span data-stu-id="52289-117">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="52289-118">Všimněte si, že `try` uzavře bloku `foreach` smyčky a není dotaz.</span><span class="sxs-lookup"><span data-stu-id="52289-118">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="52289-119">Důvodem je, že `foreach` smyčka je bod, ve kterém je ve skutečnosti spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="52289-119">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="52289-120">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="52289-120">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="52289-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="52289-121">See Also</span></span>  
 [<span data-ttu-id="52289-122">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="52289-122">LINQ query expressions</span></span>](index.md)
