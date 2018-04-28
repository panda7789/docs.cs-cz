---
title: Delegáti (F#)
description: 'Naučte se pracovat s Delegáti v jazyce F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 56520cc631d889f390a7d4300be1cb3185306be9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="delegates"></a><span data-ttu-id="d1390-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="d1390-103">Delegates</span></span>

<span data-ttu-id="d1390-104">Delegát představuje volání funkce, jako objekt.</span><span class="sxs-lookup"><span data-stu-id="d1390-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="d1390-105">V jazyce F # normálně měli byste použít funkce hodnoty k reprezentaci funkce jako hodnoty první třídy; Delegáti však se používají v rozhraní .NET Framework a proto je třeba při spolupráci s rozhraní API, která je očekávali.</span><span class="sxs-lookup"><span data-stu-id="d1390-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="d1390-106">Může také používají při vytváření knihovny určená pro použití z jinými jazyky rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1390-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="d1390-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1390-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="d1390-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1390-108">Remarks</span></span>
<span data-ttu-id="d1390-109">V předchozích syntaxi `type1` reprezentuje typ argumentu nebo typy a `type2` představuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="d1390-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="d1390-110">Typy argumentů, které jsou reprezentované pomocí `type1` jsou automaticky curryfikované.</span><span class="sxs-lookup"><span data-stu-id="d1390-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="d1390-111">To naznačuje, že pro tento typ používat formulář řazené kolekce členů, pokud jsou argumenty funkce cíl curryfikované a řazené kolekce členů v závorkách argumenty, které jsou již v podobě řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="d1390-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="d1390-112">Automatické currying odebere sadu závorky, ponechat argument řazené kolekce členů, která odpovídá cílové metody.</span><span class="sxs-lookup"><span data-stu-id="d1390-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="d1390-113">Naleznete příklad kódu pro syntaxi, kterou byste měli použít v každém případu.</span><span class="sxs-lookup"><span data-stu-id="d1390-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="d1390-114">Delegáti lze připojit k F # funkce hodnoty a statické nebo instanci metody.</span><span class="sxs-lookup"><span data-stu-id="d1390-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="d1390-115">F # funkce hodnoty lze předat přímo jako argumenty pro delegování konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d1390-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="d1390-116">Pro statickou metodu vytvoříte pomocí názvu třídy a metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="d1390-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="d1390-117">Pro metodu instance poskytnete instance objektu a metoda v jeden argument.</span><span class="sxs-lookup"><span data-stu-id="d1390-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="d1390-118">V obou případech člen přístup – operátor (`.`) se používá.</span><span class="sxs-lookup"><span data-stu-id="d1390-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="d1390-119">`Invoke` Metoda typu delegáta volání zapouzdřené funkce.</span><span class="sxs-lookup"><span data-stu-id="d1390-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="d1390-120">Delegáti také může být předán jako funkce hodnoty pod položkou Název metody Invoke bez závorek.</span><span class="sxs-lookup"><span data-stu-id="d1390-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="d1390-121">Následující kód ukazuje syntaxi pro vytváření delegátů, které představují různé metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="d1390-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="d1390-122">Syntaxe deklarace a přiřazení delegát je v závislosti na tom, zda je metoda statickou metodu nebo instanci metody a jestli má argumenty v podobě řazené kolekce členů nebo curryfikované formuláře, mírně liší.</span><span class="sxs-lookup"><span data-stu-id="d1390-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="d1390-123">Následující kód ukazuje některé různými způsoby, kterými můžete pracovat s delegáti.</span><span class="sxs-lookup"><span data-stu-id="d1390-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="d1390-124">Výstupem předchozího příkladu kódu je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d1390-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="d1390-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1390-125">See Also</span></span>
[<span data-ttu-id="d1390-126">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="d1390-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="d1390-127">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="d1390-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="d1390-128">Události</span><span class="sxs-lookup"><span data-stu-id="d1390-128">Events</span></span>](members/events.md)
