---
title: Porovnávání vzorů
description: 'Naučte se, jak se používají vzory v F # pro porovnání dat s logickými strukturami, rozložení dat na části prvků nebo extrakce informací z dat.'
ms.date: 08/15/2020
ms.openlocfilehash: 6d284b941824bc15a8e872a4e28e22c0e159191d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811506"
---
# <a name="pattern-matching"></a><span data-ttu-id="73642-103">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="73642-103">Pattern Matching</span></span>

<span data-ttu-id="73642-104">Vzory jsou pravidla pro transformaci vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="73642-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="73642-105">Používají se v celém jazyce F # pro porovnání dat s logickou strukturou nebo strukturami, rozložení dat na části prvků nebo extrakce informací z dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="73642-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="73642-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73642-106">Remarks</span></span>

<span data-ttu-id="73642-107">Vzory se používají v mnoha konstrukcích jazyka, jako je například `match` výraz.</span><span class="sxs-lookup"><span data-stu-id="73642-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="73642-108">Používají se při zpracovávání argumentů pro funkce v `let` Bindings, lambda výrazech a v obslužných rutinách výjimek přidružených k `try...with` výrazu.</span><span class="sxs-lookup"><span data-stu-id="73642-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="73642-109">Další informace naleznete v tématu [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [lambda Expressions: `fun` klíčové slovo](./functions/lambda-expressions-the-fun-keyword.md)a [výjimky: `try...with` výraz](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="73642-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="73642-110">Například ve `match` výrazu je *vzor* následujícím způsobem jako symbol kanálu.</span><span class="sxs-lookup"><span data-stu-id="73642-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="73642-111">Každý vzor funguje jako pravidlo pro transformaci vstupu nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="73642-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="73642-112">Ve `match` výrazu je každý vzor zkontrolován a je možné zjistit, zda jsou vstupní data kompatibilní se vzorem.</span><span class="sxs-lookup"><span data-stu-id="73642-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="73642-113">Pokud je nalezena shoda, je proveden výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="73642-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="73642-114">Pokud se shoda nenajde, otestuje se další pravidlo vzoru.</span><span class="sxs-lookup"><span data-stu-id="73642-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="73642-115">Volitelná část when *podmínky* je vysvětlena ve [výrazech shody](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="73642-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="73642-116">V následující tabulce jsou uvedeny podporované vzory.</span><span class="sxs-lookup"><span data-stu-id="73642-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="73642-117">V době spuštění je vstup testován proti každému z následujících vzorů v pořadí uvedeném v tabulce a vzory jsou aplikovány rekurzivně, od první až po zobrazení ve vašem kódu a zleva doprava pro vzorce na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="73642-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="73642-118">Název</span><span class="sxs-lookup"><span data-stu-id="73642-118">Name</span></span>|<span data-ttu-id="73642-119">Popis</span><span class="sxs-lookup"><span data-stu-id="73642-119">Description</span></span>|<span data-ttu-id="73642-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="73642-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="73642-121">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="73642-121">Constant pattern</span></span>|<span data-ttu-id="73642-122">Jakýkoli numerický, znakový nebo řetězcový literál, konstanta výčtu nebo definovaný identifikátor literálu</span><span class="sxs-lookup"><span data-stu-id="73642-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="73642-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="73642-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="73642-124">Vzor identifikátoru</span><span class="sxs-lookup"><span data-stu-id="73642-124">Identifier pattern</span></span>|<span data-ttu-id="73642-125">Hodnota případu rozlišeného sjednocení, popisek výjimky nebo aktivní vzor případu</span><span class="sxs-lookup"><span data-stu-id="73642-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="73642-126">Vzorec proměnné</span><span class="sxs-lookup"><span data-stu-id="73642-126">Variable pattern</span></span>|<span data-ttu-id="73642-127">*RID*</span><span class="sxs-lookup"><span data-stu-id="73642-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="73642-128">`as` vzorku</span><span class="sxs-lookup"><span data-stu-id="73642-128">`as` pattern</span></span>|<span data-ttu-id="73642-129">*vzor* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="73642-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="73642-130">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="73642-130">OR pattern</span></span>|<span data-ttu-id="73642-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="73642-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="73642-132">AND – vzor</span><span class="sxs-lookup"><span data-stu-id="73642-132">AND pattern</span></span>|<span data-ttu-id="73642-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="73642-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="73642-134">Model nevýhody</span><span class="sxs-lookup"><span data-stu-id="73642-134">Cons pattern</span></span>|<span data-ttu-id="73642-135">*identifikátor* :: *list-Identifier*</span><span class="sxs-lookup"><span data-stu-id="73642-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="73642-136">Vzor seznamu</span><span class="sxs-lookup"><span data-stu-id="73642-136">List pattern</span></span>|<span data-ttu-id="73642-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="73642-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="73642-138">Vzor pole</span><span class="sxs-lookup"><span data-stu-id="73642-138">Array pattern</span></span>|<span data-ttu-id="73642-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="73642-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="73642-140">Vzor v závorce</span><span class="sxs-lookup"><span data-stu-id="73642-140">Parenthesized pattern</span></span>|<span data-ttu-id="73642-141">( *vzor* )</span><span class="sxs-lookup"><span data-stu-id="73642-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="73642-142">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="73642-142">Tuple pattern</span></span>|<span data-ttu-id="73642-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="73642-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="73642-144">Vzor záznamu</span><span class="sxs-lookup"><span data-stu-id="73642-144">Record pattern</span></span>|<span data-ttu-id="73642-145">{ *identifier1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="73642-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="73642-146">Vzor zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="73642-146">Wildcard pattern</span></span>|<span data-ttu-id="73642-147">_</span><span class="sxs-lookup"><span data-stu-id="73642-147">_</span></span>|`_`|
|<span data-ttu-id="73642-148">Vzor spolu s anotací typu</span><span class="sxs-lookup"><span data-stu-id="73642-148">Pattern together with type annotation</span></span>|<span data-ttu-id="73642-149">*vzor* : *typ*</span><span class="sxs-lookup"><span data-stu-id="73642-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="73642-150">Vzorek testu typu</span><span class="sxs-lookup"><span data-stu-id="73642-150">Type test pattern</span></span>|<span data-ttu-id="73642-151">:?</span><span class="sxs-lookup"><span data-stu-id="73642-151">:?</span></span> <span data-ttu-id="73642-152">*typ* [jako *identifikátor* ]</span><span class="sxs-lookup"><span data-stu-id="73642-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="73642-153">Vzor null</span><span class="sxs-lookup"><span data-stu-id="73642-153">Null pattern</span></span>|<span data-ttu-id="73642-154">null</span><span class="sxs-lookup"><span data-stu-id="73642-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="73642-155">Konstantní vzorce</span><span class="sxs-lookup"><span data-stu-id="73642-155">Constant Patterns</span></span>

<span data-ttu-id="73642-156">Konstantní vzorce jsou číselné, znakové a řetězcové literály, výčty výčtu (včetně názvu typu výčtu).</span><span class="sxs-lookup"><span data-stu-id="73642-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="73642-157">`match`Výraz, který má pouze konstantní vzorce, lze porovnat s příkazem Case v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="73642-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="73642-158">Vstup je porovnán s hodnotou literálu a vzor se shoduje, pokud jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="73642-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="73642-159">Typ literálu musí být kompatibilní s typem vstupu.</span><span class="sxs-lookup"><span data-stu-id="73642-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="73642-160">Následující příklad ukazuje použití vzorů literálu a také používá vzorec proměnné a vzor nebo.</span><span class="sxs-lookup"><span data-stu-id="73642-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="73642-161">Dalším příkladem literálního vzoru je vzor založený na konstantách výčtu.</span><span class="sxs-lookup"><span data-stu-id="73642-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="73642-162">Pokud používáte konstanty výčtu, je nutné zadat název typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="73642-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="73642-163">Vzory identifikátorů</span><span class="sxs-lookup"><span data-stu-id="73642-163">Identifier Patterns</span></span>

<span data-ttu-id="73642-164">Je-li vzor řetězcem znaků, které tvoří platný identifikátor, forma identifikátoru určuje, jak odpovídá vzor.</span><span class="sxs-lookup"><span data-stu-id="73642-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="73642-165">Pokud je identifikátor delší než jeden znak a začíná velkým znakem, kompilátor se pokusí provést shodu se vzorem identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="73642-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="73642-166">Identifikátor pro tento vzor může být hodnota označená atributem literálu, případem rozlišeného sjednocení, identifikátorem výjimky nebo aktivním vzorem případu.</span><span class="sxs-lookup"><span data-stu-id="73642-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="73642-167">Pokud není nalezen žádný odpovídající identifikátor, shoda se nezdařila a další pravidlo vzoru, proměnná vzor, je porovnána se vstupem.</span><span class="sxs-lookup"><span data-stu-id="73642-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="73642-168">Vzorce rozlišených sjednocení mohou být jednoduché pojmenované případy nebo mohou mít hodnotu nebo řazené kolekce členů obsahující více hodnot.</span><span class="sxs-lookup"><span data-stu-id="73642-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="73642-169">Pokud je hodnota, je nutné zadat identifikátor hodnoty.</span><span class="sxs-lookup"><span data-stu-id="73642-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="73642-170">V případě řazené kolekce členů je nutné dodat vzor řazené kolekce členů s identifikátorem pro každý prvek řazené kolekce členů nebo identifikátor s názvem pole pro jedno nebo více pojmenovaných polí Union.</span><span class="sxs-lookup"><span data-stu-id="73642-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="73642-171">Příklady najdete v příkladech kódu v této části.</span><span class="sxs-lookup"><span data-stu-id="73642-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="73642-172">`option`Typ je rozlišené sjednocení, které má dva případy `Some` a `None` .</span><span class="sxs-lookup"><span data-stu-id="73642-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="73642-173">Jeden případ ( `Some` ) má hodnotu, ale druhý ( `None` ) je pouze pojmenovaný případ.</span><span class="sxs-lookup"><span data-stu-id="73642-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="73642-174">Proto `Some` musí mít proměnnou pro hodnotu přidruženou k `Some` případu, ale `None` musí být uvedena samostatně.</span><span class="sxs-lookup"><span data-stu-id="73642-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="73642-175">V následujícím kódu `var1` je proměnná udělena hodnotě, která je získána spárováním s `Some` případem.</span><span class="sxs-lookup"><span data-stu-id="73642-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="73642-176">V následujícím příkladu `PersonName` obsahuje rozlišené sjednocení kombinaci řetězců a znaků, které reprezentují možné formy názvů.</span><span class="sxs-lookup"><span data-stu-id="73642-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="73642-177">Případy rozlišeného sjednocení jsou `FirstOnly` , `LastOnly` a `FirstLast` .</span><span class="sxs-lookup"><span data-stu-id="73642-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="73642-178">Pro rozlišené sjednocení, která mají pojmenovaná pole, použijte znaménko rovná se (=) k extrakci hodnoty pojmenovaného pole.</span><span class="sxs-lookup"><span data-stu-id="73642-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="73642-179">Zvažte například rozlišené sjednocení s deklarací, jako je následující.</span><span class="sxs-lookup"><span data-stu-id="73642-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="73642-180">Pojmenovaná pole ve výrazu pro porovnávání se vzorci můžete použít následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="73642-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="73642-181">Použití pojmenovaného pole je volitelné, takže v předchozím příkladu má obojí `Circle(r)` a má `Circle(radius = r)` stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="73642-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="73642-182">Pokud zadáte více polí, použijte středník (;) jako oddělovač.</span><span class="sxs-lookup"><span data-stu-id="73642-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="73642-183">Aktivní vzory umožňují definovat komplexnější vlastní porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="73642-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="73642-184">Další informace o aktivních vzorech najdete v tématu [aktivní vzory](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="73642-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="73642-185">Případ, ve kterém je identifikátor výjimkou, se používá v porovnávání vzorů v kontextu obslužných rutin výjimek.</span><span class="sxs-lookup"><span data-stu-id="73642-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="73642-186">Informace o porovnávání vzorů při zpracování výjimek naleznete v tématu [výjimky: `try...with` výraz](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="73642-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="73642-187">Vzorce proměnných</span><span class="sxs-lookup"><span data-stu-id="73642-187">Variable Patterns</span></span>

<span data-ttu-id="73642-188">Vzorec proměnné přiřadí hodnotu, která odpovídá názvu proměnné, který je pak k dispozici pro použití ve výrazu spuštění napravo od `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="73642-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="73642-189">Proměnlivý vzorek se shoduje se všemi vstupy, ale vzory proměnných se často zobrazují v rámci jiných vzorů, čímž je umožněno rozložit komplexnější struktury, jako jsou například řazené kolekce členů a pole, aby byly rozložené do proměnných</span><span class="sxs-lookup"><span data-stu-id="73642-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="73642-190">Následující příklad ukazuje vzor proměnné v rámci vzoru řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="73642-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="73642-191">jako vzor</span><span class="sxs-lookup"><span data-stu-id="73642-191">as Pattern</span></span>

<span data-ttu-id="73642-192">`as`Vzor je vzor, ke kterému je `as` připojena klauzule.</span><span class="sxs-lookup"><span data-stu-id="73642-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="73642-193">`as`Klauzule váže odpovídající hodnotu k názvu, který lze použít ve výrazu provedení `match` výrazu, nebo v případě, že je tento vzor použit ve `let` vazbě, je název přidán jako vazba do místního oboru.</span><span class="sxs-lookup"><span data-stu-id="73642-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="73642-194">Následující příklad používá `as` vzor.</span><span class="sxs-lookup"><span data-stu-id="73642-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="73642-195">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="73642-195">OR Pattern</span></span>

<span data-ttu-id="73642-196">Vzor nebo se používá, pokud vstupní data mohou odpovídat více vzorům a chcete spustit stejný kód jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="73642-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="73642-197">Typy obou stran vzoru OR musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="73642-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="73642-198">Následující příklad znázorňuje vzor nebo.</span><span class="sxs-lookup"><span data-stu-id="73642-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="73642-199">AND – vzor</span><span class="sxs-lookup"><span data-stu-id="73642-199">AND Pattern</span></span>

<span data-ttu-id="73642-200">Vzor a vyžaduje, aby vstup odpovídal dvěma vzorům.</span><span class="sxs-lookup"><span data-stu-id="73642-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="73642-201">Typy obou stran vzoru a musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="73642-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="73642-202">Následující příklad je podobný jako `detectZeroTuple` v části vzor řazené kolekce členů dále v tomto tématu, ale tady `var1` a `var2` se získává jako hodnoty pomocí vzoru a.</span><span class="sxs-lookup"><span data-stu-id="73642-202">The following example is like `detectZeroTuple` shown in the Tuple Pattern section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="73642-203">Model nevýhody</span><span class="sxs-lookup"><span data-stu-id="73642-203">Cons Pattern</span></span>

<span data-ttu-id="73642-204">Vzorec nevýhody slouží k rozloží seznamu do prvního prvku, *záhlaví*a seznamu, který obsahuje zbývající prvky, *konec*.</span><span class="sxs-lookup"><span data-stu-id="73642-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="73642-205">Vzor seznamu</span><span class="sxs-lookup"><span data-stu-id="73642-205">List Pattern</span></span>

<span data-ttu-id="73642-206">Vzor seznamu umožňuje rozložit seznamy na několik prvků.</span><span class="sxs-lookup"><span data-stu-id="73642-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="73642-207">Samotný vzor seznamu může odpovídat pouze seznamům určitého počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="73642-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="73642-208">Vzor pole</span><span class="sxs-lookup"><span data-stu-id="73642-208">Array Pattern</span></span>

<span data-ttu-id="73642-209">Vzor pole se podobá vzoru seznamu a lze jej použít k rozložení polí určité délky.</span><span class="sxs-lookup"><span data-stu-id="73642-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="73642-210">Vzor v závorce</span><span class="sxs-lookup"><span data-stu-id="73642-210">Parenthesized Pattern</span></span>

<span data-ttu-id="73642-211">Závorky lze seskupit kolem vzorů, abyste dosáhli požadovaného asociativita.</span><span class="sxs-lookup"><span data-stu-id="73642-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="73642-212">V následujícím příkladu jsou použity kulaté závorky k řízení asociativita mezi vzorem a a modelem nevýhody.</span><span class="sxs-lookup"><span data-stu-id="73642-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="73642-213">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="73642-213">Tuple Pattern</span></span>

<span data-ttu-id="73642-214">Vzor řazené kolekce členů odpovídá vstupu ve formuláři řazené kolekce členů a umožňuje rozdělit řazené kolekce členů pomocí proměnných pro porovnávání vzorů pro každou pozici v řazené kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="73642-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="73642-215">Následující příklad znázorňuje vzor řazené kolekce členů a také používá vzory literálů, vzorce proměnných a vzor zástupného znaku.</span><span class="sxs-lookup"><span data-stu-id="73642-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="73642-216">Vzor záznamu</span><span class="sxs-lookup"><span data-stu-id="73642-216">Record Pattern</span></span>

<span data-ttu-id="73642-217">Vzor záznamu slouží k rozbalování záznamů pro extrakci hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="73642-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="73642-218">Vzor nemusí odkazovat na všechna pole záznamu; všechna vynechaná pole se nepodílejí na shodě a nejsou extrahována.</span><span class="sxs-lookup"><span data-stu-id="73642-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="73642-219">Vzor zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="73642-219">Wildcard Pattern</span></span>

<span data-ttu-id="73642-220">Vzor zástupných znaků je reprezentován znakem podtržítka ( `_` ) a odpovídá jakémukoli vstupu, stejně jako variabilní vzorek, s tím rozdílem, že vstup je zahozen namísto přiřazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="73642-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="73642-221">Vzor zástupných znaků se často používá v jiných vzorcích jako zástupný symbol pro hodnoty, které nejsou nutné ve výrazu napravo od `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="73642-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="73642-222">Vzor zástupných znaků se také často používá na konci seznamu vzorů, aby odpovídal jakémukoli neodpovídajícímu vstupu.</span><span class="sxs-lookup"><span data-stu-id="73642-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="73642-223">Vzor zástupných znaků je znázorněn v mnoha příkladech kódu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="73642-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="73642-224">Viz předchozí kód pro jeden příklad.</span><span class="sxs-lookup"><span data-stu-id="73642-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="73642-225">Vzory, které mají anotace typu</span><span class="sxs-lookup"><span data-stu-id="73642-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="73642-226">Vzory mohou mít anotace typu.</span><span class="sxs-lookup"><span data-stu-id="73642-226">Patterns can have type annotations.</span></span> <span data-ttu-id="73642-227">Chovají se podobně jako jiné anotace typu a odvozené vodítko jako jiné anotace typu.</span><span class="sxs-lookup"><span data-stu-id="73642-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="73642-228">Pro anotace typu ve vzorcích jsou vyžadovány kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="73642-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="73642-229">Následující kód ukazuje vzor, který má anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="73642-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="73642-230">Vzorek testu typu</span><span class="sxs-lookup"><span data-stu-id="73642-230">Type Test Pattern</span></span>

<span data-ttu-id="73642-231">Vzor testu typu se používá pro porovnání vstupu proti typu.</span><span class="sxs-lookup"><span data-stu-id="73642-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="73642-232">Pokud je vstupní typ shodný s typem (nebo odvozeného typu) typu zadaného ve vzorku, shoda se zdaří.</span><span class="sxs-lookup"><span data-stu-id="73642-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="73642-233">Následující příklad ukazuje vzorek testu typu.</span><span class="sxs-lookup"><span data-stu-id="73642-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="73642-234">Pokud pouze kontrolujete, zda je identifikátor určitého odvozeného typu, nepotřebujete `as identifier` část vzoru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="73642-234">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a><span data-ttu-id="73642-235">Vzor null</span><span class="sxs-lookup"><span data-stu-id="73642-235">Null Pattern</span></span>

<span data-ttu-id="73642-236">Vzor null odpovídá hodnotě null, která se může zobrazit při práci s typy, které povolují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="73642-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="73642-237">Vzory null jsou často používány při spolupráci s .NET Framework kódem.</span><span class="sxs-lookup"><span data-stu-id="73642-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="73642-238">Například návratová hodnota rozhraní .NET API může být vstupní hodnotou `match` výrazu.</span><span class="sxs-lookup"><span data-stu-id="73642-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="73642-239">Můžete řídit tok programu na základě toho, zda vrácená hodnota je null, a také na dalších charakteristikách vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="73642-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="73642-240">Pomocí vzoru null můžete zabránit šíření hodnot null do zbytku programu.</span><span class="sxs-lookup"><span data-stu-id="73642-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="73642-241">Následující příklad používá vzory null a variabilní vzorek.</span><span class="sxs-lookup"><span data-stu-id="73642-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="73642-242">Viz také</span><span class="sxs-lookup"><span data-stu-id="73642-242">See also</span></span>

- [<span data-ttu-id="73642-243">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="73642-243">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="73642-244">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="73642-244">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="73642-245">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="73642-245">F# Language Reference</span></span>](index.md)
