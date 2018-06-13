---
title: try-finally (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 696eb531fe3e340f7fe0ae12483648119cf5a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288291"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="d566f-102">try-finally (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d566f-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="d566f-103">Pomocí `finally` blok, můžete vyčistit všechny prostředky, které jsou přiděleny v [zkuste](../../../csharp/language-reference/keywords/try-catch.md) blok a kód můžete spustit i v případě, že dojde k výjimce v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="d566f-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="d566f-104">Obvykle prohlášení o `finally` bloku spustit, když opustí řízení `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d566f-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="d566f-105">Přenos řízení může nastat v důsledku normální spuštění, spuštění `break`, `continue`, `goto`, nebo `return` prohlášení, nebo propagace výjimku z `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d566f-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="d566f-106">V rámci zpracování výjimek, přidruženého `finally` bloku záruku, že chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="d566f-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="d566f-107">Ale pokud neošetřená výjimka, provádění `finally` blok je závislá na jak výjimka unwind operace se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="d566f-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="d566f-108">Pak je závislá na nastavení počítače.</span><span class="sxs-lookup"><span data-stu-id="d566f-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="d566f-109">Obvykle při k neošetřené výjimce ukončení aplikace, zda `finally` bloku běží, není důležité.</span><span class="sxs-lookup"><span data-stu-id="d566f-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="d566f-110">Ale pokud máte příkazy ve `finally` blok, který se musí spustit i v takovém případě jedno řešení je přidání `catch` zablokujte `try` - `finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d566f-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="d566f-111">Alternativně můžete zachytit výjimku, která může být vyvolána v `try` blokovat z `try` - `finally` příkaz vyšší zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="d566f-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="d566f-112">To znamená, můžete zachytit výjimka v metodě, která volá metodu, která obsahuje `try` - `finally` prohlášení, nebo v metodu, která volá tuto metodu, nebo v jakékoli metody v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="d566f-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="d566f-113">Pokud není výjimka zachycena, provádění `finally` bloku závisí na tom, jestli operační systém rozhodne pro spuštění výjimky unwind operace.</span><span class="sxs-lookup"><span data-stu-id="d566f-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d566f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d566f-114">Example</span></span>  
 <span data-ttu-id="d566f-115">V následujícím příkladu příkazu Neplatný převod způsobí, že `System.InvalidCastException` výjimka.</span><span class="sxs-lookup"><span data-stu-id="d566f-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="d566f-116">Neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="d566f-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="d566f-117">V následujícím příkladu, výjimku z `TryCast` metoda je místo zachycení metoda dále zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="d566f-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="d566f-118">Další informace o `finally`, najdete v části [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="d566f-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="d566f-119">C# obsahuje také [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty v vhodné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="d566f-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d566f-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d566f-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d566f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d566f-121">See Also</span></span>  
 [<span data-ttu-id="d566f-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d566f-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d566f-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d566f-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d566f-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d566f-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d566f-125">try, throw a catch – příkazy (C++)</span><span class="sxs-lookup"><span data-stu-id="d566f-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="d566f-126">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d566f-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="d566f-127">throw</span><span class="sxs-lookup"><span data-stu-id="d566f-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="d566f-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="d566f-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="d566f-129">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="d566f-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
