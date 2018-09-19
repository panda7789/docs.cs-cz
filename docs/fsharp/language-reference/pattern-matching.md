---
title: Porovnávání vzorů (F#)
description: 'Zjistěte, jak se používají vzory v F # k porovnání dat s logické struktury, jak rozložit data na základní části nebo extrahovat informace z dat.'
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991421"
---
# <a name="pattern-matching"></a><span data-ttu-id="acede-103">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="acede-103">Pattern Matching</span></span>

<span data-ttu-id="acede-104">Vzorky jsou pravidla pro transformování vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="acede-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="acede-105">Používají se v celém jazyce F # k porovnání dat s logickou strukturou nebo strukturami, rozložení dat na základní části nebo extrahovat informace z dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="acede-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="acede-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acede-106">Remarks</span></span>

<span data-ttu-id="acede-107">Vzorky se používají v mnoha konstrukcích jazyka, jako `match` výrazu.</span><span class="sxs-lookup"><span data-stu-id="acede-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="acede-108">Používají se při zpracování argumentů pro funkce v `let` vazeb, lambda výrazy a v obslužných rutinách výjimek spojených s `try...with` výrazu.</span><span class="sxs-lookup"><span data-stu-id="acede-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="acede-109">Další informace najdete v tématu [odpovídající výrazy](match-expressions.md), [vazby let](functions/let-bindings.md), [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md), a [výjimky: `try...with` Výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="acede-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="acede-110">Například v `match` výrazu, *vzor* co následuje symbol svislé čáry.</span><span class="sxs-lookup"><span data-stu-id="acede-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="acede-111">Každý vzorek se chová jako pravidlo pro transformování vstupu nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="acede-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="acede-112">V `match` výrazu, každý vzorek je zkoumán zjistit, jestli se vstupní data kompatibilní se vzorkem.</span><span class="sxs-lookup"><span data-stu-id="acede-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="acede-113">Pokud se najde shoda, výsledkem spuštění výrazu.</span><span class="sxs-lookup"><span data-stu-id="acede-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="acede-114">Pokud není nalezena shoda, je testováno další pravidlo vzorku.</span><span class="sxs-lookup"><span data-stu-id="acede-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="acede-115">Volitelně při *podmínku* části je vysvětlen v [odpovídající výrazy](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="acede-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="acede-116">Podporované vzory jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="acede-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="acede-117">V době běhu vstup je testován oproti každému z následujících vzorů v uvedeném pořadí v tabulce a vzory se používají rekurzivně, od nejprve na poslední, jak se objeví ve vašem kódu a zleva doprava pro vzory na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="acede-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="acede-118">Název</span><span class="sxs-lookup"><span data-stu-id="acede-118">Name</span></span>|<span data-ttu-id="acede-119">Popis</span><span class="sxs-lookup"><span data-stu-id="acede-119">Description</span></span>|<span data-ttu-id="acede-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="acede-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="acede-121">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="acede-121">Constant pattern</span></span>|<span data-ttu-id="acede-122">Všechny číselné, znak, nebo textový literál, konstanta výčtu nebo definovaný identifikátor literálu</span><span class="sxs-lookup"><span data-stu-id="acede-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="acede-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="acede-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="acede-124">Vzor identifikátoru</span><span class="sxs-lookup"><span data-stu-id="acede-124">Identifier pattern</span></span>|<span data-ttu-id="acede-125">Hodnota case diskriminované sjednocení, popisku výjimky nebo případ aktivního vzoru</span><span class="sxs-lookup"><span data-stu-id="acede-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="acede-126">Variabilní vzor</span><span class="sxs-lookup"><span data-stu-id="acede-126">Variable pattern</span></span>|<span data-ttu-id="acede-127">*identifikátor*</span><span class="sxs-lookup"><span data-stu-id="acede-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="acede-128">`as` Vzor</span><span class="sxs-lookup"><span data-stu-id="acede-128">`as` pattern</span></span>|<span data-ttu-id="acede-129">*vzor* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="acede-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="acede-130">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="acede-130">OR pattern</span></span>|<span data-ttu-id="acede-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="acede-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="acede-132">Vzor AND</span><span class="sxs-lookup"><span data-stu-id="acede-132">AND pattern</span></span>|<span data-ttu-id="acede-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="acede-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="acede-134">Nevýhody vzoru</span><span class="sxs-lookup"><span data-stu-id="acede-134">Cons pattern</span></span>|<span data-ttu-id="acede-135">*identifikátor* :: *identifikátor seznamu*</span><span class="sxs-lookup"><span data-stu-id="acede-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="acede-136">Vzor seznamu</span><span class="sxs-lookup"><span data-stu-id="acede-136">List pattern</span></span>|<span data-ttu-id="acede-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="acede-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="acede-138">Vzor pole</span><span class="sxs-lookup"><span data-stu-id="acede-138">Array pattern</span></span>|<span data-ttu-id="acede-139">[&#124; *pattern_1*;.; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="acede-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="acede-140">Vzor v závorce</span><span class="sxs-lookup"><span data-stu-id="acede-140">Parenthesized pattern</span></span>|<span data-ttu-id="acede-141">( *vzor* )</span><span class="sxs-lookup"><span data-stu-id="acede-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="acede-142">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="acede-142">Tuple pattern</span></span>|<span data-ttu-id="acede-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="acede-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="acede-144">Vzor záznamu</span><span class="sxs-lookup"><span data-stu-id="acede-144">Record pattern</span></span>|<span data-ttu-id="acede-145">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="acede-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="acede-146">Vzorec zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="acede-146">Wildcard pattern</span></span>|<span data-ttu-id="acede-147">_</span><span class="sxs-lookup"><span data-stu-id="acede-147">_</span></span>|`_`|
|<span data-ttu-id="acede-148">Vzorek společně s anotací typu</span><span class="sxs-lookup"><span data-stu-id="acede-148">Pattern together with type annotation</span></span>|<span data-ttu-id="acede-149">*vzor* : *typu*</span><span class="sxs-lookup"><span data-stu-id="acede-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="acede-150">Testovací vzorek typu</span><span class="sxs-lookup"><span data-stu-id="acede-150">Type test pattern</span></span>|<span data-ttu-id="acede-151">:?</span><span class="sxs-lookup"><span data-stu-id="acede-151">:?</span></span> <span data-ttu-id="acede-152">*typ* [jako *identifikátor* ]</span><span class="sxs-lookup"><span data-stu-id="acede-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="acede-153">Vzor Null</span><span class="sxs-lookup"><span data-stu-id="acede-153">Null pattern</span></span>|<span data-ttu-id="acede-154">null</span><span class="sxs-lookup"><span data-stu-id="acede-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="acede-155">Konstantní vzorky</span><span class="sxs-lookup"><span data-stu-id="acede-155">Constant Patterns</span></span>

<span data-ttu-id="acede-156">Konstantní vzorky jsou číselné, znakové a řetězcové literály výčtu konstant (se zahrnutým názvem výčtu typu).</span><span class="sxs-lookup"><span data-stu-id="acede-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="acede-157">A `match` výraz, který má pouze konstantní vzory, je možné porovnat s příkazy case v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="acede-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="acede-158">Vstup je porovnán s hodnotou literálu a vzor odpovídá, pokud jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="acede-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="acede-159">Typ literálu musí být kompatibilní s typem vstupu.</span><span class="sxs-lookup"><span data-stu-id="acede-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="acede-160">Následující příklad ukazuje použití vzorů literálu a také používá vzory proměnné a vzor OR.</span><span class="sxs-lookup"><span data-stu-id="acede-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="acede-161">Dalším příkladem vzoru literálu je vzor založený na výčtu konstant.</span><span class="sxs-lookup"><span data-stu-id="acede-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="acede-162">Při použití konstant výčtu, musíte zadat název typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="acede-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="acede-163">Vzorky identifikátoru</span><span class="sxs-lookup"><span data-stu-id="acede-163">Identifier Patterns</span></span>

<span data-ttu-id="acede-164">Pokud vzorek je řetězec znaků, který tvoří platný identifikátor, forma identifikátoru Určuje, jak je vzorek párován.</span><span class="sxs-lookup"><span data-stu-id="acede-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="acede-165">Pokud identifikátor je delší než jeden znak a začíná velkým písmenem, kompilátor se pokusí spárovat se vzorkem identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="acede-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="acede-166">Identifikátor pro tento model může být hodnota označená jako literální atribut, případ diskriminovaného sjednocení, identifikátor výjimky nebo případ aktivního vzoru.</span><span class="sxs-lookup"><span data-stu-id="acede-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="acede-167">Pokud není nalezen žádný odpovídající identifikátor, shoda se nezdaří a další pravidlo pro vzorek, vzorek proměnné, se porovná se vstupem.</span><span class="sxs-lookup"><span data-stu-id="acede-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="acede-168">Vzorky rozlišeného sjednocení mohou být jednoduše pojmenované případy nebo mají hodnotu či n-tici obsahující více hodnot.</span><span class="sxs-lookup"><span data-stu-id="acede-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="acede-169">Pokud je hodnota, je nutné zadat identifikátor pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="acede-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="acede-170">V případě řazené kolekce členů je nutné zadat vzor n-tice s identifikátor pro každý element n-tice nebo identifikátor s názvem pole pro jedno nebo více sjednocených polí.</span><span class="sxs-lookup"><span data-stu-id="acede-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="acede-171">Podívejte se na příklady kódu v této části s příklady.</span><span class="sxs-lookup"><span data-stu-id="acede-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="acede-172">`option` Typ je diskriminovaným sjednocením, které má dva případy `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="acede-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="acede-173">Jeden případ (`Some`) má hodnotu, ale další (`None`) je pouze pojmenovaný případ.</span><span class="sxs-lookup"><span data-stu-id="acede-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="acede-174">Proto `Some` musí mít proměnnou pro hodnotu spojenou s `Some` případu, ale `None` musí zobrazovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="acede-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="acede-175">V následujícím kódu, proměnná `var1` přiřazena hodnota získaná pomocí odpovídajícího `Some` případ.</span><span class="sxs-lookup"><span data-stu-id="acede-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="acede-176">V následujícím příkladu `PersonName` diskriminované sjednocení obsahuje směs řetězců a znaků, které představují možné formy jména.</span><span class="sxs-lookup"><span data-stu-id="acede-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="acede-177">Případy diskriminovaného sjednocení jsou `FirstOnly`, `LastOnly`, a `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="acede-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="acede-178">Pro rozlišovaná sjednocení, které mají pojmenované názvy polí použijte znaménko rovná se (=) k získání hodnoty pojmenovaného pole.</span><span class="sxs-lookup"><span data-stu-id="acede-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="acede-179">Zvažte například diskriminované sjednocení s deklarací, jako následující.</span><span class="sxs-lookup"><span data-stu-id="acede-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="acede-180">Můžete použít pojmenovaná pole ve výrazu odpovídajícímu vzorci následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="acede-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="acede-181">Použití pojmenovaného pole je volitelné, protože v předchozím příkladu obě `Circle(r)` a `Circle(radius = r)` stejný efekt.</span><span class="sxs-lookup"><span data-stu-id="acede-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="acede-182">Pokud zadáte více polí, použijte středník (;) jako oddělovač.</span><span class="sxs-lookup"><span data-stu-id="acede-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="acede-183">Aktivní vzorky umožňují definovat složitější vlastní porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="acede-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="acede-184">Další informace o aktivních vzorech naleznete v tématu [aktivní vzory](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="acede-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="acede-185">Případ, ve kterém je identifikátor výjimkou se používá v porovnávání vzorů v kontextu obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="acede-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="acede-186">Informace o vzoru porovnávání ve zpracování výjimek naleznete v tématu [výjimky: `try...with` výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="acede-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="acede-187">Vzorce proměnné</span><span class="sxs-lookup"><span data-stu-id="acede-187">Variable Patterns</span></span>

<span data-ttu-id="acede-188">Variabilní vzor přiřadí hodnotu porovnávanou s názvem proměnné, který je k dispozici pro použití v prováděném výrazu vpravo od `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="acede-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="acede-189">Variabilní vzor odpovídá jakémukoliv vstupu, ale variabilní vzorky se často objevuje v rámci jiných vzorků, proto umožňuje složitější struktury, jako například záznamy a pole, které lze rozložit na proměnné.</span><span class="sxs-lookup"><span data-stu-id="acede-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="acede-190">Následující příklad ukazuje vzor proměnné v rámci vzoru n-tice.</span><span class="sxs-lookup"><span data-stu-id="acede-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="acede-191">jako vzor</span><span class="sxs-lookup"><span data-stu-id="acede-191">as Pattern</span></span>

<span data-ttu-id="acede-192">`as` Vzor je vzor, který má `as` připojena k němu klauzule.</span><span class="sxs-lookup"><span data-stu-id="acede-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="acede-193">`as` Klauzule váže odpovídající hodnotu pro název, který lze použít ve výrazu spuštění `match` výrazu, nebo v případě, kdy se tento model používá v `let` vazby, přidání názvu jako vazby v místním rozsahu.</span><span class="sxs-lookup"><span data-stu-id="acede-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="acede-194">Následující příklad používá `as` vzor.</span><span class="sxs-lookup"><span data-stu-id="acede-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="acede-195">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="acede-195">OR Pattern</span></span>

<span data-ttu-id="acede-196">Vzor OR se používá, když vstupní data mohou odpovídat více vzorům a chcete provést ve výsledku stejný kód.</span><span class="sxs-lookup"><span data-stu-id="acede-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="acede-197">Typy obou stran vzoru operátoru OR musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="acede-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="acede-198">Následující příklad demonstruje vzory OR.</span><span class="sxs-lookup"><span data-stu-id="acede-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="acede-199">Vzor AND</span><span class="sxs-lookup"><span data-stu-id="acede-199">AND Pattern</span></span>

<span data-ttu-id="acede-200">Vzor AND vyžaduje, aby vstupu shoda dvou vzorků.</span><span class="sxs-lookup"><span data-stu-id="acede-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="acede-201">Typy obou stran vzoru operátoru AND musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="acede-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="acede-202">Následující příklad je podobný `detectZeroTuple` ukazuje [vzor n-tice](https://msdn.microsoft.com/library/#tuple) dále v tomto tématu, ale zde jsou `var1` a `var2` získány jako hodnoty pomocí vzoru.</span><span class="sxs-lookup"><span data-stu-id="acede-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="acede-203">Nevýhody vzoru</span><span class="sxs-lookup"><span data-stu-id="acede-203">Cons Pattern</span></span>

<span data-ttu-id="acede-204">Vzorek nevýhod se používá rozložení seznamu na první prvek *head*a seznam, který obsahuje zbývající prvky *tail*.</span><span class="sxs-lookup"><span data-stu-id="acede-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="acede-205">Vzor seznamu</span><span class="sxs-lookup"><span data-stu-id="acede-205">List Pattern</span></span>

<span data-ttu-id="acede-206">Vzor seznamu umožňuje seznamů lze rozložit na počet prvků.</span><span class="sxs-lookup"><span data-stu-id="acede-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="acede-207">Vzor seznamu sám může odpovídat pouze seznamům určitého počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="acede-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="acede-208">Vzor pole</span><span class="sxs-lookup"><span data-stu-id="acede-208">Array Pattern</span></span>

<span data-ttu-id="acede-209">Vzor pole podobá vzoru seznamu a lze použít k rozložení polí určité délky.</span><span class="sxs-lookup"><span data-stu-id="acede-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="acede-210">Vzor v závorce</span><span class="sxs-lookup"><span data-stu-id="acede-210">Parenthesized Pattern</span></span>

<span data-ttu-id="acede-211">Závorky mohou být seskupeny kolem vzorků k dosažení požadované asociativity.</span><span class="sxs-lookup"><span data-stu-id="acede-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="acede-212">V následujícím příkladu jsou použity závorky pro řízení asociativity mezi vzorcem a nevýhody vzoru.</span><span class="sxs-lookup"><span data-stu-id="acede-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="acede-213">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="acede-213">Tuple Pattern</span></span>

<span data-ttu-id="acede-214">Vzor řazené kolekce členů odpovídá formě řazené kolekce členů a umožňuje řazené kolekce členů, které lze rozložit na jeho základní prvky pomocí proměnných porovnání vzorce pro každou pozici v řazené kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="acede-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="acede-215">Následující příklad ukazuje vzor n-tice a také používá vzor literálu, vzory proměnné a vzor zástupných znaků.</span><span class="sxs-lookup"><span data-stu-id="acede-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="acede-216">Vzor záznamu</span><span class="sxs-lookup"><span data-stu-id="acede-216">Record Pattern</span></span>

<span data-ttu-id="acede-217">Vzor záznamu slouží k rozložení záznamů pro extrahování hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="acede-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="acede-218">Vzor nemá odkaz na všechna pole záznamu; Vynechaná pole pouze nejsou součástí srovnávání a nejsou extrahována.</span><span class="sxs-lookup"><span data-stu-id="acede-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="acede-219">Vzorec zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="acede-219">Wildcard Pattern</span></span>

<span data-ttu-id="acede-220">Vzorec zástupných znaků je vyjádřen podtržítkem (`_`) znak a odpovídá jakémukoli zadání, stejně jako vzorec proměnné s tím rozdílem, že je vstup ignorován místo přiřazen proměnné.</span><span class="sxs-lookup"><span data-stu-id="acede-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="acede-221">Vzorec zástupných znaků se často používá v rámci jiných vzorků jako zástupný symbol pro hodnoty, které nejsou potřeba ve výrazu vpravo od `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="acede-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="acede-222">Vzorec zástupných znaků se také často používá na konci seznamu vzorků tak, aby odpovídaly jakémukoli neodpovídajícímu vstupu.</span><span class="sxs-lookup"><span data-stu-id="acede-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="acede-223">Vzorec zástupných znaků je znázorněna v mnoha příkladech kódu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="acede-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="acede-224">Viz předchozí kód pro jedním z příkladů.</span><span class="sxs-lookup"><span data-stu-id="acede-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="acede-225">Vzorky, které mají anotace typu</span><span class="sxs-lookup"><span data-stu-id="acede-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="acede-226">Vzorky mohou mít anotace typu.</span><span class="sxs-lookup"><span data-stu-id="acede-226">Patterns can have type annotations.</span></span> <span data-ttu-id="acede-227">Ty se chovají stejně jako ostatní poznámky typu a příručka pro odvození stejně jako ostatní poznámky typu.</span><span class="sxs-lookup"><span data-stu-id="acede-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="acede-228">Jsou vyžadovány závorky kolem anotace typu ve vzorcích.</span><span class="sxs-lookup"><span data-stu-id="acede-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="acede-229">Následující kód popisuje vzor, který má anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="acede-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="acede-230">Testovací vzorek typu</span><span class="sxs-lookup"><span data-stu-id="acede-230">Type Test Pattern</span></span>

<span data-ttu-id="acede-231">Vzor testovacího typu slouží k porovnání vstupu oproti typu.</span><span class="sxs-lookup"><span data-stu-id="acede-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="acede-232">Pokud je vstupní typ pro vyhledání shody (nebo odvozeným typem) typem určeným ve vzorku, porovnávání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="acede-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="acede-233">Následující příklad ukazuje vzor testu typu.</span><span class="sxs-lookup"><span data-stu-id="acede-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="acede-234">Vzor Null</span><span class="sxs-lookup"><span data-stu-id="acede-234">Null Pattern</span></span>

<span data-ttu-id="acede-235">Vzor null odpovídá hodnotě null, který může zobrazit při práci s typy, které umožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="acede-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="acede-236">Vzory Null jsou často používány při spolupráci s kódu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acede-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="acede-237">Návratová hodnota rozhraní API .NET může být například vstup do `match` výrazu.</span><span class="sxs-lookup"><span data-stu-id="acede-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="acede-238">Můžete řídit tok programu na základě, zda je návratová hodnota null a také na jiných vlastnostech vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="acede-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="acede-239">Vzor null můžete zabránit ostatních částí programu šíření hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="acede-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="acede-240">Následující příklad používá vzor null a vzor proměnné.</span><span class="sxs-lookup"><span data-stu-id="acede-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="acede-241">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acede-241">See also</span></span>

- [<span data-ttu-id="acede-242">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="acede-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="acede-243">Aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="acede-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="acede-244">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="acede-244">F# Language Reference</span></span>](index.md)
