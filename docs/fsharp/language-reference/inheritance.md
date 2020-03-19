---
title: Dědičnost
description: Naučte se, jak zadat f# dědičnost vztahy pomocí 'inherit' klíčové slovo.
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400286"
---
# <a name="inheritance"></a><span data-ttu-id="260e4-103">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="260e4-103">Inheritance</span></span>

<span data-ttu-id="260e4-104">Dědičnost se používá k modelování vztahu "is-a" nebo subtypingu v objektově orientovaném programování.</span><span class="sxs-lookup"><span data-stu-id="260e4-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="260e4-105">Určení vztahů dědičnosti</span><span class="sxs-lookup"><span data-stu-id="260e4-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="260e4-106">Vztahy dědičnosti zadejte `inherit` pomocí klíčového slova v deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="260e4-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="260e4-107">Základní syntaktická forma je uvedena v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="260e4-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="260e4-108">Třída může mít maximálně jednu přímou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="260e4-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="260e4-109">Pokud nezadáte základní třídu pomocí `inherit` klíčového slova, třída `System.Object`implicitně dědí z .</span><span class="sxs-lookup"><span data-stu-id="260e4-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="260e4-110">Zdědění členové</span><span class="sxs-lookup"><span data-stu-id="260e4-110">Inherited Members</span></span>

<span data-ttu-id="260e4-111">Pokud třída dědí z jiné třídy, metody a členy základní třídy jsou k dispozici uživatelům odvozené třídy, jako by byli přímými členy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="260e4-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="260e4-112">Všechny let vazby a parametry konstruktoru jsou soukromé třídy a proto nelze přistupovat z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="260e4-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="260e4-113">Klíčové `base` slovo je k dispozici v odvozených třídách a odkazuje na instanci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="260e4-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="260e4-114">Používá se jako vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="260e4-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="260e4-115">Virtuální metody a lokální změny</span><span class="sxs-lookup"><span data-stu-id="260e4-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="260e4-116">Virtuální metody (a vlastnosti) fungují v jazyce F# poněkud odlišně ve srovnání s jinými jazyky .NET.</span><span class="sxs-lookup"><span data-stu-id="260e4-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="260e4-117">Chcete-li deklarovat nový `abstract` virtuální člen, použijte klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="260e4-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="260e4-118">To bez ohledu na to, zda zadáte výchozí implementaci pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="260e4-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="260e4-119">Úplná definice virtuální metody v základní třídě se tedy řídí tímto vzorem:</span><span class="sxs-lookup"><span data-stu-id="260e4-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="260e4-120">A v odvozené třídě přepsání této virtuální metody následuje tento vzor:</span><span class="sxs-lookup"><span data-stu-id="260e4-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="260e4-121">Pokud vyneche výchozí implementaci v základní třídě, základní třída se stane abstraktní třídou.</span><span class="sxs-lookup"><span data-stu-id="260e4-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="260e4-122">Následující příklad kódu ilustruje deklaraci nové `function1` virtuální metody v základní třídě a jak ji přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="260e4-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="260e4-123">Konstruktory a dědičnost</span><span class="sxs-lookup"><span data-stu-id="260e4-123">Constructors and Inheritance</span></span>

<span data-ttu-id="260e4-124">Konstruktor pro základní třídu musí být volána v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="260e4-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="260e4-125">Argumenty pro konstruktor základní třídy se zobrazí `inherit` v seznamu argumentů v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="260e4-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="260e4-126">Hodnoty, které jsou použity, musí být určeny z argumentů poskytnutých konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="260e4-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="260e4-127">Následující kód ukazuje základní třídu a odvozenou třídu, kde odvozená třída volá konstruktor základní třídy v klauzuli inherit:</span><span class="sxs-lookup"><span data-stu-id="260e4-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="260e4-128">V případě více konstruktorů lze použít následující kód.</span><span class="sxs-lookup"><span data-stu-id="260e4-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="260e4-129">První řádek konstruktorů odvozené třídy `inherit` je klauzule a pole se zobrazí `val` jako explicitní pole, která jsou deklarována pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="260e4-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="260e4-130">Další informace naleznete [v tématu Explicitní pole: `val` Klíčové slovo](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="260e4-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="260e4-131">Alternativy k dědičnosti</span><span class="sxs-lookup"><span data-stu-id="260e4-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="260e4-132">V případech, kdy je požadována menší změna typu, zvažte použití výrazu objektu jako alternativy k dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="260e4-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="260e4-133">Následující příklad ilustruje použití výrazu objektu jako alternativu k vytvoření nového odvozeného typu:</span><span class="sxs-lookup"><span data-stu-id="260e4-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="260e4-134">Další informace o výrazech objektů naleznete v [tématu Object Expressions](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="260e4-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="260e4-135">Při vytváření hierarchií objektů zvažte použití discriminated unie namísto dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="260e4-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="260e4-136">Discriminated sjednocení můžete také modelovat různé chování různých objektů, které sdílejí společný celkový typ.</span><span class="sxs-lookup"><span data-stu-id="260e4-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="260e4-137">Jeden discriminated unie může často eliminovat potřebu počet odvozených tříd, které jsou malé varianty navzájem.</span><span class="sxs-lookup"><span data-stu-id="260e4-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="260e4-138">Informace o discriminated sjednocení, naleznete [v tématu discriminated sjednocení](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="260e4-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="260e4-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="260e4-139">See also</span></span>

- [<span data-ttu-id="260e4-140">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="260e4-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="260e4-141">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="260e4-141">F# Language Reference</span></span>](index.md)
