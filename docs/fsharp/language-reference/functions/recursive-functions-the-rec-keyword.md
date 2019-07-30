---
title: 'Rekurzivní funkce: Klíčové slovo REC'
description: Zjistěte, F# jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630654"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="e5277-103">Rekurzivní funkce: Klíčové slovo REC</span><span class="sxs-lookup"><span data-stu-id="e5277-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="e5277-104">Klíčové slovo se používá společně `let` s klíčovým slovem k definování rekurzivní funkce. `rec`</span><span class="sxs-lookup"><span data-stu-id="e5277-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5277-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5277-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="e5277-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5277-106">Remarks</span></span>

<span data-ttu-id="e5277-107">Rekurzivní funkce, funkce, které volají samy sebe, jsou identifikovány F# explicitně v jazyce.</span><span class="sxs-lookup"><span data-stu-id="e5277-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="e5277-108">Tím se identifikátorem, které je definováno v oboru funkce.</span><span class="sxs-lookup"><span data-stu-id="e5277-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="e5277-109">Následující kód ilustruje rekurzivní funkci, která vypočítá n-<sup>tý</sup> Fibonacci číslo.</span><span class="sxs-lookup"><span data-stu-id="e5277-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="e5277-110">V praxi kód podobný výše je wasteful paměti a času procesoru, protože zahrnuje recompute dříve počítaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="e5277-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="e5277-111">Metody jsou implicitně rekurzivní v rámci typu; není nutné přidávat `rec` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e5277-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="e5277-112">Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="e5277-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="e5277-113">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="e5277-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="e5277-114">Funkce jsou někdy *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá metodu, která zavolá první, s libovolným počtem volání mezi.</span><span class="sxs-lookup"><span data-stu-id="e5277-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="e5277-115">Tyto funkce musíte definovat společně v jedné `let` vazbě `and` pomocí klíčového slova k jejich propojení.</span><span class="sxs-lookup"><span data-stu-id="e5277-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="e5277-116">Následující příklad ukazuje dvě vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="e5277-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="e5277-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5277-117">See also</span></span>

- [<span data-ttu-id="e5277-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="e5277-118">Functions</span></span>](index.md)
