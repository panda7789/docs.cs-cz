---
title: Delegáty
description: Naučte se pracovat s delegáty F#v.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630367"
---
# <a name="delegates"></a><span data-ttu-id="b8fca-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="b8fca-103">Delegates</span></span>

<span data-ttu-id="b8fca-104">Delegát představuje volání funkce jako objekt.</span><span class="sxs-lookup"><span data-stu-id="b8fca-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="b8fca-105">V F#aplikaci je obvykle vhodné použít hodnoty funkcí k reprezentování funkcí jako hodnot první třídy; Delegáti se ale používají v .NET Framework, takže je potřeba, když pracujete s rozhraními API, která je očekávají.</span><span class="sxs-lookup"><span data-stu-id="b8fca-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="b8fca-106">Můžou se používat taky při vytváření knihoven určených pro použití z jiných .NET Frameworkch jazyků.</span><span class="sxs-lookup"><span data-stu-id="b8fca-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8fca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8fca-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="b8fca-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8fca-108">Remarks</span></span>

<span data-ttu-id="b8fca-109">V předchozí syntaxi `type1` představuje typ argumentu nebo typy a `type2` představuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="b8fca-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="b8fca-110">Typy argumentů, které jsou reprezentovány `type1` , jsou automaticky curryfikované.</span><span class="sxs-lookup"><span data-stu-id="b8fca-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="b8fca-111">To naznačuje, že pro tento typ použijete formulář řazené kolekce členů, pokud jsou argumenty cílové funkce curryfikované a řazená kolekce členů v závorkách pro argumenty, které jsou již ve formuláři řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="b8fca-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="b8fca-112">Automatický procesu curryfikace odebere sadu závorek a ponechává argument řazené kolekce členů, který odpovídá cílové metodě.</span><span class="sxs-lookup"><span data-stu-id="b8fca-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="b8fca-113">Podívejte se na příklad kódu pro syntaxi, kterou byste měli použít v každém případě.</span><span class="sxs-lookup"><span data-stu-id="b8fca-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="b8fca-114">Delegáty lze připojit k F# hodnotám funkcí a statickým nebo instančním metodám.</span><span class="sxs-lookup"><span data-stu-id="b8fca-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="b8fca-115">F#hodnoty funkcí lze předat přímo jako argumenty pro konstruktory Delegate.</span><span class="sxs-lookup"><span data-stu-id="b8fca-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="b8fca-116">Pro statickou metodu sestavíte delegáty pomocí názvu třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="b8fca-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="b8fca-117">V případě metody instance poskytujete instanci objektu a metodu v jednom argumentu.</span><span class="sxs-lookup"><span data-stu-id="b8fca-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="b8fca-118">V obou případech je použit operátor přístupu ke členu (`.`).</span><span class="sxs-lookup"><span data-stu-id="b8fca-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="b8fca-119">`Invoke` Metoda na typu delegáta volá zapouzdřenou funkci.</span><span class="sxs-lookup"><span data-stu-id="b8fca-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="b8fca-120">Delegáty lze také předat jako hodnoty funkcí odkazem na název metody Invoke bez závorek.</span><span class="sxs-lookup"><span data-stu-id="b8fca-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="b8fca-121">Následující kód ukazuje syntaxi pro vytváření delegátů, kteří reprezentují různé metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="b8fca-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="b8fca-122">V závislosti na tom, zda je metoda statickou metodou nebo metodou instance a zda má argumenty ve formuláři řazené kolekce členů nebo ve formuláři curryfikované, syntaxe pro deklaraci a přiřazení delegáta je trochu odlišná.</span><span class="sxs-lookup"><span data-stu-id="b8fca-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="b8fca-123">Následující kód ukazuje některé z různých způsobů, jak můžete s delegáty pracovat.</span><span class="sxs-lookup"><span data-stu-id="b8fca-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="b8fca-124">Výstup předchozího příkladu kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="b8fca-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="b8fca-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8fca-125">See also</span></span>

- [<span data-ttu-id="b8fca-126">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b8fca-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b8fca-127">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="b8fca-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="b8fca-128">Události</span><span class="sxs-lookup"><span data-stu-id="b8fca-128">Events</span></span>](./members/events.md)
