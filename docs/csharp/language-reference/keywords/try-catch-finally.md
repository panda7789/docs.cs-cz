---
title: try-catch-finally- C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 9f2c82fb140e18454491660d17b570db0a8a2aef
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168592"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="6fbef-102">try-catch-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6fbef-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="6fbef-103">`catch` Společné použití `finally` nástroje a `finally` společně je získání `try` a používání prostředků v `catch` bloku, zaznamenání mimořádných okolností v bloku a uvolnění prostředků do bloku.</span><span class="sxs-lookup"><span data-stu-id="6fbef-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="6fbef-104">Další informace a příklady pro opětovné vyvolání výjimek naleznete v tématu [try-catch](try-catch.md) and [throw Exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6fbef-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="6fbef-105">Další informace o `finally` bloku naleznete v tématu [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="6fbef-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="6fbef-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fbef-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="6fbef-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6fbef-107">C# language specification</span></span>

<span data-ttu-id="6fbef-108">Další informace naleznete v části [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6fbef-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbef-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fbef-109">See also</span></span>

- [<span data-ttu-id="6fbef-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="6fbef-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6fbef-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6fbef-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6fbef-112">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6fbef-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6fbef-113">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="6fbef-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="6fbef-114">throw</span><span class="sxs-lookup"><span data-stu-id="6fbef-114">throw</span></span>](throw.md)
- [<span data-ttu-id="6fbef-115">Postupy: Explicitně vyvolat výjimky</span><span class="sxs-lookup"><span data-stu-id="6fbef-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="6fbef-116">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="6fbef-116">using Statement</span></span>](using-statement.md)
