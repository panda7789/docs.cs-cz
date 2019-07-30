---
title: 'Výrazy lambda: Klíčové slovo fun'
description: Naučte se používat F# klíčové slovo fun k definování výrazu lambda, který je anonymní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630660"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="bcf91-103">Výrazy lambda: Klíčové slovo Fun (F#)</span><span class="sxs-lookup"><span data-stu-id="bcf91-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="bcf91-104">`fun` Klíčové slovo slouží k definování výrazu lambda, tedy anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="bcf91-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="bcf91-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcf91-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="bcf91-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcf91-106">Remarks</span></span>

<span data-ttu-id="bcf91-107">*Seznam parametrů* se obvykle skládá z názvů a volitelně typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="bcf91-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="bcf91-108">Obecně platí, že *seznam parametrů* se může skládat z libovolného F# vzoru.</span><span class="sxs-lookup"><span data-stu-id="bcf91-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="bcf91-109">Úplný seznam možných vzorů naleznete v tématu [porovnávání vzorů](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="bcf91-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="bcf91-110">K seznamům platných parametrů patří následující příklady.</span><span class="sxs-lookup"><span data-stu-id="bcf91-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="bcf91-111">*Výraz* je tělo funkce, poslední výraz, který generuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bcf91-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="bcf91-112">Příklady platných výrazů lambda jsou následující:</span><span class="sxs-lookup"><span data-stu-id="bcf91-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="bcf91-113">Používání výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="bcf91-113">Using Lambda Expressions</span></span>

<span data-ttu-id="bcf91-114">Výrazy lambda jsou obzvláště užitečné, pokud chcete provádět operace na seznamu nebo jiné kolekci a chcete se vyhnout nadbytečné práci s definováním funkce.</span><span class="sxs-lookup"><span data-stu-id="bcf91-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="bcf91-115">Mnoho F# funkcí knihovny přijímá hodnoty funkcí jako argumenty a v těchto případech může být obzvláště užitečná pro použití výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="bcf91-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="bcf91-116">Následující kód použije výraz lambda na prvky seznamu.</span><span class="sxs-lookup"><span data-stu-id="bcf91-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="bcf91-117">V tomto případě anonymní funkce přidá 1 do každého prvku seznamu.</span><span class="sxs-lookup"><span data-stu-id="bcf91-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="bcf91-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcf91-118">See also</span></span>

- [<span data-ttu-id="bcf91-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="bcf91-119">Functions</span></span>](index.md)
