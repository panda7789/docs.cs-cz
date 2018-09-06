---
title: Dědičnost (F#)
description: "Zjistěte, jak určit dědičnosti relací F # pomocí klíčového slova 'inherit'."
ms.date: 05/16/2016
ms.openlocfilehash: e4d79244fb9bada5db0c5c4c7179d4bfe6e21f3d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864466"
---
# <a name="inheritance"></a><span data-ttu-id="17b53-103">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="17b53-103">Inheritance</span></span>

<span data-ttu-id="17b53-104">Dědičnost se používají k modelování vztah "je a", nebo vytvoření podtypů v objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="17b53-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="17b53-105">Určení vztahy dědičnosti</span><span class="sxs-lookup"><span data-stu-id="17b53-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="17b53-106">Zadejte vztahy dědičnosti pomocí `inherit` – klíčové slovo v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="17b53-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="17b53-107">Základní formulář syntaktické je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="17b53-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="17b53-108">Třída může mít maximálně jednu přímou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="17b53-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="17b53-109">Pokud nezadáte základní třídy pomocí `inherit` – klíčové slovo, třídy implicitně dědí z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="17b53-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="17b53-110">Zděděné členy</span><span class="sxs-lookup"><span data-stu-id="17b53-110">Inherited Members</span></span>

<span data-ttu-id="17b53-111">Pokud třída dědí z jiné třídy, metody a členy základní třídy jsou dostupné uživatelům odvozené třídy, jako by byly přímé členy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="17b53-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="17b53-112">Některé vazby let a parametry konstruktoru jsou privátní pro třídu a proto ji nejde přistupovat z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="17b53-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="17b53-113">Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na základní třídu instance.</span><span class="sxs-lookup"><span data-stu-id="17b53-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="17b53-114">Používá se jako vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="17b53-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="17b53-115">Virtuální metody a přepsání</span><span class="sxs-lookup"><span data-stu-id="17b53-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="17b53-116">Virtuální metody (a vlastnosti) fungují odlišně v jazyce F # porovnání s jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="17b53-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="17b53-117">Chcete-li deklarovat nový virtuální člen, můžete použít `abstract` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="17b53-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="17b53-118">Můžete to provést bez ohledu na to, zda poskytuje výchozí implementaci pro danou metodu.</span><span class="sxs-lookup"><span data-stu-id="17b53-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="17b53-119">Kompletní definici virtuální metodu v základní třídě proto používá tento vzor:</span><span class="sxs-lookup"><span data-stu-id="17b53-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="17b53-120">A přepsání této virtuální metody v odvozené třídě, následuje tento model:</span><span class="sxs-lookup"><span data-stu-id="17b53-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="17b53-121">Vynecháte-li výchozí implementace v základní třídě, stane základní třídy abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="17b53-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="17b53-122">Následující příklad kódu znázorňuje deklaraci novou virtuální metodu `function1` v základní třídě a jak přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="17b53-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="17b53-123">Konstruktory a dědičnost</span><span class="sxs-lookup"><span data-stu-id="17b53-123">Constructors and Inheritance</span></span>

<span data-ttu-id="17b53-124">Musí být volána konstruktor základní třídy v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="17b53-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="17b53-125">Argumenty pro konstruktor základní třídy se zobrazí v seznamu argumentů v `inherit` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="17b53-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="17b53-126">Argumenty předány konstruktoru odvozené třídy musí určit hodnoty, které se používají.</span><span class="sxs-lookup"><span data-stu-id="17b53-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="17b53-127">Následující kód ukazuje základní třídu a odvozené třídy, kde odvozená třída volá konstruktor základní třídy v klauzuli dědičnosti:</span><span class="sxs-lookup"><span data-stu-id="17b53-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="17b53-128">V případě více konstruktorů můžete použít následující kód.</span><span class="sxs-lookup"><span data-stu-id="17b53-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="17b53-129">První řádek konstruktory odvozené třídy je `inherit` klauzule a pole se zobrazí jako explicitní pole, které jsou deklarovány pomocí `val` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="17b53-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="17b53-130">Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="17b53-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="17b53-131">Alternativy k dědičnosti</span><span class="sxs-lookup"><span data-stu-id="17b53-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="17b53-132">V případech, kdy se vyžaduje méně závažnou změnu typu zvažte použití výrazu objektu jako alternativu k dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="17b53-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="17b53-133">Následující příklad ukazuje použití výrazu objektu jako alternativu k vytváření nového odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="17b53-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="17b53-134">Další informace o objektových výrazů naleznete v tématu [objektové výrazy](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17b53-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="17b53-135">Při vytváření hierarchie objektů, zvažte použití diskriminované sjednocení namísto dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="17b53-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="17b53-136">Rozlišovaná sjednocení můžou také modelu měnit chování různých objektů, které sdílejí společný typ celkové.</span><span class="sxs-lookup"><span data-stu-id="17b53-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="17b53-137">Jeden diskriminované sjednocení může často eliminovat potřebu počet odvozených tříd, které jsou menší variant.</span><span class="sxs-lookup"><span data-stu-id="17b53-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="17b53-138">Informace o rozlišovaná sjednocení, naleznete v tématu [Rozlišované sjednocení](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="17b53-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17b53-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17b53-139">See also</span></span>

- [<span data-ttu-id="17b53-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="17b53-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="17b53-141">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="17b53-141">F# Language Reference</span></span>](index.md)
