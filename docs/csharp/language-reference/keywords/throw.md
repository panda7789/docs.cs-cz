---
title: odkaz na C# vyvolání
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713050"
---
# <a name="throw-c-reference"></a><span data-ttu-id="4516b-102">throw (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4516b-102">throw (C# Reference)</span></span>

<span data-ttu-id="4516b-103">Signalizuje výskyt výjimky během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="4516b-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4516b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4516b-104">Remarks</span></span>

<span data-ttu-id="4516b-105">Syntaxe `throw` je:</span><span class="sxs-lookup"><span data-stu-id="4516b-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="4516b-106">kde `e` je instance třídy odvozené z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4516b-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4516b-107">V následujícím příkladu se používá příkaz `throw` k vyvolání <xref:System.IndexOutOfRangeException>, pokud argument předaný metodě s názvem `GetNumber` neodpovídá platnému indexu interního pole.</span><span class="sxs-lookup"><span data-stu-id="4516b-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="4516b-108">Volající metody pak používají `try-catch` nebo `try-catch-finally` blok pro zpracování vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="4516b-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="4516b-109">Následující příklad zpracovává výjimku vyvolanou metodou `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="4516b-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="4516b-110">Opětovné vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="4516b-110">Re-throwing an exception</span></span>

<span data-ttu-id="4516b-111">`throw` lze také použít v bloku `catch` k opětovnému vyvolání výjimky, která byla zpracována v bloku `catch`.</span><span class="sxs-lookup"><span data-stu-id="4516b-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="4516b-112">V tomto případě `throw` nepřijímá operand výjimky.</span><span class="sxs-lookup"><span data-stu-id="4516b-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="4516b-113">Je nejužitečnější, pokud metoda předává argumentu od volajícího k některé jiné metodě knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu.</span><span class="sxs-lookup"><span data-stu-id="4516b-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="4516b-114">Například následující příklad znovu vyvolá <xref:System.NullReferenceException>, která je vyvolána při pokusu o načtení prvního znaku neinicializovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="4516b-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="4516b-115">Můžete také použít syntaxi `throw e` v bloku `catch` a vytvořit tak novou výjimku, kterou předáte volajícímu.</span><span class="sxs-lookup"><span data-stu-id="4516b-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="4516b-116">V tomto případě není zachováno trasování zásobníku původní výjimky, které je k dispozici z vlastnosti <xref:System.Exception.StackTrace>.</span><span class="sxs-lookup"><span data-stu-id="4516b-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="4516b-117">Výraz `throw`</span><span class="sxs-lookup"><span data-stu-id="4516b-117">The `throw` expression</span></span>

<span data-ttu-id="4516b-118">Počínaje C# 7,0 se dá `throw` použít jako výraz a také jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="4516b-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="4516b-119">To umožňuje vyvolání výjimky v kontextech, které byly dříve nepodporované.</span><span class="sxs-lookup"><span data-stu-id="4516b-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="4516b-120">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="4516b-120">These include:</span></span>

- <span data-ttu-id="4516b-121">[podmíněný operátor](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4516b-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="4516b-122">Následující příklad používá výraz `throw` k vyvolání <xref:System.ArgumentException>, pokud je metoda předána prázdnému poli řetězce.</span><span class="sxs-lookup"><span data-stu-id="4516b-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="4516b-123">Před C# 7,0 se tato logika musí objevit v příkazu `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="4516b-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="4516b-124">[operátor slučování s hodnotou null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4516b-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="4516b-125">V následujícím příkladu je použit výraz `throw` s operátorem pro sjednocení s hodnotou null, který vyvolá výjimku, pokud je řetězec přiřazený vlastnosti `Name` `null`.</span><span class="sxs-lookup"><span data-stu-id="4516b-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="4516b-126">výraz [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metoda těle.</span><span class="sxs-lookup"><span data-stu-id="4516b-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="4516b-127">Následující příklad znázorňuje metodu těle výrazu, která vyvolá <xref:System.InvalidCastException>, protože převod na <xref:System.DateTime> hodnotu není podporován.</span><span class="sxs-lookup"><span data-stu-id="4516b-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="4516b-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4516b-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4516b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4516b-129">See also</span></span>

- [<span data-ttu-id="4516b-130">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="4516b-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4516b-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4516b-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4516b-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="4516b-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="4516b-133">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4516b-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4516b-134">Postupy: Explicitní generování výjimek</span><span class="sxs-lookup"><span data-stu-id="4516b-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
