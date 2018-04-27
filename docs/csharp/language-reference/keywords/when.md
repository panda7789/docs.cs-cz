---
title: Když (referenční dokumentace jazyka C#)
ms.date: 03/07/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbf150940be040a179618b6964608c8f2a72fc17
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
 # <a name="when-c-reference"></a><span data-ttu-id="45d4d-102">Když (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="45d4d-102">when (C# Reference)</span></span>

<span data-ttu-id="45d4d-103">Můžete použít `when` kontextové klíčové slovo chcete zadat podmínku filtrování do dvou kontextů:</span><span class="sxs-lookup"><span data-stu-id="45d4d-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="45d4d-104">V `catch` prohlášení o [try/catch –](try-catch.md) nebo [try/catch/finally –](try-catch-finally.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="45d4d-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="45d4d-105">V `case` popisek [přepínač](switch.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="45d4d-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="45d4d-106">`when` v `catch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="45d4d-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="45d4d-107">Od verze jazyka C# 6, `When` mohou být používány `catch` lze zadat podmínku, která musí být splněny pro obslužnou rutinu pro konkrétní výjimky k provedení.</span><span class="sxs-lookup"><span data-stu-id="45d4d-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="45d4d-108">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="45d4d-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="45d4d-109">kde *expr* je výraz, který se vyhodnotí jako logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="45d4d-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="45d4d-110">Vrátí-li `true`, zpracuje obslužná rutina výjimky; Pokud `false`, neexistuje.</span><span class="sxs-lookup"><span data-stu-id="45d4d-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="45d4d-111">Následující příklad používá `when` – klíčové slovo k podmíněnému spuštění obslužné rutiny pro <xref:System.Net.Http.HttpRequestException> v závislosti na text zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="45d4d-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="45d4d-112">`when` v `switch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="45d4d-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="45d4d-113">Od verze jazyka C# 7.0, `case` popisky už musí být vzájemně vylučují a pořadí, v jakém `case` zobrazí popisky v `switch` příkaz můžete určit, které bloku přepínačů provede.</span><span class="sxs-lookup"><span data-stu-id="45d4d-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="45d4d-114">`when` – Klíčové slovo lze použít k určení podmínku filtrování, který způsobuje její přidružené návěstí pravdivá pouze v případě, že podmínku filtrování platí taky.</span><span class="sxs-lookup"><span data-stu-id="45d4d-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="45d4d-115">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="45d4d-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="45d4d-116">kde *expr* konstantní vzor nebo typ vzor, který je ve srovnání s výrazu shody a *podmínka v případě* je libovolný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="45d4d-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="45d4d-117">Následující příklad používá `when` – klíčové slovo chcete otestovat `Shape` objekty, které mají určitou oblast nula, také tak, aby testovací pro celou řadu `Shape` objekty, které mají určitou oblast, která je větší než nula.</span><span class="sxs-lookup"><span data-stu-id="45d4d-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a><span data-ttu-id="45d4d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="45d4d-118">See also</span></span> 
  [<span data-ttu-id="45d4d-119">Switch – příkaz</span><span class="sxs-lookup"><span data-stu-id="45d4d-119">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="45d4d-120">try/catch – příkaz</span><span class="sxs-lookup"><span data-stu-id="45d4d-120">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="45d4d-121">try/catch/finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="45d4d-121">try/catch/finally statement</span></span>](try-catch-finally.md) 

