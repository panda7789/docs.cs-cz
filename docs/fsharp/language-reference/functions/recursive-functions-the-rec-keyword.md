---
title: "Rekurzivní funkce: Klíčové slovo rec (F#)"
description: "Zjistěte, jak se používá F # 'rec' – klíčové slovo se – klíčové slovo 'let' Definice rekurzivní funkce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="6bb0b-104">Rekurzivní funkce: Klíčové slovo rec</span><span class="sxs-lookup"><span data-stu-id="6bb0b-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="6bb0b-105">`rec` – Klíčové slovo je použít v kombinaci s `let` – klíčové slovo definice rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="6bb0b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb0b-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6bb0b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bb0b-107">Remarks</span></span>
<span data-ttu-id="6bb0b-108">Rekurzivní funkce, funkce, které se označují, jsou identifikovány explicitně v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="6bb0b-109">To zpřístupňuje identifikátor, který je definovaný v oboru funkce.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="6bb0b-110">Následující kód ukazuje rekurzivní funkci, která vypočítá  *n* tý Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="6bb0b-111">V praxi jako je například výše uvedený kód je plýtvání paměti a procesoru času, protože se týká recomputation dříve počítaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="6bb0b-112">Metody jsou implicitně rekurzivní v rámci typu; je nutné přidat `rec` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="6bb0b-113">Umožňují vazby v rámci třídy nejsou implicitně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="6bb0b-114">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="6bb0b-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="6bb0b-115">V některých případech se funkce *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jeden funkce volá jiné, které volá první, s libovolný počet volání v rozmezí.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="6bb0b-116">Je nutné definovat takové funkce společně do jedné `let` vazby, pomocí `and` – klíčové slovo je propojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="6bb0b-117">Následující příklad ukazuje dva vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="6bb0b-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="6bb0b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bb0b-118">See Also</span></span>
[<span data-ttu-id="6bb0b-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="6bb0b-119">Functions</span></span>](index.md)
