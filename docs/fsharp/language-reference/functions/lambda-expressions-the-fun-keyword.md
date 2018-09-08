---
title: 'Výrazy lambda: Klíčové slovo fun (F#)'
description: 'Další informace o použití F # "zábavu" – klíčové slovo k definování výraz lambda, který je anonymní funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141175"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="59253-103">Výrazy lambda: Klíčové slovo fun (F#)</span><span class="sxs-lookup"><span data-stu-id="59253-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="59253-104">`fun` – Klíčové slovo se používá k definování výraz lambda, to znamená, anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="59253-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="59253-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59253-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="59253-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59253-106">Remarks</span></span>

<span data-ttu-id="59253-107">*Seznam parametrů* se obvykle skládá z názvů a volitelně typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="59253-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="59253-108">Obecně platí *seznam parametrů* může skládat z jakékoli vzorky F #.</span><span class="sxs-lookup"><span data-stu-id="59253-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="59253-109">Úplný seznam možných vzory, naleznete v tématu [porovnávání vzorů](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="59253-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="59253-110">Seznam platných parametrů zahrnují následující příklady.</span><span class="sxs-lookup"><span data-stu-id="59253-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="59253-111">*Výraz* tělo funkce posledního výrazu z nich generuje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59253-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="59253-112">Příklady výrazů lambda platné patří:</span><span class="sxs-lookup"><span data-stu-id="59253-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="59253-113">Používání výrazů lambda</span><span class="sxs-lookup"><span data-stu-id="59253-113">Using Lambda Expressions</span></span>

<span data-ttu-id="59253-114">Výrazy lambda jsou zvláště užitečné, pokud chcete provádět operace v seznamu nebo z jiné kolekce a chcete se vyhnout nadbytečné práci spojené se definice funkce.</span><span class="sxs-lookup"><span data-stu-id="59253-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="59253-115">Řada funkcí knihovny F # přebírají hodnoty funkce jako argumenty a může být zvláště praktické použití lambda výrazů v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="59253-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="59253-116">Následující kód platí pro prvky seznamu výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="59253-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="59253-117">V takovém případě anonymní funkce přičte 1 k každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="59253-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="59253-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59253-118">See also</span></span>

- [<span data-ttu-id="59253-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="59253-119">Functions</span></span>](index.md)
