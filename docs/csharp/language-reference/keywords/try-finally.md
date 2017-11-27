---
title: "try-finally (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="9db59-102">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9db59-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="9db59-103">Pomocí `finally` blok, můžete vyčistit všechny prostředky, které jsou přiděleny v [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blok a kód můžete spustit i v případě, že dojde k výjimce v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="9db59-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="9db59-104">Obvykle prohlášení o `finally` bloku spustit, když opustí řízení `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9db59-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="9db59-105">Přenos řízení může nastat v důsledku normální spuštění, spuštění `break`, `continue`, `goto`, nebo `return` prohlášení, nebo propagace výjimku z `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9db59-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="9db59-106">V rámci zpracování výjimek, přidruženého `finally` bloku záruku, že chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="9db59-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="9db59-107">Ale pokud neošetřená výjimka, provádění `finally` blok je závislá na jak výjimka unwind operace se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="9db59-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="9db59-108">Pak je závislá na nastavení počítače.</span><span class="sxs-lookup"><span data-stu-id="9db59-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="9db59-109">Obvykle při k neošetřené výjimce ukončení aplikace, zda `finally` bloku běží, není důležité.</span><span class="sxs-lookup"><span data-stu-id="9db59-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="9db59-110">Ale pokud máte příkazy ve `finally` blok, který se musí spustit i v takovém případě jedno řešení je přidání `catch` zablokujte `try` - `finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9db59-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="9db59-111">Alternativně můžete zachytit výjimku, která může být vyvolána v `try` blokovat z `try` - `finally` příkaz vyšší zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="9db59-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="9db59-112">To znamená, můžete zachytit výjimka v metodě, která volá metodu, která obsahuje `try` - `finally` prohlášení, nebo v metodu, která volá tuto metodu, nebo v jakékoli metody v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="9db59-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="9db59-113">Pokud není výjimka zachycena, provádění `finally` bloku závisí na tom, jestli operační systém rozhodne pro spuštění výjimky unwind operace.</span><span class="sxs-lookup"><span data-stu-id="9db59-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9db59-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9db59-114">Example</span></span>  
 <span data-ttu-id="9db59-115">V následujícím příkladu příkazu Neplatný převod způsobí, že `System.InvalidCastException` výjimka.</span><span class="sxs-lookup"><span data-stu-id="9db59-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="9db59-116">Neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="9db59-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="9db59-117">V následujícím příkladu, výjimku z `TryCast` metoda je místo zachycení metoda dále zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="9db59-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="9db59-118">Další informace o `finally`, najdete v části [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="9db59-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="9db59-119">C# obsahuje také [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty v vhodné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="9db59-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9db59-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9db59-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9db59-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9db59-121">See Also</span></span>  
 [<span data-ttu-id="9db59-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9db59-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9db59-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9db59-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9db59-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9db59-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9db59-125">Zkuste, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="9db59-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="9db59-126">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="9db59-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="9db59-127">throw</span><span class="sxs-lookup"><span data-stu-id="9db59-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="9db59-128">try-catch –</span><span class="sxs-lookup"><span data-stu-id="9db59-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="9db59-129">Postupy: explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="9db59-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
