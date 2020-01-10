---
title: Když se odkazuje na C# kontextové klíčové slovo
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712829"
---
# <a name="when-c-reference"></a><span data-ttu-id="c5523-102">When (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c5523-102">when (C# Reference)</span></span>

<span data-ttu-id="c5523-103">Pomocí klíčového slova `when` kontextové můžete určit podmínku filtru ve dvou kontextech:</span><span class="sxs-lookup"><span data-stu-id="c5523-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="c5523-104">V příkazu `catch` bloku [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="c5523-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="c5523-105">V popisku `case` příkazu [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="c5523-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="c5523-106">`when` v příkazu `catch`</span><span class="sxs-lookup"><span data-stu-id="c5523-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="c5523-107">Počínaje C# 6 `when` lze použít v příkazu `catch` k určení podmínky, která musí být pravdivá pro obslužnou rutinu pro spuštění konkrétní výjimky.</span><span class="sxs-lookup"><span data-stu-id="c5523-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="c5523-108">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="c5523-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="c5523-109">kde *expr* je výraz, který je vyhodnocen jako logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="c5523-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="c5523-110">Pokud vrátí `true`, spustí se obslužná rutina výjimky; Pokud `false`, není.</span><span class="sxs-lookup"><span data-stu-id="c5523-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="c5523-111">Následující příklad používá klíčové slovo `when` k podmíněnému provedení obslužných rutin pro <xref:System.Net.Http.HttpRequestException> v závislosti na textu zprávy o výjimce.</span><span class="sxs-lookup"><span data-stu-id="c5523-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="c5523-112">`when` v příkazu `switch`</span><span class="sxs-lookup"><span data-stu-id="c5523-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="c5523-113">Počínaje C# 7,0 `case` popisky již nemusejí být vzájemně exkluzivní a pořadí, ve kterém `case` popisky se zobrazí v příkazu `switch`, mohou určit, který blok přepínače se spustí.</span><span class="sxs-lookup"><span data-stu-id="c5523-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="c5523-114">Klíčové slovo `when` lze použít k určení podmínky filtru, která způsobí, že popisek jeho přidruženého případu bude platit pouze v případě, že je podmínka filtru pravdivá.</span><span class="sxs-lookup"><span data-stu-id="c5523-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="c5523-115">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="c5523-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="c5523-116">kde *expr* je konstanta vzoru nebo typu, která je porovnána s výrazem Match, a *Podmínka when* je libovolný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="c5523-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="c5523-117">Následující příklad používá klíčové slovo `when` k otestování `Shape` objektů, které mají oblast nula, a také k otestování celé řady `Shape` objektů, které mají oblast větší než nula.</span><span class="sxs-lookup"><span data-stu-id="c5523-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="c5523-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5523-118">See also</span></span>

- [<span data-ttu-id="c5523-119">příkaz switch</span><span class="sxs-lookup"><span data-stu-id="c5523-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="c5523-120">try/catch – příkaz</span><span class="sxs-lookup"><span data-stu-id="c5523-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="c5523-121">try/catch/finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="c5523-121">try/catch/finally statement</span></span>](try-catch-finally.md)
