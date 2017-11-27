---
title: "Řazené kolekce členů (F#)"
description: "Další informace o F # tuple, seskupení nepojmenované ale seřazené hodnoty, které by mohly mít různých typů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: c6a0565ac7022928f5c2bdad5387d896c6c3d387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tuples"></a><span data-ttu-id="504d4-104">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="504d4-104">Tuples</span></span>

<span data-ttu-id="504d4-105">A *řazené kolekce členů* je seskupení nepojmenované ale seřazené hodnoty, které by mohly mít různých typů.</span><span class="sxs-lookup"><span data-stu-id="504d4-105">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="504d4-106">Řazené kolekce členů může být buď odkazové typy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="504d4-106">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="504d4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="504d4-107">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="504d4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="504d4-108">Remarks</span></span>
<span data-ttu-id="504d4-109">Každý *element* v předchozí syntaxi, může být jakýkoli platný výraz F #.</span><span class="sxs-lookup"><span data-stu-id="504d4-109">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="504d4-110">Příklady</span><span class="sxs-lookup"><span data-stu-id="504d4-110">Examples</span></span>
<span data-ttu-id="504d4-111">Řazené kolekce členů příklady páry, triples a tak dále, stejné nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="504d4-111">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="504d4-112">Některé příklady jsou znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="504d4-112">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="504d4-113">Získání jednotlivých hodnot</span><span class="sxs-lookup"><span data-stu-id="504d4-113">Obtaining Individual Values</span></span>
<span data-ttu-id="504d4-114">Můžete porovnávání vzorů pro přístup a přiřadit názvy elementů řazené kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="504d4-114">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="504d4-115">Můžete také deconstruct řazené kolekce členů prostřednictvím shoda vzoru mimo `match` výraz prostřednictvím `let` vazby:</span><span class="sxs-lookup"><span data-stu-id="504d4-115">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="504d4-116">Nebo můžete vzor shodného řazených kolekcí členů jako vstupy do funkce:</span><span class="sxs-lookup"><span data-stu-id="504d4-116">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="504d4-117">Pokud budete potřebovat pouze jeden element řazenou kolekci členů, zástupný znak (podtržítko) slouží k Vyhněte se vytváření nový název pro hodnotu, která není nutné.</span><span class="sxs-lookup"><span data-stu-id="504d4-117">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="504d4-118">Kopírování prvků z odkazu řazené kolekce členů do struktura řazené kolekce členů je také jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="504d4-118">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="504d4-119">Funkce `fst` a `snd` (odkazovat jenom řazených kolekcí členů) vrátí první a druhé elementy řazené kolekce členů, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="504d4-119">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="504d4-120">Neexistuje žádné integrované funkce, která vrátí třetí elementu triple, ale jeden takto snadno zápisu.</span><span class="sxs-lookup"><span data-stu-id="504d4-120">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="504d4-121">Obecně platí je lepší použít porovnávání vzorů pro přístup k elementům jednotlivých řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="504d4-121">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="504d4-122">Pomocí řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="504d4-122">Using Tuples</span></span>
<span data-ttu-id="504d4-123">Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="504d4-123">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="504d4-124">Tento příklad provede celočíselné dělení a vrátí zaokrouhlené výsledek operace jako první člen pár řazené kolekce členů a zbývající jako druhý člen, které odpovídá páru.</span><span class="sxs-lookup"><span data-stu-id="504d4-124">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="504d4-125">Řazené kolekce členů můžete také použít jako argumenty funkce když budete chtít vyhnout implicitní currying argumenty funkce, které je zahrnuto v syntaxi obvyklé funkce.</span><span class="sxs-lookup"><span data-stu-id="504d4-125">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="504d4-126">Obvyklé syntaxi pro definování funkce `let sum a b = a + b` umožňuje definovat funkci, která je částečné aplikace prvního argumentu funkce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="504d4-126">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="504d4-127">Pomocí řazené kolekce členů jako parametr zakáže currying.</span><span class="sxs-lookup"><span data-stu-id="504d4-127">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="504d4-128">Další informace najdete v tématu "Částečné aplikace argumenty" v [funkce](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="504d4-128">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="504d4-129">Názvy typů řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="504d4-129">Names of Tuple Types</span></span>
<span data-ttu-id="504d4-130">Při psaní název typu, který je řazené kolekce členů použijete `*` symbol jednotlivé prvky.</span><span class="sxs-lookup"><span data-stu-id="504d4-130">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="504d4-131">Pro řazené kolekce členů, která se skládá z `int`, `float`a `string`, jako například `(10, 10.0, "ten")`, typ by byla zapsána následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="504d4-131">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="504d4-132">Vzájemná spolupráce s řazenými kolekcemi členů C#</span><span class="sxs-lookup"><span data-stu-id="504d4-132">Interoperation with C# Tuples</span></span>

<span data-ttu-id="504d4-133">Pro jazyk C# 7 zavést řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="504d4-133">C# 7 introduced tuples to the language.</span></span>  <span data-ttu-id="504d4-134">Řazených kolekcí členů v C# a jsou struktury a jsou ekvivalentní struktura řazených kolekcí členů v F #.</span><span class="sxs-lookup"><span data-stu-id="504d4-134">Tuples in C# and are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="504d4-135">Pokud potřebujete zajistit vzájemnou funkční spolupráci s C# používá řazené kolekce členů, je nutné použít struktura řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="504d4-135">If you need to interoperate with C# uses tuples, you must use struct tuples.</span></span>

<span data-ttu-id="504d4-136">Toto je snadné provést.</span><span class="sxs-lookup"><span data-stu-id="504d4-136">This is easy to do.</span></span>  <span data-ttu-id="504d4-137">Představte si například, že je nutné předat řazené kolekce členů třídy jazyka C# a pak využívat jeho výsledek, který je také řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="504d4-137">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="504d4-138">V F # kódu můžete pak předejte řazené kolekce členů struktura jako parametr a využívat výsledek v podobě struktura řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="504d4-138">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="504d4-139">Převod mezi odkaz řazených kolekcí členů a řazené kolekce členů – struktura</span><span class="sxs-lookup"><span data-stu-id="504d4-139">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="504d4-140">Protože odkaz řazených kolekcí členů a struktura řazených kolekcí členů mají základní znázornění úplně jiné, nejsou implicitně převést.</span><span class="sxs-lookup"><span data-stu-id="504d4-140">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="504d4-141">To znamená nebude kompilace kódu, například následující:</span><span class="sxs-lookup"><span data-stu-id="504d4-141">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="504d4-142">Musí vzor odpovídající na jeden záznam a ostatní části základní vytvořit.</span><span class="sxs-lookup"><span data-stu-id="504d4-142">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="504d4-143">Příklad:</span><span class="sxs-lookup"><span data-stu-id="504d4-143">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="504d4-144">Kompilované formuláře odkaz řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="504d4-144">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="504d4-145">Tato část vysvětluje formu řazených kolekcí členů v případě, že se kompilují.</span><span class="sxs-lookup"><span data-stu-id="504d4-145">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="504d4-146">Zde uvedené informace není nezbytné pro čtení, pokud cílíte na rozhraní .NET Framework 3.5 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="504d4-146">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="504d4-147">Řazené kolekce členů kompilovány do jednoho z několika obecné typy všechny pojmenované objekty `System.Tuple`, která jsou přetížené na Arita nebo počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="504d4-147">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="504d4-148">Typy řazené kolekce členů se zobrazí v tomto formuláři, když zobrazujete v jiném jazyce, jako je například C# nebo Visual Basic nebo používáte nástroj, který nemá informace o konstrukce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="504d4-148">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="504d4-149">`Tuple` Typy byly zavedeny v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="504d4-149">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="504d4-150">Pokud jsou cílení na dřívější verzi rozhraní .NET Framework, kompilátor použije verzích [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2.0 základní knihovny F #.</span><span class="sxs-lookup"><span data-stu-id="504d4-150">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="504d4-151">Typy v této knihovně se používají pouze pro aplikace, které cílí 2.0, 3.0 a 3.5 verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="504d4-151">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="504d4-152">Předávání typů slouží k zajištění binární kompatibilitu mezi jednotlivými součásti rozhraní .NET Framework 2.0 a .NET Framework 4 F #.</span><span class="sxs-lookup"><span data-stu-id="504d4-152">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="504d4-153">Kompilované formuláře řazené kolekce členů – struktura</span><span class="sxs-lookup"><span data-stu-id="504d4-153">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="504d4-154">Struktura řazených kolekcí členů (například `struct (x, y)`), se zásadně liší od odkaz řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="504d4-154">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="504d4-155">Že se kompilují do <xref:System.ValueTuple> typu, přetížené Arita nebo počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="504d4-155">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="504d4-156">Jsou ekvivalentní [C# 7 řazených kolekcí členů](../../csharp/tuples.md) a [jazyka Visual Basic 2017 řazených kolekcí členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a zajistit vzájemnou funkční spolupráci obousměrně.</span><span class="sxs-lookup"><span data-stu-id="504d4-156">They are equivalent to [C# 7 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="504d4-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="504d4-157">See Also</span></span>
[<span data-ttu-id="504d4-158">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="504d4-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="504d4-159">Typy F #</span><span class="sxs-lookup"><span data-stu-id="504d4-159">F# Types</span></span>](fsharp-types.md)
