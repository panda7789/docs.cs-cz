---
title: "Dědičnost (F#)"
description: "Zjistěte, jak určit vztahy F # dědičnosti pomocí klíčového slova 'inherit'."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a><span data-ttu-id="fda14-104">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="fda14-104">Inheritance</span></span>

<span data-ttu-id="fda14-105">Dědičnost je použita k modelování relace "je a", nebo vytvoření podtypů v objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="fda14-105">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="fda14-106">Určení relace dědičnosti</span><span class="sxs-lookup"><span data-stu-id="fda14-106">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="fda14-107">Zadejte vztahy dědičnosti pomocí `inherit` – klíčové slovo v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-107">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="fda14-108">Základní syntaktické formuláře je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fda14-108">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="fda14-109">Třída může mít maximálně jeden přímé základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-109">A class can have at most one direct base class.</span></span> <span data-ttu-id="fda14-110">Pokud nezadáte základní třídu pomocí `inherit` – klíčové slovo, třída implicitně dědí z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="fda14-110">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="fda14-111">Zděděné členy</span><span class="sxs-lookup"><span data-stu-id="fda14-111">Inherited Members</span></span>
<span data-ttu-id="fda14-112">Pokud třídy dědí z jiné třídy, jsou k dispozici uživatelům odvozené třídy, jako kdyby byly přímé členy odvozené třídy metody a členy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-112">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="fda14-113">Žádné let – vazby a konstruktor parametry jsou soukromá na třídu a proto nelze získat přístup z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-113">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="fda14-114">Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na instance základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-114">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="fda14-115">Používá se jako vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="fda14-115">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="fda14-116">Virtuální metody a přepsání</span><span class="sxs-lookup"><span data-stu-id="fda14-116">Virtual Methods and Overrides</span></span>
<span data-ttu-id="fda14-117">Virtuální metody (a vlastnosti) fungují trochu jinak F # porovnání s jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="fda14-117">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="fda14-118">Pokud chcete deklarovat nového člena virtuální, použijte `abstract` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fda14-118">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="fda14-119">Můžete to udělat bez ohledu na to, jestli je zadat výchozí implementace této metody.</span><span class="sxs-lookup"><span data-stu-id="fda14-119">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="fda14-120">Dokončení definice virtuální metodu v základní třídě tedy dodržuje tento vzor:</span><span class="sxs-lookup"><span data-stu-id="fda14-120">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="fda14-121">A v odvozené třídě, přepsání této virtuální metody, následuje tento vzor:</span><span class="sxs-lookup"><span data-stu-id="fda14-121">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="fda14-122">Pokud vynecháte výchozí implementace v základní třídě, základní třídy se změní na abstraktní třídu.</span><span class="sxs-lookup"><span data-stu-id="fda14-122">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="fda14-123">Následující příklad kódu ukazuje deklaraci nové virtuální metody `function1` ve základní třídu, jak k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fda14-123">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="fda14-124">Konstruktory a dědičnost</span><span class="sxs-lookup"><span data-stu-id="fda14-124">Constructors and Inheritance</span></span>
<span data-ttu-id="fda14-125">V konstruktoru pro základní třídy musí být voláno v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fda14-125">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="fda14-126">Argumenty pro konstruktor základní třídy se zobrazí v seznamu argument `inherit` klauzule.</span><span class="sxs-lookup"><span data-stu-id="fda14-126">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="fda14-127">Zadané argumenty konstruktoru odvozené třídy musí určit hodnoty, které se používají.</span><span class="sxs-lookup"><span data-stu-id="fda14-127">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="fda14-128">Následující kód ukazuje základní a odvozené třídy, kde odvozené třídě volá konstruktor základní třídy v klauzuli inherit:</span><span class="sxs-lookup"><span data-stu-id="fda14-128">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="fda14-129">V případě více konstruktory můžete použít následující kód.</span><span class="sxs-lookup"><span data-stu-id="fda14-129">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="fda14-130">První řádek z konstruktorů odvozené třídě je `inherit` klauzule a pole se zobrazí jako explicitní pole, které jsou deklarovány s `val` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fda14-130">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="fda14-131">Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="fda14-131">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="fda14-132">Alternativy k dědičnosti</span><span class="sxs-lookup"><span data-stu-id="fda14-132">Alternatives to Inheritance</span></span>
<span data-ttu-id="fda14-133">V případech, kdy je potřeba méně závažné změny typu zvažte použití výraz objektu jako alternativu k dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="fda14-133">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="fda14-134">Následující příklad ukazuje použití výraz objektu jako alternativu k vytvoření nového typu odvozené:</span><span class="sxs-lookup"><span data-stu-id="fda14-134">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="fda14-135">Další informace o objektové výrazy najdete v tématu [objektové výrazy](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fda14-135">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="fda14-136">Při vytváření objektu hierarchií, zvažte použití rozlišovaná sjednocení místo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="fda14-136">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="fda14-137">Rozlišovaná sjednocení může taky modelu nejrůznější chování různých objektů, které sdílejí společný typ celkové.</span><span class="sxs-lookup"><span data-stu-id="fda14-137">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="fda14-138">Jeden rozlišovaná sjednocení často eliminovat potřebu počet odvozené třídy, které jsou malým změnám.</span><span class="sxs-lookup"><span data-stu-id="fda14-138">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="fda14-139">Informace o rozlišovaná sjednocení najdete v tématu [Rozlišované sjednocení](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="fda14-139">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="fda14-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="fda14-140">See Also</span></span>
[<span data-ttu-id="fda14-141">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="fda14-141">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="fda14-142">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="fda14-142">F# Language Reference</span></span>](index.md)
