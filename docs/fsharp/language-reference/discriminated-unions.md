---
title: Rozlišovaná sjednocení
description: Naučte se používat F# rozlišené sjednocení.
ms.date: 05/16/2016
ms.openlocfilehash: 940bc51f49e283c31846dd2047b749769b919838
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630360"
---
# <a name="discriminated-unions"></a><span data-ttu-id="7d7d9-103">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="7d7d9-103">Discriminated Unions</span></span>

<span data-ttu-id="7d7d9-104">Rozlišené sjednocení poskytují podporu pro hodnoty, které mohou být jedním z mnoha pojmenovaných případů, případně každý s různými hodnotami a typy.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="7d7d9-105">Rozlišené sjednocení jsou užitečné pro heterogenní data; data, která mohou mít zvláštní případy, včetně platných a chybových případů; data, která se liší v typu z jedné instance do druhé; a jako alternativu pro malé hierarchie objektů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="7d7d9-106">Kromě toho rekurzivní rozlišené sjednocení slouží k reprezentaci stromových struktur dat.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d7d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d7d9-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="7d7d9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d7d9-108">Remarks</span></span>

<span data-ttu-id="7d7d9-109">Rozlišené sjednocení jsou podobné typům sjednocení v jiných jazycích, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="7d7d9-110">Stejně jako u typu sjednocení C++ nebo v typu variant v Visual Basic, nejsou data uložená v hodnotě pevná; může to být jedna z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="7d7d9-111">Na rozdíl od sjednocení v těchto jiných jazycích ale každá z možných možností má za následek *identifikátor případu*.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="7d7d9-112">Identifikátory případů jsou názvy různých možných typů hodnot, které mohou být objekty tohoto typu. hodnoty jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="7d7d9-113">Pokud hodnoty nejsou k dispozici, je případ ekvivalentní s případem výčtu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="7d7d9-114">Pokud jsou zadány hodnoty, každá hodnota může být buď jediná hodnota zadaného typu, nebo řazená kolekce členů, která agreguje více polí stejného nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="7d7d9-115">Individuálnímu poli můžete zadat název, ale název je nepovinný, i když se pojmenují další pole ve stejném případě.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="7d7d9-116">Přístupnost pro rozlišené sjednocení je ve `public`výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="7d7d9-117">Zvažte například následující deklaraci typu tvaru.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="7d7d9-118">Předchozí kód deklaruje nerozlišený obrazec sjednocení, který může mít hodnoty ze tří případů: Obdélník, Circle a Prism.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="7d7d9-119">Každý případ má jinou sadu polí.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-119">Each case has a different set of fields.</span></span> <span data-ttu-id="7d7d9-120">V případě obdélníku jsou k dispozici dvě pojmenovaná pole, obě typu `float`, jejichž názvy mají šířku a délku.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="7d7d9-121">KRUHOVÁ velikost má pouze jedno pojmenované pole, poloměr.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="7d7d9-122">PRISM případ obsahuje tři pole, z nichž dva mají (šířka a výška) pojmenovaná pole.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="7d7d9-123">Nepojmenovaná pole se nazývají anonymní pole.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="7d7d9-124">Sestavíte objekty zadáním hodnot pro pojmenované a anonymní pole podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="7d7d9-125">Tento kód ukazuje, že můžete buď použít pojmenovaná pole v inicializaci, nebo můžete spoléhat na řazení polí v deklaraci a zadat pouze hodnoty pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="7d7d9-126">Volání `rect` konstruktoru v předchozím kódu používá pojmenovaná pole, ale `circ` volání konstruktoru používá řazení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="7d7d9-127">Můžete kombinovat uspořádaná pole a pojmenovaná pole, jako v konstrukci `prism`.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="7d7d9-128">Typ je jednoduché rozlišené sjednocení v F# základní knihovně. `option`</span><span class="sxs-lookup"><span data-stu-id="7d7d9-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="7d7d9-129">`option` Typ je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="7d7d9-130">Předchozí kód určuje, že typ `Option` je rozlišené sjednocení, které má dva `Some` případy a `None`.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="7d7d9-131">Případ má přidruženou hodnotu, která se skládá z jednoho anonymního pole, jehož typ je reprezentován parametrem `'a`typu. `Some`</span><span class="sxs-lookup"><span data-stu-id="7d7d9-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="7d7d9-132">K `None` případu není přidružena žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-132">The `None` case has no associated value.</span></span> <span data-ttu-id="7d7d9-133">`option` Proto typ určuje obecný typ, který má buď hodnotu nějakého typu, nebo žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="7d7d9-134">Typ `Option` má také alias typu malý malý typ, `option`který se častěji používá.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="7d7d9-135">Identifikátory případu lze použít jako konstruktory pro rozlišený typ sjednocení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="7d7d9-136">Například následující kód se používá k vytvoření hodnot `option` typu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="7d7d9-137">Identifikátory Case se používají také ve výrazech pro porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="7d7d9-138">Ve výrazu pro porovnávání vzorů jsou identifikátory k dispozici pro hodnoty přidružené k jednotlivým případům.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="7d7d9-139">Například v následujícím kódu `x` je identifikátor přiřazený k hodnotě, která je spojena `Some` s případem `option` typu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="7d7d9-140">Ve výrazech porovnávání se vzorci můžete použít pojmenovaná pole k určení shod rozlišených sjednocení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="7d7d9-141">Pro typ obrazce, který byl dřív deklarovaný, můžete použít pojmenovaná pole, jak ukazuje následující kód k extrakci hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="7d7d9-142">V normálním případě lze identifikátory případu použít bez kvalifikovaného názvu sjednocení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="7d7d9-143">Pokud chcete, aby byl název vždy kvalifikován s názvem sjednocení, můžete použít atribut [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) na definici typu sjednocení.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="7d7d9-144">Rozbalení rozlišených sjednocení</span><span class="sxs-lookup"><span data-stu-id="7d7d9-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="7d7d9-145">V F# rozlišených sjednoceních se často používají modelování domén pro zabalení jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="7d7d9-146">Základní hodnotu lze snadno extrahovat také pomocí porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="7d7d9-147">Výraz shody nemusíte používat pro jeden případ:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="7d7d9-148">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="7d7d9-149">Porovnávání vzorů je také povoleno přímo v parametrech funkcí, takže můžete rozbalit jeden případ:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="7d7d9-150">Struktury rozlišených sjednocení</span><span class="sxs-lookup"><span data-stu-id="7d7d9-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="7d7d9-151">Můžete také znázornit rozlišené sjednocení jako struktury.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="7d7d9-152">To se provádí s `[<Struct>]` atributem.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="7d7d9-153">Vzhledem k tomu, že se jedná o typy hodnot a typy odkazů, existují další požadavky v porovnání s referenčními sjednoceními:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="7d7d9-154">Jsou zkopírovány jako typy hodnot a mají sémantiku typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="7d7d9-155">Nemůžete použít definici rekurzivního typu s neomezeným sjednocením struktury s více případy.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="7d7d9-156">Je nutné zadat jedinečné názvy případů pro rozlišené sjednocení ve více případech.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="7d7d9-157">Použití rozlišených sjednocení místo hierarchií objektů</span><span class="sxs-lookup"><span data-stu-id="7d7d9-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="7d7d9-158">Můžete často použít rozlišené sjednocení jako jednodušší alternativu k malé hierarchii objektů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="7d7d9-159">Například následující rozlišené sjednocení lze použít místo `Shape` základní třídy, která má odvozené typy pro kruh, čtverce a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="7d7d9-160">Místo virtuální metody pro výpočet oblasti nebo hraničního prostředí, stejně jako při použití v objektově orientované implementaci, můžete použít porovnávání vzorů pro větvení s vhodnými vzorci k výpočtu těchto množství.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="7d7d9-161">V následujícím příkladu jsou pro výpočet oblasti použity různé vzorce v závislosti na tvaru.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="7d7d9-162">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="7d7d9-163">Použití rozlišených sjednocení pro struktury dat stromu</span><span class="sxs-lookup"><span data-stu-id="7d7d9-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="7d7d9-164">Rozlišené sjednocení mohou být rekurzivní, což znamená, že samotné sjednocení lze zahrnout do typu jednoho nebo více případů.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="7d7d9-165">Rekurzivní rozlišené sjednocení lze použít k vytvoření stromové struktury, které se používají k modelování výrazů v programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="7d7d9-166">V následujícím kódu se rekurzivní rozlišené sjednocení používá k vytvoření binární struktury dat stromu.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="7d7d9-167">Sjednocení se skládá ze dvou případů `Node`, který je uzel s celočíselnou hodnotou, levým a pravým podstromem `Tip`a, který ukončí strom.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="7d7d9-168">V předchozím kódu `resultSumTree` má hodnotu 10.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="7d7d9-169">Následující ilustrace znázorňuje stromovou strukturu pro `myTree`.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagram, který zobrazuje stromovou strukturu pro myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="7d7d9-171">Rozlišené sjednocení dobře fungují, pokud jsou uzly ve stromové struktuře heterogenní.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="7d7d9-172">V následujícím kódu typ `Expression` představuje abstraktní strom syntaxe výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="7d7d9-173">Některé případy sjednocení nejsou rekurzivní a představují buď čísla (`Number`) nebo proměnné (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="7d7d9-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="7d7d9-174">Jiné případy jsou rekurzivní a představují operace (`Add` a `Multiply`), kde operandy jsou také výrazy.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="7d7d9-175">`Evaluate` Funkce používá výraz shody k rekurzivnímu zpracování stromu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="7d7d9-176">Při spuštění tohoto kódu `result` je hodnota 5.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="7d7d9-177">Členové</span><span class="sxs-lookup"><span data-stu-id="7d7d9-177">Members</span></span>

<span data-ttu-id="7d7d9-178">Je možné definovat členy v rozlišených sjednoceních.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="7d7d9-179">Následující příklad ukazuje, jak definovat vlastnost a implementovat rozhraní:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-179">The following example shows how to define a property and implement an interface:</span></span>

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a><span data-ttu-id="7d7d9-180">Společné atributy</span><span class="sxs-lookup"><span data-stu-id="7d7d9-180">Common attributes</span></span>

<span data-ttu-id="7d7d9-181">Následující atributy se běžně zobrazují v rozlišených sjednoceních:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-181">The following attributes are commonly seen in discriminated unions:</span></span>

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="7d7d9-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d7d9-182">See also</span></span>

- [<span data-ttu-id="7d7d9-183">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="7d7d9-183">F# Language Reference</span></span>](index.md)
