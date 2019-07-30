---
title: Rozhraní
description: Přečtěte F# si, jak rozhraní určují sady souvisejících členů, které implementují jiné třídy.
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627647"
---
# <a name="interfaces"></a><span data-ttu-id="993ad-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="993ad-103">Interfaces</span></span>

<span data-ttu-id="993ad-104">*Rozhraní* určují sady souvisejících členů, které implementují jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="993ad-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="993ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993ad-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="993ad-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="993ad-106">Remarks</span></span>

<span data-ttu-id="993ad-107">Deklarace rozhraní se podobají deklaracím třídy s tím rozdílem, že žádné členy nejsou implementovány.</span><span class="sxs-lookup"><span data-stu-id="993ad-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="993ad-108">Místo toho jsou všichni členové abstrakcí, jak je uvedeno v klíčovém slově `abstract`.</span><span class="sxs-lookup"><span data-stu-id="993ad-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="993ad-109">Pro abstraktní metody neposkytujete tělo metody.</span><span class="sxs-lookup"><span data-stu-id="993ad-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="993ad-110">Můžete však zadat výchozí implementaci zahrnutím samostatné definice člena jako metody společně s `default` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="993ad-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="993ad-111">To je ekvivalentní vytvoření virtuální metody v základní třídě v jiných jazycích .NET.</span><span class="sxs-lookup"><span data-stu-id="993ad-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="993ad-112">Taková virtuální metoda může být přepsána ve třídách, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="993ad-113">Výchozí přístupnost rozhraní je `public`.</span><span class="sxs-lookup"><span data-stu-id="993ad-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="993ad-114">Volitelně můžete každému parametru metody přiřadit název pomocí normální F# syntaxe:</span><span class="sxs-lookup"><span data-stu-id="993ad-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="993ad-115">V předchozím `ISprintable` příkladu `Print` má metoda jeden parametr typu `string` s názvem `format`.</span><span class="sxs-lookup"><span data-stu-id="993ad-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="993ad-116">Existují dva způsoby, jak implementovat rozhraní: pomocí výrazů objektů a pomocí typů tříd.</span><span class="sxs-lookup"><span data-stu-id="993ad-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="993ad-117">V obou případech typ třídy nebo výraz objektu poskytuje tělo metody pro abstraktní metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="993ad-118">Implementace jsou specifické pro každý typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="993ad-119">Proto se metody rozhraní u různých typů mohou lišit od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="993ad-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="993ad-120">Klíčová `interface` slova `end`a, která označují začátek a konec definice, jsou volitelná při použití zjednodušené syntaxe.</span><span class="sxs-lookup"><span data-stu-id="993ad-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="993ad-121">Pokud tato klíčová slova nepoužíváte, kompilátor se pokusí odvodit, zda je typ třídou nebo rozhraním analýzou konstrukcí, které používáte.</span><span class="sxs-lookup"><span data-stu-id="993ad-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="993ad-122">Pokud definujete člena nebo použijete jinou syntaxi třídy, je typ interpretován jako třída.</span><span class="sxs-lookup"><span data-stu-id="993ad-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="993ad-123">Styl kódování .NET je začít všechna rozhraní s velkým písmenem `I`.</span><span class="sxs-lookup"><span data-stu-id="993ad-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="993ad-124">Implementace rozhraní pomocí typů tříd</span><span class="sxs-lookup"><span data-stu-id="993ad-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="993ad-125">Můžete implementovat jedno nebo více rozhraní v typu třídy pomocí `interface` klíčového slova, názvu rozhraní `with` a klíčového slova následovaných definicemi člena rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="993ad-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="993ad-126">Implementace rozhraní jsou zděděny, takže jakékoli odvozené třídy není nutné je znovu implementovat.</span><span class="sxs-lookup"><span data-stu-id="993ad-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="993ad-127">Volání metod rozhraní</span><span class="sxs-lookup"><span data-stu-id="993ad-127">Calling Interface Methods</span></span>

<span data-ttu-id="993ad-128">Metody rozhraní lze volat pouze prostřednictvím rozhraní, nikoli prostřednictvím libovolného objektu typu, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="993ad-129">Proto může být nutné přetypování na typ rozhraní pomocí `:>` operátoru `upcast` nebo operátoru, aby bylo možné tyto metody volat.</span><span class="sxs-lookup"><span data-stu-id="993ad-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="993ad-130">Chcete-li volat metodu rozhraní, když máte objekt typu `SomeClass`, je nutné přetypování objektu na typ rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="993ad-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="993ad-131">Alternativou je deklarovat metodu pro objekt, který přechází a volá metodu rozhraní, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="993ad-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="993ad-132">Implementace rozhraní pomocí objektových výrazů</span><span class="sxs-lookup"><span data-stu-id="993ad-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="993ad-133">Výrazy objektu představují krátký způsob, jak implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="993ad-134">Jsou užitečné v případě, že nemusíte vytvářet pojmenovaný typ a vy chcete pouze objekt, který podporuje metody rozhraní bez jakýchkoli dalších metod.</span><span class="sxs-lookup"><span data-stu-id="993ad-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="993ad-135">Výraz objektu je znázorněn v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="993ad-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="993ad-136">Dědičnost rozhraní</span><span class="sxs-lookup"><span data-stu-id="993ad-136">Interface Inheritance</span></span>

<span data-ttu-id="993ad-137">Rozhraní mohou dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993ad-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="993ad-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="993ad-138">See also</span></span>

- [<span data-ttu-id="993ad-139">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="993ad-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="993ad-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="993ad-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="993ad-141">Třídy</span><span class="sxs-lookup"><span data-stu-id="993ad-141">Classes</span></span>](classes.md)
