---
title: Parametry a argumenty (F#)
description: 'Další informace o F # jazyková podpora pro definování parametry a předání argumentů do funkce, metod a vlastností.'
ms.date: 05/16/2016
ms.openlocfilehash: 319cf0e7346d498ce34e41a9993fe0160038461a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566217"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="10d8c-103">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="10d8c-103">Parameters and Arguments</span></span>

<span data-ttu-id="10d8c-104">Toto téma popisuje jazyková podpora pro definování parametry a předání argumentů do funkce, metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="10d8c-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="10d8c-105">Obsahuje informace o tom, k předání odkazem a definování a používání metody, které může provádět proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="10d8c-106">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="10d8c-106">Parameters and Arguments</span></span>
<span data-ttu-id="10d8c-107">Termín *parametr* se používá k popisu názvy hodnot, které se očekává, že je nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="10d8c-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="10d8c-108">Termín *argument* se používá pro hodnoty poskytnuté pro jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="10d8c-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="10d8c-109">Parametry lze v řazené kolekce členů nebo curryfikované formuláře nebo v některé kombinaci obojího.</span><span class="sxs-lookup"><span data-stu-id="10d8c-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="10d8c-110">Argumenty můžete předat pomocí názvu objektu explicitní parametr.</span><span class="sxs-lookup"><span data-stu-id="10d8c-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="10d8c-111">Parametry metody můžete zadat jako volitelné a zadané výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="10d8c-112">Parametr vzory</span><span class="sxs-lookup"><span data-stu-id="10d8c-112">Parameter Patterns</span></span>
<span data-ttu-id="10d8c-113">Parametry zadané pro funkce a metody jsou obecně vzory oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="10d8c-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="10d8c-114">To znamená, že v zásadě některé vzory popsané v [výrazy shody](match-expressions.md) lze použít v seznamu parametrů pro funkci nebo člen.</span><span class="sxs-lookup"><span data-stu-id="10d8c-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="10d8c-115">Metody obvykle formulář řazené kolekce členů předávání argumentů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="10d8c-116">Toto dosahuje výsledku jasnější z perspektivy jinými jazyky rozhraní .NET, protože formuláře řazené kolekce členů odpovídá způsob, jakým jsou argumenty předané metod rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="10d8c-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="10d8c-117">Curryfikované formuláře se nejčastěji používá s funkcemi, které jsou vytvořeny pomocí `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="10d8c-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="10d8c-118">Následující pseudokódu zobrazuje příklady řazené kolekce členů a curryfikované argumenty.</span><span class="sxs-lookup"><span data-stu-id="10d8c-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="10d8c-119">Kombinovaná formuláře je možné, pokud jsou některé argumenty v řazené kolekce členů a některé nejsou.</span><span class="sxs-lookup"><span data-stu-id="10d8c-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="10d8c-120">Jiných vzorů můžete použít i v seznamy parametrů, ale pokud vzor parametr neodpovídá všechny možné vstupy, může být neúplné shoda v době běhu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="10d8c-121">Výjimka `MatchFailureException` se vygeneruje, když je hodnota argumentu neodpovídá vzory uvedený v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="10d8c-122">Vydá výstrahu, pokud parametr vzor umožňuje pro neúplné odpovídá.</span><span class="sxs-lookup"><span data-stu-id="10d8c-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="10d8c-123">Alespoň jeden další vzor je často užitečné pro seznamy parametrů a který je zástupný znak – vzor.</span><span class="sxs-lookup"><span data-stu-id="10d8c-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="10d8c-124">Použít zástupný znak – vzor v seznamu parametrů. Pokud chcete jednoduše ignorovat všechny argumenty, které jsou zadány.</span><span class="sxs-lookup"><span data-stu-id="10d8c-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="10d8c-125">Následující kód ukazuje použití vzoru zástupný znak v seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="10d8c-126">Zástupný znak – vzor může být užitečné vždy, když není nutné argumentů předaných v, například v hlavní vstupní bod programu, pokud si nejste zájem o argumenty příkazového řádku, které jsou obvykle poskytovány jako pole řetězců, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="10d8c-127">Další vzory, které se někdy používají v argumentech `as` vzor a vzory identifikátor přidružené rozlišovaná sjednocení a aktivní vzorky.</span><span class="sxs-lookup"><span data-stu-id="10d8c-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="10d8c-128">Můžete použít případě jedním rozlišovaná sjednocení – vzor následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="10d8c-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="10d8c-129">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="10d8c-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="10d8c-130">Aktivní vzorky může být užitečné jako parametry, například při transformaci argumentu na požadovaný formát, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="10d8c-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="10d8c-131">Můžete použít `as` vzor ukládání odpovídající hodnotu jako hodnotu místní, jak je znázorněno na následujícím řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="10d8c-132">Jiné vzor, který se používá příležitostně je funkce, která zůstane poslední argument nepojmenované tím, že poskytuje jako text funkce, která okamžitě provede vzor shody implicitní argument výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="10d8c-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="10d8c-133">Příkladem je následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="10d8c-134">Tento kód definuje funkci, která přebírá seznam obecné a vrátí `true` Pokud je seznam prázdný, a `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="10d8c-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="10d8c-135">Použití těchto postupů můžete nastavit kód obtížněji čitelný.</span><span class="sxs-lookup"><span data-stu-id="10d8c-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="10d8c-136">V některých případech vzorů, které se týkají neúplné odpovídá jsou užitečné, například pokud jste si jisti, že seznamy v programu mají jenom tři prvky, můžete použít připomínat následující v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="10d8c-137">Použití vzorů, které obsahuje neúplné odpovídající se nejlépe hodí pro rychlé při vytváření prototypu a dalších dočasné používá.</span><span class="sxs-lookup"><span data-stu-id="10d8c-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="10d8c-138">Kompilátor vydá upozornění pro takový kód.</span><span class="sxs-lookup"><span data-stu-id="10d8c-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="10d8c-139">Tyto vzory nelze zahrnují obecné malá všechny možné vstupy a proto nejsou vhodné pro součást rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="10d8c-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="10d8c-140">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="10d8c-140">Named Arguments</span></span>
<span data-ttu-id="10d8c-141">Argumenty pro metody lze zadat podle pozice v seznamu odděleném čárkami argument, nebo je můžete předat metodě explicitně tím, že poskytuje název, za nímž následuje znak rovná a hodnota, která má být předán.</span><span class="sxs-lookup"><span data-stu-id="10d8c-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="10d8c-142">-Li zadána, poskytnutím názvu, se objeví v jiném pořadí, ze kterého v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="10d8c-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="10d8c-143">Pojmenované argumenty můžete provést kód srozumitelnější a další přizpůsobitelné určité typy změn v rozhraní API, jako je například změna pořadí parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="10d8c-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="10d8c-144">Pojmenované argumenty jsou povoleny pouze pro metody, ne pro `let`-vázána funkce, funkce hodnoty nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="10d8c-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="10d8c-145">Následující příklad kódu ukazuje použití pojmenovaných argumentech.</span><span class="sxs-lookup"><span data-stu-id="10d8c-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="10d8c-146">Ve volání konstruktoru třídy můžete nastavit hodnoty vlastností třídy pomocí pomocí syntaxe podobná pojmenované argumenty.</span><span class="sxs-lookup"><span data-stu-id="10d8c-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="10d8c-147">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="10d8c-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="10d8c-148">Další informace najdete v tématu [konstruktory (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="10d8c-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="10d8c-149">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="10d8c-149">Optional Parameters</span></span>
<span data-ttu-id="10d8c-150">Můžete zadat volitelný parametr pro metodu pomocí otazník před název parametru.</span><span class="sxs-lookup"><span data-stu-id="10d8c-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="10d8c-151">Volitelné parametry jsou interpretovány jako typ F # možnost, můžete zadávat dotazy běžným způsobem, že se dotaz typy možností, pomocí `match` výraz s `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="10d8c-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="10d8c-152">Volitelné parametry jsou povoleny pouze u členů, nikoli na funkce, které jsou vytvořeny pomocí `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="10d8c-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="10d8c-153">Můžete použít také funkci `defaultArg`, který nastaví výchozí hodnota je za volitelným argumentem.</span><span class="sxs-lookup"><span data-stu-id="10d8c-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="10d8c-154">`defaultArg` Funkce přebírá volitelný parametr jako první argument a výchozí hodnotu jako druhý.</span><span class="sxs-lookup"><span data-stu-id="10d8c-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="10d8c-155">Následující příklad ukazuje použití volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="10d8c-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="10d8c-156">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="10d8c-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="10d8c-157">Předávání odkazem</span><span class="sxs-lookup"><span data-stu-id="10d8c-157">Passing by Reference</span></span>
<span data-ttu-id="10d8c-158">F # podporuje `byref` – klíčové slovo, které určuje, že je parametr předaný odkazem.</span><span class="sxs-lookup"><span data-stu-id="10d8c-158">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="10d8c-159">To znamená, že po spuštění funkce se zachovají všechny změny na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-159">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="10d8c-160">Hodnoty poskytnuté `byref` parametr musí být měnitelný.</span><span class="sxs-lookup"><span data-stu-id="10d8c-160">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="10d8c-161">Alternativně můžete předat referenční buňky příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-161">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="10d8c-162">Předání odkazem v jazycích .NET vyvinuly jako způsob, jak z funkce vrátí více než jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-162">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="10d8c-163">V F # můžete vrátit řazené kolekce členů pro tento účel, nebo použít buňku proměnlivé odkazové jako parametr.</span><span class="sxs-lookup"><span data-stu-id="10d8c-163">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="10d8c-164">`byref` Parametr je poskytován interoperability s knihovnami .NET.</span><span class="sxs-lookup"><span data-stu-id="10d8c-164">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="10d8c-165">Následující příklady ilustrují použití `byref` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="10d8c-165">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="10d8c-166">Všimněte si, že použijete-li odkaz na buňku jako parametr, musíte vytvořit odkaz na buňku jako hodnotu s názvem a použít je jako parametr, nejen přidat `ref` operátor, jak je znázorněno v prvním volání `Increment` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-166">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="10d8c-167">Vzhledem k tomu, že vytváření odkaz na buňku vytvoří kopii základní hodnoty, první volání právě zvýší dočasnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="10d8c-167">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="10d8c-168">Řazené kolekce členů jako návratová hodnota můžete použít k uložení žádné `out` parametry v metod knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="10d8c-168">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="10d8c-169">Alternativně lze považovat `out` parametr jako `byref` parametr.</span><span class="sxs-lookup"><span data-stu-id="10d8c-169">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="10d8c-170">Následující příklad kódu ukazuje obou směrech.</span><span class="sxs-lookup"><span data-stu-id="10d8c-170">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="10d8c-171">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="10d8c-171">Parameter Arrays</span></span>
<span data-ttu-id="10d8c-172">Někdy je nutné definovat funkci, která přebírá libovolný počet parametrů heterogenní typu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-172">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="10d8c-173">Nebude potřeba vytvořit všechny možné přetížené metody pro účet pro všechny typy, které by mohly být použity.</span><span class="sxs-lookup"><span data-stu-id="10d8c-173">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="10d8c-174">Implementace rozhraní .NET poskytuje podporu pro tyto metody prostřednictvím funkce parametr pole.</span><span class="sxs-lookup"><span data-stu-id="10d8c-174">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="10d8c-175">Metoda, která přebírá parametr pole podpis lze zadat s libovolný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="10d8c-175">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="10d8c-176">Parametry jsou vloženy do pole.</span><span class="sxs-lookup"><span data-stu-id="10d8c-176">The parameters are put into an array.</span></span> <span data-ttu-id="10d8c-177">Typ elementů pole určuje typy parametrů, které lze předat funkce.</span><span class="sxs-lookup"><span data-stu-id="10d8c-177">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="10d8c-178">Pokud definujete pole parametrů s `System.Object` jako typ elementu, pak kód klienta můžete předat hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="10d8c-178">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="10d8c-179">V jazyce F # můžete pole parametrů definována pouze v metodách.</span><span class="sxs-lookup"><span data-stu-id="10d8c-179">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="10d8c-180">Nelze použít v samostatné funkce nebo funkce, které jsou definovány v modulech.</span><span class="sxs-lookup"><span data-stu-id="10d8c-180">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="10d8c-181">Pole parametrů se definují pomocí `ParamArray` atribut.</span><span class="sxs-lookup"><span data-stu-id="10d8c-181">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="10d8c-182">`ParamArray` Atribut lze použít pouze na poslední parametr.</span><span class="sxs-lookup"><span data-stu-id="10d8c-182">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="10d8c-183">Následující kód ukazuje, jak volání metody rozhraní .NET, která použije parametr pole a definici typu v F #, která se má metoda, která přebírá parametr pole.</span><span class="sxs-lookup"><span data-stu-id="10d8c-183">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="10d8c-184">Při spuštění v projektu, výstup předchozí kód je následující:</span><span class="sxs-lookup"><span data-stu-id="10d8c-184">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="10d8c-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="10d8c-185">See Also</span></span>
[<span data-ttu-id="10d8c-186">Členové</span><span class="sxs-lookup"><span data-stu-id="10d8c-186">Members</span></span>](members/index.md)
