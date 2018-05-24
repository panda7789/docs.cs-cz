---
title: throw (Referenční dokumentace jazyka C#)
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e944f224ff9bf6dc3b8cefc293182bb79f74f2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="throw-c-reference"></a><span data-ttu-id="ace88-102">throw (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ace88-102">throw (C# Reference)</span></span>
<span data-ttu-id="ace88-103">Signály výskytem výjimku při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="ace88-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ace88-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ace88-104">Remarks</span></span>

<span data-ttu-id="ace88-105">Syntaxe `throw` je:</span><span class="sxs-lookup"><span data-stu-id="ace88-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="ace88-106">kde `e` je instance třídy odvozené od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ace88-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ace88-107">Následující příklad používá `throw` příkaz má být vyvolána <xref:System.IndexOutOfRangeException> Pokud argument předaný metodu s názvem `GetNumber` neodpovídá platný index interní pole.</span><span class="sxs-lookup"><span data-stu-id="ace88-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="ace88-108">Metoda pak volající `try-catch` nebo `try-catch-finally` bloku pro zpracování vyvolaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="ace88-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="ace88-109">Následující příklad zpracovává výjimky vyvolané `GetNumber` metoda.</span><span class="sxs-lookup"><span data-stu-id="ace88-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="ace88-110">Znovu došlo k výjimce</span><span class="sxs-lookup"><span data-stu-id="ace88-110">Re-throwing an exception</span></span>

<span data-ttu-id="ace88-111">`throw` Můžete také použít v `catch` zpracovává blok k znovu vyvolat výjimku při `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="ace88-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="ace88-112">V takovém případě `throw` nevyžaduje operand výjimka.</span><span class="sxs-lookup"><span data-stu-id="ace88-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="ace88-113">Je velmi užitečné při metodu předá na argument z volající nějaké jiné metody knihovny a knihovna metoda vyvolá výjimku, která musí být předán volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ace88-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="ace88-114">Například v následujícím příkladu je znovu vyvolá <xref:System.NullReferenceException> , je vyvolána při pokusu o načtení první znak řetězec Neinicializovaný.</span><span class="sxs-lookup"><span data-stu-id="ace88-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="ace88-115">Můžete také `throw e` syntaxi `catch` bloku se vytvořit novou výjimku, kterou předáte volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ace88-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="ace88-116">V tomto případě trasování zásobníku pro původní výjimka, která je k dispozici z <xref:System.Exception.StackTrace> vlastnost, není zachována.</span><span class="sxs-lookup"><span data-stu-id="ace88-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="ace88-117">`throw` Výraz</span><span class="sxs-lookup"><span data-stu-id="ace88-117">The `throw` expression</span></span>

<span data-ttu-id="ace88-118">Od verze jazyka C# 7.0, `throw` lze použít jako výraz, jakož i příkaz.</span><span class="sxs-lookup"><span data-stu-id="ace88-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="ace88-119">To umožňuje výjimku vyvolání v kontextu, které byly dříve nepodporovaný.</span><span class="sxs-lookup"><span data-stu-id="ace88-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="ace88-120">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="ace88-120">These include:</span></span>

- <span data-ttu-id="ace88-121">[Podmíněný operátor](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ace88-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="ace88-122">Následující příklad používá `throw` výraz, který se throw <xref:System.ArgumentException> Pokud metoda je předán prázdný řetězec pole.</span><span class="sxs-lookup"><span data-stu-id="ace88-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="ace88-123">Před C# 7.0, by potřeba se zobrazí v této logiky `if` / `else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ace88-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="ace88-124">[operátor slučování null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ace88-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="ace88-125">V následujícím příkladu `throw` výraz se používá s operátorem se slučování null vyvolá výjimku, pokud řetězec přiřazené `Name` vlastnost je `null`.</span><span class="sxs-lookup"><span data-stu-id="ace88-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="ace88-126">výrazu vozidlo [lambda](../../lambda-expressions.md) nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="ace88-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="ace88-127">Následující příklad ukazuje metodu vozidlo výrazu, která způsobí výjimku, <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnota není podporována.</span><span class="sxs-lookup"><span data-stu-id="ace88-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="ace88-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ace88-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ace88-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ace88-129">See Also</span></span>  
 [<span data-ttu-id="ace88-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ace88-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ace88-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ace88-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ace88-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="ace88-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="ace88-133">Try, catch a throw – příkazy v jazyce C++</span><span class="sxs-lookup"><span data-stu-id="ace88-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="ace88-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ace88-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ace88-135">Příkazy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="ace88-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="ace88-136">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="ace88-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
