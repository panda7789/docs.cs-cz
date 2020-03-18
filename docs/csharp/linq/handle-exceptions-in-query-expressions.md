---
title: Zpracování výjimek ve výrazech dotazů (LINQ v c#)
description: Zjistěte, jak zpracovat výjimky ve výrazech dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688498"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="29080-103">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="29080-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="29080-104">Je možné volat libovolnou metodu v kontextu výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="29080-105">Doporučujeme však vyhnout se volání jakékoli metody ve výrazu dotazu, který může vytvořit vedlejší účinek, jako je například úprava obsahu zdroje dat nebo vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="29080-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="29080-106">Tento příklad ukazuje, jak se vyhnout vyvolání výjimek při volání metod ve výrazu dotazu bez porušení obecných pokynů rozhraní .NET pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="29080-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="29080-107">Tyto pokyny uvádějí, že je přijatelné zachytit konkrétní výjimku, když pochopíte, proč je vyvolána v daném kontextu.</span><span class="sxs-lookup"><span data-stu-id="29080-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="29080-108">Další informace naleznete v [tématu Doporučené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="29080-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="29080-109">Poslední příklad ukazuje, jak zpracovat tyto případy, kdy je nutné vyvolat výjimku při provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="29080-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="29080-110">Example</span></span>

<span data-ttu-id="29080-111">Následující příklad ukazuje, jak přesunout kód zpracování výjimek mimo výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="29080-112">To je možné pouze v případě, že metoda nezávisí na žádné proměnné místní dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="29080-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="29080-113">Example</span></span>

<span data-ttu-id="29080-114">V některých případech nejlepší odpověď na výjimku, která je vyvolána z v rámci dotazu může být okamžité zastavení provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="29080-115">Následující příklad ukazuje, jak zpracovat výjimky, které mohou být vyvolány z uvnitř těla dotazu.</span><span class="sxs-lookup"><span data-stu-id="29080-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="29080-116">Předpokládejme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu zastavit.</span><span class="sxs-lookup"><span data-stu-id="29080-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="29080-117">Všimněte `try` si, že `foreach` blok obklopuje smyčku a ne samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="29080-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="29080-118">Důvodem je, `foreach` že smyčka je bod, ve kterém je dotaz skutečně spuštěn.</span><span class="sxs-lookup"><span data-stu-id="29080-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="29080-119">Další informace naleznete [v tématu Úvod do linq dotazy](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="29080-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="29080-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="29080-120">See also</span></span>

- [<span data-ttu-id="29080-121">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="29080-121">Language Integrated Query (LINQ)</span></span>](index.md)
