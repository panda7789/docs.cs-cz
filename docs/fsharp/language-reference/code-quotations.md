---
title: "Uvozovky kódu (F#)"
description: "Další informace o F # uvozovky kódu, funkce jazyka, která umožňuje generovat a pracovat s výrazy kódu F # prostřednictvím kódu programu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4559e659-2b04-48bd-8a0b-8527920eec95
ms.openlocfilehash: f7a08013bc6487b570a62576bb01ca2dd65ce8b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="code-quotations"></a><span data-ttu-id="b0ec6-104">Uvozovky kódu</span><span class="sxs-lookup"><span data-stu-id="b0ec6-104">Code Quotations</span></span>

> [!NOTE]
<span data-ttu-id="b0ec6-105">Rozhraní API použití odkazu přejdete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-105">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="b0ec6-106">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="b0ec6-107">Toto téma popisuje *code uvozovky*, funkce jazyka, která umožňuje generovat a pracovat s výrazy kódu F # prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-107">This topic describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="b0ec6-108">Tato funkce umožňuje vygenerovat abstraktního syntaktického stromové struktury, která představuje F # – kód.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-108">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="b0ec6-109">Abstraktního syntaktického stromu můžete pak provázán a zpracovat podle potřeb vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-109">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="b0ec6-110">Například můžete stromu ke generování kódu F # nebo generování kódu v některých dalších jazyků.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-110">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>


## <a name="quoted-expressions"></a><span data-ttu-id="b0ec6-111">Uvozovkách výrazy</span><span class="sxs-lookup"><span data-stu-id="b0ec6-111">Quoted Expressions</span></span>
<span data-ttu-id="b0ec6-112">A *výrazu v uvozovkách* je výraz F # ve vašem kódu, která je oddělená tak, že není kompilována jako součást vašeho programu, ale místo toho se zkompiluje do objekt, který představuje výraz F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-112">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="b0ec6-113">Můžete označit výraz uvozovkách v jednom ze dvou způsobů: buď s informací o typu nebo bez informací o typu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-113">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="b0ec6-114">Pokud chcete zahrnout informace o typu, můžete použít symboly `<@` a `@>` pro vymezení je výraz v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-114">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="b0ec6-115">Pokud nepotřebujete informace o typu, můžete použít symboly `<@@` a `@@>`.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-115">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="b0ec6-116">Následující kód ukazuje typové a bez typu uvozovky.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-116">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="b0ec6-117">Procházení strom velké výrazu je vyšší, pokud nebudou obsahovat informace o typu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-117">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="b0ec6-118">Výsledný typ výraz s typem symboly v uvozovkách je `Expr<'T>`, kde parametr typu má typ výrazu určeného algoritmus odvození typu kompilátoru F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-118">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="b0ec6-119">Když použijete uvozovky kódu bez informací o typu, je typ výrazu uvozovkách neobecný typ [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span><span class="sxs-lookup"><span data-stu-id="b0ec6-119">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span></span> <span data-ttu-id="b0ec6-120">Můžete volat [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) vlastnost u zadaného objektu `Expr` třída získat netypové `Expr` objektu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-120">You can call the [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="b0ec6-121">Existuje mnoho různých statických metod, které vám umožní generovat F # výraz objekty prostřednictvím kódu programu v `Expr` třída bez použití v uvozovkách výrazy.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-121">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="b0ec6-122">Všimněte si, že kód uvozovek musí obsahovat úplný výraz.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-122">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="b0ec6-123">Pro `let` vazby, například musíte definice vázané název a další výraz, který používá vazby.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-123">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="b0ec6-124">V podrobná syntaxe, jedná se o výraz, který následuje `in` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-124">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="b0ec6-125">Na nejvyšší úrovni v modulu jedná se jenom další výraz v modulu, ale v uvozovky, se výslovně vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-125">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="b0ec6-126">Následující výraz proto není platný.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-126">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="b0ec6-127">Ale těchto výrazů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-127">But the following expressions are valid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="b0ec6-128">Chcete-li použít uvozovky kódu, je nutné přidat deklarace importu (pomocí `open` – klíčové slovo), otevře se [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-128">To use code quotations, you must add an import declaration (by using the `open` keyword) that opens the [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.</span></span>

<span data-ttu-id="b0ec6-129">F # PowerPack poskytuje podporu pro vyhodnocení a provádění výrazu objekty F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-129">The F# PowerPack provides support for evaluating and executing F# expression objects.</span></span>


## <a name="expr-type"></a><span data-ttu-id="b0ec6-130">Výraz typu</span><span class="sxs-lookup"><span data-stu-id="b0ec6-130">Expr Type</span></span>
<span data-ttu-id="b0ec6-131">Instance `Expr` typ představuje výraz F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-131">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="b0ec6-132">Obecná i neobecnou `Expr` typy jsou popsané v dokumentaci knihovny F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-132">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="b0ec6-133">Další informace najdete v tématu [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) a [quotations.Expr – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="b0ec6-133">For more information, see [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) and [Quotations.Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span></span>


## <a name="splicing-operators"></a><span data-ttu-id="b0ec6-134">Splétání operátory</span><span class="sxs-lookup"><span data-stu-id="b0ec6-134">Splicing Operators</span></span>
<span data-ttu-id="b0ec6-135">Splétání umožňuje zkombinovat uvozovky literálu kódu s výrazy, které jste vytvořili prostřednictvím kódu programu, nebo z jiného uvozovky kódu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-135">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="b0ec6-136">`%` a `%%` operátory umožňují do uvozovek kód přidejte objekt výraz F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-136">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="b0ec6-137">Můžete použít `%` operátor vložení objekt typu výrazu do typu uvozovek; můžete použít `%%` operátor vložení objektu bez typu výraz do bez typu nabídky.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-137">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="b0ec6-138">Unární operátory předpony jsou obě operátory.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-138">Both operators are unary prefix operators.</span></span> <span data-ttu-id="b0ec6-139">Proto pokud `expr` je netypové výrazu typu `Expr`, následující kód je platný.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-139">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="b0ec6-140">A pokud `expr` je typu uvozovek typu `Expr<int>`, následující kód je platný.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-140">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="b0ec6-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0ec6-141">Example</span></span>

### <a name="description"></a><span data-ttu-id="b0ec6-142">Popis</span><span class="sxs-lookup"><span data-stu-id="b0ec6-142">Description</span></span>
<span data-ttu-id="b0ec6-143">Následující příklad ukazuje použití uvozovky kódu F # – kód vložena objekt výraz a pak postupně kód F #, který představuje výraz.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-143">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="b0ec6-144">Funkce `println` je definována obsahující rekurzivní funkce `print` který zobrazí objekt výraz F # (typu `Expr`) ve formátu popisný.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-144">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="b0ec6-145">Existuje několik aktivní vzorky v [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) a [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) moduly, které lze použít k analýze výraz objekty.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-145">There are several active patterns in the [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) and [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="b0ec6-146">Tento příklad nezahrnuje všechny možné vzorů, které se může objevit ve výrazu F #.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-146">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="b0ec6-147">Všechny nerozpoznané vzor aktivuje shoda se zástupnými znaky vzorem (`_`) a je vykreslen pomocí `ToString` metoda, která, na `Expr` typ, umožňuje znáte aktivní vzor pro přidání do vaší výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-147">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>


### <a name="code"></a><span data-ttu-id="b0ec6-148">Kód</span><span class="sxs-lookup"><span data-stu-id="b0ec6-148">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a><span data-ttu-id="b0ec6-149">Výstup</span><span class="sxs-lookup"><span data-stu-id="b0ec6-149">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="b0ec6-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0ec6-150">Example</span></span>

### <a name="description"></a><span data-ttu-id="b0ec6-151">Popis</span><span class="sxs-lookup"><span data-stu-id="b0ec6-151">Description</span></span>
<span data-ttu-id="b0ec6-152">Můžete také tři aktivní vzorky v [exprshape – modul](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) procházení stromů výrazů s méně aktivní vzorky.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-152">You can also use the three active patterns in the [ExprShape module](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="b0ec6-153">Tyto vzory aktivní může být užitečné, když chcete procházení stromu, ale není nutné všechny informace ve většině uzlů.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-153">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="b0ec6-154">Použijete-li tyto vzory, jakýkoli výraz F # odpovídá jednomu z následujících tří vzorů: `ShapeVar` li výraz proměnnou, `ShapeLambda` li výraz výraz lambda nebo `ShapeCombination` Pokud je výraz jiný.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-154">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="b0ec6-155">Pokud jste pomocí aktivní vzorky jako v předchozím příkladu kódu procházejí strom výrazu, budete muset použít mnoho další vzory pro zpracování všech možných typů F # výraz a váš kód bude složitější.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-155">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="b0ec6-156">Další informace najdete v tématu [ExprShape.ShapeVar &#124; Shapelambda – &#124; Shapecombination – aktivní vzor](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="b0ec6-156">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span></span>

<span data-ttu-id="b0ec6-157">Následující příklad kódu můžete použít jako základ pro složitější traversals.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-157">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="b0ec6-158">V tomto kódu strom výrazu se vytvoří pro výraz, který zahrnuje volání funkce `add`.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-158">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="b0ec6-159">[Specificcall –](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) – aktivní vzor slouží ke zjištění všech volání `add` ve stromové struktuře výraz.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-159">The [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="b0ec6-160">Tato – aktivní vzor přiřadí argumenty volání `exprList` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-160">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="b0ec6-161">V takovém případě jsou uvedeny pouze dvě, tak, aby tyto jsou vyžádat a funkce se volá rekurzivní na argumenty.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-161">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="b0ec6-162">Výsledky jsou vloženy do uvozovek kód, který představuje volání `mul` pomocí operátoru uživatele programu splice (`%%`).</span><span class="sxs-lookup"><span data-stu-id="b0ec6-162">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="b0ec6-163">`println` Funkce z předchozího příkladu se používá k zobrazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-163">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="b0ec6-164">Kód v jiných – aktivní vzor větví právě regeneruje stejném stromu pro výraz, tak, aby pouze změnu v hodnotě výsledný výraz změnu z `add` k `mul`.</span><span class="sxs-lookup"><span data-stu-id="b0ec6-164">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>


### <a name="code"></a><span data-ttu-id="b0ec6-165">Kód</span><span class="sxs-lookup"><span data-stu-id="b0ec6-165">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a><span data-ttu-id="b0ec6-166">Výstup</span><span class="sxs-lookup"><span data-stu-id="b0ec6-166">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="b0ec6-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0ec6-167">See Also</span></span>
[<span data-ttu-id="b0ec6-168">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="b0ec6-168">F# Language Reference</span></span>](index.md)

