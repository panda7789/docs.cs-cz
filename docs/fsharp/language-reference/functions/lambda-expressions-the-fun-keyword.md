---
title: 'Výrazy lambda: Klíčové slovo fun (F#)'
description: 'Naučte se používat k definování výrazu lambda, což je anonymní funkce klíčového} zábavu"F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="59a1a-103">Výrazy lambda: Klíčové slovo fun (F#)</span><span class="sxs-lookup"><span data-stu-id="59a1a-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="59a1a-104">`fun` – Klíčové slovo se používá k definování výrazu lambda, který je anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="59a1a-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="59a1a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59a1a-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="59a1a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59a1a-106">Remarks</span></span>
<span data-ttu-id="59a1a-107">*Seznam parametrů* se obvykle skládá z názvy a volitelně typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="59a1a-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="59a1a-108">Obecně platí *seznam parametrů* může být složený z jakékoli vzory F #.</span><span class="sxs-lookup"><span data-stu-id="59a1a-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="59a1a-109">Úplný seznam možných vzory, najdete v části [porovnávání vzorů](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="59a1a-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="59a1a-110">Seznam platné parametry patří následující příklady.</span><span class="sxs-lookup"><span data-stu-id="59a1a-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="59a1a-111">*Výraz* tělo funkce, poslední výraz, který generuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59a1a-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="59a1a-112">Příklady výrazů lambda platný zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="59a1a-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="59a1a-113">Používání výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="59a1a-113">Using Lambda Expressions</span></span>
<span data-ttu-id="59a1a-114">Lambda – výrazy jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo jiné kolekci a chcete vyhnout další práci definice funkce.</span><span class="sxs-lookup"><span data-stu-id="59a1a-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="59a1a-115">Mnoho funkcí knihovny F # trvat hodnoty funkce jako argumenty, a může být obzvláště vhodnější pomocí výrazu lambda v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="59a1a-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="59a1a-116">Následující kód vztahuje k elementům seznamu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="59a1a-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="59a1a-117">V takovém případě anonymní funkce přidá 1 každý element seznamu.</span><span class="sxs-lookup"><span data-stu-id="59a1a-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="59a1a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="59a1a-118">See Also</span></span>
[<span data-ttu-id="59a1a-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="59a1a-119">Functions</span></span>](index.md)
