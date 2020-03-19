---
title: Parametry a argumenty
description: Další informace o podpoře jazyka F# pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400195"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="cf87a-103">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="cf87a-103">Parameters and Arguments</span></span>

<span data-ttu-id="cf87a-104">Toto téma popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="cf87a-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="cf87a-105">Obsahuje informace o tom, jak předat odkaz emitovat a jak definovat a používat metody, které mohou mít proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="cf87a-106">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="cf87a-106">Parameters and Arguments</span></span>

<span data-ttu-id="cf87a-107">Termín *parametr* se používá k popisu názvů pro hodnoty, které se očekává, že budou dodány.</span><span class="sxs-lookup"><span data-stu-id="cf87a-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="cf87a-108">Termín *argument* se používá pro hodnoty uvedené pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="cf87a-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="cf87a-109">Parametry lze zadat v n-tice nebo curried formě nebo v nějaké kombinaci obou.</span><span class="sxs-lookup"><span data-stu-id="cf87a-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="cf87a-110">Argumenty můžete předat pomocí explicitního názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="cf87a-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="cf87a-111">Parametry metod mohou být zadány jako volitelné a má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="cf87a-112">Vzorky parametrů</span><span class="sxs-lookup"><span data-stu-id="cf87a-112">Parameter Patterns</span></span>

<span data-ttu-id="cf87a-113">Parametry dodávané funkcím a metodám jsou obecně vzory oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="cf87a-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="cf87a-114">To znamená, že v zásadě některý ze vzorů popsaných v [match výrazy](match-expressions.md) lze použít v seznamu parametrů pro funkci nebo člena.</span><span class="sxs-lookup"><span data-stu-id="cf87a-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="cf87a-115">Metody obvykle používají n-tice formulář předávání argumentů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="cf87a-116">Tím se dosáhne jasnější výsledek z hlediska jiných jazyků .NET, protože n-tice formulář odpovídá způsobu, jakým jsou argumenty předány v metodách .NET.</span><span class="sxs-lookup"><span data-stu-id="cf87a-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="cf87a-117">Curried formulář se nejčastěji používá s `let` funkcemi vytvořenými pomocí vazeb.</span><span class="sxs-lookup"><span data-stu-id="cf87a-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="cf87a-118">Následující pseudokód ukazuje příklady řazené kolekce členů a curried argumenty.</span><span class="sxs-lookup"><span data-stu-id="cf87a-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="cf87a-119">Kombinované formuláře jsou možné, pokud některé argumenty jsou v řazených kolekcí členů a některé nejsou.</span><span class="sxs-lookup"><span data-stu-id="cf87a-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="cf87a-120">Jiné vzorky lze také použít v seznamech parametrů, ale pokud vzorek parametru neodpovídá všem možným vstupům, může být neúplná shoda za běhu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="cf87a-121">Výjimka `MatchFailureException` je generována, pokud hodnota argumentu neodpovídá vzorům zadaným v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="cf87a-122">Kompilátor vydá upozornění, pokud vzor parametru umožňuje neúplné shody.</span><span class="sxs-lookup"><span data-stu-id="cf87a-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="cf87a-123">Alespoň jeden další vzor je běžně užitečné pro seznamy parametrů, a to je zástupný vzor.</span><span class="sxs-lookup"><span data-stu-id="cf87a-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="cf87a-124">Vzor se zástupnými kódy v seznamu parametrů použijete, pokud chcete jednoduše ignorovat všechny zadané argumenty.</span><span class="sxs-lookup"><span data-stu-id="cf87a-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="cf87a-125">Následující kód ilustruje použití zástupného vzoru v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="cf87a-126">Vzorek se zástupnými symboly může být užitečný vždy, když nepotřebujete předané argumenty, například v hlavním vstupním bodu programu, pokud vás nezajímají argumenty příkazového řádku, které jsou obvykle dodávány jako pole řetězců, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="cf87a-127">Jiné vzory, které se někdy používají `as` v argumentech jsou vzor a identifikátor vzory spojené s discriminated sjednocení a aktivní vzory.</span><span class="sxs-lookup"><span data-stu-id="cf87a-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="cf87a-128">Můžete použít jeden případ discriminated unie vzor takto.</span><span class="sxs-lookup"><span data-stu-id="cf87a-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="cf87a-129">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf87a-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="cf87a-130">Aktivní vzorky mohou být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cf87a-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="cf87a-131">`as` Vzor můžete použít k uložení odpovídající hodnoty jako místní hodnoty, jak je znázorněno v následujícím řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="cf87a-132">Jiný vzor, který se používá příležitostně je funkce, která ponechává poslední argument nepojmenovaný poskytnutím, jako tělo funkce, lambda výraz, který okamžitě provede porovnávání vzoru na implicitní argument.</span><span class="sxs-lookup"><span data-stu-id="cf87a-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="cf87a-133">Příkladem je následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="cf87a-134">Tento kód definuje funkci, která přebírá `true` obecný seznam a vrátí, pokud je seznam prázdný a `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="cf87a-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="cf87a-135">Použití těchto technik může ztížit čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="cf87a-136">V některých případě vzorky, které zahrnují neúplné shody jsou užitečné, například pokud víte, že seznamy v programu mají pouze tři prvky, můžete použít vzor, jako je následující v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="cf87a-137">Použití vzorů, které mají neúplné shody je nejlepší vyhrazena pro rychlé vytváření prototypů a další dočasná použití.</span><span class="sxs-lookup"><span data-stu-id="cf87a-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="cf87a-138">Kompilátor vydá upozornění pro takový kód.</span><span class="sxs-lookup"><span data-stu-id="cf87a-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="cf87a-139">Takové vzory nemohou pokrývat obecný případ všech možných vstupů, a proto nejsou vhodné pro komponentní api.</span><span class="sxs-lookup"><span data-stu-id="cf87a-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="cf87a-140">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="cf87a-140">Named Arguments</span></span>

<span data-ttu-id="cf87a-141">Argumenty pro metody mohou být určeny podle pozice v seznamu argumentů oddělených čárkami nebo mohou být explicitně předány metodě zadáním názvu, následovaným rovnítkem a hodnotou, která má být předána.</span><span class="sxs-lookup"><span data-stu-id="cf87a-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="cf87a-142">Pokud je zadán zadáním názvu, mohou se objevit v jiném pořadí, než které bylo použito v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="cf87a-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="cf87a-143">Pojmenované argumenty mohou kód čitelnější a adaptabilnější pro určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="cf87a-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="cf87a-144">Pojmenované argumenty jsou povoleny pouze `let`pro metody, nikoli pro vázané funkce, hodnoty funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="cf87a-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="cf87a-145">Následující příklad kódu ukazuje použití pojmenovaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="cf87a-146">Při volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné syntaxi pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="cf87a-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="cf87a-147">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="cf87a-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="cf87a-148">Další informace naleznete v [tématu Konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="cf87a-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="cf87a-149">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="cf87a-149">Optional Parameters</span></span>

<span data-ttu-id="cf87a-150">Volitelný parametr metody můžete zadat pomocí otazníku před názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="cf87a-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="cf87a-151">Volitelné parametry jsou interpretovány jako typ možnosti F#, takže je můžete pravidelně dotazovat, `match` že `Some` `None`typy možností jsou dotazovány pomocí výrazu s a .</span><span class="sxs-lookup"><span data-stu-id="cf87a-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="cf87a-152">Volitelné parametry jsou povoleny pouze na členy, `let` nikoli na funkce vytvořené pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="cf87a-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="cf87a-153">Existující volitelné hodnoty můžete předat metodě podle `?arg=None` `?arg=Some(3)` názvu `?arg=arg`parametru, například nebo nebo .</span><span class="sxs-lookup"><span data-stu-id="cf87a-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="cf87a-154">To může být užitečné při vytváření metody, která předá volitelné argumenty jiné metodě.</span><span class="sxs-lookup"><span data-stu-id="cf87a-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="cf87a-155">Můžete také použít `defaultArg`funkci , která nastaví výchozí hodnotu volitelného argumentu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="cf87a-156">Funkce `defaultArg` přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.</span><span class="sxs-lookup"><span data-stu-id="cf87a-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="cf87a-157">Následující příklad ilustruje použití volitelných parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="cf87a-158">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf87a-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="cf87a-159">Pro účely Interop Jazyka C# a Visual Basic `[<Optional; DefaultParameterValue<(...)>]` můžete použít atributy v Jazyce F#, takže volající uvidí argument jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="cf87a-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="cf87a-160">To je ekvivalentní definování argumentu jako volitelné `MyMethod(int i = 3)`v c# jako v .</span><span class="sxs-lookup"><span data-stu-id="cf87a-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="cf87a-161">Jako výchozí hodnotu parametru můžete také zadat nový objekt.</span><span class="sxs-lookup"><span data-stu-id="cf87a-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="cf87a-162">`Foo` Člen může mít například `CancellationToken` volitelný jako vstup místo:</span><span class="sxs-lookup"><span data-stu-id="cf87a-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="cf87a-163">Hodnota uvedená jako `DefaultParameterValue` argument musí odpovídat typu parametru.</span><span class="sxs-lookup"><span data-stu-id="cf87a-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="cf87a-164">Například následující není povoleno:</span><span class="sxs-lookup"><span data-stu-id="cf87a-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="cf87a-165">V tomto případě kompilátor generuje upozornění a bude ignorovat oba atributy úplně.</span><span class="sxs-lookup"><span data-stu-id="cf87a-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="cf87a-166">Všimněte si, `null` že výchozí hodnota musí být typu anotována, protože jinak kompilátor `[<Optional; DefaultParameterValue(null:obj)>] o:obj`odvodí nesprávný typ, tj.</span><span class="sxs-lookup"><span data-stu-id="cf87a-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="cf87a-167">Předání odkazem</span><span class="sxs-lookup"><span data-stu-id="cf87a-167">Passing by Reference</span></span>

<span data-ttu-id="cf87a-168">Předání hodnoty F# odkazem zahrnuje [byrefs](byrefs.md), které jsou spravované typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="cf87a-169">Pokyny, pro který typ použít, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="cf87a-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="cf87a-170">Použijte, `inref<'T>` pokud potřebujete pouze číst ukazatel.</span><span class="sxs-lookup"><span data-stu-id="cf87a-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="cf87a-171">Použijte, `outref<'T>` pokud potřebujete pouze zapisovat do ukazatele.</span><span class="sxs-lookup"><span data-stu-id="cf87a-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="cf87a-172">Použijte, `byref<'T>` pokud potřebujete číst z a zapisovat do ukazatele.</span><span class="sxs-lookup"><span data-stu-id="cf87a-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="cf87a-173">Vzhledem k tomu, že parametr je ukazatel a hodnota je proměnlivá, všechny změny hodnoty jsou zachovány po spuštění funkce.</span><span class="sxs-lookup"><span data-stu-id="cf87a-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="cf87a-174">Řazenou kolekce členů můžete použít `out` jako vrácenou hodnotu k uložení libovolných parametrů v metodách knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="cf87a-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="cf87a-175">Alternativně můžete považovat `out` parametr jako `byref` parametr.</span><span class="sxs-lookup"><span data-stu-id="cf87a-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="cf87a-176">Následující příklad kódu ilustruje oba způsoby.</span><span class="sxs-lookup"><span data-stu-id="cf87a-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="cf87a-177">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="cf87a-177">Parameter Arrays</span></span>

<span data-ttu-id="cf87a-178">V některých případě je nutné definovat funkci, která má libovolný počet parametrů heterogenního typu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="cf87a-179">Nebylo by praktické vytvořit všechny možné přetížené metody k účtu pro všechny typy, které by mohly být použity.</span><span class="sxs-lookup"><span data-stu-id="cf87a-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="cf87a-180">Implementace .NET poskytují podporu pro tyto metody prostřednictvím funkce pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="cf87a-181">Metoda, která má pole parametrů v jeho podpisu může být poskytnuta libovolný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="cf87a-182">Parametry jsou vloženy do pole.</span><span class="sxs-lookup"><span data-stu-id="cf87a-182">The parameters are put into an array.</span></span> <span data-ttu-id="cf87a-183">Typ prvků pole určuje typy parametrů, které mohou být předány funkci.</span><span class="sxs-lookup"><span data-stu-id="cf87a-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="cf87a-184">Pokud definujete pole `System.Object` parametrů jako typ prvku, pak kód klienta může předat hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="cf87a-185">V F# pole parametrů lze definovat pouze v metodách.</span><span class="sxs-lookup"><span data-stu-id="cf87a-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="cf87a-186">Nelze je použít v samostatných funkcích nebo funkcích, které jsou definovány v modulech.</span><span class="sxs-lookup"><span data-stu-id="cf87a-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="cf87a-187">Pole parametrů definujete pomocí `ParamArray` atributu.</span><span class="sxs-lookup"><span data-stu-id="cf87a-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="cf87a-188">Atribut `ParamArray` lze použít pouze na poslední parametr.</span><span class="sxs-lookup"><span data-stu-id="cf87a-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="cf87a-189">Následující kód ilustruje volání metody .NET, která přebírá pole parametrů, a definici typu v f#, která má metodu, která přebírá pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="cf87a-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="cf87a-190">Při spuštění v projektu je výstup předchozího kódu následující:</span><span class="sxs-lookup"><span data-stu-id="cf87a-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="cf87a-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf87a-191">See also</span></span>

- [<span data-ttu-id="cf87a-192">Členové</span><span class="sxs-lookup"><span data-stu-id="cf87a-192">Members</span></span>](./members/index.md)
