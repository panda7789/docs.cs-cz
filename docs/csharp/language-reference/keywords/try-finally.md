---
description: try-finally-reference jazyka C#
title: try-finally-reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141969"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="71487-103">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="71487-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="71487-104">Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v bloku [Try](try-catch.md) , a můžete kód spustit i v případě, že v bloku dojde k výjimce `try` .</span><span class="sxs-lookup"><span data-stu-id="71487-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="71487-105">Obvykle jsou příkazy `finally` bloku spouštěny, když ovládací prvek opustí `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="71487-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="71487-106">Přenos řízení může nastat v důsledku normálního spuštění, provedení `break` příkazu,, `continue` `goto` nebo `return` nebo šíření výjimky z `try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="71487-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="71487-107">V rámci ošetřené výjimky `finally` je zaručeno spuštění přidruženého bloku.</span><span class="sxs-lookup"><span data-stu-id="71487-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="71487-108">Nicméně pokud je výjimka Neošetřená, `finally` je spuštění bloku závislé na tom, jak je spuštěna operace unwind výjimky.</span><span class="sxs-lookup"><span data-stu-id="71487-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="71487-109">To znamená, že je závislý na tom, jak je počítač nastavený.</span><span class="sxs-lookup"><span data-stu-id="71487-109">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="71487-110">Obvykle, pokud Neošetřená výjimka ukončí aplikaci, bez ohledu na to, zda je `finally` blok spuštěn, není důležité.</span><span class="sxs-lookup"><span data-stu-id="71487-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="71487-111">Nicméně pokud máte příkazy v `finally` bloku, který musí být spuštěn dokonce i v takovém případě, jedním řešením je přidání `catch` bloku do `try` - `finally` příkazu.</span><span class="sxs-lookup"><span data-stu-id="71487-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="71487-112">Alternativně můžete zachytit výjimku, která může být vyvolána v `try` bloku `try` - `finally` příkazu výše v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="71487-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="71487-113">To znamená, že výjimku můžete zachytit v metodě, která volá metodu, která obsahuje `try` - `finally` příkaz, nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="71487-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="71487-114">Pokud není výjimka zachycena, spuštění `finally` bloku závisí na tom, zda se rozhodne operační systém aktivovat výjimku unwind operace.</span><span class="sxs-lookup"><span data-stu-id="71487-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="71487-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="71487-115">Example</span></span>

<span data-ttu-id="71487-116">V následujícím příkladu je neplatný příkaz převodu způsobil `System.InvalidCastException` výjimku.</span><span class="sxs-lookup"><span data-stu-id="71487-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="71487-117">Výjimka je Neošetřená.</span><span class="sxs-lookup"><span data-stu-id="71487-117">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="71487-118">V následujícím příkladu je výjimka z `TryCast` metody zachycena v metodě dále v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="71487-118">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="71487-119">Další informace o `finally` naleznete v tématu [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="71487-119">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="71487-120">Jazyk C# obsahuje také [příkaz using](using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty ve vhodné syntaxi.</span><span class="sxs-lookup"><span data-stu-id="71487-120">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="71487-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71487-121">C# language specification</span></span>

<span data-ttu-id="71487-122">Další informace naleznete v oddílu [Try příkazu](~/_csharplang/spec/statements.md#the-try-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="71487-122">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71487-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="71487-123">See also</span></span>

- [<span data-ttu-id="71487-124">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71487-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="71487-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="71487-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="71487-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71487-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="71487-127">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="71487-127">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="71487-128">throw</span><span class="sxs-lookup"><span data-stu-id="71487-128">throw</span></span>](throw.md)
- [<span data-ttu-id="71487-129">try-catch</span><span class="sxs-lookup"><span data-stu-id="71487-129">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="71487-130">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="71487-130">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
