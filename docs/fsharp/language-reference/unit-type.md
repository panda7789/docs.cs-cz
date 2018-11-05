---
title: Typ jednotky (F#)
description: 'Zjistěte, jak "jednotka" typu jazyka F # se často používá k uložení na místě, kde hodnota vyžaduje syntaxi jazyka při je potřeba nebo požadovaných žádná hodnota.'
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204653"
---
# <a name="unit-type"></a><span data-ttu-id="f6a98-103">Typ jednotky</span><span class="sxs-lookup"><span data-stu-id="f6a98-103">Unit Type</span></span>

<span data-ttu-id="f6a98-104">`unit` Typ je typ, který ukazuje na nepřítomnost určitou hodnotu; `unit` typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud neexistuje žádná hodnota nebo je potřeba.</span><span class="sxs-lookup"><span data-stu-id="f6a98-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6a98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6a98-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="f6a98-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6a98-106">Remarks</span></span>

<span data-ttu-id="f6a98-107">Každý výraz F # se musí vyhodnotit na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6a98-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="f6a98-108">Pro výrazy, které nejsou generovány hodnotu, která je zapotřebí, hodnota typu `unit` se používá.</span><span class="sxs-lookup"><span data-stu-id="f6a98-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="f6a98-109">`unit` Vypadá podobně jako typ `void` typ v jazycích, jako je C# a C++.</span><span class="sxs-lookup"><span data-stu-id="f6a98-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="f6a98-110">`unit` Typ má jednu hodnotu a tuto hodnotu je indikován token `()`.</span><span class="sxs-lookup"><span data-stu-id="f6a98-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="f6a98-111">Hodnota `unit` typ se často používá v programování pro uložení místo syntaxe jazyka vyžaduje hodnotu, ale pokud žádná hodnota je potřeba nebo požadovaného F #.</span><span class="sxs-lookup"><span data-stu-id="f6a98-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="f6a98-112">Příkladem mohou být návratovou hodnotu `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6a98-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="f6a98-113">Protože důležité akce `printf` ve funkci, dojde k operaci, funkce nemusí vrátit skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6a98-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="f6a98-114">Proto, že návratová hodnota je typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="f6a98-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="f6a98-115">Očekávat některé konstrukce `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6a98-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="f6a98-116">Například `do` vazby nebo jakéhokoli kódu na nejvyšší úrovni modulu se má vyhodnotit `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6a98-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="f6a98-117">Kompilátor oznámí upozornění při `do` vazbami nebo kódem na nejvyšší úrovni modulu vytváří výsledek, než `unit` hodnotu, která se nepoužívá, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f6a98-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="f6a98-118">Toto upozornění je typické pro funkční programování. nezobrazí se v jiných .NET programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="f6a98-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="f6a98-119">Čistě funkční aplikaci, ve kterém funkce nemají žádné vedlejší účinky, poslední vrácená hodnota je jediným výsledkem volání funkce.</span><span class="sxs-lookup"><span data-stu-id="f6a98-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="f6a98-120">Proto když výsledek je ignorován, je možné programovací chyba.</span><span class="sxs-lookup"><span data-stu-id="f6a98-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="f6a98-121">I když F # není čistě funkcionálním programovacím jazyce, je vhodné provést funkční styl programování, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="f6a98-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6a98-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6a98-122">See also</span></span>

- [<span data-ttu-id="f6a98-123">Primitivní</span><span class="sxs-lookup"><span data-stu-id="f6a98-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="f6a98-124">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="f6a98-124">F# Language Reference</span></span>](index.md)
