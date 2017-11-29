---
title: "Rozlišovaná sjednocení (F#)"
description: "Další informace o použití F # rozlišované sjednocení."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e2a011-c785-48c8-859f-79df7f3a0e29
ms.openlocfilehash: a374f521bcde7506bb3a9eebb627eaffcd8b94a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="discriminated-unions"></a><span data-ttu-id="2045a-104">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="2045a-104">Discriminated Unions</span></span>

<span data-ttu-id="2045a-105">Rozlišovaná sjednocení poskytuje podporu pro hodnoty, které může být jedna z číslo pojmenované případů, které by mohly mít každý s různými hodnotami a typy.</span><span class="sxs-lookup"><span data-stu-id="2045a-105">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="2045a-106">Rozlišovaná sjednocení jsou užitečné pro heterogenní data; data, která může mít speciální případech, včetně platný a chybových případech; data, která se liší v typu z jedné instance a jako alternativu pro malé objekt hierarchie.</span><span class="sxs-lookup"><span data-stu-id="2045a-106">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="2045a-107">Kromě toho rekurzivní rozlišované sjednocení se používají k vyjádření stromu datové struktury.</span><span class="sxs-lookup"><span data-stu-id="2045a-107">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="2045a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2045a-108">Syntax</span></span>

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a><span data-ttu-id="2045a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2045a-109">Remarks</span></span>
<span data-ttu-id="2045a-110">Rozlišovaná sjednocení jsou podobné typy union v jiných jazycích, ale jsou rozdíly.</span><span class="sxs-lookup"><span data-stu-id="2045a-110">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="2045a-111">Jako s typu union v jazyce C++ nebo typu variant v jazyce Visual Basic odstraněny data uložená v hodnotě; může být jeden z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="2045a-111">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="2045a-112">Na rozdíl od sjednocení v těchto dalších jazycích, ale každá z možných možností je uveden *případu identifikátor*.</span><span class="sxs-lookup"><span data-stu-id="2045a-112">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="2045a-113">Case identifikátory jsou názvy pro různé druhy hodnoty, které by mohly být objekty tohoto typu; hodnoty jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="2045a-113">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="2045a-114">Pokud nejsou zadány hodnoty, tak je ekvivalentní – případ výčtu.</span><span class="sxs-lookup"><span data-stu-id="2045a-114">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="2045a-115">Pokud jsou v něm hodnoty, každá hodnota může být buď jednu hodnotu na zadaný typ nebo řazené kolekce členů, která agreguje více polí stejné nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="2045a-115">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="2045a-116">Od F # 3.1 je jednotlivá pole zadejte název, ale název je volitelný, i když mají další pole v případě, že stejný název.</span><span class="sxs-lookup"><span data-stu-id="2045a-116">As of F# 3.1, you can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="2045a-117">Zvažte například následující deklaraci typu tvaru.</span><span class="sxs-lookup"><span data-stu-id="2045a-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="2045a-118">Předchozí kód deklaruje rozlišovaná sjednocení tvar, který může mít hodnoty všech třech případech: obdélníku, kruh a modulu Prism.</span><span class="sxs-lookup"><span data-stu-id="2045a-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="2045a-119">Každý případ má jinou sadu polí.</span><span class="sxs-lookup"><span data-stu-id="2045a-119">Each case has a different set of fields.</span></span> <span data-ttu-id="2045a-120">Pole rámeček případ má dva s názvem, obě typu `float`, které mají názvy šířky a výšky.</span><span class="sxs-lookup"><span data-stu-id="2045a-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="2045a-121">Kruh případě má pouze jedno pole s názvem, protokolu radius.</span><span class="sxs-lookup"><span data-stu-id="2045a-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="2045a-122">Tento případ modulu Prism má tři pole dva které (šířky a výšky) jsou pojmenované pole.</span><span class="sxs-lookup"><span data-stu-id="2045a-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="2045a-123">Nepojmenované pole jsou označovány jako anonymní pole.</span><span class="sxs-lookup"><span data-stu-id="2045a-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="2045a-124">Můžete vytvořit objekty tím, že poskytuje hodnoty pro pole pojmenované a anonymní podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="2045a-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="2045a-125">Tento kód ukazuje, že můžete použít buď pole s názvem při inicializaci, nebo můžete spoléhat na pořadí polí v deklaraci a stačí zadat hodnoty pro každé pole, pak.</span><span class="sxs-lookup"><span data-stu-id="2045a-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="2045a-126">Volání konstruktoru pro `rect` v předchozí kód používá pole s názvem, ale volání konstruktoru pro `circ` používá řazení.</span><span class="sxs-lookup"><span data-stu-id="2045a-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="2045a-127">Můžete kombinovat uspořádaného pole a s názvem pole, jako vytváření `prism`.</span><span class="sxs-lookup"><span data-stu-id="2045a-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="2045a-128">`option` Typ je jednoduchý rozlišovaná sjednocení v základní knihovny F #.</span><span class="sxs-lookup"><span data-stu-id="2045a-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="2045a-129">`option` Typ je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="2045a-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="2045a-130">Předchozí kód určuje, že typ `Option` je rozlišovaná sjednocení, která má dva případy `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="2045a-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="2045a-131">`Some` Případ má přidružené hodnotu, která se skládá z jednoho anonymní pole, jejichž typ je reprezentována parametr typu `'a`.</span><span class="sxs-lookup"><span data-stu-id="2045a-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="2045a-132">`None` Případ nemá žádné přidružené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2045a-132">The `None` case has no associated value.</span></span> <span data-ttu-id="2045a-133">Proto `option` typ určuje obecného typu, který má buď hodnotu nějaký typ nebo žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="2045a-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="2045a-134">Typ `Option` má také alias malá typ `option`, který je informace, které se běžně používá.</span><span class="sxs-lookup"><span data-stu-id="2045a-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="2045a-135">Case identifikátory slouží jako konstruktory rozlišovaná sjednocení typu.</span><span class="sxs-lookup"><span data-stu-id="2045a-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="2045a-136">Například následující kód slouží k vytvoření hodnoty `option` typu.</span><span class="sxs-lookup"><span data-stu-id="2045a-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="2045a-137">Case identifikátory používají taky ve výrazech porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="2045a-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="2045a-138">Ve tvaru odpovídající výrazu jsou uvedené identifikátory pro hodnoty přidružené k jednotlivých případech.</span><span class="sxs-lookup"><span data-stu-id="2045a-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="2045a-139">Například v následujícím kódu `x` je identifikátor zadána hodnota, která je přidružená `Some` případu z `option` typu.</span><span class="sxs-lookup"><span data-stu-id="2045a-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="2045a-140">Ve vzoru odpovídající výrazy můžete použít pole s názvem k určení rozlišovaná sjednocení odpovídá.</span><span class="sxs-lookup"><span data-stu-id="2045a-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="2045a-141">Pro typ tvar, který byl předtím deklarován můžete použít pole s názvem, jak ukazuje následující kód k extrakci hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="2045a-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="2045a-142">Za normálních okolností případu identifikátory lze použít bez jejich kvalifikující s názvem sjednocení.</span><span class="sxs-lookup"><span data-stu-id="2045a-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="2045a-143">Pokud chcete název, který má být vždy kvalifikovaný pomocí názvu sjednocení, můžete použít [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut definici typu union.</span><span class="sxs-lookup"><span data-stu-id="2045a-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="2045a-144">Rozbalení rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="2045a-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="2045a-145">V Rozlišované sjednocení F # se často používají v doméně modelování pro zabalení jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="2045a-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="2045a-146">Je snadno rozbalte základní hodnotu prostřednictvím také porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="2045a-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="2045a-147">Nemusíte používat výrazu shody pro jeden případ:</span><span class="sxs-lookup"><span data-stu-id="2045a-147">You don't need to use a match expression for a single case:</span></span>
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="2045a-148">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="2045a-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="2045a-149">Rozlišované sjednocení – struktura</span><span class="sxs-lookup"><span data-stu-id="2045a-149">Struct Discriminated Unions</span></span>

<span data-ttu-id="2045a-150">Od verze 4.1 F #, může také představovat Rozlišované sjednocení jako struktury.</span><span class="sxs-lookup"><span data-stu-id="2045a-150">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="2045a-151">To lze provést pomocí `[<Struct>]` atribut.</span><span class="sxs-lookup"><span data-stu-id="2045a-151">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of string
    | Case2 of int
    | Case3 of double
```

<span data-ttu-id="2045a-152">Protože jsou typy hodnot a není odkazové typy, jsou doplňující aspekty ve srovnání s odkazem na rozlišované sjednocení:</span><span class="sxs-lookup"><span data-stu-id="2045a-152">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="2045a-153">Že se zkopírují jako typy hodnot a mít Sémantika typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2045a-153">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="2045a-154">Rekurzivní definici typu nelze použít s multicase struktury Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="2045a-154">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="2045a-155">Musíte zadat jedinečné názvy případu pro multicase struktury Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="2045a-155">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="2045a-156">Použití rozlišovaná sjednocení namísto objektu hierarchie</span><span class="sxs-lookup"><span data-stu-id="2045a-156">Using Discriminated Unions Instead of Object Hierarchies</span></span>
<span data-ttu-id="2045a-157">Rozlišovaná sjednocení můžete často použít jako jednodušší alternativa k hierarchie malé objektů.</span><span class="sxs-lookup"><span data-stu-id="2045a-157">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="2045a-158">Například následující rozlišovaná sjednocení může místo `Shape` základní třídu, která má odvozených typů pro kruh, čtvercovou, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2045a-158">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="2045a-159">Virtuální metody k výpočtu oblasti nebo hraniční, jako je by použijte pro implementaci objektově orientované, můžete použít k výpočtu tyto počty porovnávání vzorů pro firemní pobočky na příslušné vzorce.</span><span class="sxs-lookup"><span data-stu-id="2045a-159">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="2045a-160">V následujícím příkladu se používají různé vzorce k výpočtu oblasti, v závislosti na tvaru.</span><span class="sxs-lookup"><span data-stu-id="2045a-160">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="2045a-161">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="2045a-161">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="2045a-162">Použití rozlišovaná sjednocení pro strom datové struktury</span><span class="sxs-lookup"><span data-stu-id="2045a-162">Using Discriminated Unions for Tree Data Structures</span></span>
<span data-ttu-id="2045a-163">Rozlišovaná sjednocení může být rekurzivní, což znamená, že sjednocení samotné můžou být součástí typ jeden nebo více případů.</span><span class="sxs-lookup"><span data-stu-id="2045a-163">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="2045a-164">Rekurzivní rozlišovaná sjednocení lze použít k vytvoření stromové struktury, které se používají k modelu výrazy v programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="2045a-164">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="2045a-165">V následujícím kódu rekurzivního rozlišované sjednocení se používá k vytvoření datová struktura binárního stromu.</span><span class="sxs-lookup"><span data-stu-id="2045a-165">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="2045a-166">Sjednocení se skládá ze dvou případech `Node`, který je uzlem s celočíselnou hodnotu a levé a pravé podstromy a `Tip`, který ukončí stromu.</span><span class="sxs-lookup"><span data-stu-id="2045a-166">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="2045a-167">V předchozí kód `resultSumTree` má hodnotu 10.</span><span class="sxs-lookup"><span data-stu-id="2045a-167">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="2045a-168">Následující obrázek znázorňuje stromové struktury pro `myTree`.</span><span class="sxs-lookup"><span data-stu-id="2045a-168">The following illustration shows the tree structure for `myTree`.</span></span>

![Stromovou strukturu pro myTree](../media/TreeStructureDiagram.png)

<span data-ttu-id="2045a-170">Rozlišovaná sjednocení vhodný, pokud jsou heterogenní uzly ve stromu.</span><span class="sxs-lookup"><span data-stu-id="2045a-170">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="2045a-171">V následujícím kódu, typ `Expression` představuje abstraktního syntaktického stromu výrazu v jednoduchý programovací jazyk, který podporuje přidání a násobení čísel a proměnné.</span><span class="sxs-lookup"><span data-stu-id="2045a-171">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="2045a-172">Některé union případů nejsou rekurzivní a představují buď čísla (`Number`) nebo proměnné (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="2045a-172">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="2045a-173">Ostatních případech jsou rekurzivní a představují operací (`Add` a `Multiply`), kde jsou operandy také výrazy.</span><span class="sxs-lookup"><span data-stu-id="2045a-173">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="2045a-174">`Evaluate` Funkce používá výrazu shody rekurzivně procesu stromu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="2045a-174">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="2045a-175">Při spuštění tohoto kódu, hodnota `result` je 5.</span><span class="sxs-lookup"><span data-stu-id="2045a-175">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="2045a-176">Běžné atributy</span><span class="sxs-lookup"><span data-stu-id="2045a-176">Common Attributes</span></span>

<span data-ttu-id="2045a-177">Následující atributy jsou běžně zobrazená v rozlišovaná sjednocení:</span><span class="sxs-lookup"><span data-stu-id="2045a-177">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* <span data-ttu-id="2045a-178">`[Struct]`(F # 4.1 a vyšší)</span><span class="sxs-lookup"><span data-stu-id="2045a-178">`[Struct]` (F# 4.1 and higher)</span></span>

## <a name="see-also"></a><span data-ttu-id="2045a-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="2045a-179">See Also</span></span>
[<span data-ttu-id="2045a-180">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="2045a-180">F# Language Reference</span></span>](index.md)
