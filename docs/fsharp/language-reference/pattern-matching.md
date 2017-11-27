---
title: "Porovnávání vzorů (F#)"
description: "Zjistěte, jak se používají vzory v jazyce F # k porovnání dat pomocí logické struktury, rozloží data na základní části nebo extrahovat informace z dat."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a><span data-ttu-id="858a8-104">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="858a8-104">Pattern Matching</span></span>

<span data-ttu-id="858a8-105">Vzory jsou pravidla pro transformaci vstupní data.</span><span class="sxs-lookup"><span data-stu-id="858a8-105">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="858a8-106">Používají se v průběhu jazyk F # k porovnání data pomocí logické struktury nebo struktury, rozloží data na základní části nebo extrahovat informace z dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="858a8-106">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="858a8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="858a8-107">Remarks</span></span>
<span data-ttu-id="858a8-108">Vzorky se používají v mnoha jazykové konstrukty, jako `match` výraz.</span><span class="sxs-lookup"><span data-stu-id="858a8-108">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="858a8-109">Se používají při zpracování argumenty pro funkce v `let` vazby, výrazů lambda a v obslužné rutiny výjimek, které jsou přidružené k `try...with` výraz.</span><span class="sxs-lookup"><span data-stu-id="858a8-109">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="858a8-110">Další informace najdete v tématu [výrazy shody](match-expressions.md), [let – vazby](functions/let-bindings.md), [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md), a [výjimkami: `try...with` Výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="858a8-110">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="858a8-111">Například v `match` výrazu *vzor* je co následuje symbol kanálu.</span><span class="sxs-lookup"><span data-stu-id="858a8-111">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="858a8-112">Každý vzor funguje jako pravidlo pro transformaci vstup nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="858a8-112">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="858a8-113">V `match` výrazu, každý vzor je ověřuje, pak pokud vstupní data je kompatibilní s vzoru.</span><span class="sxs-lookup"><span data-stu-id="858a8-113">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="858a8-114">Pokud je nalezena shoda, se spustí výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="858a8-114">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="858a8-115">Pokud není nalezena shoda, je otestovat další vzor pravidel.</span><span class="sxs-lookup"><span data-stu-id="858a8-115">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="858a8-116">Volitelné při *podmínku* části je vysvětlen v [výrazy shody](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="858a8-116">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="858a8-117">V následující tabulce jsou uvedeny podporované vzory.</span><span class="sxs-lookup"><span data-stu-id="858a8-117">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="858a8-118">V době běhu vstup je testován vůči každé z následujících vzory v uvedeném v tabulce pořadí a vzory jsou rekurzivně, z první poslední jak se objeví ve vašem kódu a zleva doprava pro vzory na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="858a8-118">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="858a8-119">Název</span><span class="sxs-lookup"><span data-stu-id="858a8-119">Name</span></span>|<span data-ttu-id="858a8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="858a8-120">Description</span></span>|<span data-ttu-id="858a8-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="858a8-121">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="858a8-122">Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-122">Constant pattern</span></span>|<span data-ttu-id="858a8-123">Jakékoli číselné, znak, nebo řetězcový literál, konstanta výčtu nebo identifikátor definovaný literálu</span><span class="sxs-lookup"><span data-stu-id="858a8-123">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="858a8-124">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="858a8-124">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="858a8-125">Identifikátor – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-125">Identifier pattern</span></span>|<span data-ttu-id="858a8-126">Hodnota case rozlišovaná sjednocení, popisek výjimky nebo s případem – aktivní vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-126">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="858a8-127">Proměnná – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-127">Variable pattern</span></span>|<span data-ttu-id="858a8-128">*identifikátor*</span><span class="sxs-lookup"><span data-stu-id="858a8-128">*identifier*</span></span>|`a`|
|<span data-ttu-id="858a8-129">`as`vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-129">`as` pattern</span></span>|<span data-ttu-id="858a8-130">*vzor* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="858a8-130">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="858a8-131">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-131">OR pattern</span></span>|<span data-ttu-id="858a8-132">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="858a8-132">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="858a8-133">A vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-133">AND pattern</span></span>|<span data-ttu-id="858a8-134">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="858a8-134">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="858a8-135">Cons vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-135">Cons pattern</span></span>|<span data-ttu-id="858a8-136">*identifikátor* :: *seznamu identifikátorů*</span><span class="sxs-lookup"><span data-stu-id="858a8-136">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="858a8-137">Seznam – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-137">List pattern</span></span>|<span data-ttu-id="858a8-138">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="858a8-138">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="858a8-139">Pole – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-139">Array pattern</span></span>|<span data-ttu-id="858a8-140">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="858a8-140">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="858a8-141">Závorky – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-141">Parenthesized pattern</span></span>|<span data-ttu-id="858a8-142">( *vzor* )</span><span class="sxs-lookup"><span data-stu-id="858a8-142">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="858a8-143">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="858a8-143">Tuple pattern</span></span>|<span data-ttu-id="858a8-144">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="858a8-144">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="858a8-145">Záznam – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-145">Record pattern</span></span>|<span data-ttu-id="858a8-146">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="858a8-146">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="858a8-147">Zástupný znak – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-147">Wildcard pattern</span></span>|<span data-ttu-id="858a8-148">_</span><span class="sxs-lookup"><span data-stu-id="858a8-148">_</span></span>|`_`|
|<span data-ttu-id="858a8-149">Vzor společně s anotaci typu</span><span class="sxs-lookup"><span data-stu-id="858a8-149">Pattern together with type annotation</span></span>|<span data-ttu-id="858a8-150">*vzor* : *typu*</span><span class="sxs-lookup"><span data-stu-id="858a8-150">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="858a8-151">Typ testu vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-151">Type test pattern</span></span>|<span data-ttu-id="858a8-152">:?</span><span class="sxs-lookup"><span data-stu-id="858a8-152">:?</span></span> <span data-ttu-id="858a8-153">*typ* [jako *identifikátor* ]</span><span class="sxs-lookup"><span data-stu-id="858a8-153">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="858a8-154">Null – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-154">Null pattern</span></span>|<span data-ttu-id="858a8-155">null</span><span class="sxs-lookup"><span data-stu-id="858a8-155">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="858a8-156">Konstantní vzory</span><span class="sxs-lookup"><span data-stu-id="858a8-156">Constant Patterns</span></span>
<span data-ttu-id="858a8-157">Konstantní vzorky se číselný znak a textové literály konstanty výčtu (s názvem typu výčtu zahrnuté).</span><span class="sxs-lookup"><span data-stu-id="858a8-157">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="858a8-158">A `match` výraz, který má pouze konstantní vzory lze porovnat s hodnotou pro příkaz case v dalších jazycích.</span><span class="sxs-lookup"><span data-stu-id="858a8-158">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="858a8-159">Vstup se porovná s literálovou hodnotou a vzor odpovídá, pokud jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="858a8-159">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="858a8-160">Typ literál musí být kompatibilní s typem vstupu.</span><span class="sxs-lookup"><span data-stu-id="858a8-160">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="858a8-161">Následující příklad ukazuje použití literálu vzory a také používá proměnné vzor a nebo vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-161">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="858a8-162">Další příklad literálu vzor je vzor, podle konstanty výčtu.</span><span class="sxs-lookup"><span data-stu-id="858a8-162">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="858a8-163">Při použití konstanty výčtu, musíte zadat název typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="858a8-163">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="858a8-164">Identifikátor vzory</span><span class="sxs-lookup"><span data-stu-id="858a8-164">Identifier Patterns</span></span>
<span data-ttu-id="858a8-165">Pokud vzor je řetězec znaků, která tvoří platný identifikátor, formu identifikátor určuje, jak je shodují se vzorem.</span><span class="sxs-lookup"><span data-stu-id="858a8-165">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="858a8-166">Pokud identifikátor je delší než jeden znak a začíná velké písmeno, kompilátor se pokouší provést odpovídající vzor identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="858a8-166">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="858a8-167">Identifikátor pro tento vzor může být hodnota označené jako atribut literálu, rozlišovaná – případ typu union, výjimka identifikátoru nebo případ – aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-167">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="858a8-168">Pokud se nenajde žádný odpovídající identifikátor, shoda se nezdaří a další vzor pravidel, proměnná – vzor, je ve srovnání s vstupu.</span><span class="sxs-lookup"><span data-stu-id="858a8-168">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="858a8-169">Rozlišovaná sjednocení vzory může být jednoduchý s názvem případech nebo můžou mít hodnotu nebo řazené kolekce členů obsahující více hodnot.</span><span class="sxs-lookup"><span data-stu-id="858a8-169">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="858a8-170">Pokud je hodnota, je nutné zadat identifikátor pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="858a8-170">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="858a8-171">V případě řazené kolekce členů je nutné zadat vzorek řazené kolekce členů s identifikátorem pro každý prvek řazenou kolekci členů nebo identifikátor jiný název pro jednu nebo více s názvem union pole.</span><span class="sxs-lookup"><span data-stu-id="858a8-171">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="858a8-172">Příklady kódu v této části Příklady.</span><span class="sxs-lookup"><span data-stu-id="858a8-172">See the code examples in this section for examples.</span></span>

<span data-ttu-id="858a8-173">`option` Typ je rozlišovaná sjednocení, která má dva případy `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="858a8-173">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="858a8-174">Jeden případ (`Some`) má hodnotu, ale druhá (`None`) je právě pojmenované případu.</span><span class="sxs-lookup"><span data-stu-id="858a8-174">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="858a8-175">Proto `Some` musí mít proměnnou pro hodnotu přidruženou `Some` případu, ale `None` musí být samostatně.</span><span class="sxs-lookup"><span data-stu-id="858a8-175">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="858a8-176">V následujícím kódu, proměnná `var1` je zadána hodnota, která se získávají pomocí odpovídajících k `Some` případu.</span><span class="sxs-lookup"><span data-stu-id="858a8-176">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="858a8-177">V následujícím příkladu `PersonName` rozlišovaná sjednocení obsahuje směs řetězce a znaky, které představují možné formy názvy.</span><span class="sxs-lookup"><span data-stu-id="858a8-177">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="858a8-178">V případech rozlišovaná sjednocení jsou `FirstOnly`, `LastOnly`, a `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="858a8-178">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="858a8-179">Pro rozlišovaná sjednocení, které mají pojmenované pole použijete k získání hodnoty z pole s názvem symbolem rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="858a8-179">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="858a8-180">Představte si třeba rozlišovaná sjednocení s deklaraci podobně jako tento.</span><span class="sxs-lookup"><span data-stu-id="858a8-180">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="858a8-181">Pole s názvem ve výrazu odpovídající vzor můžete použít následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="858a8-181">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="858a8-182">Použití s názvem pole je volitelné, takže v předchozím příkladu obě `Circle(r)` a `Circle(radius = r)` mají stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="858a8-182">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="858a8-183">Pokud zadáte více polí, použijte středník (;) jako oddělovač.</span><span class="sxs-lookup"><span data-stu-id="858a8-183">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="858a8-184">Aktivní vzorky umožňují definovat složitější odpovídající vlastní vzorek.</span><span class="sxs-lookup"><span data-stu-id="858a8-184">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="858a8-185">Další informace o aktivní vzorky najdete v tématu [aktivní vzorky](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="858a8-185">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="858a8-186">Případ, ve kterém je identifikátor výjimku se používá v porovnávání se v kontextu obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="858a8-186">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="858a8-187">Informace o porovnávání se ve zpracování výjimek najdete v tématu [výjimkami: `try...with` výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="858a8-187">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="858a8-188">Proměnné vzory</span><span class="sxs-lookup"><span data-stu-id="858a8-188">Variable Patterns</span></span>
<span data-ttu-id="858a8-189">Hodnota se namapovat na název proměnné, která je pak k dispozici pro použití ve výrazu provádění napravo od přiřadí proměnné vzor `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="858a8-189">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="858a8-190">Žádný vstup odpovídá proměnné vzor samostatně, ale proměnné vzory často se v rámci jiné vzory, proto povolení složitější struktury například řazených kolekcí členů a aby rozložit na proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="858a8-190">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="858a8-191">Následující příklad ukazuje, proměnná – vzor v rámci vzor řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="858a8-191">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="858a8-192">As – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-192">as Pattern</span></span>
<span data-ttu-id="858a8-193">`as` Vzor je vzor, který má `as` klauzule, přidá se k němu.</span><span class="sxs-lookup"><span data-stu-id="858a8-193">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="858a8-194">`as` Klauzule váže odpovídající hodnotu pro název, který lze použít ve výrazu provádění `match` výrazu, nebo v případě, kdy se tento vzor používá v `let` vazby, název je přidán jako vazbu na místní obor.</span><span class="sxs-lookup"><span data-stu-id="858a8-194">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="858a8-195">Následující příklad používá `as` vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-195">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="858a8-196">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-196">OR Pattern</span></span>
<span data-ttu-id="858a8-197">Vzor nebo se používá, pokud vstupní data může odpovídat více vzorů, a chcete provést v důsledku stejný kód.</span><span class="sxs-lookup"><span data-stu-id="858a8-197">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="858a8-198">Typy obou stranách vzoru nebo musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="858a8-198">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="858a8-199">Následující příklad ukazuje nebo vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-199">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="858a8-200">A vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-200">AND Pattern</span></span>
<span data-ttu-id="858a8-201">Vzor a vyžaduje, aby vstupní shodovala dva vzory.</span><span class="sxs-lookup"><span data-stu-id="858a8-201">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="858a8-202">Typy obou stranách tohoto vzoru a musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="858a8-202">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="858a8-203">V následujícím příkladu je stejná jako `detectZeroTuple` ukazuje [řazené kolekce členů vzor](https://msdn.microsoft.com/library/#tuple) části později v tomto tématu, ale zde obě `var1` a `var2` zjištěny jako hodnoty pomocí vzoru a.</span><span class="sxs-lookup"><span data-stu-id="858a8-203">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="858a8-204">Cons vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-204">Cons Pattern</span></span>
<span data-ttu-id="858a8-205">Vzor cons se používá k rozložit na první prvek seznamu *head*a seznam obsahující zbývající elementy, *tail*.</span><span class="sxs-lookup"><span data-stu-id="858a8-205">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="858a8-206">Seznam – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-206">List Pattern</span></span>
<span data-ttu-id="858a8-207">Vzor seznamu umožňuje seznamy musí rozložit na počet elementů.</span><span class="sxs-lookup"><span data-stu-id="858a8-207">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="858a8-208">Vzor seznamu sám může odpovídat pouze seznam konkrétní počet elementů.</span><span class="sxs-lookup"><span data-stu-id="858a8-208">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="858a8-209">Pole – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-209">Array Pattern</span></span>
<span data-ttu-id="858a8-210">Vzor pole vypadá takto: seznam – vzor a slouží k rozložit pole konkrétní délku.</span><span class="sxs-lookup"><span data-stu-id="858a8-210">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="858a8-211">Závorky – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-211">Parenthesized Pattern</span></span>
<span data-ttu-id="858a8-212">Závorky lze seskupovat kolem vzory k dosažení požadované asociativnost.</span><span class="sxs-lookup"><span data-stu-id="858a8-212">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="858a8-213">V následujícím příkladu kulaté závorky slouží k řízení asociativnost mezi a vzor a vzor nevýhody.</span><span class="sxs-lookup"><span data-stu-id="858a8-213">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="858a8-214">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="858a8-214">Tuple Pattern</span></span>
<span data-ttu-id="858a8-215">Řazené kolekce členů vzor odpovídá vstup ve formuláři řazené kolekce členů a umožňuje řazené kolekce členů musí rozložit na jeho základní prvky pomocí proměnných pro každý pozice v řazené kolekci členů porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="858a8-215">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="858a8-216">Následující příklad ukazuje vzoru řazené kolekce členů a také používá literálu vzory, proměnné vzorce a zástupný znak – vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-216">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="858a8-217">Záznam – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-217">Record Pattern</span></span>
<span data-ttu-id="858a8-218">Vzor záznam se používá k rozložit záznamy k extrakci hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="858a8-218">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="858a8-219">Chcete-li všechna pole záznamu; nemá vzoru všechna pole vynechání právě neúčastnit odpovídající a nejsou rozbalené.</span><span class="sxs-lookup"><span data-stu-id="858a8-219">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="858a8-220">Zástupný znak – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-220">Wildcard Pattern</span></span>
<span data-ttu-id="858a8-221">Zástupný znak – vzor je reprezentována podtržítko (`_`) znak a odpovídá žádný vstup, stejně jako proměnné vzor, s tím rozdílem, že vstup se zahodí místo přiřazený k proměnné.</span><span class="sxs-lookup"><span data-stu-id="858a8-221">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="858a8-222">Zástupný znak – vzor se často používá v rámci jiných vzorů jako zástupný symbol pro hodnoty, které nejsou potřebné ve výrazu napravo `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="858a8-222">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="858a8-223">Zástupný znak – vzor slouží také často na konci seznam vzorů tak, aby odpovídaly jakékoli neodpovídající vstup.</span><span class="sxs-lookup"><span data-stu-id="858a8-223">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="858a8-224">Zástupný znak – vzor je znázorněn v mnoha příklady kódu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="858a8-224">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="858a8-225">Viz předchozí kód pro jedním z příkladů.</span><span class="sxs-lookup"><span data-stu-id="858a8-225">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="858a8-226">Vzorce, které mají typ poznámky</span><span class="sxs-lookup"><span data-stu-id="858a8-226">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="858a8-227">Vzory může mít typ poznámek.</span><span class="sxs-lookup"><span data-stu-id="858a8-227">Patterns can have type annotations.</span></span> <span data-ttu-id="858a8-228">Tyto chovají jako dalších typů poznámek a Průvodce odvození jako dalších typ poznámek.</span><span class="sxs-lookup"><span data-stu-id="858a8-228">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="858a8-229">Kolem typ poznámky v vzory jsou vyžadovány závorky.</span><span class="sxs-lookup"><span data-stu-id="858a8-229">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="858a8-230">Následující kód ukazuje vzor, který má anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="858a8-230">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="858a8-231">Typ testu vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-231">Type Test Pattern</span></span>
<span data-ttu-id="858a8-232">Typ testu vzor slouží k přiřazování vstup podle typu.</span><span class="sxs-lookup"><span data-stu-id="858a8-232">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="858a8-233">Pokud vstupní typ je shoda pro (nebo odvozené typ) s typem zadaným ve vzoru shody úspěšné.</span><span class="sxs-lookup"><span data-stu-id="858a8-233">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="858a8-234">Následující příklad ukazuje typ testovací vzorek.</span><span class="sxs-lookup"><span data-stu-id="858a8-234">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="858a8-235">Null – vzor</span><span class="sxs-lookup"><span data-stu-id="858a8-235">Null Pattern</span></span>
<span data-ttu-id="858a8-236">Null vzor odpovídá hodnotu null, která se může zobrazit při práci s typy, které umožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="858a8-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="858a8-237">Null vzorů se často používají při interoperabilitě se službou kódu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="858a8-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="858a8-238">Návratová hodnota rozhraní API .NET může být například vstup `match` výraz.</span><span class="sxs-lookup"><span data-stu-id="858a8-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="858a8-239">Můžete řídit tok programu na základě, zda je návratovou hodnotu null a také na dalších vlastností vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="858a8-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="858a8-240">Null vzor můžete zabránit s ostatními vašeho programu při šíření hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="858a8-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="858a8-241">Následující příklad používá vzoru hodnotu null a proměnná – vzor.</span><span class="sxs-lookup"><span data-stu-id="858a8-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="858a8-242">Viz také</span><span class="sxs-lookup"><span data-stu-id="858a8-242">See Also</span></span>
[<span data-ttu-id="858a8-243">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="858a8-243">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="858a8-244">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="858a8-244">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="858a8-245">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="858a8-245">F# Language Reference</span></span>](index.md)
