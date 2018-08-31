---
title: Parametry a argumenty (F#)
description: 'Další informace o podpora jazyka F # pro definování parametrů a předávání argumentů do funkce, metody a vlastnosti.'
ms.date: 05/16/2016
ms.openlocfilehash: 9744339110314e4e6b3c3cf8d49b1c988bc25e3c
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254006"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="977ab-103">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="977ab-103">Parameters and Arguments</span></span>

<span data-ttu-id="977ab-104">Toto téma popisuje podporu jazyka pro definování parametrů a předávání argumentů do funkce, metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="977ab-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="977ab-105">Obsahuje informace o předávání pomocí odkazu a k definování a použití metod, které mohou provádět proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="977ab-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="977ab-106">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="977ab-106">Parameters and Arguments</span></span>
<span data-ttu-id="977ab-107">Termín *parametr* se používá k popisu názvy pro hodnoty, které se očekává, že @username.</span><span class="sxs-lookup"><span data-stu-id="977ab-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="977ab-108">Termín *argument* se používá pro hodnoty poskytnuté pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="977ab-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="977ab-109">Parametry můžete zadat v n-tici nebo curryfikované formuláře, nebo určitou kombinaci obou.</span><span class="sxs-lookup"><span data-stu-id="977ab-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="977ab-110">Pomocí názvu explicitní parametr můžete předat argumenty.</span><span class="sxs-lookup"><span data-stu-id="977ab-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="977ab-111">Parametry metod můžete zadaný jako volitelný a zadaný výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="977ab-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="977ab-112">Vzory parametrů</span><span class="sxs-lookup"><span data-stu-id="977ab-112">Parameter Patterns</span></span>
<span data-ttu-id="977ab-113">Parametry zadané funkce a metody jsou obecně vzory oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="977ab-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="977ab-114">To znamená, že v zásadě, všechny tyto vzory se dají podle [odpovídající výrazy](match-expressions.md) lze použít v seznamu parametrů funkce nebo člen.</span><span class="sxs-lookup"><span data-stu-id="977ab-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="977ab-115">Metody obvykle používají formě řazené kolekce členů předávání argumentů.</span><span class="sxs-lookup"><span data-stu-id="977ab-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="977ab-116">Toto dosahuje jasnější výsledek z hlediska jinými jazyky rozhraní .NET, protože odpovídá formě řazené kolekce členů způsob, jakým jsou argumenty předávány v metod rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="977ab-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="977ab-117">Curryfikované formuláře se nejčastěji používá s funkcemi, které jsou vytvářeny instalační sadou `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="977ab-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="977ab-118">Následujícím pseudokódu ukazuje příklady řazené kolekce členů a curryfikované argumenty.</span><span class="sxs-lookup"><span data-stu-id="977ab-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="977ab-119">Kombinované formuláře je možné, pokud některé argumenty jsou v řazených kolekcí členů a některé nejsou.</span><span class="sxs-lookup"><span data-stu-id="977ab-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="977ab-120">Další způsoby lze také v seznamech parametrů, ale pokud vzor parametru se neshoduje s všech vstupů je to možné, může být nekompletní shoda v době běhu.</span><span class="sxs-lookup"><span data-stu-id="977ab-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="977ab-121">Výjimka `MatchFailureException` se vygeneruje, když hodnota argumentu není odpovídající vzorům uvedeným v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="977ab-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="977ab-122">Kompilátor vyvolá upozornění, pokud parametr vzoru umožňuje pro úplné shody.</span><span class="sxs-lookup"><span data-stu-id="977ab-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="977ab-123">Alespoň jeden další vzorek je často užitečné pro seznamy parametrů a, který je vzor zástupných znaků.</span><span class="sxs-lookup"><span data-stu-id="977ab-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="977ab-124">Vzorec zástupných znaků v seznamu parametrů. použijte chcete jednoduše ignorovat všechny argumenty, které jsou dodávány.</span><span class="sxs-lookup"><span data-stu-id="977ab-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="977ab-125">Následující kód ukazuje použití zástupných v seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="977ab-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="977ab-126">Vzorec zástupných znaků může být užitečné pokaždé, když není nutné předaných argumentech, například hlavní vstupní bod programu, když vás nezajímají argumentů příkazového řádku, které jsou obvykle dodávány jako pole řetězců, stejně jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="977ab-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="977ab-127">Další způsoby, které se občas používají v argumenty jsou `as` vzoru a vzorky identifikátoru přidružené rozlišovaná sjednocení a aktivní vzory.</span><span class="sxs-lookup"><span data-stu-id="977ab-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="977ab-128">Rozlišovaná sjednocení vzor jedním případem můžete následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="977ab-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="977ab-129">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="977ab-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="977ab-130">Aktivní vzory může být užitečné jako parametry, například při transformaci argumentu do požadovaného formátu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="977ab-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="977ab-131">Můžete použít `as` vzor ukládání odpovídající hodnotu jako místní hodnoty, jak je znázorněno v následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="977ab-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="977ab-132">Jiný model, který se používá čas od času je funkce, které se zasílají posledním argumentem nepojmenované poskytnutím jako tělo funkce, výraz lambda, který se okamžitě provede porovnávání na implicitní argument.</span><span class="sxs-lookup"><span data-stu-id="977ab-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="977ab-133">Příkladem je následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="977ab-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="977ab-134">Tento kód definuje funkci, která přebírá seznam obecných a vrací `true` Pokud je seznam prázdný, a `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="977ab-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="977ab-135">Použití těchto metod může ztížit kód ke čtení.</span><span class="sxs-lookup"><span data-stu-id="977ab-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="977ab-136">V některých případech způsoby, které se týkají neúplné shody jsou užitečné, například pokud víte, že seznamy v aplikaci mají pouze tři prvky, můžete použít model následujícím postupem v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="977ab-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="977ab-137">Použití vzorů, které obsahuje neúplné odpovídající se nejlépe hodí pro rychlé vytváření prototypů a jiné dočasné účely.</span><span class="sxs-lookup"><span data-stu-id="977ab-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="977ab-138">Kompilátor vygeneruje upozornění pro takového kódu.</span><span class="sxs-lookup"><span data-stu-id="977ab-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="977ab-139">Tyto vzory pokrýt obecné velikost všech vstupů je to možné a proto nejsou vhodné pro komponentu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="977ab-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="977ab-140">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="977ab-140">Named Arguments</span></span>
<span data-ttu-id="977ab-141">Argumenty pro metody je možné zadat tak pozice v seznamu oddělovači argumentů nebo je můžete předat metodě explicitně zadáním názvu, za nímž následuje rovnítko a hodnota, která má být předán v.</span><span class="sxs-lookup"><span data-stu-id="977ab-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="977ab-142">-Li zadán zadáním názvu, můžete zobrazit v jiném pořadí z použitého v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="977ab-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="977ab-143">Pojmenované argumenty můžete provést kód lépe čitelný a další přizpůsobitelné určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="977ab-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="977ab-144">Pojmenované argumenty jsou povoleny pouze pro metody, ne pro `let`-vázaná funkce, funkce hodnoty nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="977ab-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="977ab-145">Následující příklad kódu ukazuje použití pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="977ab-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="977ab-146">Ve volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí syntaxe podobné pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="977ab-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="977ab-147">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="977ab-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="977ab-148">Další informace najdete v tématu [konstruktory (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="977ab-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="977ab-149">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="977ab-149">Optional Parameters</span></span>
<span data-ttu-id="977ab-150">Můžete zadat volitelný parametr pro metodu s použitím otazník před název parametru.</span><span class="sxs-lookup"><span data-stu-id="977ab-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="977ab-151">Volitelné parametry jsou interpretovány jako typ možnost jazyka F #, proto dotazování těchto běžným způsobem, že typy možností jsou dotazovat, pomocí `match` výraz s `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="977ab-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="977ab-152">Volitelné parametry jsou povolené jenom na členy, nikoli na funkce, které jsou vytvářeny instalační sadou `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="977ab-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="977ab-153">Můžete použít také funkci `defaultArg`, která nastaví výchozí hodnota je nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="977ab-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="977ab-154">`defaultArg` Funkce přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.</span><span class="sxs-lookup"><span data-stu-id="977ab-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="977ab-155">Následující příklad ukazuje použití nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="977ab-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="977ab-156">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="977ab-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="977ab-157">Předávání odkazem.</span><span class="sxs-lookup"><span data-stu-id="977ab-157">Passing by Reference</span></span>
<span data-ttu-id="977ab-158">Předávání odkazem na hodnotu F # zahrnuje `byref` – klíčové slovo, které určuje, že ve skutečnosti ukazatel na hodnotu předávaný odkazem parametr.</span><span class="sxs-lookup"><span data-stu-id="977ab-158">Passing an F# value by reference involves the `byref` keyword, which specifies that the parameter is actually a pointer to the value being passed by reference.</span></span> <span data-ttu-id="977ab-159">Libovolná hodnota předaná do metody s `byref` jako argument musí být `mutable`.</span><span class="sxs-lookup"><span data-stu-id="977ab-159">Any value passed into a method with a `byref` as the argument must be `mutable`.</span></span>

<span data-ttu-id="977ab-160">Protože parametru je ukazatel a hodnota je proměnlivá, všechny změny hodnoty se uchovávají po spuštění funkce.</span><span class="sxs-lookup"><span data-stu-id="977ab-160">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="977ab-161">Můžete provést totéž s [odkazové buňky](reference-cells.md), ale je důležité si uvědomit, že **odkazové buňky a `byref`s nejsou totéž**.</span><span class="sxs-lookup"><span data-stu-id="977ab-161">You can accomplish the same thing with [Reference Cells](reference-cells.md), but it's important to note that **reference cells and `byref`s are not the same thing**.</span></span> <span data-ttu-id="977ab-162">Odkazové buňky je kontejner pro hodnotu, která můžete zkontrolovat a změnit obsah, ale tato hodnota se nachází v haldě a je ekvivalentní s tím, že záznam s proměnlivou hodnotu jsou v něm obsaženy.</span><span class="sxs-lookup"><span data-stu-id="977ab-162">A reference cell is a container for a value that you can inspect and change the contents of, but this value lives on the heap and is equivalent to having a record with a mutable value contained within it.</span></span> <span data-ttu-id="977ab-163">A `byref` skutečný ukazatel, je tak, aby byl odlišnou sémantiku základní a použití pravidel (může být poměrně omezující).</span><span class="sxs-lookup"><span data-stu-id="977ab-163">A `byref` is an actual pointer, so it is different underlying semantics and usage rules (which can be quite restrictive).</span></span>

<span data-ttu-id="977ab-164">Následující příklady ilustrují použití `byref` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="977ab-164">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="977ab-165">Všimněte si, že při použití odkazovou buňku jako parametr, musíte vytvořit odkazovou buňku jako hodnotu s názvem a použít jako parametr, ne jenom přidat `ref` operátor, jak je znázorněno v prvním volání `Increment` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="977ab-165">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="977ab-166">Protože vytvoření odkazové buňky se vytvoří kopie zdrojové hodnoty, první volání pouze zvýší dočasná hodnota.</span><span class="sxs-lookup"><span data-stu-id="977ab-166">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="977ab-167">Řazené kolekce členů jako návratovou hodnotu můžete použít k ukládání žádné `out` parametrů metod knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="977ab-167">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="977ab-168">Alternativně lze považovat `out` parametrem jako `byref` parametru.</span><span class="sxs-lookup"><span data-stu-id="977ab-168">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="977ab-169">Následující příklad kódu znázorňuje oba způsoby.</span><span class="sxs-lookup"><span data-stu-id="977ab-169">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="977ab-170">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="977ab-170">Parameter Arrays</span></span>
<span data-ttu-id="977ab-171">Někdy je potřeba definovat funkci, která přijímá libovolný počet parametrů typu heterogenní.</span><span class="sxs-lookup"><span data-stu-id="977ab-171">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="977ab-172">Nemusí být praktické k vytvoření všech možných přetížených metod pro všechny typy, které by bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="977ab-172">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="977ab-173">Implementace .NET poskytují podporu pro tyto metody prostřednictvím pole funkce parametr.</span><span class="sxs-lookup"><span data-stu-id="977ab-173">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="977ab-174">Metodu, která přebírá parametr pole v jeho podpisu může zobrazovat libovolný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="977ab-174">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="977ab-175">Parametry jsou vloženy do pole.</span><span class="sxs-lookup"><span data-stu-id="977ab-175">The parameters are put into an array.</span></span> <span data-ttu-id="977ab-176">Typ prvků pole určuje typy parametrů, které může být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="977ab-176">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="977ab-177">Při definování pole parametrů s `System.Object` jako typ elementu, pak klient může kód předat hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="977ab-177">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="977ab-178">V jazyce F # je pole parametrů definovat pouze v metodách.</span><span class="sxs-lookup"><span data-stu-id="977ab-178">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="977ab-179">Nelze je použít v samostatné funkce nebo funkce, které jsou definovány v modulech.</span><span class="sxs-lookup"><span data-stu-id="977ab-179">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="977ab-180">Definování pole parametrů s použitím `ParamArray` atribut.</span><span class="sxs-lookup"><span data-stu-id="977ab-180">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="977ab-181">`ParamArray` Atribut lze použít pouze pro poslední parametr.</span><span class="sxs-lookup"><span data-stu-id="977ab-181">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="977ab-182">Následující kód ukazuje obě volání metody rozhraní .NET, která přijímá pole parametrů a definice typu v jazyce F #, která obsahuje metodu, která přebírá parametr pole.</span><span class="sxs-lookup"><span data-stu-id="977ab-182">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="977ab-183">Při spuštění v projektu, výstup předchozího kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="977ab-183">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="977ab-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="977ab-184">See Also</span></span>
[<span data-ttu-id="977ab-185">Členové</span><span class="sxs-lookup"><span data-stu-id="977ab-185">Members</span></span>](members/index.md)
