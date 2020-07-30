---
title: When – kontextové klíčové slovo – Reference jazyka C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 2b041ca3a821f45dd63ce3f6bee7a920eb495651
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426992"
---
# <a name="when-c-reference"></a><span data-ttu-id="0130c-102">When (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0130c-102">when (C# Reference)</span></span>

<span data-ttu-id="0130c-103">Pomocí `when` klíčového slova kontext můžete určit podmínku filtru v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="0130c-103">You can use the `when` contextual keyword to specify a filter condition in the following contexts:</span></span>

- <span data-ttu-id="0130c-104">V `catch` příkazu pro blok [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="0130c-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="0130c-105">V `case` popisku příkazu [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="0130c-105">In the `case` label of a [switch](switch.md) statement.</span></span>
- <span data-ttu-id="0130c-106">Ve [ `switch` výrazu](../operators/switch-expression.md).</span><span class="sxs-lookup"><span data-stu-id="0130c-106">In the [`switch` expression](../operators/switch-expression.md).</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="0130c-107">`when`v `catch` příkazu</span><span class="sxs-lookup"><span data-stu-id="0130c-107">`when` in a `catch` statement</span></span>

<span data-ttu-id="0130c-108">Počínaje jazykem C# 6 `when` lze použít v `catch` příkazu k určení podmínky, která musí být pravdivá pro obslužnou rutinu pro spuštění konkrétní výjimky.</span><span class="sxs-lookup"><span data-stu-id="0130c-108">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="0130c-109">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="0130c-109">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="0130c-110">kde *expr* je výraz, který je vyhodnocen jako logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="0130c-110">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="0130c-111">Pokud se vrátí `true` , spustí se obslužná rutina výjimky, pokud `false` není.</span><span class="sxs-lookup"><span data-stu-id="0130c-111">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="0130c-112">Následující příklad používá `when` klíčové slovo k podmíněnému provedení obslužných rutin pro <xref:System.Net.Http.HttpRequestException> v závislosti na textu zprávy o výjimce.</span><span class="sxs-lookup"><span data-stu-id="0130c-112">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="0130c-113">`when`v `switch` příkazu</span><span class="sxs-lookup"><span data-stu-id="0130c-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="0130c-114">Počínaje jazykem C# 7,0 `case` popisky již nemusejí být vzájemně exkluzivní a pořadí, ve kterém `case` se popisky zobrazí v `switch` příkazu, mohou určit, který blok přepínače se spustí.</span><span class="sxs-lookup"><span data-stu-id="0130c-114">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="0130c-115">`when`Klíčové slovo lze použít k určení podmínky filtru, která způsobí, že popisek jeho přidruženého případu bude platit pouze v případě, že je podmínka filtru pravdivá.</span><span class="sxs-lookup"><span data-stu-id="0130c-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="0130c-116">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="0130c-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="0130c-117">kde *expr* je konstanta vzoru nebo typu, která je porovnána s výrazem Match, a *Podmínka when* je libovolný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="0130c-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="0130c-118">Následující příklad používá `when` klíčové slovo pro otestování `Shape` objektů, které mají oblast nula, a také pro testování nejrůznějších `Shape` objektů, které mají oblast větší než nula.</span><span class="sxs-lookup"><span data-stu-id="0130c-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="0130c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0130c-119">See also</span></span>

- [<span data-ttu-id="0130c-120">switch – příkaz</span><span class="sxs-lookup"><span data-stu-id="0130c-120">switch statement</span></span>](switch.md)
- [<span data-ttu-id="0130c-121">try/catch – příkaz</span><span class="sxs-lookup"><span data-stu-id="0130c-121">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="0130c-122">try/catch/finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="0130c-122">try/catch/finally statement</span></span>](try-catch-finally.md)
