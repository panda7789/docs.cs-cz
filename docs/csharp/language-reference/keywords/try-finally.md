---
title: try-finally - C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713011"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="a5754-102">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a5754-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="a5754-103">Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v [bloku try,](try-catch.md) a můžete spustit `try` kód i v případě, že dojde k výjimce v bloku.</span><span class="sxs-lookup"><span data-stu-id="a5754-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="a5754-104">Obvykle příkazy `finally` bloku spustit při ovládacíprvek `try` opustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="a5754-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="a5754-105">K převodu ovládacího prvku může dojít v důsledku `break` `continue`normálního spuštění, provedení , , `goto`nebo `return` příkazu `try` nebo šíření výjimky z příkazu.</span><span class="sxs-lookup"><span data-stu-id="a5754-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="a5754-106">V rámci zpracované výjimky je zaručeno spuštění přidruženého `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="a5754-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="a5754-107">Pokud je však výjimka neošetřena, je spuštění `finally` bloku závislé na způsobu, jakým je spuštěna operace unwind výjimky.</span><span class="sxs-lookup"><span data-stu-id="a5754-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="a5754-108">To zase závisí na tom, jak je počítač nastaven.</span><span class="sxs-lookup"><span data-stu-id="a5754-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="a5754-109">Obvykle při neošetřené výjimky ukončí aplikaci, zda `finally` je či není blok je spuštěn není důležité.</span><span class="sxs-lookup"><span data-stu-id="a5754-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="a5754-110">Však pokud máte příkazy v `finally` bloku, který musí být spuštěn i `catch` v `try` - `finally` této situaci, jedním z řešení je přidat blok do příkazu.</span><span class="sxs-lookup"><span data-stu-id="a5754-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="a5754-111">Alternativně můžete zachytit výjimku, která může `try` být vyvolána v bloku příkazu `try` - `finally` vyšší zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="a5754-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="a5754-112">To znamená, že můžete zachytit výjimku v metodě, která volá metodu, která obsahuje `try` - `finally` příkaz, nebo v metodě, která volá tuto metodu, nebo v libovolné metodě v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="a5754-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="a5754-113">Pokud výjimka není zachycena, `finally` spuštění bloku závisí na tom, zda se operační systém rozhodne aktivovat operaci unwind výjimky.</span><span class="sxs-lookup"><span data-stu-id="a5754-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="a5754-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5754-114">Example</span></span>

<span data-ttu-id="a5754-115">V následujícím příkladu neplatný příkaz `System.InvalidCastException` převodu způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="a5754-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="a5754-116">Výjimka není zpracována.</span><span class="sxs-lookup"><span data-stu-id="a5754-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="a5754-117">V následujícím příkladu je `TryCast` výjimka z metody zachycena v metodě dále v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="a5754-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="a5754-118">Další informace `finally`o tématu [naleznete v tématu try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="a5754-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="a5754-119">C# také obsahuje [using příkaz](using-statement.md), který <xref:System.IDisposable> poskytuje podobné funkce pro objekty ve vhodné syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a5754-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a5754-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a5754-120">C# language specification</span></span>

<span data-ttu-id="a5754-121">Další informace naleznete v části [try statement](~/_csharplang/spec/statements.md#the-try-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a5754-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5754-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5754-122">See also</span></span>

- [<span data-ttu-id="a5754-123">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a5754-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a5754-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a5754-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5754-125">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a5754-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5754-126">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="a5754-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="a5754-127">throw</span><span class="sxs-lookup"><span data-stu-id="a5754-127">throw</span></span>](throw.md)
- [<span data-ttu-id="a5754-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="a5754-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="a5754-129">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="a5754-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
