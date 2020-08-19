---
title: Rozhraní
description: 'Přečtěte si, jak rozhraní F # určují sady souvisejících členů, které implementují jiné třídy.'
ms.date: 08/15/2020
ms.openlocfilehash: 36272b52fcff83e8e8a54ccc4e6ecd1252a91819
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558124"
---
# <a name="interfaces"></a><span data-ttu-id="083e5-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="083e5-103">Interfaces</span></span>

<span data-ttu-id="083e5-104">*Rozhraní* určují sady souvisejících členů, které implementují jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="083e5-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="083e5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="083e5-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="083e5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="083e5-106">Remarks</span></span>

<span data-ttu-id="083e5-107">Deklarace rozhraní se podobají deklaracím třídy s tím rozdílem, že žádné členy nejsou implementovány.</span><span class="sxs-lookup"><span data-stu-id="083e5-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="083e5-108">Místo toho jsou všichni členové abstrakcí, jak je uvedeno v klíčovém slově `abstract` .</span><span class="sxs-lookup"><span data-stu-id="083e5-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="083e5-109">Pro abstraktní metody neposkytujete tělo metody.</span><span class="sxs-lookup"><span data-stu-id="083e5-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="083e5-110">Můžete však zadat výchozí implementaci zahrnutím samostatné definice člena jako metody společně s `default` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="083e5-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="083e5-111">To je ekvivalentní vytvoření virtuální metody v základní třídě v jiných jazycích .NET.</span><span class="sxs-lookup"><span data-stu-id="083e5-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="083e5-112">Taková virtuální metoda může být přepsána ve třídách, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="083e5-113">Výchozí přístupnost rozhraní je `public` .</span><span class="sxs-lookup"><span data-stu-id="083e5-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="083e5-114">Volitelně můžete každému parametru metody poskytnout název pomocí normální syntaxe F #:</span><span class="sxs-lookup"><span data-stu-id="083e5-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="083e5-115">V předchozím `ISprintable` příkladu `Print` má metoda jeden parametr typu `string` s názvem `format` .</span><span class="sxs-lookup"><span data-stu-id="083e5-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="083e5-116">Existují dva způsoby, jak implementovat rozhraní: pomocí výrazů objektů a pomocí typů tříd.</span><span class="sxs-lookup"><span data-stu-id="083e5-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="083e5-117">V obou případech typ třídy nebo výraz objektu poskytuje tělo metody pro abstraktní metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="083e5-118">Implementace jsou specifické pro každý typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="083e5-119">Proto se metody rozhraní u různých typů mohou lišit od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="083e5-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="083e5-120">Klíčová slova `interface` a `end` , která označují začátek a konec definice, jsou volitelná při použití zjednodušené syntaxe.</span><span class="sxs-lookup"><span data-stu-id="083e5-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="083e5-121">Pokud tato klíčová slova nepoužíváte, kompilátor se pokusí odvodit, zda je typ třídou nebo rozhraním analýzou konstrukcí, které používáte.</span><span class="sxs-lookup"><span data-stu-id="083e5-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="083e5-122">Pokud definujete člena nebo použijete jinou syntaxi třídy, je typ interpretován jako třída.</span><span class="sxs-lookup"><span data-stu-id="083e5-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="083e5-123">Styl kódování .NET je začít všechna rozhraní s velkým písmenem `I` .</span><span class="sxs-lookup"><span data-stu-id="083e5-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="083e5-124">Více parametrů lze zadat dvěma způsoby: F #-Style a. Typ sítě.</span><span class="sxs-lookup"><span data-stu-id="083e5-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="083e5-125">Obě budou kompilovat stejným způsobem pro příjemce .NET, ale styl F # Vynutí, aby volající F # používali parametr F # Style a. NET-Style vynutí, aby volající F # používali aplikaci argumentu s řazenou kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="083e5-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="083e5-126">Implementace rozhraní pomocí typů tříd</span><span class="sxs-lookup"><span data-stu-id="083e5-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="083e5-127">Můžete implementovat jedno nebo více rozhraní v typu třídy pomocí `interface` klíčového slova, názvu rozhraní a `with` klíčového slova následovaných definicemi člena rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="083e5-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="083e5-128">Implementace rozhraní jsou zděděny, takže jakékoli odvozené třídy není nutné je znovu implementovat.</span><span class="sxs-lookup"><span data-stu-id="083e5-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="083e5-129">Volání metod rozhraní</span><span class="sxs-lookup"><span data-stu-id="083e5-129">Calling Interface Methods</span></span>

<span data-ttu-id="083e5-130">Metody rozhraní lze volat pouze prostřednictvím rozhraní, nikoli prostřednictvím libovolného objektu typu, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="083e5-131">Proto může být nutné přetypování na typ rozhraní pomocí `:>` operátoru nebo operátoru, aby bylo možné `upcast` tyto metody volat.</span><span class="sxs-lookup"><span data-stu-id="083e5-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="083e5-132">Chcete-li volat metodu rozhraní, když máte objekt typu `SomeClass` , je nutné přetypování objektu na typ rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="083e5-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="083e5-133">Alternativou je deklarovat metodu pro objekt, který přechází a volá metodu rozhraní, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="083e5-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="083e5-134">Implementace rozhraní pomocí objektových výrazů</span><span class="sxs-lookup"><span data-stu-id="083e5-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="083e5-135">Výrazy objektu představují krátký způsob, jak implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="083e5-136">Jsou užitečné v případě, že nemusíte vytvářet pojmenovaný typ a vy chcete pouze objekt, který podporuje metody rozhraní bez jakýchkoli dalších metod.</span><span class="sxs-lookup"><span data-stu-id="083e5-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="083e5-137">Výraz objektu je znázorněn v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="083e5-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="083e5-138">Dědičnost rozhraní</span><span class="sxs-lookup"><span data-stu-id="083e5-138">Interface Inheritance</span></span>

<span data-ttu-id="083e5-139">Rozhraní mohou dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="083e5-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="083e5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="083e5-140">See also</span></span>

- [<span data-ttu-id="083e5-141">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="083e5-141">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="083e5-142">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="083e5-142">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="083e5-143">Třídy</span><span class="sxs-lookup"><span data-stu-id="083e5-143">Classes</span></span>](classes.md)
