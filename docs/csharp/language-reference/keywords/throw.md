---
description: throw – reference jazyka C#
title: throw – reference jazyka C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142034"
---
# <a name="throw-c-reference"></a><span data-ttu-id="6fb47-103">throw (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6fb47-103">throw (C# Reference)</span></span>

<span data-ttu-id="6fb47-104">Signalizuje výskyt výjimky během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="6fb47-104">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fb47-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fb47-105">Remarks</span></span>

<span data-ttu-id="6fb47-106">Syntaxe `throw` je:</span><span class="sxs-lookup"><span data-stu-id="6fb47-106">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="6fb47-107">kde `e` je instance třídy odvozené z <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6fb47-107">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6fb47-108">Následující příklad používá `throw` příkaz k vyvolání příkazu, <xref:System.IndexOutOfRangeException> Pokud argument předaný metodě s názvem neodpovídá `GetNumber` platnému indexu interního pole.</span><span class="sxs-lookup"><span data-stu-id="6fb47-108">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="6fb47-109">Volající metody pak používají `try-catch` `try-catch-finally` blok nebo pro zpracování vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="6fb47-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="6fb47-110">Následující příklad zpracovává výjimku vyvolanou `GetNumber` metodou.</span><span class="sxs-lookup"><span data-stu-id="6fb47-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="6fb47-111">Opětovné vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="6fb47-111">Re-throwing an exception</span></span>

<span data-ttu-id="6fb47-112">`throw` lze také použít v `catch` bloku k opětovnému vyvolání výjimky zpracované v `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="6fb47-112">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="6fb47-113">V tomto případě `throw` nebere v úvahu operand výjimky.</span><span class="sxs-lookup"><span data-stu-id="6fb47-113">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="6fb47-114">Je nejužitečnější, pokud metoda předává argumentu od volajícího k některé jiné metodě knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu.</span><span class="sxs-lookup"><span data-stu-id="6fb47-114">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="6fb47-115">Například následující příklad znovu vyvolá výjimku <xref:System.NullReferenceException> , která je vyvolána při pokusu o načtení prvního znaku neinicializovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="6fb47-115">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="6fb47-116">Můžete také použít `throw e` syntaxi v `catch` bloku pro vytvoření instance nové výjimky, kterou předáte volajícímu.</span><span class="sxs-lookup"><span data-stu-id="6fb47-116">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="6fb47-117">V tomto případě není zachováno trasování zásobníku původní výjimky, která je k dispozici z <xref:System.Exception.StackTrace> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6fb47-117">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="6fb47-118">`throw`Výraz</span><span class="sxs-lookup"><span data-stu-id="6fb47-118">The `throw` expression</span></span>

<span data-ttu-id="6fb47-119">Počínaje jazykem C# 7,0 `throw` lze použít jako výraz i příkaz.</span><span class="sxs-lookup"><span data-stu-id="6fb47-119">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="6fb47-120">To umožňuje vyvolání výjimky v kontextech, které byly dříve nepodporované.</span><span class="sxs-lookup"><span data-stu-id="6fb47-120">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="6fb47-121">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="6fb47-121">These include:</span></span>

- <span data-ttu-id="6fb47-122">[podmíněný operátor](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6fb47-122">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="6fb47-123">Následující příklad používá `throw` výraz k vyvolání, <xref:System.ArgumentException> Pokud je metoda předána prázdnému poli řetězce.</span><span class="sxs-lookup"><span data-stu-id="6fb47-123">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="6fb47-124">Před C# 7,0 se tato logika musí objevit v `if` / `else` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6fb47-124">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="6fb47-125">[operátor slučování s hodnotou null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6fb47-125">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="6fb47-126">V následujícím příkladu `throw` se výraz používá s operátorem pro sjednocení s hodnotou null, který vyvolá výjimku, pokud je řetězec přiřazený `Name` vlastnosti `null` .</span><span class="sxs-lookup"><span data-stu-id="6fb47-126">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="6fb47-127">výraz [lambda](../operators/lambda-expressions.md) nebo metoda těle.</span><span class="sxs-lookup"><span data-stu-id="6fb47-127">an expression-bodied [lambda](../operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="6fb47-128">Následující příklad znázorňuje metodu těle výrazu, která vyvolá výjimku, <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnotu není podporován.</span><span class="sxs-lookup"><span data-stu-id="6fb47-128">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="6fb47-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6fb47-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6fb47-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fb47-130">See also</span></span>

- [<span data-ttu-id="6fb47-131">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6fb47-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6fb47-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6fb47-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6fb47-133">try-catch</span><span class="sxs-lookup"><span data-stu-id="6fb47-133">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="6fb47-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6fb47-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6fb47-135">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="6fb47-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
