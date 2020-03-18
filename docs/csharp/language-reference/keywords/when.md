---
title: při kontextovém klíčovém slově – c# odkaz
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712829"
---
# <a name="when-c-reference"></a><span data-ttu-id="fd4f0-102">když (Odkaz jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fd4f0-102">when (C# Reference)</span></span>

<span data-ttu-id="fd4f0-103">Kontextové `when` klíčové slovo můžete použít k určení podmínky filtru ve dvou kontextech:</span><span class="sxs-lookup"><span data-stu-id="fd4f0-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="fd4f0-104">V `catch` příkazu [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) block.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="fd4f0-105">V `case` popisku [příkazu switch.](switch.md)</span><span class="sxs-lookup"><span data-stu-id="fd4f0-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="fd4f0-106">`when`v `catch` prohlášení</span><span class="sxs-lookup"><span data-stu-id="fd4f0-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="fd4f0-107">Počínaje C# 6, `when` lze použít `catch` v příkazu k určení podmínky, která musí být true pro obslužnou rutinu pro konkrétní výjimku spustit.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-107">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="fd4f0-108">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="fd4f0-108">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="fd4f0-109">kde *expr* je výraz, který je vyhodnocen jako logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="fd4f0-110">Pokud vrátí `true`, obslužná rutina výjimky se spustí; pokud `false`tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="fd4f0-111">Následující příklad používá `when` klíčové slovo podmíněně spustit <xref:System.Net.Http.HttpRequestException> obslužné rutiny pro v závislosti na textu zprávy o výjimce.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="fd4f0-112">`when`v `switch` prohlášení</span><span class="sxs-lookup"><span data-stu-id="fd4f0-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="fd4f0-113">Počínaje C# 7.0 `case` popisky již nemusí být vzájemně vylučovat a pořadí, ve kterém `case` popisky se zobrazí v příkazu `switch` můžete určit, který přepínač blok spustí.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="fd4f0-114">Klíčové `when` slovo lze použít k určení podmínky filtru, která způsobí, že jeho přidružený popisek případu bude pravdivý pouze v případě, že je splněna také podmínka filtru.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="fd4f0-115">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="fd4f0-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="fd4f0-116">kde *expr* je konstantní vzor nebo vzorek typu, který je porovnán s výrazem shody, a *když podmínka* je jakýkoli logický výraz.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="fd4f0-117">Následující příklad používá `when` klíčové slovo `Shape` k testování objektů, které mají oblast nula, `Shape` stejně jako k testování různých objektů, které mají oblast větší než nula.</span><span class="sxs-lookup"><span data-stu-id="fd4f0-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="fd4f0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd4f0-118">See also</span></span>

- [<span data-ttu-id="fd4f0-119">příkaz switch</span><span class="sxs-lookup"><span data-stu-id="fd4f0-119">switch statement</span></span>](switch.md)
- [<span data-ttu-id="fd4f0-120">try/catch prohlášení</span><span class="sxs-lookup"><span data-stu-id="fd4f0-120">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="fd4f0-121">příkaz try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="fd4f0-121">try/catch/finally statement</span></span>](try-catch-finally.md)
