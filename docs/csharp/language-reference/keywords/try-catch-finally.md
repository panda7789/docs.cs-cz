---
title: try-catch-finally- C# reference
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713037"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="66ad5-102">try-catch-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="66ad5-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="66ad5-103">Běžné použití `catch` a `finally` společně je získání a používání prostředků v bloku `try`, v `catch` bloku se zabývat mimořádnými okolnostmi a uvolněte prostředky v bloku `finally`.</span><span class="sxs-lookup"><span data-stu-id="66ad5-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="66ad5-104">Další informace a příklady pro opětovné vyvolání výjimek naleznete v tématu [try-catch](try-catch.md) and [throw Exceptions](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="66ad5-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="66ad5-105">Další informace o bloku `finally` naleznete v tématu [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="66ad5-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="66ad5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="66ad5-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="66ad5-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="66ad5-107">C# language specification</span></span>

<span data-ttu-id="66ad5-108">Další informace naleznete v části [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="66ad5-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66ad5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66ad5-109">See also</span></span>

- [<span data-ttu-id="66ad5-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="66ad5-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="66ad5-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="66ad5-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="66ad5-112">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="66ad5-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="66ad5-113">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="66ad5-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="66ad5-114">throw</span><span class="sxs-lookup"><span data-stu-id="66ad5-114">throw</span></span>](throw.md)
- [<span data-ttu-id="66ad5-115">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="66ad5-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="66ad5-116">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="66ad5-116">using Statement</span></span>](using-statement.md)
