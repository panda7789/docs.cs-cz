---
title: Když (referenční dokumentace jazyka C#)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a71cbdce256b1c1bd5d101d66f216fb229d70adf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844901"
---
 # <a name="when-c-reference"></a><span data-ttu-id="4a96e-102">Když (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4a96e-102">when (C# Reference)</span></span>

<span data-ttu-id="4a96e-103">Můžete použít `when` kontextové klíčové slovo k určení podmínky filtru ve dvou kontextů:</span><span class="sxs-lookup"><span data-stu-id="4a96e-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="4a96e-104">V `catch` příkazem [bloku try/catch](try-catch.md) nebo [konstrukce try/catch/finally](try-catch-finally.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="4a96e-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="4a96e-105">V `case` popisek [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="4a96e-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="4a96e-106">`when` v `catch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a96e-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="4a96e-107">Od verze C# 6, `When` lze použít v `catch` příkaz a zadejte podmínku, která musí mít hodnotu true pro obslužnou rutinu pro určité výjimky k provedení.</span><span class="sxs-lookup"><span data-stu-id="4a96e-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="4a96e-108">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="4a96e-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="4a96e-109">kde *expr* je výraz, který se vyhodnocuje na logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4a96e-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="4a96e-110">Vrátí-li `true`, spustí obslužnou rutinu výjimky; Pokud `false`, tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="4a96e-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="4a96e-111">V následujícím příkladu `when` – klíčové slovo k podmíněnému spuštění obslužné rutiny pro <xref:System.Net.Http.HttpRequestException> v závislosti na text zpráva o výjimce.</span><span class="sxs-lookup"><span data-stu-id="4a96e-111">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="4a96e-112">`when` v `switch` – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a96e-112">`when` in a `switch` statement</span></span>

<span data-ttu-id="4a96e-113">Od verze C# 7.0, `case` popisky už musí být vzájemně vylučují a pořadí, ve kterém `case` popisků se zobrazí v `switch` příkazu můžete určit, které blok switch spustí.</span><span class="sxs-lookup"><span data-stu-id="4a96e-113">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="4a96e-114">`when` – Klíčové slovo lze použít k určení podmínky filtru, který způsobí, že jeho přidružené popisek případu na hodnotu true pouze v případě, že podmínka platí to i naopak.</span><span class="sxs-lookup"><span data-stu-id="4a96e-114">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="4a96e-115">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="4a96e-115">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="4a96e-116">kde *expr* je konstantní vzorek nebo vzor typu, který je ve srovnání s výrazu shody a *podmínka v případě* je libovolný výraz Boolean.</span><span class="sxs-lookup"><span data-stu-id="4a96e-116">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="4a96e-117">V následujícím příkladu `when` – klíčové slovo pro testování `Shape` objekty, které mají určitou oblast nula, stejně jako test pro širokou škálu `Shape` objekty, které mají větší než nula oblasti.</span><span class="sxs-lookup"><span data-stu-id="4a96e-117">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a><span data-ttu-id="4a96e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a96e-118">See also</span></span>

- [<span data-ttu-id="4a96e-119">Switch – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a96e-119">switch statement</span></span>](switch.md)  
- [<span data-ttu-id="4a96e-120">try/catch – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a96e-120">try/catch statement</span></span>](try-catch.md)  
- [<span data-ttu-id="4a96e-121">konstrukce try/catch/finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="4a96e-121">try/catch/finally statement</span></span>](try-catch-finally.md) 
