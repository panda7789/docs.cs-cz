---
title: Zpracování výjimek ve výrazech dotazů (LINQ v JAZYKU C#)
description: Informace o zpracování výjimek ve výrazech dotazů LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857499"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="56aa3-103">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="56aa3-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="56aa3-104">Je možné volat jakékoli metody v kontextu výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="56aa3-105">Doporučujeme však, že byste se vyhnout voláním jakékoli metody ve výrazu dotazu, můžete vytvořit vedlejší účinek, jako je například změna obsahu zdroje dat nebo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="56aa3-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="56aa3-106">Tento příklad ukazuje, jak se vyhnout vyvolání výjimky při volání metody ve výrazu dotazu, aniž by byla porušena obecné pokyny .NET pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="56aa3-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="56aa3-107">Tyto pokyny stavu, která je akceptovatelná podle zachycení konkrétní výjimky, když víte, proč je vyvolána v daném kontextu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="56aa3-108">Další informace najdete v tématu [osvědčené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="56aa3-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="56aa3-109">Poslední příklad ukazuje, jak zpracovat případy, když musíte vyvolat výjimku během provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="56aa3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="56aa3-110">Example</span></span>

<span data-ttu-id="56aa3-111">Následující příklad ukazuje, jak přesunout kód mimo výraz dotazu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="56aa3-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="56aa3-112">To je možné jenom Pokud metoda nezávisí na žádné proměnné pro dotaz místní.</span><span class="sxs-lookup"><span data-stu-id="56aa3-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="56aa3-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="56aa3-113">Example</span></span>

<span data-ttu-id="56aa3-114">V některých případech může být nejlepší odpověď na výjimku, která je vyvolána z v rámci dotazu okamžitě zastavit provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="56aa3-115">Následující příklad ukazuje, jak zpracovat výjimky, které mohou být vyvolány z uvnitř za tělem dotazu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="56aa3-116">Předpokládejme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu se zastavit.</span><span class="sxs-lookup"><span data-stu-id="56aa3-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="56aa3-117">Všimněte si, že `try` obklopuje bloku `foreach` smyčky a ne samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="56aa3-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="56aa3-118">Je to proto, `foreach` smyčky je bod, ve kterém ve skutečnosti spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="56aa3-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="56aa3-119">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="56aa3-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="56aa3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56aa3-120">See also</span></span>

- [<span data-ttu-id="56aa3-121">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="56aa3-121">Language Integrated Query (LINQ)</span></span>](index.md)
