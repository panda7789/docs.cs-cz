---
title: "Výrazy lambda: Klíčové slovo fun (F#)"
description: "Naučte se používat k definování výrazu lambda, což je anonymní funkce klíčového} zábavu\"F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="751fa-104">Výrazy lambda: Klíčové slovo fun (F#)</span><span class="sxs-lookup"><span data-stu-id="751fa-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="751fa-105">`fun` – Klíčové slovo se používá k definování výrazu lambda, který je anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="751fa-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="751fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="751fa-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="751fa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="751fa-107">Remarks</span></span>
<span data-ttu-id="751fa-108">*Seznam parametrů* se obvykle skládá z názvy a volitelně typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="751fa-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="751fa-109">Obecně platí *seznam parametrů* může být složený z jakékoli vzory F #.</span><span class="sxs-lookup"><span data-stu-id="751fa-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="751fa-110">Úplný seznam možných vzory, najdete v části [porovnávání vzorů](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="751fa-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="751fa-111">Seznam platné parametry patří následující příklady.</span><span class="sxs-lookup"><span data-stu-id="751fa-111">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="751fa-112">*Výraz* tělo funkce, poslední výraz, který generuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="751fa-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="751fa-113">Příklady výrazů lambda platný zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="751fa-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="751fa-114">Používání výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="751fa-114">Using Lambda Expressions</span></span>
<span data-ttu-id="751fa-115">Lambda – výrazy jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo jiné kolekci a chcete vyhnout další práci definice funkce.</span><span class="sxs-lookup"><span data-stu-id="751fa-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="751fa-116">Mnoho funkcí knihovny F # trvat hodnoty funkce jako argumenty, a může být obzvláště vhodnější pomocí výrazu lambda v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="751fa-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="751fa-117">Následující kód vztahuje k elementům seznamu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="751fa-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="751fa-118">V takovém případě anonymní funkce přidá 1 každý element seznamu.</span><span class="sxs-lookup"><span data-stu-id="751fa-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="751fa-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="751fa-119">See Also</span></span>
[<span data-ttu-id="751fa-120">Funkce</span><span class="sxs-lookup"><span data-stu-id="751fa-120">Functions</span></span>](index.md)
