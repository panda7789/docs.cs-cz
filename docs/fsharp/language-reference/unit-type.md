---
title: Typ jednotky (F#)
description: 'Zjistěte, jak je "jednotkou" typ F # často používané pro udržení na místě, kde hodnota je vyžadováno pomocí syntaxe jazyka žádná hodnota, je potřeba nebo požadovaných.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a><span data-ttu-id="34b64-103">Typ jednotky</span><span class="sxs-lookup"><span data-stu-id="34b64-103">Unit Type</span></span>

<span data-ttu-id="34b64-104">`unit` Typ je typ, který ukazuje na nepřítomnost konkrétní hodnotu `unit` typ má pouze jednu hodnotu, která funguje jako zástupný znak, pokud jiná hodnota existuje nebo je potřeba.</span><span class="sxs-lookup"><span data-stu-id="34b64-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="34b64-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34b64-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="34b64-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34b64-106">Remarks</span></span>
<span data-ttu-id="34b64-107">Každý výraz F # musí vyhodnotit na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34b64-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="34b64-108">Pro výrazy, které nevydávají hodnotu, která je v zájmu, hodnota typu `unit` se používá.</span><span class="sxs-lookup"><span data-stu-id="34b64-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="34b64-109">`unit` Vypadá takto: typ `void` typu v jazyků, například c a C++.</span><span class="sxs-lookup"><span data-stu-id="34b64-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="34b64-110">`unit` Typ má jednu hodnotu a tato hodnota je indikován token `()`.</span><span class="sxs-lookup"><span data-stu-id="34b64-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="34b64-111">Hodnota `unit` typu se často používá v programování pro uložení na místě, kde hodnota vyžadují na syntaxi jazyka, ale v případě, že žádná hodnota, je potřeba nebo požadovaných F #.</span><span class="sxs-lookup"><span data-stu-id="34b64-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="34b64-112">Příkladem může být návratová hodnota `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="34b64-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="34b64-113">Protože důležité akce `printf` operace nastat ve funkci, funkce nemá vrátit skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34b64-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="34b64-114">Proto se vrácená hodnota je typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="34b64-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="34b64-115">Některé konstrukce očekávat `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34b64-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="34b64-116">Například `do` je očekávána vazba nebo žádný kód na nejvyšší úrovni modulu k vyhodnocení `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="34b64-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="34b64-117">Kompilátor sestavy upozornění při `do` vazba nebo kódu na nejvyšší úrovni modulu vytvoří výsledek jiné než `unit` hodnotu, která se nepoužívá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="34b64-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="34b64-118">Toto upozornění je vlastnost funkční programování; nezobrazí se v jiných .NET programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="34b64-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="34b64-119">V čistě funkční programu, ve kterém funkce nemají žádné vedlejší účinky poslední vrácená hodnota je pouze výsledek volání funkce.</span><span class="sxs-lookup"><span data-stu-id="34b64-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="34b64-120">Proto když výsledek je ignorován, je možné chybě programování.</span><span class="sxs-lookup"><span data-stu-id="34b64-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="34b64-121">I když F # není plně funkční programovací jazyk, je vhodné postupovat podle funkční programovací styl, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="34b64-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="34b64-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="34b64-122">See Also</span></span>
[<span data-ttu-id="34b64-123">Primitivní</span><span class="sxs-lookup"><span data-stu-id="34b64-123">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="34b64-124">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="34b64-124">F# Language Reference</span></span>](index.md)
