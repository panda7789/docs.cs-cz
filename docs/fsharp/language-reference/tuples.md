---
title: Řazené kolekce členů
description: Další informace o F# řazené kolekce členů, seskupení nepojmenované ale seřazené hodnoty, může být různých typů.
ms.date: 05/16/2016
ms.openlocfilehash: a1fc31d4dc97c0921545e53b91dcde0547002006
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611045"
---
# <a name="tuples"></a><span data-ttu-id="ebe43-103">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="ebe43-103">Tuples</span></span>

<span data-ttu-id="ebe43-104">A *řazené kolekce členů* je seskupení nepojmenované ale seřazené hodnoty, může být různých typů.</span><span class="sxs-lookup"><span data-stu-id="ebe43-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="ebe43-105">Řazené kolekce členů může být buď referenční typy a struktury.</span><span class="sxs-lookup"><span data-stu-id="ebe43-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebe43-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebe43-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="ebe43-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebe43-107">Remarks</span></span>

<span data-ttu-id="ebe43-108">Každý *element* v předchozí syntaxi může být libovolný platný F# výrazu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="ebe43-109">Příklady</span><span class="sxs-lookup"><span data-stu-id="ebe43-109">Examples</span></span>

<span data-ttu-id="ebe43-110">Příklady řazených kolekcí členů: dvojice, trojic a tak dále, stejných nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="ebe43-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="ebe43-111">Některé příklady jsou znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="ebe43-112">Získání jednotlivých hodnot</span><span class="sxs-lookup"><span data-stu-id="ebe43-112">Obtaining Individual Values</span></span>

<span data-ttu-id="ebe43-113">Můžete porovnávání vzorů pro přístup k a přiřadit názvy elementů řazené kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="ebe43-114">Můžete také dekonstruovat řazené kolekce členů přes porovnávání vzorů mimo `match` výraz prostřednictvím `let` vazby:</span><span class="sxs-lookup"><span data-stu-id="ebe43-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="ebe43-115">Nebo můžete vzorku odpovídají na řazené kolekce členů jako vstupy do funkce:</span><span class="sxs-lookup"><span data-stu-id="ebe43-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="ebe43-116">Pokud potřebujete pouze jeden prvek řazené kolekce členů, zástupný znak (podtržítko) lze se vyhnout, vytvářet nový název pro hodnotu, která není nutné.</span><span class="sxs-lookup"><span data-stu-id="ebe43-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="ebe43-117">Zkopírování prvků z řazené kolekce členů odkazu do řazené kolekce členů struktury je také jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="ebe43-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="ebe43-118">Funkce `fst` a `snd` (odkazovat jenom řazených kolekcí členů) vrátí první a druhý elementů řazené kolekce členů, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ebe43-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="ebe43-119">Neexistuje žádná integrované funkce, která vrací třetího prvku pole s trojitými, ale jeden takto snadno zápisu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="ebe43-120">Obecně je vhodnější použít porovnávání vzorů pro přístup k prvkům jednotlivé řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="ebe43-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="ebe43-121">Použití řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="ebe43-121">Using Tuples</span></span>

<span data-ttu-id="ebe43-122">Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="ebe43-123">V tomto příkladu provede dělení celého čísla a vrátí zaokrouhlené výsledek operace jako první člen pár řazené kolekce členů a zbytek jako druhý člen, které odpovídá páru licencí.</span><span class="sxs-lookup"><span data-stu-id="ebe43-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="ebe43-124">Řazené kolekce členů můžete také použít jako argumenty funkce chcete se vyhnout implicitní curryfikaci argumentů funkce, které je vyjádřena pomocí syntaxe běžné funkce.</span><span class="sxs-lookup"><span data-stu-id="ebe43-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="ebe43-125">Běžné syntaxi pro definici funkce `let sum a b = a + b` vám umožní definovat funkci, která je částečné použití argumentů prvního argumentu funkce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="ebe43-126">Pomocí řazené kolekce členů jako parametr zakáže curryfikace.</span><span class="sxs-lookup"><span data-stu-id="ebe43-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="ebe43-127">Další informace najdete v části "Částečné použití argumentů" v [funkce](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebe43-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="ebe43-128">Názvy typů pro řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="ebe43-128">Names of Tuple Types</span></span>

<span data-ttu-id="ebe43-129">Při psaní název typu, který je řazená kolekce členů je použít `*` k oddělování elementů symbol.</span><span class="sxs-lookup"><span data-stu-id="ebe43-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="ebe43-130">Pro n-tice, která se skládá `int`, `float`a `string`, jako například `(10, 10.0, "ten")`, typu by byla zapsána následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ebe43-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="ebe43-131">Vzájemná spolupráce s řazenými kolekcemi členů jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ebe43-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="ebe43-132">C# 7.0 seznámili s řazenými kolekcemi členů jazyka.</span><span class="sxs-lookup"><span data-stu-id="ebe43-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="ebe43-133">Řazené kolekce členů v C# jsou struktury a je stejná u strukturovaných řazených kolekcí členů v F#.</span><span class="sxs-lookup"><span data-stu-id="ebe43-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="ebe43-134">Pokud potřebujete zajistit vzájemnou funkční spolupráci s jazykem C#, je nutné použít strukturovaných řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="ebe43-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="ebe43-135">To je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="ebe43-135">This is easy to do.</span></span>  <span data-ttu-id="ebe43-136">Představte si například, že je nutné předat řazené kolekce členů třídy C# a jeho výsledek, který je zároveň řazené kolekce členů je pak využívat:</span><span class="sxs-lookup"><span data-stu-id="ebe43-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="ebe43-137">Ve vaší F# kódu, můžete předat jako parametr řazené kolekce členů struktury a využívat výsledek v podobě řazené kolekce členů struktury.</span><span class="sxs-lookup"><span data-stu-id="ebe43-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="ebe43-138">Převod mezi řazené kolekce členů odkazů a strukturovaných řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="ebe43-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="ebe43-139">Protože řazené kolekce členů odkazů a strukturovaných řazených kolekcí členů mají úplně jiné základní reprezentaci, nejsou implicitně převoditelné.</span><span class="sxs-lookup"><span data-stu-id="ebe43-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="ebe43-140">To znamená nebude kompilovat kód například následující:</span><span class="sxs-lookup"><span data-stu-id="ebe43-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="ebe43-141">Třeba vzor odpovídající jedna n-tice a druhý s základní části vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ebe43-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="ebe43-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ebe43-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="ebe43-143">Zkompilovaná forma řazené kolekce členů odkazů</span><span class="sxs-lookup"><span data-stu-id="ebe43-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="ebe43-144">Tato část vysvětluje formě řazené kolekce členů, když jsou kompilovány.</span><span class="sxs-lookup"><span data-stu-id="ebe43-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="ebe43-145">Tyto informace tady není nutné číst, pokud se zaměřujete na rozhraní .NET Framework 3.5 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="ebe43-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="ebe43-146">Řazené kolekce členů jsou kompilovány do jednoho z několika obecných typů všechny pojmenované objekty `System.Tuple`, které jsou přetížené Arita nebo počtu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="ebe43-147">Typy řazené kolekce členů se zobrazí v tomto formuláři při zobrazení je z jiného jazyka, jako například C# nebo Visual Basic, nebo pokud používáte nástroj, který nemá žádné informace o F# vytvoří.</span><span class="sxs-lookup"><span data-stu-id="ebe43-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="ebe43-148">`Tuple` Typy byly zavedeny v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ebe43-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="ebe43-149">Pokud se zaměřujete na starší verzi rozhraní .NET Framework, kterou kompilátor používá verze [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2.0 F# Core Library.</span><span class="sxs-lookup"><span data-stu-id="ebe43-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="ebe43-150">Typy v této knihovně se používají pouze pro aplikace, které se zaměřují 2.0, 3.0 a 3.5 verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebe43-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="ebe43-151">Předávání typů se používá k zajištění binární kompatibilitu mezi rozhraní .NET Framework 2.0 a .NET Framework 4 F# komponenty.</span><span class="sxs-lookup"><span data-stu-id="ebe43-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="ebe43-152">Zkompilovaná forma strukturovaných řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="ebe43-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="ebe43-153">Strukturovaných řazených kolekcí členů (například `struct (x, y)`), jsou v podstatě totéž řazené kolekce členů odkazů.</span><span class="sxs-lookup"><span data-stu-id="ebe43-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="ebe43-154">Jsou zkompilovány do <xref:System.ValueTuple> typ přetížení Arita nebo počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="ebe43-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="ebe43-155">Jsou ekvivalentní [jazyka C# 7.0 řazených kolekcí členů](../../csharp/tuples.md) a [jazyka Visual Basic 2017 řazených kolekcí členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a zajistit vzájemnou funkční spolupráci obousměrně.</span><span class="sxs-lookup"><span data-stu-id="ebe43-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebe43-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebe43-156">See also</span></span>

- [<span data-ttu-id="ebe43-157">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ebe43-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ebe43-158">Typy F#</span><span class="sxs-lookup"><span data-stu-id="ebe43-158">F# Types</span></span>](fsharp-types.md)