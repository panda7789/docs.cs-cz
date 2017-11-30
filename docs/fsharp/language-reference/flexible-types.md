---
title: "Flexibilní typy (F#)"
description: "Další informace o použití F # anotaci typu flexibilní, což znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="c6fdd-104">Flexibilní typy</span><span class="sxs-lookup"><span data-stu-id="c6fdd-104">Flexible Types</span></span>

<span data-ttu-id="c6fdd-105">A *anotaci typu flexibilní* znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu, kde je určen kompatibility pozici v hierarchii objektově orientované třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="c6fdd-106">Flexibilní typy jsou užitečné, konkrétně v případě, že automatický převod na typy v hierarchii typu nedojde ale přesto chcete povolit vaší funkce pro práci s libovolného typu v hierarchii nebo žádný typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6fdd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6fdd-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="c6fdd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6fdd-108">Remarks</span></span>

<span data-ttu-id="c6fdd-109">V předchozích syntaxi *typ* představuje základní třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="c6fdd-110">Flexibilní typ je stejná jako obecný typ, který obsahuje omezení, která omezuje povolené typy pro typy, které jsou kompatibilní s typem základní nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="c6fdd-111">To znamená že následující dva řádky kódu jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="c6fdd-112">Flexibilní typy jsou užitečné v situacích několik typů.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="c6fdd-113">Například pokud máte vyšší funkci order (funkce, která přebírá funkce jako argument), je často užitečné používat funkce vrátí flexibilní typu.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="c6fdd-114">V následujícím příkladu, použití flexibilní typu s argumentem pořadí v `iterate2` umožňuje vyšší pořadí funkce pro práci s funkcí, které generují pořadí, pole, seznamy a další vyčíslitelná typu.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="c6fdd-115">Vezměte v úvahu následující dvě funkce, jeden z které vrátí pořadí, druhé straně, který vrátí typ, flexibilní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="c6fdd-116">Další příklad, zvažte [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkce knihovny:</span><span class="sxs-lookup"><span data-stu-id="c6fdd-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="c6fdd-117">Této funkci můžete projít žádnou z následujících vyčíslitelná pořadí:</span><span class="sxs-lookup"><span data-stu-id="c6fdd-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="c6fdd-118">Seznam seznamů</span><span class="sxs-lookup"><span data-stu-id="c6fdd-118">A list of lists</span></span>
- <span data-ttu-id="c6fdd-119">Seznam polí</span><span class="sxs-lookup"><span data-stu-id="c6fdd-119">A list of arrays</span></span>
- <span data-ttu-id="c6fdd-120">Pole seznamy</span><span class="sxs-lookup"><span data-stu-id="c6fdd-120">An array of lists</span></span>
- <span data-ttu-id="c6fdd-121">Pole sekvence</span><span class="sxs-lookup"><span data-stu-id="c6fdd-121">An array of sequences</span></span>
- <span data-ttu-id="c6fdd-122">Jiné kombinace vyčíslitelná pořadí</span><span class="sxs-lookup"><span data-stu-id="c6fdd-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="c6fdd-123">Následující kód používá `Seq.concat` k předvedení scénáře, které můžete podporovat pomocí flexibilní typy.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="c6fdd-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="c6fdd-125">V F # jako v dalších jazycích objektově orientované jsou kontexty, ve kterých odvozené typy nebo typy, které implementují rozhraní jsou automaticky převedeny na základní typ nebo typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="c6fdd-126">Tyto automatické převody dojít přímé argumenty, ale ne v případě, že typ je v podřízené pozice, v rámci více komplexního typu, jako je například návratovým typem funkce typ, nebo jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="c6fdd-127">Flexibilní typu notation tedy užitečné hlavně pokud je součást složitější typu typ, které jsou jeho použití.</span><span class="sxs-lookup"><span data-stu-id="c6fdd-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6fdd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6fdd-128">See Also</span></span>

[<span data-ttu-id="c6fdd-129">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="c6fdd-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c6fdd-130">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="c6fdd-130">Generics</span></span>](generics/index.md)
