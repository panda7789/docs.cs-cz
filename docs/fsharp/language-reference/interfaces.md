---
title: Rozhraní (F#)
description: 'Zjistěte, jak určit sadu souvisejících členů, které implementují jiné třídy rozhraní F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201514"
---
# <a name="interfaces"></a><span data-ttu-id="c93cb-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c93cb-103">Interfaces</span></span>

<span data-ttu-id="c93cb-104">*Rozhraní* zadat sady souvisejících členů, které implementují jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="c93cb-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="c93cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c93cb-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="c93cb-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c93cb-106">Remarks</span></span>

<span data-ttu-id="c93cb-107">Deklarace rozhraní vypadat podobně jako deklarace tříd s tím rozdílem, že jsou implementovány žádní členové.</span><span class="sxs-lookup"><span data-stu-id="c93cb-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="c93cb-108">Místo toho jsou všechny členy abstract, jak je uvedeno klíčové slovo `abstract`.</span><span class="sxs-lookup"><span data-stu-id="c93cb-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="c93cb-109">Tělo metody se neposkytují pro abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="c93cb-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="c93cb-110">Ale může poskytovat výchozí implementace také zahrnutím samostatné definice člena jako metoda spolu s `default` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c93cb-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="c93cb-111">To je ekvivalentní k vytváření virtuální metodu v základní třídě v jiných jazycích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c93cb-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="c93cb-112">Virtuální metoda může přepsat ve třídách, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="c93cb-113">Výchozí dostupnost pro rozhraní je `public`.</span><span class="sxs-lookup"><span data-stu-id="c93cb-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="c93cb-114">Můžete volitelně zadejte každý parametr metody název pomocí syntaxe normální F #:</span><span class="sxs-lookup"><span data-stu-id="c93cb-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="c93cb-115">V uvedeném `ISprintable` například `Print` metoda má jeden parametr typu `string` s názvem `format`.</span><span class="sxs-lookup"><span data-stu-id="c93cb-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="c93cb-116">Existují dva způsoby, jak implementovat rozhraní: použitím objektových výrazů a použitím typů tříd.</span><span class="sxs-lookup"><span data-stu-id="c93cb-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="c93cb-117">V obou případech se výraz typu nebo objekt třídy poskytuje těla metod pro abstraktní metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="c93cb-118">Implementace jsou specifické pro každý typ, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="c93cb-119">Proto může být metody rozhraní s různými typy liší od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="c93cb-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="c93cb-120">Klíčová slova `interface` a `end`, které označení začátku a konce definice, jsou při použití nenáročném syntaxi volitelné.</span><span class="sxs-lookup"><span data-stu-id="c93cb-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="c93cb-121">Pokud použijete tato klíčová slova, kompilátor se pokusí odvodit, zda je typ třídy nebo rozhraní díky analýze konstrukce, které používáte.</span><span class="sxs-lookup"><span data-stu-id="c93cb-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="c93cb-122">Pokud definujete člena nebo použijte jiné syntaxe třídy, typ je interpretován jako třídu.</span><span class="sxs-lookup"><span data-stu-id="c93cb-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="c93cb-123">Styl kódování .NET, je začít všechna rozhraní s velkým `I`.</span><span class="sxs-lookup"><span data-stu-id="c93cb-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="c93cb-124">Implementace rozhraní pomocí třídy typů</span><span class="sxs-lookup"><span data-stu-id="c93cb-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="c93cb-125">Můžete implementovat jednu nebo více rozhraní v typu třídy pomocí `interface` – klíčové slovo, název rozhraní a `with` – klíčové slovo, za nímž následuje definice členů rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c93cb-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="c93cb-126">Implementace rozhraní se dědí, takže není potřeba znovu implementovat je všechny odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="c93cb-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="c93cb-127">Volání metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="c93cb-127">Calling Interface Methods</span></span>

<span data-ttu-id="c93cb-128">Metody rozhraní lze volat pouze prostřednictvím rozhraní, ne prostřednictvím libovolného objektu typu, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="c93cb-129">Proto může být nutné přetypování nahoru na typ rozhraní pomocí `:>` operátor nebo `upcast` operátor pro volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="c93cb-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="c93cb-130">Volání metody rozhraní, až budete mít objekt typu `SomeClass`, je nutné přetypování nahoru objektu na typ rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c93cb-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="c93cb-131">Alternativou je deklarovat metodu na objekt této upcasts a volá metodu rozhraní, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c93cb-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="c93cb-132">Implementace rozhraní s použitím objektových výrazů</span><span class="sxs-lookup"><span data-stu-id="c93cb-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="c93cb-133">Objektové výrazy poskytují krátký způsob, jak implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="c93cb-134">Jsou užitečné v případě nemusíte vytvářet pojmenované typy a chcete jenom objekt, který podporuje metody rozhraní, bez jakékoli další metody.</span><span class="sxs-lookup"><span data-stu-id="c93cb-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="c93cb-135">V následujícím kódu je znázorněn objektový výraz.</span><span class="sxs-lookup"><span data-stu-id="c93cb-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="c93cb-136">Dědičnost rozhraní</span><span class="sxs-lookup"><span data-stu-id="c93cb-136">Interface Inheritance</span></span>

<span data-ttu-id="c93cb-137">Rozhraní může dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c93cb-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="c93cb-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c93cb-138">See also</span></span>

- [<span data-ttu-id="c93cb-139">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="c93cb-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c93cb-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="c93cb-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="c93cb-141">Třídy</span><span class="sxs-lookup"><span data-stu-id="c93cb-141">Classes</span></span>](classes.md)
