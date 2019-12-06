---
title: Parametry a argumenty
description: Přečtěte F# si o jazykové podpoře pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837126"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="3cd9b-103">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="3cd9b-103">Parameters and Arguments</span></span>

<span data-ttu-id="3cd9b-104">Toto téma popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="3cd9b-105">Obsahuje informace o tom, jak předat odkaz, a jak definovat a používat metody, které mohou převzít proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="3cd9b-106">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="3cd9b-106">Parameters and Arguments</span></span>

<span data-ttu-id="3cd9b-107">*Parametr* Term slouží k popisu názvů pro hodnoty, které mají být dodány.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="3cd9b-108">Termínový *argument* se používá pro hodnoty zadané pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="3cd9b-109">Parametry lze zadat v řazené kolekci členů nebo ve formě curryfikované nebo v některé kombinaci dvou.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="3cd9b-110">Argumenty můžete předat pomocí explicitního názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="3cd9b-111">Parametry metod lze zadat jako nepovinné a předávat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="3cd9b-112">Vzory parametrů</span><span class="sxs-lookup"><span data-stu-id="3cd9b-112">Parameter Patterns</span></span>

<span data-ttu-id="3cd9b-113">Parametry, které jsou zadány pro funkce a metody, jsou obecně vzory oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="3cd9b-114">To znamená, že v zásadě lze kterýkoli ze vzorů popsaných ve [výrazech shody](match-expressions.md) použít v seznamu parametrů pro funkci nebo člena.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="3cd9b-115">Metody obvykle používají formulář řazené kolekce členů s předáváním argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="3cd9b-116">Výsledkem je jasný výsledek z perspektivy dalších jazyků .NET, protože formulář řazené kolekce členů odpovídá způsobu předání argumentů do metod .NET.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="3cd9b-117">Formulář curryfikované se nejčastěji používá s funkcemi vytvořenými pomocí vazeb `let`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="3cd9b-118">Následující pseudokódu ukazuje příklady řazené kolekce členů a argumentů curryfikované.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="3cd9b-119">Kombinované formuláře jsou možné, pokud jsou některé argumenty v řazené kolekci členů a některé nejsou.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="3cd9b-120">Další vzory lze také použít v seznamech parametrů, ale pokud vzor parametru neodpovídá všem možným vstupům, může být v době běhu neúplná shoda.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="3cd9b-121">Výjimka `MatchFailureException` je vygenerována, pokud hodnota argumentu neodpovídá vzorům uvedeným v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="3cd9b-122">Kompilátor vydá upozornění, když vzor parametru umožňuje neúplné shody.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="3cd9b-123">Minimálně jeden další vzor je běžně užitečný pro seznamy parametrů a je to vzor zástupného znaku.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="3cd9b-124">Vzor zástupného znaku v seznamu parametrů použijete, když jednoduše chcete ignorovat všechny argumenty, které jsou dodány.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="3cd9b-125">Následující kód ilustruje použití zástupného vzoru v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="3cd9b-126">Vzor zástupných znaků může být užitečný kdykoli, když nepotřebujete předávat argumenty, jako je například v hlavním vstupním bodě do programu, pokud se nechcete zajímat o argumenty příkazového řádku, které jsou obvykle dodávány jako pole řetězců, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="3cd9b-127">Další vzory, které jsou někdy používány v argumentech, jsou `as` vzor a vzory identifikátorů přidružené k rozlišeným sjednocením a aktivním vzorům.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="3cd9b-128">Můžete použít vzor sjednocení s jedním případem, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="3cd9b-129">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="3cd9b-130">Aktivní vzory mohou být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="3cd9b-131">Můžete použít vzor `as` k uložení odpovídající hodnoty jako místní hodnoty, jak je znázorněno v následujícím řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="3cd9b-132">Jiný model, který je používán občas, je funkce, která opustí poslední argument bez názvu uvedením, jako tělo funkce, výraz lambda, který okamžitě provede porovnávání vzorů implicitního argumentu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="3cd9b-133">Příkladem je následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="3cd9b-134">Tento kód definuje funkci, která přijímá obecný seznam a vrátí `true`, pokud je seznam prázdný, a `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="3cd9b-135">Použití takových technik může ztížit čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="3cd9b-136">Modely, které zahrnují neúplné shody, jsou užitečné, například pokud víte, že seznamy v programu mají pouze tři prvky, můžete použít vzor podobný následujícímu v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="3cd9b-137">Používání vzorů, které mají neúplné shody, je nejlépe vyhrazené pro rychlé vytváření prototypů a další dočasné účely.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="3cd9b-138">Kompilátor vydá upozornění pro takový kód.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="3cd9b-139">Takové vzory nemůžou pokrývat obecný případ všech možných vstupů, takže nejsou vhodné pro rozhraní API komponent.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="3cd9b-140">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="3cd9b-140">Named Arguments</span></span>

<span data-ttu-id="3cd9b-141">Argumenty pro metody lze zadat podle pozice v seznamu argumentů oddělených čárkou nebo je lze předat metodě explicitně zadáním názvu, následovaným rovnítkem a hodnotou, která má být předána.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="3cd9b-142">Pokud je zadáno zadáním názvu, mohou se zobrazit v jiném pořadí, než je použito v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="3cd9b-143">Pojmenované argumenty mohou zvýšit čitelnost kódu a můžou být přizpůsobitelné na určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="3cd9b-144">Pojmenované argumenty jsou povoleny pouze pro metody, nikoli pro funkce vázané na `let`, hodnoty funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="3cd9b-145">Následující příklad kódu ukazuje použití pojmenovaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="3cd9b-146">V volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné syntaxi pojmenovaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="3cd9b-147">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="3cd9b-148">Další informace naleznete v tématu [konstruktory (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="3cd9b-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="3cd9b-149">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="3cd9b-149">Optional Parameters</span></span>

<span data-ttu-id="3cd9b-150">Můžete zadat volitelný parametr pro metodu pomocí otazníku před názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="3cd9b-151">Volitelné parametry jsou interpretovány jako F# typ možnosti, takže je lze dotazovat běžným způsobem, jakým jsou dotazovány typy možností, pomocí výrazu `match` s `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="3cd9b-152">Volitelné parametry jsou povoleny pouze u členů, nikoli u funkcí vytvořených pomocí vazeb `let`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="3cd9b-153">Můžete předat existující volitelné hodnoty metodě podle názvu parametru, například `?arg=None` nebo `?arg=Some(3)` nebo `?arg=arg`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="3cd9b-154">To může být užitečné při vytváření metody, která předá volitelné argumenty jiné metodě.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="3cd9b-155">Můžete také použít `defaultArg`funkce, která nastaví výchozí hodnotu volitelného argumentu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="3cd9b-156">Funkce `defaultArg` přebírá volitelný parametr jako první argument a výchozí hodnotu jako sekundu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="3cd9b-157">Následující příklad ilustruje použití nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="3cd9b-158">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="3cd9b-159">Pro účely C# a Visual Basic spolupráci můžete použít atributy `[<Optional; DefaultParameterValue<(...)>]` v F#, aby volající jako volitelnou viděli argument.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="3cd9b-160">To je ekvivalentní k definování argumentu jako volitelné v C# `MyMethod(int i = 3)`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="3cd9b-161">Můžete také zadat nový objekt jako výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="3cd9b-162">Například člen `Foo` mohl mít místo toho volitelný `CancellationToken` jako vstup:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="3cd9b-163">Hodnota zadaná jako argument pro `DefaultParameterValue` musí odpovídat typu parametru.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="3cd9b-164">Například následující nejsou povoleny:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="3cd9b-165">V tomto případě kompilátor vygeneruje upozornění a bude zcela ignorovat oba atributy.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="3cd9b-166">Všimněte si, že výchozí hodnota `null` nutné zadat anotaci, jinak kompilátor odvodí nesprávný typ, tj. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="3cd9b-167">Předávání odkazem</span><span class="sxs-lookup"><span data-stu-id="3cd9b-167">Passing by Reference</span></span>

<span data-ttu-id="3cd9b-168">Předání F# hodnoty odkazem zahrnuje [byrefs](byrefs.md), které jsou spravované typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="3cd9b-169">Pokyny pro typ, který se má použít, jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="3cd9b-170">Použijte `inref<'T>`, pokud potřebujete jen číst ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="3cd9b-171">Pokud potřebujete zapisovat jenom na ukazatel, použijte `outref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="3cd9b-172">Použijte `byref<'T>`, pokud potřebujete číst a zapisovat do ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="3cd9b-173">Vzhledem k tomu, že parametr je ukazatel a hodnota je proměnlivá, všechny změny hodnoty se uchovávají po spuštění funkce.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="3cd9b-174">Můžete použít řazenou kolekci členů jako návratovou hodnotu pro uložení parametrů `out` v metodách knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="3cd9b-175">Alternativně můžete s parametrem `out` zacházet jako s parametrem `byref`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="3cd9b-176">Následující příklad kódu ukazuje oba způsoby.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="3cd9b-177">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="3cd9b-177">Parameter Arrays</span></span>

<span data-ttu-id="3cd9b-178">V některých případech je nutné definovat funkci, která přebírá libovolný počet parametrů heterogenního typu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="3cd9b-179">Nebylo by praktické vytvořit všechny možné přetížené metody pro všechny typy, které by mohly být použity.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="3cd9b-180">Implementace rozhraní .NET poskytují podporu pro tyto metody prostřednictvím funkce pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="3cd9b-181">Metoda, která přebírá pole parametrů v jeho podpisu, může být poskytnuta s libovolným počtem parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="3cd9b-182">Parametry jsou vloženy do pole.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-182">The parameters are put into an array.</span></span> <span data-ttu-id="3cd9b-183">Typ prvků pole určuje typy parametrů, které mohou být předány do funkce.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="3cd9b-184">Definujete-li pole parametrů s `System.Object` jako typ prvku, může kód klienta předat hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="3cd9b-185">V F#nástroji lze pole parametrů definovat pouze v metodách.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="3cd9b-186">Nelze je použít v samostatných funkcích nebo funkcích, které jsou definovány v modulech.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="3cd9b-187">Pole parametrů definujete pomocí atributu `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="3cd9b-188">Atribut `ParamArray` lze použít pouze pro poslední parametr.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="3cd9b-189">Následující kód ilustruje volání metody .NET, která přijímá pole parametrů a definice typu v F# , který má metodu, která přijímá pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="3cd9b-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="3cd9b-190">Při spuštění v projektu je výstupem předchozího kódu následující:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="3cd9b-191">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cd9b-191">See also</span></span>

- [<span data-ttu-id="3cd9b-192">Členové</span><span class="sxs-lookup"><span data-stu-id="3cd9b-192">Members</span></span>](./members/index.md)
