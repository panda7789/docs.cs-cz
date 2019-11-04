---
title: Typ jednotky
description: Zjistěte, F# jak se typ Unit často používá k uchování místa, kde je hodnota požadovaná syntaxí jazyka, když není nutná žádná hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424028"
---
# <a name="unit-type"></a><span data-ttu-id="c9acb-103">Typ jednotky</span><span class="sxs-lookup"><span data-stu-id="c9acb-103">Unit Type</span></span>

<span data-ttu-id="c9acb-104">Typ `unit` je typ, který označuje absenci konkrétní hodnoty; typ `unit` má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je potřeba.</span><span class="sxs-lookup"><span data-stu-id="c9acb-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9acb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9acb-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="c9acb-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9acb-106">Remarks</span></span>

<span data-ttu-id="c9acb-107">Každý F# výraz se musí vyhodnotit na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c9acb-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="c9acb-108">Pro výrazy, které negenerují hodnotu, která je zajímavá, je použita hodnota typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="c9acb-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="c9acb-109">Typ `unit` se podobá `void` typu v jazycích, jako jsou C# a C++.</span><span class="sxs-lookup"><span data-stu-id="c9acb-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="c9acb-110">Typ `unit` má jedinou hodnotu a tato hodnota je označena `()`tokenu.</span><span class="sxs-lookup"><span data-stu-id="c9acb-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="c9acb-111">Hodnota typu `unit` se často používá při F# programování k uchování místa, kde je hodnota požadovaná syntaxí jazyka, ale když není potřebná nebo požadovaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c9acb-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="c9acb-112">Příkladem může být návratová hodnota funkce `printf`.</span><span class="sxs-lookup"><span data-stu-id="c9acb-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="c9acb-113">Vzhledem k tomu, že ve funkci dojde k důležitým akcím operace `printf`, funkce nemusí vracet skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c9acb-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="c9acb-114">Proto je návratová hodnota typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="c9acb-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="c9acb-115">Některé konstruktory očekávají `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c9acb-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="c9acb-116">Například `do` vazba nebo jakýkoli kód na nejvyšší úrovni modulu se očekává, že se vyhodnotí na hodnotu `unit`.</span><span class="sxs-lookup"><span data-stu-id="c9acb-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="c9acb-117">Kompilátor ohlásí upozornění, když `do` vazba nebo kód na nejvyšší úrovni modulu vytvoří výsledek jiný než hodnota `unit`, která není použita, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c9acb-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="c9acb-118">Toto upozornění je charakteristické pro funkční programování; nezobrazuje se v jiných programovacích jazycích .NET.</span><span class="sxs-lookup"><span data-stu-id="c9acb-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="c9acb-119">V čistě funkčním programu, ve kterém funkce nemají žádné vedlejší účinky, je konečný návratová hodnota jediným výsledkem volání funkce.</span><span class="sxs-lookup"><span data-stu-id="c9acb-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="c9acb-120">Proto pokud je výsledek ignorován, může to být chyba programování.</span><span class="sxs-lookup"><span data-stu-id="c9acb-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="c9acb-121">I F# když není čistě funkční jazyk programování, je dobrým zvykem sledovat funkční styl programování, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="c9acb-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9acb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9acb-122">See also</span></span>

- [<span data-ttu-id="c9acb-123">Primitivní</span><span class="sxs-lookup"><span data-stu-id="c9acb-123">Primitive</span></span>](basic-types.md)
- [<span data-ttu-id="c9acb-124">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="c9acb-124">F# Language Reference</span></span>](index.md)
