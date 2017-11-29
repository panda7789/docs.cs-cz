---
title: "Delegáti (F#)"
description: "Naučte se pracovat s Delegáti v jazyce F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="21c66-104">Delegáty</span><span class="sxs-lookup"><span data-stu-id="21c66-104">Delegates</span></span>

<span data-ttu-id="21c66-105">Delegát představuje volání funkce, jako objekt.</span><span class="sxs-lookup"><span data-stu-id="21c66-105">A delegate represents a function call as an object.</span></span> <span data-ttu-id="21c66-106">V jazyce F # normálně měli byste použít funkce hodnoty k reprezentaci funkce jako hodnoty první třídy; Delegáti však se používají v rozhraní .NET Framework a proto je třeba při spolupráci s rozhraní API, která je očekávali.</span><span class="sxs-lookup"><span data-stu-id="21c66-106">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="21c66-107">Může také používají při vytváření knihovny určená pro použití z jinými jazyky rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21c66-107">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="21c66-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21c66-108">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="21c66-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21c66-109">Remarks</span></span>
<span data-ttu-id="21c66-110">V předchozích syntaxi `type1` reprezentuje typ argumentu nebo typy a `type2` představuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="21c66-110">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="21c66-111">Typy argumentů, které jsou reprezentované pomocí `type1` jsou automaticky curryfikované.</span><span class="sxs-lookup"><span data-stu-id="21c66-111">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="21c66-112">To naznačuje, že pro tento typ používat formulář řazené kolekce členů, pokud jsou argumenty funkce cíl curryfikované a řazené kolekce členů v závorkách argumenty, které jsou již v podobě řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="21c66-112">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="21c66-113">Automatické currying odebere sadu závorky, ponechat argument řazené kolekce členů, která odpovídá cílové metody.</span><span class="sxs-lookup"><span data-stu-id="21c66-113">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="21c66-114">Naleznete příklad kódu pro syntaxi, kterou byste měli použít v každém případu.</span><span class="sxs-lookup"><span data-stu-id="21c66-114">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="21c66-115">Delegáti lze připojit k F # funkce hodnoty a statické nebo instanci metody.</span><span class="sxs-lookup"><span data-stu-id="21c66-115">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="21c66-116">F # funkce hodnoty lze předat přímo jako argumenty pro delegování konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="21c66-116">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="21c66-117">Pro statickou metodu vytvoříte pomocí názvu třídy a metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="21c66-117">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="21c66-118">Pro metodu instance poskytnete instance objektu a metoda v jeden argument.</span><span class="sxs-lookup"><span data-stu-id="21c66-118">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="21c66-119">V obou případech člen přístup – operátor (`.`) se používá.</span><span class="sxs-lookup"><span data-stu-id="21c66-119">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="21c66-120">`Invoke` Metoda typu delegáta volání zapouzdřené funkce.</span><span class="sxs-lookup"><span data-stu-id="21c66-120">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="21c66-121">Delegáti také může být předán jako funkce hodnoty pod položkou Název metody Invoke bez závorek.</span><span class="sxs-lookup"><span data-stu-id="21c66-121">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="21c66-122">Následující kód ukazuje syntaxi pro vytváření delegátů, které představují různé metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="21c66-122">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="21c66-123">Syntaxe deklarace a přiřazení delegát je v závislosti na tom, zda je metoda statickou metodu nebo instanci metody a jestli má argumenty v podobě řazené kolekce členů nebo curryfikované formuláře, mírně liší.</span><span class="sxs-lookup"><span data-stu-id="21c66-123">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="21c66-124">Následující kód ukazuje některé různými způsoby, kterými můžete pracovat s delegáti.</span><span class="sxs-lookup"><span data-stu-id="21c66-124">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="21c66-125">Výstupem předchozího příkladu kódu je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="21c66-125">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="21c66-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="21c66-126">See Also</span></span>
[<span data-ttu-id="21c66-127">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="21c66-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="21c66-128">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="21c66-128">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="21c66-129">Události</span><span class="sxs-lookup"><span data-stu-id="21c66-129">Events</span></span>](members/events.md)
