---
title: try-finally- C# reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713011"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="d99d8-102">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d99d8-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="d99d8-103">Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v bloku [Try](try-catch.md) , a můžete kód spustit i v případě, že dojde k výjimce v bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="d99d8-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="d99d8-104">Příkazy `finally` bloku jsou obvykle spouštěny, když ovládací prvek opustí příkaz `try`.</span><span class="sxs-lookup"><span data-stu-id="d99d8-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="d99d8-105">Přenos řízení může nastat v důsledku normálního spuštění, spuštění `break`, `continue`, `goto`nebo `return`ho příkazu nebo šíření výjimky z příkazu `try`.</span><span class="sxs-lookup"><span data-stu-id="d99d8-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="d99d8-106">V rámci ošetřené výjimky je zaručeno spuštění přidruženého `finally`ho bloku.</span><span class="sxs-lookup"><span data-stu-id="d99d8-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="d99d8-107">Nicméně pokud je výjimka Neošetřená, spuštění bloku `finally` závisí na tom, jak je spuštěna operace unwind výjimky.</span><span class="sxs-lookup"><span data-stu-id="d99d8-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="d99d8-108">To znamená, že je závislý na tom, jak je počítač nastavený.</span><span class="sxs-lookup"><span data-stu-id="d99d8-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="d99d8-109">Obvykle, pokud Neošetřená výjimka ukončí aplikaci, bez ohledu na to, zda je spuštěn blok `finally`, není důležité.</span><span class="sxs-lookup"><span data-stu-id="d99d8-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="d99d8-110">Nicméně pokud máte příkazy v bloku `finally`, které musí být spuštěny i v takové situaci, jedním z řešení je přidání bloku `catch` do příkazu `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="d99d8-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="d99d8-111">Alternativně můžete zachytit výjimku, která může být vyvolána v `try` bloku `try`-příkazu `finally` výše v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="d99d8-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="d99d8-112">To znamená, že výjimku můžete zachytit v metodě, která volá metodu, která obsahuje příkaz `try`-`finally` nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="d99d8-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="d99d8-113">Pokud není výjimka zachycena, provedení `finally`ho bloku závisí na tom, zda se rozhodne operační systém aktivovat výjimku unwind operace.</span><span class="sxs-lookup"><span data-stu-id="d99d8-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="d99d8-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d99d8-114">Example</span></span>

<span data-ttu-id="d99d8-115">V následujícím příkladu neplatný příkaz převodu způsobí výjimku `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="d99d8-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="d99d8-116">Výjimka je Neošetřená.</span><span class="sxs-lookup"><span data-stu-id="d99d8-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="d99d8-117">V následujícím příkladu je zachycena výjimka z metody `TryCast` v metodě dále v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="d99d8-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="d99d8-118">Další informace o `finally`najdete v tématu [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="d99d8-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="d99d8-119">C#obsahuje také [příkaz using](using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty ve vhodné syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d99d8-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d99d8-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d99d8-120">C# language specification</span></span>

<span data-ttu-id="d99d8-121">Další informace naleznete v části [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d99d8-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d99d8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d99d8-122">See also</span></span>

- [<span data-ttu-id="d99d8-123">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="d99d8-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d99d8-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d99d8-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d99d8-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d99d8-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d99d8-126">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="d99d8-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="d99d8-127">throw</span><span class="sxs-lookup"><span data-stu-id="d99d8-127">throw</span></span>](throw.md)
- [<span data-ttu-id="d99d8-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="d99d8-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="d99d8-129">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="d99d8-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
