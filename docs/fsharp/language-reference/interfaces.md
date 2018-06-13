---
title: Rozhraní (F#)
description: 'Zjistěte, jak zadat F # rozhraní sady souvisejících členů, které implementují jiné třídy.'
ms.date: 05/16/2016
ms.openlocfilehash: 54ae8a2840ce26814be25f08c3ed02e12df6b7c0
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058894"
---
# <a name="interfaces"></a><span data-ttu-id="b8b4a-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8b4a-103">Interfaces</span></span>

<span data-ttu-id="b8b4a-104">*Rozhraní* zadejte sady souvisejících členů, které implementují jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8b4a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8b4a-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="b8b4a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8b4a-106">Remarks</span></span>
<span data-ttu-id="b8b4a-107">Deklarace rozhraní vypadat podobně jako deklarace tříd s tím rozdílem, že jsou implementované žádní členové.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="b8b4a-108">Místo toho jsou všechny členy abstraktní, jak je uvedeno klíčovým slovem `abstract`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="b8b4a-109">Pro abstraktní metody nezadáte těla metody.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="b8b4a-110">Výchozí implementace však můžete zadat také zahrnutím samostatné definice člena jako metodu společně s `default` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="b8b4a-111">Díky tomu je ekvivalentní k vytvoření virtuální metodu v základní třídě v jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="b8b4a-112">Virtuální metoda může být přepsána nastaveními v třídy, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="b8b4a-113">Je výchozí usnadnění pro rozhraní `public`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="b8b4a-114">Můžete volitelně zadejte každý parametr metody název pomocí normální F # – syntaxe:</span><span class="sxs-lookup"><span data-stu-id="b8b4a-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="b8b4a-115">Ve výše `ISprintable` například `Print` metoda má jeden parametr typu `string` s názvem `format`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="b8b4a-116">Existují dva způsoby, jak implementovat rozhraní: pomocí objektové výrazy a pomocí typy tříd.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="b8b4a-117">V obou případech výraz typu nebo objektu třídy poskytuje těla metodu pro abstraktní metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="b8b4a-118">Implementace jsou specifické pro každý typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="b8b4a-119">Proto může být metody rozhraní na různé typy liší od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="b8b4a-120">Klíčová slova `interface` a `end`, který označit počáteční a koncová definice, jsou volitelné, pokud použijete prostá syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="b8b4a-121">Pokud nepoužijete tato klíčová slova, pokusí se kompilátor odvození, zda je typ třídy nebo rozhraní analýzou konstrukce, které používáte.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="b8b4a-122">Pokud definovat člena nebo použijte jiné třídy syntaxi, typ interpretována jako třída.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="b8b4a-123">Kódování styl .NET je začít všech rozhraní s velkým `I`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="b8b4a-124">Implementace rozhraní pomocí typy tříd</span><span class="sxs-lookup"><span data-stu-id="b8b4a-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="b8b4a-125">V typu třídy můžete implementovat jednu nebo více rozhraní pomocí `interface` – klíčové slovo, název rozhraní a `with` – klíčové slovo, za nímž následuje člen definice rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="b8b4a-126">Implementace rozhraní jsou zděděné, takže není nutné je přeimplementovat všechny odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="b8b4a-127">Volání metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8b4a-127">Calling Interface Methods</span></span>
<span data-ttu-id="b8b4a-128">Metody rozhraní lze volat pouze přes rozhraní, nikoli pomocí libovolného objektu typu, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="b8b4a-129">Proto může být nutné přetypování nahoru na typ rozhraní pomocí `:>` operátor nebo `upcast` operátor k volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="b8b4a-130">K volání metody rozhraní, když máte objekt typu `SomeClass`, musíte přetypování nahoru objekt, který má typ rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="b8b4a-131">Alternativou je deklarujte metodu pro objekt, že upcasts a volá metodu rozhraní, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="b8b4a-132">Implementace rozhraní pomocí objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="b8b4a-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="b8b4a-133">Objektové výrazy zadejte krátký způsob, jak implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="b8b4a-134">Jsou užitečné v případě, že nemáte k vytvoření pojmenovaného typu, a chcete objekt, který podporuje metody rozhraní, bez jakékoli další metody.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="b8b4a-135">Výraz objektu je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="b8b4a-136">Rozhraní dědičnosti</span><span class="sxs-lookup"><span data-stu-id="b8b4a-136">Interface Inheritance</span></span>
<span data-ttu-id="b8b4a-137">Rozhraní může dědit vlastnosti z jednoho nebo více základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="b8b4a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8b4a-138">See Also</span></span>
[<span data-ttu-id="b8b4a-139">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b8b4a-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="b8b4a-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="b8b4a-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="b8b4a-141">Třídy</span><span class="sxs-lookup"><span data-stu-id="b8b4a-141">Classes</span></span>](classes.md)
