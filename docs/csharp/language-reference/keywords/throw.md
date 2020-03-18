---
title: throw - C# Reference
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399334"
---
# <a name="throw-c-reference"></a><span data-ttu-id="c925a-102">throw (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c925a-102">throw (C# Reference)</span></span>

<span data-ttu-id="c925a-103">Signalizuje výskyt výjimky během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="c925a-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c925a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c925a-104">Remarks</span></span>

<span data-ttu-id="c925a-105">Syntaxe `throw` je:</span><span class="sxs-lookup"><span data-stu-id="c925a-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="c925a-106">kde `e` je instancí třídy <xref:System.Exception?displayProperty=nameWithType>odvozené z .</span><span class="sxs-lookup"><span data-stu-id="c925a-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c925a-107">Následující příklad používá `throw` příkaz k <xref:System.IndexOutOfRangeException> vyvolání, pokud argument `GetNumber` předaný metodě s názvem neodpovídá platnému indexu vnitřního pole.</span><span class="sxs-lookup"><span data-stu-id="c925a-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="c925a-108">Metoda volající pak `try-catch` použít `try-catch-finally` nebo blok pro zpracování vyvolána výjimku.</span><span class="sxs-lookup"><span data-stu-id="c925a-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="c925a-109">Následující příklad zpracovává výjimku vyváděnou `GetNumber` metodou.</span><span class="sxs-lookup"><span data-stu-id="c925a-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="c925a-110">Opětovné vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="c925a-110">Re-throwing an exception</span></span>

<span data-ttu-id="c925a-111">`throw`lze také použít `catch` v bloku znovu vyvolat výjimku `catch` zpracovány v bloku.</span><span class="sxs-lookup"><span data-stu-id="c925a-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="c925a-112">V tomto `throw` případě nebere výjimku operand.</span><span class="sxs-lookup"><span data-stu-id="c925a-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="c925a-113">Je nejužitečnější, když metoda předá argument z volajícího na jinou metodu knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c925a-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="c925a-114">Například následující příklad znovu vyvolá, <xref:System.NullReferenceException> který je vyvolán při pokusu o načtení prvního znaku neinicializovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c925a-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="c925a-115">`throw e` Syntaxi v `catch` bloku můžete také použít k vytvoření instance nové výjimky, kterou předáte volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c925a-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="c925a-116">V tomto případě trasování zásobníku původní výjimku, <xref:System.Exception.StackTrace> která je k dispozici z vlastnosti, není zachována.</span><span class="sxs-lookup"><span data-stu-id="c925a-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="c925a-117">Výraz `throw`</span><span class="sxs-lookup"><span data-stu-id="c925a-117">The `throw` expression</span></span>

<span data-ttu-id="c925a-118">Počínaje C# 7.0, `throw` lze použít jako výraz, stejně jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="c925a-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="c925a-119">To umožňuje výjimku vyvolat v kontextech, které byly dříve nepodporované.</span><span class="sxs-lookup"><span data-stu-id="c925a-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="c925a-120">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="c925a-120">These include:</span></span>

- <span data-ttu-id="c925a-121">[podmíněný operátor](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c925a-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="c925a-122">Následující příklad používá `throw` výraz k <xref:System.ArgumentException> vyvolání metody, pokud je metoda předána prázdnému řetězci.</span><span class="sxs-lookup"><span data-stu-id="c925a-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="c925a-123">Před C# 7.0, tato logika `if` / `else` by se musel zobrazit v příkazu.</span><span class="sxs-lookup"><span data-stu-id="c925a-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="c925a-124">[operátor null-coalescing](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c925a-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="c925a-125">V následujícím příkladu `throw` se výraz používá s operátorem null-coalescing k vyvolání `null`výjimky, pokud je řetězec přiřazený vlastnosti `Name` .</span><span class="sxs-lookup"><span data-stu-id="c925a-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="c925a-126">výraz-tělesně [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="c925a-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="c925a-127">Následující příklad ilustruje metodu s výrazem, <xref:System.InvalidCastException> která vyvolá, <xref:System.DateTime> protože převod na hodnotu není podporován.</span><span class="sxs-lookup"><span data-stu-id="c925a-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="c925a-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c925a-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c925a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c925a-129">See also</span></span>

- [<span data-ttu-id="c925a-130">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c925a-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c925a-131">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c925a-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c925a-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="c925a-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="c925a-133">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c925a-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c925a-134">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="c925a-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
