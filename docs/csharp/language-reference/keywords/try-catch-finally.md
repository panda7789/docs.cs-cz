---
title: try-catch-finally (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 18625838bd36d9d32079b7c72ded7ed660b8cf3a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130660"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="c8214-102">try-catch-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c8214-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="c8214-103">Společné využití `catch` a `finally` společně se získat a používat prostředky v `try` blokovat, řešil výjimečných okolností v `catch` blokovat a uvolnit tak prostředky v `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="c8214-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="c8214-104">Další informace a příklady opětném vyvolávání výjimky, naleznete v tématu [bloku try-catch](try-catch.md) a [vyvolání výjimky](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8214-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="c8214-105">Další informace o `finally` blokovat, najdete v článku [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="c8214-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="c8214-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8214-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="c8214-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8214-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c8214-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8214-108">See also</span></span>

- [<span data-ttu-id="c8214-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8214-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c8214-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c8214-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c8214-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8214-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c8214-112">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="c8214-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="c8214-113">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="c8214-113">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="c8214-114">throw</span><span class="sxs-lookup"><span data-stu-id="c8214-114">throw</span></span>](throw.md)
- [<span data-ttu-id="c8214-115">Jak: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="c8214-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="c8214-116">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="c8214-116">using Statement</span></span>](using-statement.md)