---
title: Typ jednotky (F#)
description: "Zjistěte, jak je \"jednotkou\" typ F # často používané pro udržení na místě, kde hodnota je vyžadováno pomocí syntaxe jazyka žádná hodnota, je potřeba nebo požadovaných."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a><span data-ttu-id="01381-104">Typ jednotky</span><span class="sxs-lookup"><span data-stu-id="01381-104">Unit Type</span></span>

<span data-ttu-id="01381-105">`unit` Typ je typ, který ukazuje na nepřítomnost konkrétní hodnotu `unit` typ má pouze jednu hodnotu, která funguje jako zástupný znak, pokud jiná hodnota existuje nebo je potřeba.</span><span class="sxs-lookup"><span data-stu-id="01381-105">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="01381-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01381-106">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="01381-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01381-107">Remarks</span></span>
<span data-ttu-id="01381-108">Každý výraz F # musí vyhodnotit na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01381-108">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="01381-109">Pro výrazy, které nevydávají hodnotu, která je v zájmu, hodnota typu `unit` se používá.</span><span class="sxs-lookup"><span data-stu-id="01381-109">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="01381-110">`unit` Vypadá takto: typ `void` typu v jazyků, například c a C++.</span><span class="sxs-lookup"><span data-stu-id="01381-110">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="01381-111">`unit` Typ má jednu hodnotu a tato hodnota je indikován token `()`.</span><span class="sxs-lookup"><span data-stu-id="01381-111">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="01381-112">Hodnota `unit` typu se často používá v programování pro uložení na místě, kde hodnota vyžadují na syntaxi jazyka, ale v případě, že žádná hodnota, je potřeba nebo požadovaných F #.</span><span class="sxs-lookup"><span data-stu-id="01381-112">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="01381-113">Příkladem může být návratová hodnota `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="01381-113">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="01381-114">Protože důležité akce `printf` operace nastat ve funkci, funkce nemá vrátit skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01381-114">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="01381-115">Proto se vrácená hodnota je typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="01381-115">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="01381-116">Některé konstrukce očekávat `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01381-116">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="01381-117">Například `do` je očekávána vazba nebo žádný kód na nejvyšší úrovni modulu k vyhodnocení `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01381-117">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="01381-118">Kompilátor sestavy upozornění při `do` vazba nebo kódu na nejvyšší úrovni modulu vytvoří výsledek jiné než `unit` hodnotu, která se nepoužívá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="01381-118">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="01381-119">Toto upozornění je vlastnost funkční programování; nezobrazí se v jiných .NET programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="01381-119">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="01381-120">V čistě funkční programu, ve kterém funkce nemají žádné vedlejší účinky poslední vrácená hodnota je pouze výsledek volání funkce.</span><span class="sxs-lookup"><span data-stu-id="01381-120">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="01381-121">Proto když výsledek je ignorován, je možné chybě programování.</span><span class="sxs-lookup"><span data-stu-id="01381-121">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="01381-122">I když F # není plně funkční programovací jazyk, je vhodné postupovat podle funkční programovací styl, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="01381-122">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="01381-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="01381-123">See Also</span></span>
[<span data-ttu-id="01381-124">Primitivní</span><span class="sxs-lookup"><span data-stu-id="01381-124">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="01381-125">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="01381-125">F# Language Reference</span></span>](index.md)
