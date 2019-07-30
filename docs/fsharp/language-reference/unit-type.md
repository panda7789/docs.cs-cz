---
title: Typ jednotky
description: Zjistěte, F# jak se typ Unit často používá k uchování místa, kde je hodnota požadovaná syntaxí jazyka, když není nutná žádná hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630172"
---
# <a name="unit-type"></a><span data-ttu-id="5398e-103">Typ jednotky</span><span class="sxs-lookup"><span data-stu-id="5398e-103">Unit Type</span></span>

<span data-ttu-id="5398e-104">Typ je typ, který označuje absenci konkrétní hodnoty `unit` ; typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je vyžadována. `unit`</span><span class="sxs-lookup"><span data-stu-id="5398e-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="5398e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5398e-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="5398e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5398e-106">Remarks</span></span>

<span data-ttu-id="5398e-107">Každý F# výraz se musí vyhodnotit na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5398e-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="5398e-108">Pro výrazy, které negenerují hodnotu, která je zajímavá, je použita hodnota typu `unit` .</span><span class="sxs-lookup"><span data-stu-id="5398e-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="5398e-109">Typ se podobá `void` typu v jazycích, jako jsou C# a C++ `unit`</span><span class="sxs-lookup"><span data-stu-id="5398e-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="5398e-110">Typ má jedinou hodnotu a tato hodnota je označena tokenem `()`. `unit`</span><span class="sxs-lookup"><span data-stu-id="5398e-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="5398e-111">Hodnota `unit` typu se často používá při F# programování k uchování místa, kde je hodnota požadovaná syntaxí jazyka, ale když není potřebná nebo požadovaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5398e-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="5398e-112">Příkladem může být návratová hodnota `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="5398e-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="5398e-113">Vzhledem k tomu, že ve `printf` funkci dojde k důležitým akcím operace, funkce nemusí vracet skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5398e-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="5398e-114">Proto je návratová hodnota typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="5398e-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="5398e-115">Některé konstruktory očekávají `unit` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5398e-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="5398e-116">Například `do` vazba nebo jakýkoli kód na nejvyšší úrovni modulu se očekává pro vyhodnocení `unit` na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5398e-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="5398e-117">Kompilátor ohlásí upozornění, pokud `do` vazba nebo kód na nejvyšší úrovni modulu vytvoří výsledek jiný `unit` než hodnota, která není použita, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5398e-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="5398e-118">Toto upozornění je charakteristické pro funkční programování; nezobrazuje se v jiných programovacích jazycích .NET.</span><span class="sxs-lookup"><span data-stu-id="5398e-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="5398e-119">V čistě funkčním programu, ve kterém funkce nemají žádné vedlejší účinky, je konečný návratová hodnota jediným výsledkem volání funkce.</span><span class="sxs-lookup"><span data-stu-id="5398e-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="5398e-120">Proto pokud je výsledek ignorován, může to být chyba programování.</span><span class="sxs-lookup"><span data-stu-id="5398e-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="5398e-121">I F# když není čistě funkční jazyk programování, je dobrým zvykem sledovat funkční styl programování, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="5398e-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="5398e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5398e-122">See also</span></span>

- [<span data-ttu-id="5398e-123">Primitivní</span><span class="sxs-lookup"><span data-stu-id="5398e-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="5398e-124">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="5398e-124">F# Language Reference</span></span>](index.md)
