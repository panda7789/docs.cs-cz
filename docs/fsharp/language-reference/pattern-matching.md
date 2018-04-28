---
title: Porovnávání vzorů (F#)
description: 'Zjistěte, jak se používají vzory v jazyce F # k porovnání dat pomocí logické struktury, rozloží data na základní části nebo extrahovat informace z dat.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 31a5b321e5daecdc3add9a205d60b63b2c00ccd2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="pattern-matching"></a><span data-ttu-id="b9d44-103">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="b9d44-103">Pattern Matching</span></span>

<span data-ttu-id="b9d44-104">Vzory jsou pravidla pro transformaci vstupní data.</span><span class="sxs-lookup"><span data-stu-id="b9d44-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="b9d44-105">Používají se v průběhu jazyk F # k porovnání data pomocí logické struktury nebo struktury, rozloží data na základní části nebo extrahovat informace z dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b9d44-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="b9d44-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9d44-106">Remarks</span></span>
<span data-ttu-id="b9d44-107">Vzorky se používají v mnoha jazykové konstrukty, jako `match` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9d44-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="b9d44-108">Se používají při zpracování argumenty pro funkce v `let` vazby, výrazů lambda a v obslužné rutiny výjimek, které jsou přidružené k `try...with` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9d44-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="b9d44-109">Další informace najdete v tématu [výrazy shody](match-expressions.md), [let – vazby](functions/let-bindings.md), [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md), a [výjimkami: `try...with` Výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="b9d44-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="b9d44-110">Například v `match` výrazu *vzor* je co následuje symbol kanálu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="b9d44-111">Každý vzor funguje jako pravidlo pro transformaci vstup nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9d44-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="b9d44-112">V `match` výrazu, každý vzor je ověřuje, pak pokud vstupní data je kompatibilní s vzoru.</span><span class="sxs-lookup"><span data-stu-id="b9d44-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="b9d44-113">Pokud je nalezena shoda, se spustí výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="b9d44-114">Pokud není nalezena shoda, je otestovat další vzor pravidel.</span><span class="sxs-lookup"><span data-stu-id="b9d44-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="b9d44-115">Volitelné při *podmínku* části je vysvětlen v [výrazy shody](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b9d44-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="b9d44-116">V následující tabulce jsou uvedeny podporované vzory.</span><span class="sxs-lookup"><span data-stu-id="b9d44-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="b9d44-117">V době běhu vstup je testován vůči každé z následujících vzory v uvedeném v tabulce pořadí a vzory jsou rekurzivně, z první poslední jak se objeví ve vašem kódu a zleva doprava pro vzory na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="b9d44-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="b9d44-118">Název</span><span class="sxs-lookup"><span data-stu-id="b9d44-118">Name</span></span>|<span data-ttu-id="b9d44-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b9d44-119">Description</span></span>|<span data-ttu-id="b9d44-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9d44-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="b9d44-121">Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-121">Constant pattern</span></span>|<span data-ttu-id="b9d44-122">Jakékoli číselné, znak, nebo řetězcový literál, konstanta výčtu nebo identifikátor definovaný literálu</span><span class="sxs-lookup"><span data-stu-id="b9d44-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="b9d44-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="b9d44-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="b9d44-124">Identifikátor – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-124">Identifier pattern</span></span>|<span data-ttu-id="b9d44-125">Hodnota case rozlišovaná sjednocení, popisek výjimky nebo s případem – aktivní vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="b9d44-126">Proměnná – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-126">Variable pattern</span></span>|<span data-ttu-id="b9d44-127">*Identifikátor*</span><span class="sxs-lookup"><span data-stu-id="b9d44-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="b9d44-128">`as` vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-128">`as` pattern</span></span>|<span data-ttu-id="b9d44-129">*vzor* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="b9d44-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="b9d44-130">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-130">OR pattern</span></span>|<span data-ttu-id="b9d44-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="b9d44-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="b9d44-132">A vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-132">AND pattern</span></span>|<span data-ttu-id="b9d44-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="b9d44-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="b9d44-134">Cons vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-134">Cons pattern</span></span>|<span data-ttu-id="b9d44-135">*identifikátor* :: *seznamu identifikátorů*</span><span class="sxs-lookup"><span data-stu-id="b9d44-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="b9d44-136">Seznam – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-136">List pattern</span></span>|<span data-ttu-id="b9d44-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="b9d44-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="b9d44-138">Pole – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-138">Array pattern</span></span>|<span data-ttu-id="b9d44-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="b9d44-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="b9d44-140">Závorky – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-140">Parenthesized pattern</span></span>|<span data-ttu-id="b9d44-141">( *vzor* )</span><span class="sxs-lookup"><span data-stu-id="b9d44-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="b9d44-142">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="b9d44-142">Tuple pattern</span></span>|<span data-ttu-id="b9d44-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="b9d44-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="b9d44-144">Záznam – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-144">Record pattern</span></span>|<span data-ttu-id="b9d44-145">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="b9d44-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="b9d44-146">Zástupný znak – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-146">Wildcard pattern</span></span>|<span data-ttu-id="b9d44-147">_</span><span class="sxs-lookup"><span data-stu-id="b9d44-147">_</span></span>|`_`|
|<span data-ttu-id="b9d44-148">Vzor společně s anotaci typu</span><span class="sxs-lookup"><span data-stu-id="b9d44-148">Pattern together with type annotation</span></span>|<span data-ttu-id="b9d44-149">*vzor* : *typu*</span><span class="sxs-lookup"><span data-stu-id="b9d44-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="b9d44-150">Typ testu vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-150">Type test pattern</span></span>|<span data-ttu-id="b9d44-151">:?</span><span class="sxs-lookup"><span data-stu-id="b9d44-151">:?</span></span> <span data-ttu-id="b9d44-152">*typ* [jako *identifikátor* ]</span><span class="sxs-lookup"><span data-stu-id="b9d44-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="b9d44-153">Null – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-153">Null pattern</span></span>|<span data-ttu-id="b9d44-154">null</span><span class="sxs-lookup"><span data-stu-id="b9d44-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="b9d44-155">Konstantní vzory</span><span class="sxs-lookup"><span data-stu-id="b9d44-155">Constant Patterns</span></span>
<span data-ttu-id="b9d44-156">Konstantní vzorky se číselný znak a textové literály konstanty výčtu (s názvem typu výčtu zahrnuté).</span><span class="sxs-lookup"><span data-stu-id="b9d44-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="b9d44-157">A `match` výraz, který má pouze konstantní vzory lze porovnat s hodnotou pro příkaz case v dalších jazycích.</span><span class="sxs-lookup"><span data-stu-id="b9d44-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="b9d44-158">Vstup se porovná s literálovou hodnotou a vzor odpovídá, pokud jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="b9d44-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="b9d44-159">Typ literál musí být kompatibilní s typem vstupu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="b9d44-160">Následující příklad ukazuje použití literálu vzory a také používá proměnné vzor a nebo vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="b9d44-161">Další příklad literálu vzor je vzor, podle konstanty výčtu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="b9d44-162">Při použití konstanty výčtu, musíte zadat název typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="b9d44-163">Identifikátor vzory</span><span class="sxs-lookup"><span data-stu-id="b9d44-163">Identifier Patterns</span></span>
<span data-ttu-id="b9d44-164">Pokud vzor je řetězec znaků, která tvoří platný identifikátor, formu identifikátor určuje, jak je shodují se vzorem.</span><span class="sxs-lookup"><span data-stu-id="b9d44-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="b9d44-165">Pokud identifikátor je delší než jeden znak a začíná velké písmeno, kompilátor se pokouší provést odpovídající vzor identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b9d44-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="b9d44-166">Identifikátor pro tento vzor může být hodnota označené jako atribut literálu, rozlišovaná – případ typu union, výjimka identifikátoru nebo případ – aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="b9d44-167">Pokud se nenajde žádný odpovídající identifikátor, shoda se nezdaří a další vzor pravidel, proměnná – vzor, je ve srovnání s vstupu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="b9d44-168">Rozlišovaná sjednocení vzory může být jednoduchý s názvem případech nebo můžou mít hodnotu nebo řazené kolekce členů obsahující více hodnot.</span><span class="sxs-lookup"><span data-stu-id="b9d44-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="b9d44-169">Pokud je hodnota, je nutné zadat identifikátor pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="b9d44-170">V případě řazené kolekce členů je nutné zadat vzorek řazené kolekce členů s identifikátorem pro každý prvek řazenou kolekci členů nebo identifikátor jiný název pro jednu nebo více s názvem union pole.</span><span class="sxs-lookup"><span data-stu-id="b9d44-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="b9d44-171">Příklady kódu v této části Příklady.</span><span class="sxs-lookup"><span data-stu-id="b9d44-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="b9d44-172">`option` Typ je rozlišovaná sjednocení, která má dva případy `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="b9d44-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="b9d44-173">Jeden případ (`Some`) má hodnotu, ale druhá (`None`) je právě pojmenované případu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="b9d44-174">Proto `Some` musí mít proměnnou pro hodnotu přidruženou `Some` případu, ale `None` musí být samostatně.</span><span class="sxs-lookup"><span data-stu-id="b9d44-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="b9d44-175">V následujícím kódu, proměnná `var1` je zadána hodnota, která se získávají pomocí odpovídajících k `Some` případu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="b9d44-176">V následujícím příkladu `PersonName` rozlišovaná sjednocení obsahuje směs řetězce a znaky, které představují možné formy názvy.</span><span class="sxs-lookup"><span data-stu-id="b9d44-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="b9d44-177">V případech rozlišovaná sjednocení jsou `FirstOnly`, `LastOnly`, a `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="b9d44-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="b9d44-178">Pro rozlišovaná sjednocení, které mají pojmenované pole použijete k získání hodnoty z pole s názvem symbolem rovná se (=).</span><span class="sxs-lookup"><span data-stu-id="b9d44-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="b9d44-179">Představte si třeba rozlišovaná sjednocení s deklaraci podobně jako tento.</span><span class="sxs-lookup"><span data-stu-id="b9d44-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="b9d44-180">Pole s názvem ve výrazu odpovídající vzor můžete použít následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9d44-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="b9d44-181">Použití s názvem pole je volitelné, takže v předchozím příkladu obě `Circle(r)` a `Circle(radius = r)` mají stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="b9d44-182">Pokud zadáte více polí, použijte středník (;) jako oddělovač.</span><span class="sxs-lookup"><span data-stu-id="b9d44-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="b9d44-183">Aktivní vzorky umožňují definovat složitější odpovídající vlastní vzorek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="b9d44-184">Další informace o aktivní vzorky najdete v tématu [aktivní vzorky](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="b9d44-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="b9d44-185">Případ, ve kterém je identifikátor výjimku se používá v porovnávání se v kontextu obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="b9d44-186">Informace o porovnávání se ve zpracování výjimek najdete v tématu [výjimkami: `try...with` výraz](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="b9d44-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="b9d44-187">Proměnné vzory</span><span class="sxs-lookup"><span data-stu-id="b9d44-187">Variable Patterns</span></span>
<span data-ttu-id="b9d44-188">Hodnota se namapovat na název proměnné, která je pak k dispozici pro použití ve výrazu provádění napravo od přiřadí proměnné vzor `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="b9d44-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="b9d44-189">Žádný vstup odpovídá proměnné vzor samostatně, ale proměnné vzory často se v rámci jiné vzory, proto povolení složitější struktury například řazených kolekcí členů a aby rozložit na proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="b9d44-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="b9d44-190">Následující příklad ukazuje, proměnná – vzor v rámci vzor řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="b9d44-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="b9d44-191">As – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-191">as Pattern</span></span>
<span data-ttu-id="b9d44-192">`as` Vzor je vzor, který má `as` klauzule, přidá se k němu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="b9d44-193">`as` Klauzule váže odpovídající hodnotu pro název, který lze použít ve výrazu provádění `match` výrazu, nebo v případě, kdy se tento vzor používá v `let` vazby, název je přidán jako vazbu na místní obor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="b9d44-194">Následující příklad používá `as` vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="b9d44-195">NEBO vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-195">OR Pattern</span></span>
<span data-ttu-id="b9d44-196">Vzor nebo se používá, pokud vstupní data může odpovídat více vzorů, a chcete provést v důsledku stejný kód.</span><span class="sxs-lookup"><span data-stu-id="b9d44-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="b9d44-197">Typy obou stranách vzoru nebo musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b9d44-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="b9d44-198">Následující příklad ukazuje nebo vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="b9d44-199">A vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-199">AND Pattern</span></span>
<span data-ttu-id="b9d44-200">Vzor a vyžaduje, aby vstupní shodovala dva vzory.</span><span class="sxs-lookup"><span data-stu-id="b9d44-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="b9d44-201">Typy obou stranách tohoto vzoru a musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b9d44-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="b9d44-202">V následujícím příkladu je stejná jako `detectZeroTuple` ukazuje [řazené kolekce členů vzor](https://msdn.microsoft.com/library/#tuple) části později v tomto tématu, ale zde obě `var1` a `var2` zjištěny jako hodnoty pomocí vzoru a.</span><span class="sxs-lookup"><span data-stu-id="b9d44-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="b9d44-203">Cons vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-203">Cons Pattern</span></span>
<span data-ttu-id="b9d44-204">Vzor cons se používá k rozložit na první prvek seznamu *head*a seznam obsahující zbývající elementy, *tail*.</span><span class="sxs-lookup"><span data-stu-id="b9d44-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="b9d44-205">Seznam – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-205">List Pattern</span></span>
<span data-ttu-id="b9d44-206">Vzor seznamu umožňuje seznamy musí rozložit na počet elementů.</span><span class="sxs-lookup"><span data-stu-id="b9d44-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="b9d44-207">Vzor seznamu sám může odpovídat pouze seznam konkrétní počet elementů.</span><span class="sxs-lookup"><span data-stu-id="b9d44-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="b9d44-208">Pole – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-208">Array Pattern</span></span>
<span data-ttu-id="b9d44-209">Vzor pole vypadá takto: seznam – vzor a slouží k rozložit pole konkrétní délku.</span><span class="sxs-lookup"><span data-stu-id="b9d44-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="b9d44-210">Závorky – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-210">Parenthesized Pattern</span></span>
<span data-ttu-id="b9d44-211">Závorky lze seskupovat kolem vzory k dosažení požadované asociativnost.</span><span class="sxs-lookup"><span data-stu-id="b9d44-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="b9d44-212">V následujícím příkladu kulaté závorky slouží k řízení asociativnost mezi a vzor a vzor nevýhody.</span><span class="sxs-lookup"><span data-stu-id="b9d44-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="b9d44-213">Vzor řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="b9d44-213">Tuple Pattern</span></span>
<span data-ttu-id="b9d44-214">Řazené kolekce členů vzor odpovídá vstup ve formuláři řazené kolekce členů a umožňuje řazené kolekce členů musí rozložit na jeho základní prvky pomocí proměnných pro každý pozice v řazené kolekci členů porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="b9d44-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="b9d44-215">Následující příklad ukazuje vzoru řazené kolekce členů a také používá literálu vzory, proměnné vzorce a zástupný znak – vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="b9d44-216">Záznam – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-216">Record Pattern</span></span>
<span data-ttu-id="b9d44-217">Vzor záznam se používá k rozložit záznamy k extrakci hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="b9d44-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="b9d44-218">Chcete-li všechna pole záznamu; nemá vzoru všechna pole vynechání právě neúčastnit odpovídající a nejsou rozbalené.</span><span class="sxs-lookup"><span data-stu-id="b9d44-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="b9d44-219">Zástupný znak – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-219">Wildcard Pattern</span></span>
<span data-ttu-id="b9d44-220">Zástupný znak – vzor je reprezentována podtržítko (`_`) znak a odpovídá žádný vstup, stejně jako proměnné vzor, s tím rozdílem, že vstup se zahodí místo přiřazený k proměnné.</span><span class="sxs-lookup"><span data-stu-id="b9d44-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="b9d44-221">Zástupný znak – vzor se často používá v rámci jiných vzorů jako zástupný symbol pro hodnoty, které nejsou potřebné ve výrazu napravo `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="b9d44-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="b9d44-222">Zástupný znak – vzor slouží také často na konci seznam vzorů tak, aby odpovídaly jakékoli neodpovídající vstup.</span><span class="sxs-lookup"><span data-stu-id="b9d44-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="b9d44-223">Zástupný znak – vzor je znázorněn v mnoha příklady kódu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="b9d44-224">Viz předchozí kód pro jedním z příkladů.</span><span class="sxs-lookup"><span data-stu-id="b9d44-224">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="b9d44-225">Vzorce, které mají typ poznámky</span><span class="sxs-lookup"><span data-stu-id="b9d44-225">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="b9d44-226">Vzory může mít typ poznámek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-226">Patterns can have type annotations.</span></span> <span data-ttu-id="b9d44-227">Tyto chovají jako dalších typů poznámek a Průvodce odvození jako dalších typ poznámek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="b9d44-228">Kolem typ poznámky v vzory jsou vyžadovány závorky.</span><span class="sxs-lookup"><span data-stu-id="b9d44-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="b9d44-229">Následující kód ukazuje vzor, který má anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="b9d44-230">Typ testu vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-230">Type Test Pattern</span></span>
<span data-ttu-id="b9d44-231">Typ testu vzor slouží k přiřazování vstup podle typu.</span><span class="sxs-lookup"><span data-stu-id="b9d44-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="b9d44-232">Pokud vstupní typ je shoda pro (nebo odvozené typ) s typem zadaným ve vzoru shody úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b9d44-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="b9d44-233">Následující příklad ukazuje typ testovací vzorek.</span><span class="sxs-lookup"><span data-stu-id="b9d44-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="b9d44-234">Null – vzor</span><span class="sxs-lookup"><span data-stu-id="b9d44-234">Null Pattern</span></span>
<span data-ttu-id="b9d44-235">Null vzor odpovídá hodnotu null, která se může zobrazit při práci s typy, které umožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b9d44-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="b9d44-236">Null vzorů se často používají při interoperabilitě se službou kódu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9d44-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="b9d44-237">Návratová hodnota rozhraní API .NET může být například vstup `match` výraz.</span><span class="sxs-lookup"><span data-stu-id="b9d44-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="b9d44-238">Můžete řídit tok programu na základě, zda je návratovou hodnotu null a také na dalších vlastností vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9d44-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="b9d44-239">Null vzor můžete zabránit s ostatními vašeho programu při šíření hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="b9d44-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="b9d44-240">Následující příklad používá vzoru hodnotu null a proměnná – vzor.</span><span class="sxs-lookup"><span data-stu-id="b9d44-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="b9d44-241">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d44-241">See Also</span></span>
[<span data-ttu-id="b9d44-242">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="b9d44-242">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="b9d44-243">Aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="b9d44-243">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="b9d44-244">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b9d44-244">F# Language Reference</span></span>](index.md)
