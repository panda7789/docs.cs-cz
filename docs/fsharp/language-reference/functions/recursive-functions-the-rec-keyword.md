---
title: 'Rekurzivní funkce: Klíčové slovo rec (F#)'
description: "Zjistěte, jak se používá F # 'rec' – klíčové slovo se – klíčové slovo 'let' Definice rekurzivní funkce."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1f5302c125605d2186deab0bbeaf2e84cc51edc3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="3d720-103">Rekurzivní funkce: Klíčové slovo rec</span><span class="sxs-lookup"><span data-stu-id="3d720-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="3d720-104">`rec` – Klíčové slovo je použít v kombinaci s `let` – klíčové slovo definice rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="3d720-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="3d720-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d720-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="3d720-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d720-106">Remarks</span></span>
<span data-ttu-id="3d720-107">Rekurzivní funkce, funkce, které se označují, jsou identifikovány explicitně v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="3d720-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="3d720-108">To zpřístupňuje identifikátor, který je definovaný v oboru funkce.</span><span class="sxs-lookup"><span data-stu-id="3d720-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="3d720-109">Následující kód ukazuje rekurzivní funkci, která vypočítá *n*tý Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="3d720-109">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="3d720-110">V praxi jako je například výše uvedený kód je plýtvání paměti a procesoru času, protože se týká recomputation dříve počítaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="3d720-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="3d720-111">Metody jsou implicitně rekurzivní v rámci typu; je nutné přidat `rec` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3d720-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="3d720-112">Umožňují vazby v rámci třídy nejsou implicitně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="3d720-112">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="3d720-113">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="3d720-113">Mutually Recursive Functions</span></span>
<span data-ttu-id="3d720-114">V některých případech se funkce *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jeden funkce volá jiné, které volá první, s libovolný počet volání v rozmezí.</span><span class="sxs-lookup"><span data-stu-id="3d720-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="3d720-115">Je nutné definovat takové funkce společně do jedné `let` vazby, pomocí `and` – klíčové slovo je propojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="3d720-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="3d720-116">Následující příklad ukazuje dva vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="3d720-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="3d720-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d720-117">See Also</span></span>
[<span data-ttu-id="3d720-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="3d720-118">Functions</span></span>](index.md)
