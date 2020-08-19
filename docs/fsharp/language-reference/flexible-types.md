---
title: Flexibilní typy
description: 'Naučte se používat anotaci typu F # flexibilní typ, která indikuje, že parametr, proměnná nebo hodnota má typ, který je kompatibilní se zadaným typem.'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557747"
---
# <a name="flexible-types"></a><span data-ttu-id="44e86-103">Flexibilní typy</span><span class="sxs-lookup"><span data-stu-id="44e86-103">Flexible Types</span></span>

<span data-ttu-id="44e86-104">*Flexibilní anotace typu* indikuje, že parametr, proměnná nebo hodnota má typ, který je kompatibilní se zadaným typem, kde kompatibilita je určena pozicí v objektově orientované hierarchii tříd nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44e86-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="44e86-105">Flexibilní typy jsou užitečné, konkrétně když automatický převod na typy vyšší v hierarchii typů neprobíhá, ale přesto chcete povolit funkci pro práci s jakýmkoli typem v hierarchii nebo libovolným typem, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44e86-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="44e86-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="44e86-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="44e86-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44e86-107">Remarks</span></span>

<span data-ttu-id="44e86-108">V předchozí syntaxi *typ* představuje základní typ nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44e86-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="44e86-109">Flexibilní typ je ekvivalentní obecnému typu, který má omezení, které omezuje povolené typy na typy, které jsou kompatibilní s typem základního nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44e86-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="44e86-110">To znamená, že následující dva řádky kódu jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="44e86-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="44e86-111">Flexibilní typy jsou užitečné v několika typech situací.</span><span class="sxs-lookup"><span data-stu-id="44e86-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="44e86-112">Například pokud máte funkci s vyšším pořadím (funkce, která přebírá funkci jako argument), je často užitečné, pokud chcete, aby funkce vrátila flexibilní typ.</span><span class="sxs-lookup"><span data-stu-id="44e86-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="44e86-113">V následujícím příkladu použití flexibilního typu s argumentem Sequence v `iterate2` umožňuje funkci vyššího řádu pro práci s funkcemi, které generují sekvence, pole, seznamy a jakýkoliv jiný vyčíslitelné typ.</span><span class="sxs-lookup"><span data-stu-id="44e86-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="44e86-114">Vezměte v úvahu následující dvě funkce, z nichž jeden vrací sekvenci, druhá z nich vrací flexibilní typ.</span><span class="sxs-lookup"><span data-stu-id="44e86-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="44e86-115">Dalším příkladem je použití funkce knihovny [Seq. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) :</span><span class="sxs-lookup"><span data-stu-id="44e86-115">As another example, consider the [Seq.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="44e86-116">Této funkci můžete předat libovolné z následujících vyčíslitelné sekvencí:</span><span class="sxs-lookup"><span data-stu-id="44e86-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="44e86-117">Seznam seznamů</span><span class="sxs-lookup"><span data-stu-id="44e86-117">A list of lists</span></span>
- <span data-ttu-id="44e86-118">Seznam polí</span><span class="sxs-lookup"><span data-stu-id="44e86-118">A list of arrays</span></span>
- <span data-ttu-id="44e86-119">Pole seznamů</span><span class="sxs-lookup"><span data-stu-id="44e86-119">An array of lists</span></span>
- <span data-ttu-id="44e86-120">Pole sekvencí</span><span class="sxs-lookup"><span data-stu-id="44e86-120">An array of sequences</span></span>
- <span data-ttu-id="44e86-121">Jakákoli jiná kombinace vyčíslitelné sekvence</span><span class="sxs-lookup"><span data-stu-id="44e86-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="44e86-122">Následující kód používá `Seq.concat` k předvedení scénářů, které můžete podporovat pomocí flexibilních typů.</span><span class="sxs-lookup"><span data-stu-id="44e86-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="44e86-123">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="44e86-123">The output is as follows.</span></span>

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="44e86-124">V jazyce F #, stejně jako v jiných objektově orientovaných jazycích, existují kontexty, ve kterých jsou odvozeny typy nebo typy, které implementují rozhraní, automaticky převedeny na základní typ nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44e86-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="44e86-125">K těmto automatickým převodům dochází v přímých argumentech, ale ne v případě, že je typ na podřízené pozici, jako součást složitějšího typu, jako je návratový typ typu funkce nebo jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="44e86-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="44e86-126">Proto je flexibilní typ Notation užitečný hlavně v případě, že typ, na který jej aplikujete, je součástí složitějšího typu.</span><span class="sxs-lookup"><span data-stu-id="44e86-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="44e86-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="44e86-127">See also</span></span>

- [<span data-ttu-id="44e86-128">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="44e86-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="44e86-129">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="44e86-129">Generics</span></span>](./generics/index.md)
