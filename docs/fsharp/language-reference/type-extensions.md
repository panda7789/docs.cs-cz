---
title: Rozšíření typů (F#)
description: 'Zjistěte, jak povolit rozšíření typů F #, že přidáte nové členy typu dříve definovaném objektu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 3399778799fbf0f8eee56e332135656150918a60
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-extensions"></a><span data-ttu-id="fbeaa-103">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="fbeaa-103">Type Extensions</span></span>

<span data-ttu-id="fbeaa-104">Typ rozšíření můžete přidat nové členy typu dříve definovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-104">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbeaa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbeaa-105">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="fbeaa-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbeaa-106">Remarks</span></span>
<span data-ttu-id="fbeaa-107">Existují dvě formy typ rozšíření, které mají mírně odlišné syntaxe a chování.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-107">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="fbeaa-108">*Vnitřní rozšíření* jako typ rozšiřovanou je rozšíření, které se zobrazí ve stejném oboru názvů nebo modul, ve stejném souboru zdroje a ve stejném sestavení (DLL nebo spustitelného souboru).</span><span class="sxs-lookup"><span data-stu-id="fbeaa-108">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="fbeaa-109">*Volitelné rozšíření* je rozšíření, které se zobrazí mimo původní modulu, obor názvů nebo sestavení rozšiřovanou typu.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-109">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="fbeaa-110">Vnitřní rozšíření zobrazí na typ, pokud typ je zkontrolován pomocí reflexe, ale nechcete volitelná rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-110">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="fbeaa-111">Volitelné rozšíření musí být v modulech a jsou pouze v oboru, když modul, který obsahuje rozšíření je otevřený.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-111">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="fbeaa-112">V předchozích syntaxi *typename* představuje typ, který je právě rozšířeno.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-112">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="fbeaa-113">Je možné rozšířit žádný typ, který je přístupný, ale název typu musí být název skutečný typ zkratka typu.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-113">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="fbeaa-114">Můžete definovat více členů v jeden typ rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-114">You can define multiple members in one type extension.</span></span> <span data-ttu-id="fbeaa-115">*Vlastní identifikátor* představuje instanci objektu volaná, stejně jako obyčejnou členy.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-115">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="fbeaa-116">`end` – Klíčové slovo je v prostá syntaxe volitelné.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-116">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="fbeaa-117">Stejně jako ostatní členové na typu třídy lze členy definovanou v rozšíření typu.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-117">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="fbeaa-118">Podobně jako ostatní členové mohou být statické nebo instance členy.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-118">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="fbeaa-119">Tyto metody se také označují jako *rozšiřující metody*; vlastnosti se označují jako *– vlastnosti rozšíření*a tak dále.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-119">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="fbeaa-120">Volitelné rozšíření členy zkompilovány pro statické členy, pro které se implicitně předá instanci objektu jako první parametr.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-120">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="fbeaa-121">Však budou fungovat, jako kdyby byly členy instancí nebo statické členy podle jak jsou deklarované.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-121">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="fbeaa-122">Implicitní rozšíření členové jsou zahrnuty mezi členy typu a dá se používat bez omezení.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-122">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="fbeaa-123">Metody rozšíření nemůže být virtuální nebo abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-123">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="fbeaa-124">Se může přetížit jiných metod se stejným názvem, ale dává přednost bez rozšiřující metody v případě nejednoznačné volání do kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-124">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="fbeaa-125">Pokud pro jeden typ existuje několik rozšíření vnitřního typu, všichni členové musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-125">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="fbeaa-126">Pro typ volitelné rozšíření mohou mít členové v jiný typ rozšíření do stejného typu stejné názvy.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-126">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="fbeaa-127">Pouze v případě, že kód klienta otevře dva různé obory, které definují stejné názvy členů dojít k chybám nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-127">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="fbeaa-128">V následujícím příkladu má typ v modulu vnitřní typ rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-128">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="fbeaa-129">Na kód klienta mimo modul typ rozšíření se zobrazí jako regulární člen typu ve všech ohledech.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-129">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="fbeaa-130">Vnitřní typ rozšíření můžete použít k oddělení definici typu do oddílů.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-130">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="fbeaa-131">To může být užitečné při správě definice rozsáhlého typu, například si nechat generované kompilátorem kód a kód vytvořené v samostatné nebo seskupit kód vytvořené jiné osoby nebo ve spojení s jinou funkci.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-131">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="fbeaa-132">V následujícím příkladu rozšiřuje volitelné typu rozšíření `System.Int32` typ pomocí metody rozšíření `FromString` statický člen, který volá `Parse`.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-132">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="fbeaa-133">`testFromString` Metoda ukazuje, že stejně jako libovolný člen instance se nazývá nového člena.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-133">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="fbeaa-134">Nový člen instance se zobrazí jako jakékoliv jiné metody `Int32` typu v technologii IntelliSense, ale jenom v případě, že modul, který obsahuje rozšíření je otevřené nebo jinak v oboru.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-134">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="fbeaa-135">Obecný rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="fbeaa-135">Generic Extension Methods</span></span>
<span data-ttu-id="fbeaa-136">Před F # 3.1, kompilátor jazyka F # nepodporovala použití jazyka C# – styl rozšiřující metody s proměnné obecného typu, typ pole, řazené kolekce členů nebo typu funkce F # jako parametr "Tento".</span><span class="sxs-lookup"><span data-stu-id="fbeaa-136">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="fbeaa-137">F # 3.1 podporuje použití těchto rozšíření členů.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-137">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="fbeaa-138">Například v F # 3.1 kódu, můžete použít metody rozšíření s podpisy, které se podobají syntaxi v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="fbeaa-138">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="fbeaa-139">Tento postup je zvlášť užitečné, když je omezené parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-139">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="fbeaa-140">Navíc můžete teď deklarovat rozšíření členy takto v F # – kód a definovat další, sémanticky bohatou sadu rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-140">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="fbeaa-141">V jazyce F # obvykle definovat rozšíření členy jako následující příklad ukazuje:</span><span class="sxs-lookup"><span data-stu-id="fbeaa-141">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="fbeaa-142">Ale pro obecný typ, nemusí být omezené proměnná typu.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-142">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="fbeaa-143">Nyní můžete deklarovat C# – styl rozšíření člena v F # na toto omezení obejít.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-143">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="fbeaa-144">Když zkombinujete tento druh deklarace s vložených funkcí jazyka F #, může být obecné algoritmy jako rozšíření členy.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-144">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="fbeaa-145">Vezměte v úvahu následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="fbeaa-145">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="fbeaa-146">Pomocí tohoto prohlášení, můžete napsat kód, který se podobá následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-146">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="fbeaa-147">V tomto kódu má stejný kód obecné aritmetické použije dva typy seznamů bez přetížení definováním členem jedné rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fbeaa-147">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="fbeaa-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbeaa-148">See Also</span></span>
[<span data-ttu-id="fbeaa-149">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="fbeaa-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="fbeaa-150">Členové</span><span class="sxs-lookup"><span data-stu-id="fbeaa-150">Members</span></span>](members/index.md)
