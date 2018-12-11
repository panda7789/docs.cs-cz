---
title: 'Rekurzivní funkce: Klíčové slovo rec (F#)'
description: Zjistěte, jak F# – klíčové slovo "dop." pomocí klíčového slova "let" slouží k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 0db3ed7f85a1380654f2827b4773985b661589c7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127729"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="ebdf4-103">Rekurzivní funkce: Klíčové slovo rec</span><span class="sxs-lookup"><span data-stu-id="ebdf4-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="ebdf4-104">`rec` – Klíčové slovo se používá spolu s `let` – klíčové slovo do definuje rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebdf4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebdf4-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="ebdf4-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebdf4-106">Remarks</span></span>

<span data-ttu-id="ebdf4-107">Rekurzivní funkce, funkce, které volají samy, jsou uvedené v explicitně F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="ebdf4-108">Díky tomu identifikátor, který definuje dostupné v oboru funkce.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="ebdf4-109">Následující kód ukazuje rekurzivní funkci, která vypočítá *n*<sup>th</sup> Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="ebdf4-110">V praxi jako je například výše uvedený kód totiž plýtváním paměti a času procesoru zahrnuje kterémkoli dříve vypočítané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="ebdf4-111">Metody jsou implicitně rekurzivní v rámci typu; není nutné přidat `rec` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="ebdf4-112">Vazby let v rámci třídy nejsou implicitně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="ebdf4-113">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="ebdf4-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="ebdf4-114">Někdy jsou funkce *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá jinou která pak volá první, s libovolným počtem volání mezi.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="ebdf4-115">Je nutné definovat tyto funkce dohromady do jedné `let` vazba, pomocí `and` – klíčové slovo je propojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="ebdf4-116">Následující příklad ukazuje dva vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="ebdf4-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="ebdf4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebdf4-117">See also</span></span>

- [<span data-ttu-id="ebdf4-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="ebdf4-118">Functions</span></span>](index.md)
