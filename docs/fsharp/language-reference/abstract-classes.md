---
title: Abstraktní třídy (F#)
description: 'Další informace o F # abstraktní třídy, které nechte některé nebo všechny členy Neimplementovaný a představují běžné funkce různého typu typy objektů.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0d7ca996de89c44a5cfb9197c1b515741a2303df
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="abstract-classes"></a><span data-ttu-id="dd58c-103">Abstraktní třídy</span><span class="sxs-lookup"><span data-stu-id="dd58c-103">Abstract Classes</span></span>

<span data-ttu-id="dd58c-104">*Abstraktní třídy* jsou třídy, která opouští některé nebo všechny členy Neimplementovaný, tak, aby implementace lze zadat odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dd58c-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd58c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd58c-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="dd58c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd58c-106">Remarks</span></span>
<span data-ttu-id="dd58c-107">V objektově orientované programování abstraktní třída se používá jako základní třída hierarchie a představuje běžné funkce různého typu typy objektů.</span><span class="sxs-lookup"><span data-stu-id="dd58c-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="dd58c-108">Jako název "abstraktní" znamená, abstraktní třídy často neodpovídají přímo na konkrétní entity v doméně problému.</span><span class="sxs-lookup"><span data-stu-id="dd58c-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="dd58c-109">Však představují co mnoho různých konkrétní entit mají společnou.</span><span class="sxs-lookup"><span data-stu-id="dd58c-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="dd58c-110">Abstraktní třídy musí mít `AbstractClass` atribut.</span><span class="sxs-lookup"><span data-stu-id="dd58c-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="dd58c-111">Může být implementováno a Neimplementovaný členy.</span><span class="sxs-lookup"><span data-stu-id="dd58c-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="dd58c-112">Použití podmínek *abstraktní* při použití třídy je stejný jako jinými jazyky rozhraní .NET; však použití podmínek *abstraktní* při použití metody (a vlastnosti) je mírně liší v F # z jeho použijte v jinými jazyky rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="dd58c-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="dd58c-113">V F #, když je označené jako metodu `abstract` – klíčové slovo, to znamená, že člen má položku, označuje jako *virtuální odesílání slotu*, do interní tabulky pro tento typ virtuální funkce.</span><span class="sxs-lookup"><span data-stu-id="dd58c-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="dd58c-114">Jinými slovy, že je metoda virtuální, i když `virtual` – klíčové slovo se nepoužívá v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="dd58c-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="dd58c-115">Klíčové slovo `abstract` se používá pro virtuální metody bez ohledu na to, zda je metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="dd58c-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="dd58c-116">Prohlášení o slot virtuální odesílání je oddělené od definici metody pro tento slot odesílání.</span><span class="sxs-lookup"><span data-stu-id="dd58c-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="dd58c-117">Proto ekvivalentní F # virtuální metoda deklarace a definice v jiném jazyce .NET je kombinací deklarace abstraktní metody i samostatné definice, pomocí `default` – klíčové slovo nebo `override` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dd58c-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="dd58c-118">Další informace a příklady naleznete v tématu [metody](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="dd58c-118">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="dd58c-119">Třída je považován za abstraktní pouze v případě, že existují abstraktní metody, které jsou deklarované, ale není definován.</span><span class="sxs-lookup"><span data-stu-id="dd58c-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="dd58c-120">Proto tříd, které mají abstraktní metody nejsou nezbytně abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="dd58c-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="dd58c-121">Pokud třída má undefined abstraktní metody, nepoužívejte **abstractclass –** atribut.</span><span class="sxs-lookup"><span data-stu-id="dd58c-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="dd58c-122">V předchozích syntaxi *modifikátor dostupnosti* může být `public`, `private` nebo `internal`.</span><span class="sxs-lookup"><span data-stu-id="dd58c-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="dd58c-123">Další informace najdete v tématu [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="dd58c-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="dd58c-124">Jako u jiných typů, může mít abstraktní třídy základní třídy a jeden nebo více základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dd58c-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="dd58c-125">Každý základní třídy nebo rozhraní se zobrazí na samostatném řádku společně s `inherit` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dd58c-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="dd58c-126">Definici typu abstraktní třídy mohou obsahovat plně definované členy, ale může také obsahovat abstraktní členy.</span><span class="sxs-lookup"><span data-stu-id="dd58c-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="dd58c-127">Syntaxe pro abstraktní členy se zobrazí samostatně v předchozí syntaxi.</span><span class="sxs-lookup"><span data-stu-id="dd58c-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="dd58c-128">V této syntaxe *podpis typu* člena je seznam, který obsahuje parametr typy v pořadí a návratové typy oddělená `->` tokeny nebo `*` tokeny podle potřeby pro curryfikované a tupled Parametry.</span><span class="sxs-lookup"><span data-stu-id="dd58c-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="dd58c-129">Syntaxe pro podpisy člen abstraktní typ je stejný jako použitého v podpisu souborů a zobrazená technologii IntelliSense v editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dd58c-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="dd58c-130">Následující kód ukazuje abstraktní třídu tvar, který má jinou než abstraktní odvozené třídy hranaté a kruh.</span><span class="sxs-lookup"><span data-stu-id="dd58c-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="dd58c-131">Příklad ukazuje postup používání abstraktních tříd, metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="dd58c-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="dd58c-132">V příkladu představuje abstraktní třídu tvar běžných elementech kruh konkrétní entity a hranaté.</span><span class="sxs-lookup"><span data-stu-id="dd58c-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="dd58c-133">Běžné funkce všech tvarů (v dvourozměrná souřadnicový systém) jsou abstrahované odhlašování do třídy tvaru: pozici na mřížky, úhel otočení a vlastnosti oblasti a hraniční.</span><span class="sxs-lookup"><span data-stu-id="dd58c-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="dd58c-134">To může být přepsána, s výjimkou pozice, chování, které nelze změnit jednotlivých tvarů.</span><span class="sxs-lookup"><span data-stu-id="dd58c-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="dd58c-135">Jako kruh třída, která je otočení neutrální z důvodu jeho symetrie lze přepsat metodu otočení.</span><span class="sxs-lookup"><span data-stu-id="dd58c-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="dd58c-136">Proto v třídě kruh metodu otočení nahrazuje metodu, která se nic nestane.</span><span class="sxs-lookup"><span data-stu-id="dd58c-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="dd58c-137">**Výstup:**</span><span class="sxs-lookup"><span data-stu-id="dd58c-137">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="dd58c-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd58c-138">See Also</span></span>
[<span data-ttu-id="dd58c-139">Třídy</span><span class="sxs-lookup"><span data-stu-id="dd58c-139">Classes</span></span>](classes.md)

[<span data-ttu-id="dd58c-140">Členové</span><span class="sxs-lookup"><span data-stu-id="dd58c-140">Members</span></span>](members/index.md)

[<span data-ttu-id="dd58c-141">Metody</span><span class="sxs-lookup"><span data-stu-id="dd58c-141">Methods</span></span>](members/methods.md)

[<span data-ttu-id="dd58c-142">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dd58c-142">Properties</span></span>](members/Properties.md)
