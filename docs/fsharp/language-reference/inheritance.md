---
title: Dědičnost (F#)
description: "Zjistěte, jak určit vztahy F # dědičnosti pomocí klíčového slova 'inherit'."
ms.date: 05/16/2016
ms.openlocfilehash: 3d0c0785fc595315a8283979b99d0ec4fc5cbc0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564762"
---
# <a name="inheritance"></a><span data-ttu-id="2f810-103">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="2f810-103">Inheritance</span></span>

<span data-ttu-id="2f810-104">Dědičnost je použita k modelování relace "je a", nebo vytvoření podtypů v objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="2f810-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="2f810-105">Určení relace dědičnosti</span><span class="sxs-lookup"><span data-stu-id="2f810-105">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="2f810-106">Zadejte vztahy dědičnosti pomocí `inherit` – klíčové slovo v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="2f810-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="2f810-107">Základní syntaktické formuláře je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2f810-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="2f810-108">Třída může mít maximálně jeden přímé základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2f810-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="2f810-109">Pokud nezadáte základní třídu pomocí `inherit` – klíčové slovo, třída implicitně dědí z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="2f810-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="2f810-110">Zděděné členy</span><span class="sxs-lookup"><span data-stu-id="2f810-110">Inherited Members</span></span>
<span data-ttu-id="2f810-111">Pokud třídy dědí z jiné třídy, jsou k dispozici uživatelům odvozené třídy, jako kdyby byly přímé členy odvozené třídy metody a členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2f810-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="2f810-112">Žádné let – vazby a konstruktor parametry jsou soukromá na třídu a proto nelze získat přístup z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="2f810-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="2f810-113">Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na instance základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2f810-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="2f810-114">Používá se jako vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="2f810-114">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="2f810-115">Virtuální metody a přepsání</span><span class="sxs-lookup"><span data-stu-id="2f810-115">Virtual Methods and Overrides</span></span>
<span data-ttu-id="2f810-116">Virtuální metody (a vlastnosti) fungují trochu jinak F # porovnání s jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2f810-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="2f810-117">Pokud chcete deklarovat nového člena virtuální, použijte `abstract` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2f810-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="2f810-118">Můžete to udělat bez ohledu na to, jestli je zadat výchozí implementace této metody.</span><span class="sxs-lookup"><span data-stu-id="2f810-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="2f810-119">Dokončení definice virtuální metodu v základní třídě tedy dodržuje tento vzor:</span><span class="sxs-lookup"><span data-stu-id="2f810-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="2f810-120">A v odvozené třídě, přepsání této virtuální metody, následuje tento vzor:</span><span class="sxs-lookup"><span data-stu-id="2f810-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="2f810-121">Pokud vynecháte výchozí implementace v základní třídě, základní třídy se změní na abstraktní třídu.</span><span class="sxs-lookup"><span data-stu-id="2f810-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="2f810-122">Následující příklad kódu ukazuje deklaraci nové virtuální metody `function1` ve základní třídu, jak k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="2f810-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="2f810-123">Konstruktory a dědičnost</span><span class="sxs-lookup"><span data-stu-id="2f810-123">Constructors and Inheritance</span></span>
<span data-ttu-id="2f810-124">V konstruktoru pro základní třídy musí být voláno v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="2f810-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="2f810-125">Argumenty pro konstruktor základní třídy se zobrazí v seznamu argument `inherit` klauzule.</span><span class="sxs-lookup"><span data-stu-id="2f810-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="2f810-126">Zadané argumenty konstruktoru odvozené třídy musí určit hodnoty, které se používají.</span><span class="sxs-lookup"><span data-stu-id="2f810-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="2f810-127">Následující kód ukazuje základní a odvozené třídy, kde odvozené třídě volá konstruktor základní třídy v klauzuli inherit:</span><span class="sxs-lookup"><span data-stu-id="2f810-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="2f810-128">V případě více konstruktory můžete použít následující kód.</span><span class="sxs-lookup"><span data-stu-id="2f810-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="2f810-129">První řádek z konstruktorů odvozené třídě je `inherit` klauzule a pole se zobrazí jako explicitní pole, které jsou deklarovány s `val` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2f810-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="2f810-130">Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="2f810-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="2f810-131">Alternativy k dědičnosti</span><span class="sxs-lookup"><span data-stu-id="2f810-131">Alternatives to Inheritance</span></span>
<span data-ttu-id="2f810-132">V případech, kdy je potřeba méně závažné změny typu zvažte použití výraz objektu jako alternativu k dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="2f810-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="2f810-133">Následující příklad ukazuje použití výraz objektu jako alternativu k vytvoření nového typu odvozené:</span><span class="sxs-lookup"><span data-stu-id="2f810-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="2f810-134">Další informace o objektové výrazy najdete v tématu [objektové výrazy](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2f810-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="2f810-135">Při vytváření objektu hierarchií, zvažte použití rozlišovaná sjednocení místo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="2f810-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="2f810-136">Rozlišovaná sjednocení může taky modelu nejrůznější chování různých objektů, které sdílejí společný typ celkové.</span><span class="sxs-lookup"><span data-stu-id="2f810-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="2f810-137">Jeden rozlišovaná sjednocení často eliminovat potřebu počet odvozené třídy, které jsou malým změnám.</span><span class="sxs-lookup"><span data-stu-id="2f810-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="2f810-138">Informace o rozlišovaná sjednocení najdete v tématu [Rozlišované sjednocení](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="2f810-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="2f810-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f810-139">See Also</span></span>
[<span data-ttu-id="2f810-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="2f810-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="2f810-141">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2f810-141">F# Language Reference</span></span>](index.md)
