---
title: Rozlišovaná sjednocení
description: Naučte se používat f# discriminated sjednocení.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400216"
---
# <a name="discriminated-unions"></a><span data-ttu-id="a8773-103">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="a8773-103">Discriminated Unions</span></span>

<span data-ttu-id="a8773-104">Discriminated sjednocení poskytují podporu pro hodnoty, které mohou být jedním z několika pojmenovaných případů, případně každý s různými hodnotami a typy.</span><span class="sxs-lookup"><span data-stu-id="a8773-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="a8773-105">Diskriminované sjednocení jsou užitečné pro heterogenní data; údaje, které mohou mít zvláštní případy, včetně platných a chybových případů; data, která se v jednotlivých instanci liší typem; a jako alternativu pro malé hierarchie objektů.</span><span class="sxs-lookup"><span data-stu-id="a8773-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="a8773-106">Kromě toho rekurzivní discriminated sjednocení se používají k reprezentaci stromové datové struktury.</span><span class="sxs-lookup"><span data-stu-id="a8773-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8773-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8773-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="a8773-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8773-108">Remarks</span></span>

<span data-ttu-id="a8773-109">Discriminated sjednocení jsou podobné typy sjednocení v jiných jazycích, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="a8773-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="a8773-110">Stejně jako u typu sjednocení v jazyce C++ nebo typu varianty v jazyce Visual Basic nejsou data uložená v hodnotě pevná; může to být jedna z několika odlišných možností.</span><span class="sxs-lookup"><span data-stu-id="a8773-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="a8773-111">Na rozdíl od sjednocení v těchto jiných jazycích je však každé z možných možností přidělen *identifikátor případu*.</span><span class="sxs-lookup"><span data-stu-id="a8773-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="a8773-112">Identifikátory případu jsou názvy pro různé možné typy hodnot, které by mohly být objekty tohoto typu; hodnoty jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a8773-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="a8773-113">Pokud hodnoty nejsou k dispozici, případ je ekvivalentní případu výčtu.</span><span class="sxs-lookup"><span data-stu-id="a8773-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="a8773-114">Pokud jsou k dispozici hodnoty, každá hodnota může být buď jednu hodnotu zadaného typu nebo řazené kolekce členů, která agreguje více polí stejnénebo různé typy.</span><span class="sxs-lookup"><span data-stu-id="a8773-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="a8773-115">Jednotlivé pole můžete pojmenovat, ale název je volitelný, i když jsou pojmenována jiná pole ve stejném případě.</span><span class="sxs-lookup"><span data-stu-id="a8773-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="a8773-116">Usnadnění pro discriminated odbory `public`výchozí nastavení .</span><span class="sxs-lookup"><span data-stu-id="a8773-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="a8773-117">Zvažte například následující deklaraci typu Shape.</span><span class="sxs-lookup"><span data-stu-id="a8773-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="a8773-118">Předchozí kód deklaruje discriminated union Shape, který může mít hodnoty libovolného ze tří případů: Rectangle, Circle a Prism.</span><span class="sxs-lookup"><span data-stu-id="a8773-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="a8773-119">Každý případ má jinou sadu polí.</span><span class="sxs-lookup"><span data-stu-id="a8773-119">Each case has a different set of fields.</span></span> <span data-ttu-id="a8773-120">Rectangle případ má dvě pojmenovaná `float`pole, oba typu , které mají názvy šířku a délku.</span><span class="sxs-lookup"><span data-stu-id="a8773-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="a8773-121">Případ Kruh má jen jedno pojmenované pole, poloměr.</span><span class="sxs-lookup"><span data-stu-id="a8773-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="a8773-122">Případ Hranol má tři pole, z nichž dvě (šířka a výška) jsou pojmenována pole.</span><span class="sxs-lookup"><span data-stu-id="a8773-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="a8773-123">Nepojmenovaná pole jsou označována jako anonymní pole.</span><span class="sxs-lookup"><span data-stu-id="a8773-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="a8773-124">Objekty vytvoříte zadáním hodnot pro pojmenovaná a anonymní pole podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="a8773-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="a8773-125">Tento kód ukazuje, že můžete buď použít pojmenovaná pole v inicializaci, nebo se můžete spolehnout na pořadí polí v deklaraci a pouze zadat hodnoty pro každé pole v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a8773-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="a8773-126">Volání konstruktoru `rect` v předchozím kódu používá pojmenovaná pole, `circ` ale volání konstruktoru používá řazení.</span><span class="sxs-lookup"><span data-stu-id="a8773-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="a8773-127">Můžete kombinovat uspořádaná pole a pojmenovaná `prism`pole, jako při výstavbě .</span><span class="sxs-lookup"><span data-stu-id="a8773-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="a8773-128">Typ `option` je jednoduché discriminated unie v knihovně jádra F#.</span><span class="sxs-lookup"><span data-stu-id="a8773-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="a8773-129">Typ `option` je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a8773-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="a8773-130">Předchozí kód určuje, že `Option` typ je discriminated unie, `Some` `None`která má dva případy a .</span><span class="sxs-lookup"><span data-stu-id="a8773-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="a8773-131">Případ `Some` má přidruženou hodnotu, která se skládá z jednoho `'a`anonymního pole, jehož typ je reprezentován parametrem typu .</span><span class="sxs-lookup"><span data-stu-id="a8773-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="a8773-132">Případ `None` nemá žádnou přidruženou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8773-132">The `None` case has no associated value.</span></span> <span data-ttu-id="a8773-133">`option` Typ tedy určuje obecný typ, který má buď hodnotu nějakého typu, nebo žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8773-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="a8773-134">Typ `Option` má také alias typu `option`s nižšími písmeny , který se běžněji používá.</span><span class="sxs-lookup"><span data-stu-id="a8773-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="a8773-135">Identifikátory případu lze použít jako konstruktory pro discriminated union typu.</span><span class="sxs-lookup"><span data-stu-id="a8773-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="a8773-136">Například následující kód se používá k `option` vytvoření hodnot typu.</span><span class="sxs-lookup"><span data-stu-id="a8773-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="a8773-137">Identifikátory případu se také používají ve výrazech porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="a8773-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="a8773-138">Ve výrazu porovnávání vzorů jsou k dispozici identifikátory pro hodnoty přidružené k jednotlivým případům.</span><span class="sxs-lookup"><span data-stu-id="a8773-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="a8773-139">Například v následujícím kódu `x` je identifikátor daný hodnotu, `Some` která je `option` spojena s případem typu.</span><span class="sxs-lookup"><span data-stu-id="a8773-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="a8773-140">Ve výrazech porovnávání vzorů můžete použít pojmenovaná pole k určení diskriminovaných shod sjednocení.</span><span class="sxs-lookup"><span data-stu-id="a8773-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="a8773-141">Pro typ obrazec, který byl deklarován dříve, můžete použít pojmenovaná pole jako následující kód ukazuje extrahovat hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="a8773-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="a8773-142">Identifikátory případů lze obvykle použít, aniž by byly kvalifikovány názvem unie.</span><span class="sxs-lookup"><span data-stu-id="a8773-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="a8773-143">Pokud chcete, aby byl název vždy kvalifikován názvem unie, můžete použít atribut [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) na definici typu sjednocení.</span><span class="sxs-lookup"><span data-stu-id="a8773-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="a8773-144">Rozbalení discriminated sjednocení</span><span class="sxs-lookup"><span data-stu-id="a8773-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="a8773-145">V F# Discriminated Unions se často používají v modelování domény pro obtékání jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="a8773-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="a8773-146">Je snadné extrahovat základní hodnotu pomocí porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="a8773-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="a8773-147">Není nutné použít výraz shody pro jeden případ:</span><span class="sxs-lookup"><span data-stu-id="a8773-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="a8773-148">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="a8773-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="a8773-149">Porovnávání vzorů je také povoleno přímo v parametrech funkce, takže můžete rozbalit jeden případ:</span><span class="sxs-lookup"><span data-stu-id="a8773-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="a8773-150">Strukturovat discriminated odbory</span><span class="sxs-lookup"><span data-stu-id="a8773-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="a8773-151">Můžete také zastupovat discriminated sjednocení jako struktury.</span><span class="sxs-lookup"><span data-stu-id="a8773-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="a8773-152">To se provádí `[<Struct>]` s atributem.</span><span class="sxs-lookup"><span data-stu-id="a8773-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="a8773-153">Vzhledem k tomu, že se jedná o typy hodnot a nikoli o typy odkazů, existují další důležité informace ve srovnání s odkazem discriminated sjednocení:</span><span class="sxs-lookup"><span data-stu-id="a8773-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="a8773-154">Jsou zkopírovány jako typy hodnot a mají sémantiku typu hodnota.</span><span class="sxs-lookup"><span data-stu-id="a8773-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="a8773-155">Nelze použít definici rekurzivního typu s víceřádkovou strukturou Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="a8773-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="a8773-156">Je nutné zadat jedinečné názvy případů pro vícecase strukturované sjednocení.</span><span class="sxs-lookup"><span data-stu-id="a8773-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="a8773-157">Použití diskriminovaných sjednocení namísto hierarchií objektů</span><span class="sxs-lookup"><span data-stu-id="a8773-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="a8773-158">Často můžete použít discriminated unie jako jednodušší alternativu k hierarchii malýobjekt.</span><span class="sxs-lookup"><span data-stu-id="a8773-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="a8773-159">Například následující discriminated unie by mohla `Shape` být použita namísto základní třídy, která má odvozené typy pro kruh, čtverec a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a8773-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="a8773-160">Namísto virtuální metody pro výpočet oblasti nebo obvodu, jako byste použili v objektově orientované implementaci, můžete použít porovnávání vzorů do větvení na příslušné vzorce pro výpočet těchto množství.</span><span class="sxs-lookup"><span data-stu-id="a8773-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="a8773-161">V následujícím příkladu se k výpočtu oblasti používají různé vzorce v závislosti na tvaru.</span><span class="sxs-lookup"><span data-stu-id="a8773-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="a8773-162">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="a8773-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="a8773-163">Použití diskriminovaných sjednocení pro stromové datové struktury</span><span class="sxs-lookup"><span data-stu-id="a8773-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="a8773-164">Diskriminované sjednocení může být rekurzivní, což znamená, že unie sama může být zahrnuta do typu jednoho nebo více případů.</span><span class="sxs-lookup"><span data-stu-id="a8773-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="a8773-165">Rekurzivní discriminated sjednocení lze použít k vytvoření stromové struktury, které se používají k modelování výrazů v programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="a8773-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="a8773-166">V následujícím kódu rekurzivní discriminated unie se používá k vytvoření struktury dat binární strom.</span><span class="sxs-lookup"><span data-stu-id="a8773-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="a8773-167">Unie se skládá ze `Node`dvou případů , což je uzel s celou hodnotou a `Tip`levými a pravými podstromy a , který ukončí strom.</span><span class="sxs-lookup"><span data-stu-id="a8773-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="a8773-168">V předchozím kódu `resultSumTree` má hodnotu 10.</span><span class="sxs-lookup"><span data-stu-id="a8773-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="a8773-169">Následující obrázek znázorňuje `myTree`stromovou strukturu pro .</span><span class="sxs-lookup"><span data-stu-id="a8773-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagram, který ukazuje stromovou strukturu pro myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="a8773-171">Discriminated sjednocení fungují dobře, pokud uzly ve stromu jsou heterogenní.</span><span class="sxs-lookup"><span data-stu-id="a8773-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="a8773-172">V následujícím kódu typ `Expression` představuje abstraktní syntaktický strom výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných.</span><span class="sxs-lookup"><span data-stu-id="a8773-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="a8773-173">Některé případy sjednocení nejsou rekurzivní a představují`Number`buď čísla (`Variable`) nebo proměnné ( ).</span><span class="sxs-lookup"><span data-stu-id="a8773-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="a8773-174">Jiné případy jsou rekurzivní a`Add` představují `Multiply`operace ( a ), kde operandy jsou také výrazy.</span><span class="sxs-lookup"><span data-stu-id="a8773-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="a8773-175">Funkce `Evaluate` používá výraz shody k rekurzivnímu zpracování stromu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a8773-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="a8773-176">Při spuštění tohoto kódu `result` je hodnota 5.</span><span class="sxs-lookup"><span data-stu-id="a8773-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="a8773-177">Členové</span><span class="sxs-lookup"><span data-stu-id="a8773-177">Members</span></span>

<span data-ttu-id="a8773-178">Je možné definovat členy na diskriminované odbory.</span><span class="sxs-lookup"><span data-stu-id="a8773-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="a8773-179">Následující příklad ukazuje, jak definovat vlastnost a implementovat rozhraní:</span><span class="sxs-lookup"><span data-stu-id="a8773-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="a8773-180">Běžné atributy</span><span class="sxs-lookup"><span data-stu-id="a8773-180">Common attributes</span></span>

<span data-ttu-id="a8773-181">Následující atributy jsou běžně vidět v diskriminované sjednocení:</span><span class="sxs-lookup"><span data-stu-id="a8773-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="a8773-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8773-182">See also</span></span>

- [<span data-ttu-id="a8773-183">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="a8773-183">F# Language Reference</span></span>](index.md)
