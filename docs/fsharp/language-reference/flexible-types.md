---
title: Flexibilní typy (F#)
description: 'Další informace o použití F # anotaci typu flexibilní, což znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu.'
ms.date: 05/16/2016
ms.openlocfilehash: a54d462d04e4e65680a4612f58da72173f04d1f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563347"
---
# <a name="flexible-types"></a><span data-ttu-id="9928e-103">Flexibilní typy</span><span class="sxs-lookup"><span data-stu-id="9928e-103">Flexible Types</span></span>

<span data-ttu-id="9928e-104">A *anotaci typu flexibilní* znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu, kde je určen kompatibility pozici v hierarchii objektově orientované třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9928e-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="9928e-105">Flexibilní typy jsou užitečné, konkrétně v případě, že automatický převod na typy v hierarchii typu nedojde ale přesto chcete povolit vaší funkce pro práci s libovolného typu v hierarchii nebo žádný typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9928e-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="9928e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9928e-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="9928e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9928e-107">Remarks</span></span>

<span data-ttu-id="9928e-108">V předchozích syntaxi *typ* představuje základní třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9928e-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="9928e-109">Flexibilní typ je stejná jako obecný typ, který obsahuje omezení, která omezuje povolené typy pro typy, které jsou kompatibilní s typem základní nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9928e-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="9928e-110">To znamená že následující dva řádky kódu jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="9928e-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="9928e-111">Flexibilní typy jsou užitečné v situacích několik typů.</span><span class="sxs-lookup"><span data-stu-id="9928e-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="9928e-112">Například pokud máte vyšší funkci order (funkce, která přebírá funkce jako argument), je často užitečné používat funkce vrátí flexibilní typu.</span><span class="sxs-lookup"><span data-stu-id="9928e-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="9928e-113">V následujícím příkladu, použití flexibilní typu s argumentem pořadí v `iterate2` umožňuje vyšší pořadí funkce pro práci s funkcí, které generují pořadí, pole, seznamy a další vyčíslitelná typu.</span><span class="sxs-lookup"><span data-stu-id="9928e-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="9928e-114">Vezměte v úvahu následující dvě funkce, jeden z které vrátí pořadí, druhé straně, který vrátí typ, flexibilní.</span><span class="sxs-lookup"><span data-stu-id="9928e-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="9928e-115">Další příklad, zvažte [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkce knihovny:</span><span class="sxs-lookup"><span data-stu-id="9928e-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="9928e-116">Této funkci můžete projít žádnou z následujících vyčíslitelná pořadí:</span><span class="sxs-lookup"><span data-stu-id="9928e-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="9928e-117">Seznam seznamů</span><span class="sxs-lookup"><span data-stu-id="9928e-117">A list of lists</span></span>
- <span data-ttu-id="9928e-118">Seznam polí</span><span class="sxs-lookup"><span data-stu-id="9928e-118">A list of arrays</span></span>
- <span data-ttu-id="9928e-119">Pole seznamy</span><span class="sxs-lookup"><span data-stu-id="9928e-119">An array of lists</span></span>
- <span data-ttu-id="9928e-120">Pole sekvence</span><span class="sxs-lookup"><span data-stu-id="9928e-120">An array of sequences</span></span>
- <span data-ttu-id="9928e-121">Jiné kombinace vyčíslitelná pořadí</span><span class="sxs-lookup"><span data-stu-id="9928e-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="9928e-122">Následující kód používá `Seq.concat` k předvedení scénáře, které můžete podporovat pomocí flexibilní typy.</span><span class="sxs-lookup"><span data-stu-id="9928e-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="9928e-123">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="9928e-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="9928e-124">V F # jako v dalších jazycích objektově orientované jsou kontexty, ve kterých odvozené typy nebo typy, které implementují rozhraní jsou automaticky převedeny na základní typ nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9928e-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="9928e-125">Tyto automatické převody dojít přímé argumenty, ale ne v případě, že typ je v podřízené pozice, v rámci více komplexního typu, jako je například návratovým typem funkce typ, nebo jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="9928e-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="9928e-126">Flexibilní typu notation tedy užitečné hlavně pokud je součást složitější typu typ, které jsou jeho použití.</span><span class="sxs-lookup"><span data-stu-id="9928e-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="9928e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9928e-127">See Also</span></span>

[<span data-ttu-id="9928e-128">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="9928e-128">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9928e-129">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9928e-129">Generics</span></span>](generics/index.md)
