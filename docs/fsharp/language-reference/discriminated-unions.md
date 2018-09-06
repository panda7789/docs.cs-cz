---
title: Rozlišovaná sjednocení (F#)
description: 'Další informace o použití F # rozlišovaná sjednocení.'
ms.date: 05/16/2016
ms.openlocfilehash: 06d6c154790f659c0c7ff73290357ab50a134362
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788120"
---
# <a name="discriminated-unions"></a><span data-ttu-id="b37ce-103">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="b37ce-103">Discriminated Unions</span></span>

<span data-ttu-id="b37ce-104">Rozlišovaná sjednocení poskytují podporu pro hodnoty, které může být jedna z počty pojmenovaných případů, případně každý má jiné hodnoty a typy.</span><span class="sxs-lookup"><span data-stu-id="b37ce-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="b37ce-105">Rozlišovaná sjednocení jsou užitečná pro heterogenní data; data, která mohou mít zvláštní případy, včetně platných a chybových případů; data, která se liší v typu z jedné instance do druhé; a jako alternativu pro malé hierarchie objektů.</span><span class="sxs-lookup"><span data-stu-id="b37ce-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="b37ce-106">Navíc rekurzivně diskriminovaná sjednocení se používají ke znázornění stromových struktur dat.</span><span class="sxs-lookup"><span data-stu-id="b37ce-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="b37ce-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b37ce-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="b37ce-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b37ce-108">Remarks</span></span>

<span data-ttu-id="b37ce-109">Rozlišovaná sjednocení jsou podobná sjednocovacím typům v jiných jazycích, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="b37ce-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="b37ce-110">Jako s sjednocovacího typu v C++ nebo variantním typu v jazyce Visual Basic, data uložená v hodnotě nejsou pevná; To může být jedna z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="b37ce-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="b37ce-111">Na rozdíl od sjednocení v těchto jazycích však každé možnosti dostane *identifikátor případu*.</span><span class="sxs-lookup"><span data-stu-id="b37ce-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="b37ce-112">Identifikátory velikosti písmen jsou názvy pro různé typy hodnot, které by mohly být objekty tohoto typu; hodnoty jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="b37ce-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="b37ce-113">Pokud hodnoty nejsou k dispozici, případ je ekvivalentní případu výčtu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="b37ce-114">Pokud existují hodnoty, každá hodnota může být buď samostatná hodnota ze zadaného typu nebo n-tice, která agreguje více polí stejných nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="b37ce-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="b37ce-115">Jednotlivá pole můžete dát název, ale název je volitelný, i když jsou pojmenovány jiná pole v malých písmen.</span><span class="sxs-lookup"><span data-stu-id="b37ce-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="b37ce-116">Usnadnění pro rozlišovaná sjednocení výchozí hodnota je `public`.</span><span class="sxs-lookup"><span data-stu-id="b37ce-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="b37ce-117">Zvažte například následující deklaraci typu obrazce.</span><span class="sxs-lookup"><span data-stu-id="b37ce-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="b37ce-118">Předchozí kód deklaruje diskriminované sjednocení tvar, který může nabývat hodnot ve všech třech případech: obdélník, kruh a hranol.</span><span class="sxs-lookup"><span data-stu-id="b37ce-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="b37ce-119">Každý případ má jinou sadu polí.</span><span class="sxs-lookup"><span data-stu-id="b37ce-119">Each case has a different set of fields.</span></span> <span data-ttu-id="b37ce-120">Obdélník využívá dvě s názvem pole, oba typu `float`, které mají názvy šířka a délka.</span><span class="sxs-lookup"><span data-stu-id="b37ce-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="b37ce-121">Případ kruh má pouze jedno pole s názvem, poloměr.</span><span class="sxs-lookup"><span data-stu-id="b37ce-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="b37ce-122">Případ hranolu obsahuje tři pole dvě z které (šířka a výška) jsou pojmenované názvy polí.</span><span class="sxs-lookup"><span data-stu-id="b37ce-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="b37ce-123">Nepojmenované pole jsou označovány jako anonymní pole.</span><span class="sxs-lookup"><span data-stu-id="b37ce-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="b37ce-124">Objekty je možné vytvořit zadáním hodnot pro pojmenované a anonymní pole podle následujících příkladů.</span><span class="sxs-lookup"><span data-stu-id="b37ce-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="b37ce-125">Tento kód ukazuje, že můžete použít buď pojmenovaná pole v inicializaci, nebo můžete spoléhat na pořadí polí v deklaraci a stačí zadat hodnoty pro každé pole zase.</span><span class="sxs-lookup"><span data-stu-id="b37ce-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="b37ce-126">Volání konstruktoru pro `rect` v předcházejícím kódu používá pojmenovaná pole, ale volání konstruktoru pro `circ` používá řazení.</span><span class="sxs-lookup"><span data-stu-id="b37ce-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="b37ce-127">Můžete kombinovat objednaná pole a pojmenovaná pole jako v konstrukci `prism`.</span><span class="sxs-lookup"><span data-stu-id="b37ce-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="b37ce-128">`option` Typ je jednoduchým diskriminovaným sjednocením v základní knihovně F #.</span><span class="sxs-lookup"><span data-stu-id="b37ce-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="b37ce-129">`option` Typ je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b37ce-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="b37ce-130">Předchozí kód, který určuje typ `Option` je diskriminovaným sjednocením, které má dva případy `Some` a `None`.</span><span class="sxs-lookup"><span data-stu-id="b37ce-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="b37ce-131">`Some` Případ má přidruženou hodnotu, která se skládá z jednoho anonymní pole, jehož typ je vyjádřen parametrem typu `'a`.</span><span class="sxs-lookup"><span data-stu-id="b37ce-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="b37ce-132">`None` Případ nemá přidruženou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-132">The `None` case has no associated value.</span></span> <span data-ttu-id="b37ce-133">Proto `option` typ určuje obecný typ, který má buď hodnotu některého typu nebo žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="b37ce-134">Typ `Option` má také alias psaný malými písmeny `option`, to znamená informace, které se běžně používají.</span><span class="sxs-lookup"><span data-stu-id="b37ce-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="b37ce-135">Identifikátory velikosti písmen lze jako konstruktory diskriminovaného typu sjednocení.</span><span class="sxs-lookup"><span data-stu-id="b37ce-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="b37ce-136">Například následující kód slouží k vytvoření hodnoty `option` typu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="b37ce-137">Identifikátory velikosti písmen se také používají ve vzorech porovnávání výrazů.</span><span class="sxs-lookup"><span data-stu-id="b37ce-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="b37ce-138">Ve vzoru porovnávání výrazů jsou k dispozici identifikátory hodnot spojené s jednotlivými případy.</span><span class="sxs-lookup"><span data-stu-id="b37ce-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="b37ce-139">Například v následujícím kódu `x` identifikátorem přiřazené hodnoty, který je přidružen `Some` případě `option` typu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="b37ce-140">Ve vzoru porovnávání výrazů můžete použít pojmenovaná pole k určení diskriminovaných sjednocených shod.</span><span class="sxs-lookup"><span data-stu-id="b37ce-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="b37ce-141">Pro typ tvar, který byl deklarován dříve můžete použít pojmenovaná pole, jak ukazuje následující kód k extrahování hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="b37ce-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="b37ce-142">Za normálních okolností lze identifikátory velikosti písmen použít bez jejich kvalifikace názvu unie.</span><span class="sxs-lookup"><span data-stu-id="b37ce-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="b37ce-143">Pokud chcete, aby název, který má být vždy kvalifikovaným názvem sjednocení, můžete použít [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atributu na definici typu sjednocení.</span><span class="sxs-lookup"><span data-stu-id="b37ce-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="b37ce-144">Rozbalení rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="b37ce-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="b37ce-145">V Rozlišované sjednocení F # se často používají v doméně modelování pro obtékání jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="b37ce-146">Je snadné získání základní hodnoty přes porovnávání vzorů také.</span><span class="sxs-lookup"><span data-stu-id="b37ce-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="b37ce-147">Není nutné použít odpovídající výraz pro jeden případ:</span><span class="sxs-lookup"><span data-stu-id="b37ce-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="b37ce-148">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="b37ce-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="b37ce-149">Rozlišovaná sjednocení – struktura</span><span class="sxs-lookup"><span data-stu-id="b37ce-149">Struct Discriminated Unions</span></span>

<span data-ttu-id="b37ce-150">Od verze F # 4.1, může také představovat Rozlišované sjednocení jako struktury.</span><span class="sxs-lookup"><span data-stu-id="b37ce-150">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="b37ce-151">Používá se k tomu `[<Struct>]` atribut.</span><span class="sxs-lookup"><span data-stu-id="b37ce-151">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="b37ce-152">Protože jsou typy hodnot a typy odkazů nikoli, jsou doplňující aspekty, které jsou ve srovnání s odkazem na rozlišovaná sjednocení:</span><span class="sxs-lookup"><span data-stu-id="b37ce-152">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="b37ce-153">Tyto jsou zkopírovány jako typy hodnot a mít Sémantika typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b37ce-153">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="b37ce-154">Definice rekurzivního typu nelze použít s multicase struct Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="b37ce-154">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="b37ce-155">Musíte zadat jedinečné názvy případu pro multicase struct Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="b37ce-155">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="b37ce-156">Použití rozlišovaných Unionů místo hierarchií objektu</span><span class="sxs-lookup"><span data-stu-id="b37ce-156">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="b37ce-157">Můžete často použít diskriminované sjednocení jako jednodušší alternativu k malé hierarchii objektu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-157">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="b37ce-158">Například následující diskriminované sjednocení může místo `Shape` základní třída, která obsahuje odvozené typy pro kruh, čtverec, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b37ce-158">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="b37ce-159">Místo toho virtuální metody pro výpočet plochy nebo obvodu, jako byste použili pro objektově orientované implementaci, můžete k výpočtu těchto množství porovnávání vzorce pro větvení příslušných vzorců.</span><span class="sxs-lookup"><span data-stu-id="b37ce-159">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="b37ce-160">V následujícím příkladu se používají různé vzorce pro výpočet plochy v závislosti na tvaru.</span><span class="sxs-lookup"><span data-stu-id="b37ce-160">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="b37ce-161">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="b37ce-161">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="b37ce-162">Použití rozlišovaných Unionů pro struktury dat stromu</span><span class="sxs-lookup"><span data-stu-id="b37ce-162">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="b37ce-163">Rozlišovaná sjednocení mohou být rekurzivní, což znamená, že samotné sjednocení mohou být součástí typů jednoho nebo více případů.</span><span class="sxs-lookup"><span data-stu-id="b37ce-163">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="b37ce-164">Rekurzivní rozlišovaná sjednocení lze použít k vytvoření stromových struktur, které se používají pro modelování výrazů v programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="b37ce-164">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="b37ce-165">V následujícím kódu je rekurzivní diskriminované sjednocení použito k vytvoření struktury dat binárního stromu.</span><span class="sxs-lookup"><span data-stu-id="b37ce-165">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="b37ce-166">Union se skládá ze dvou případech `Node`, což je uzel s celočíselnou hodnotou a levým a pravým podstromem, a `Tip`, který ukončí strom.</span><span class="sxs-lookup"><span data-stu-id="b37ce-166">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="b37ce-167">V předchozím kódu `resultSumTree` má hodnotu 10.</span><span class="sxs-lookup"><span data-stu-id="b37ce-167">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="b37ce-168">Následující obrázek znázorňuje stromovou strukturu `myTree`.</span><span class="sxs-lookup"><span data-stu-id="b37ce-168">The following illustration shows the tree structure for `myTree`.</span></span>

![Stromová struktura pro myTree](../media/TreeStructureDiagram.png)

<span data-ttu-id="b37ce-170">Rozlišovaná sjednocení pracují dobře, pokud uzly ve stromu jsou heterogenní.</span><span class="sxs-lookup"><span data-stu-id="b37ce-170">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="b37ce-171">V následujícím kódu, typ `Expression` představuje abstraktní strom syntaxe výrazu v jednoduchém programovacím jazyce, který podporuje sčítání a násobení čísel a proměnných.</span><span class="sxs-lookup"><span data-stu-id="b37ce-171">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="b37ce-172">Některé sjednocovací případy nejsou rekurzivní a představují buď čísla (`Number`) nebo proměnné (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="b37ce-172">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="b37ce-173">Ostatní případy jsou rekurzivní a představují operace (`Add` a `Multiply`), kde jsou jako operandy také výrazy.</span><span class="sxs-lookup"><span data-stu-id="b37ce-173">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="b37ce-174">`Evaluate` Funkce používá odpovídající výraz pro rekurzivní zpracování stromu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b37ce-174">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="b37ce-175">Při spuštění tohoto kódu, hodnota `result` je 5.</span><span class="sxs-lookup"><span data-stu-id="b37ce-175">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="b37ce-176">Běžné atributy</span><span class="sxs-lookup"><span data-stu-id="b37ce-176">Common Attributes</span></span>

<span data-ttu-id="b37ce-177">Následující atributy se běžně zobrazují v rozlišovaných sjednoceních:</span><span class="sxs-lookup"><span data-stu-id="b37ce-177">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a><span data-ttu-id="b37ce-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b37ce-178">See also</span></span>

- [<span data-ttu-id="b37ce-179">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b37ce-179">F# Language Reference</span></span>](index.md)
