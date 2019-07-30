---
title: N-tice
description: Přečtěte si F# o řazené kolekci členů, seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630236"
---
# <a name="tuples"></a><span data-ttu-id="30b2b-103">N-tice</span><span class="sxs-lookup"><span data-stu-id="30b2b-103">Tuples</span></span>

<span data-ttu-id="30b2b-104">*Řazená kolekce členů* je seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.</span><span class="sxs-lookup"><span data-stu-id="30b2b-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="30b2b-105">Řazené kolekce členů můžou být buď odkazy na typy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="30b2b-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="30b2b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30b2b-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="30b2b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30b2b-107">Remarks</span></span>

<span data-ttu-id="30b2b-108">Každý *prvek* v předchozí syntaxi může být libovolný platný F# výraz.</span><span class="sxs-lookup"><span data-stu-id="30b2b-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="30b2b-109">Příklady</span><span class="sxs-lookup"><span data-stu-id="30b2b-109">Examples</span></span>

<span data-ttu-id="30b2b-110">Příklady řazených kolekcí členů obsahují páry, tři a tak dále, stejného nebo různých typů.</span><span class="sxs-lookup"><span data-stu-id="30b2b-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="30b2b-111">Některé příklady jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="30b2b-112">Získání individuálních hodnot</span><span class="sxs-lookup"><span data-stu-id="30b2b-112">Obtaining Individual Values</span></span>

<span data-ttu-id="30b2b-113">Můžete použít porovnávání vzorů k přístupu a přiřazování názvů prvků řazené kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="30b2b-114">Můžete také dekonstruovat řazenou kolekci členů prostřednictvím porovnávání vzorů mimo `match` výraz prostřednictvím `let` vazby:</span><span class="sxs-lookup"><span data-stu-id="30b2b-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="30b2b-115">Nebo můžete porovnávání vzorů u řazených kolekcí členů, jako jsou vstupy funkcí:</span><span class="sxs-lookup"><span data-stu-id="30b2b-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="30b2b-116">Pokud potřebujete pouze jeden prvek řazené kolekce členů, zástupný znak (podtržítko) lze použít k zamezení vytváření nového názvu pro hodnotu, kterou nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="30b2b-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="30b2b-117">Kopírování elementů z referenční řazené kolekce členů do struktury řazené kolekce členů je také jednoduché:</span><span class="sxs-lookup"><span data-stu-id="30b2b-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="30b2b-118">Funkce `fst` a`snd` (pouze řazené kolekce členů) vrací první a druhý prvek řazené kolekce členů v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="30b2b-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="30b2b-119">Neexistuje žádná předdefinovaná funkce, která vrací třetí prvek trojnásobku, ale lze ji snadno napsat následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="30b2b-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="30b2b-120">Obecně je vhodnější použít porovnávání vzorů pro přístup k jednotlivým prvkům řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="30b2b-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="30b2b-121">Použití řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="30b2b-121">Using Tuples</span></span>

<span data-ttu-id="30b2b-122">Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="30b2b-123">Tento příklad provádí celočíselné dělení a vrací zaoblený výsledek operace jako první člen dvojice řazené kolekce členů a zbytek jako druhý člen dvojice.</span><span class="sxs-lookup"><span data-stu-id="30b2b-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="30b2b-124">Řazené kolekce členů lze také použít jako argumenty funkce, pokud chcete zabránit implicitním procesu curryfikace argumentů funkce, které jsou odvozeny pomocí obvyklé syntaxe funkce.</span><span class="sxs-lookup"><span data-stu-id="30b2b-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="30b2b-125">Obvyklá syntaxe pro definování funkce `let sum a b = a + b` umožňuje definovat funkci, která je částečnou aplikací prvního argumentu funkce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="30b2b-126">Použití řazené kolekce členů jako parametru zakáže procesu curryfikace.</span><span class="sxs-lookup"><span data-stu-id="30b2b-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="30b2b-127">Další informace naleznete v části "částečné použití argumentů" ve [funkcích Functions](./functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="30b2b-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="30b2b-128">Názvy typů řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="30b2b-128">Names of Tuple Types</span></span>

<span data-ttu-id="30b2b-129">Když napíšete název typu, který je řazené kolekce členů, použijete `*` symbol k oddělení prvků.</span><span class="sxs-lookup"><span data-stu-id="30b2b-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="30b2b-130">V případě řazené kolekce členů, `int`která se `float`skládá z, `string` `(10, 10.0, "ten")`a, jako je typ, by byl zápis typu následující.</span><span class="sxs-lookup"><span data-stu-id="30b2b-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="30b2b-131">Spolupráce s C# řazenými kolekcemi členů</span><span class="sxs-lookup"><span data-stu-id="30b2b-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="30b2b-132">C#7,0 zavedl do jazyka řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="30b2b-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="30b2b-133">Řazené kolekce C# členů v jsou struktury a jsou ekvivalentní k řazeným kolekcím F#členů struktury v.</span><span class="sxs-lookup"><span data-stu-id="30b2b-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="30b2b-134">Pokud potřebujete pracovat s nástrojem C#, je nutné použít řazené kolekce členů struktury.</span><span class="sxs-lookup"><span data-stu-id="30b2b-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="30b2b-135">To je snadné.</span><span class="sxs-lookup"><span data-stu-id="30b2b-135">This is easy to do.</span></span>  <span data-ttu-id="30b2b-136">Představte si například, že musíte předat řazenou kolekci C# členů ke třídě a pak využít svůj výsledek, což je také řazená kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="30b2b-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="30b2b-137">Ve vašem F# kódu pak můžete předat řazenou kolekci členů struktury jako parametr a využít výsledek jako řazenou kolekci členů struktury.</span><span class="sxs-lookup"><span data-stu-id="30b2b-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="30b2b-138">Převod mezi řazenými kolekcemi členů a řazenými kolekcemi členů struktury</span><span class="sxs-lookup"><span data-stu-id="30b2b-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="30b2b-139">Vzhledem k tomu, že řazené kolekce členů a řazené kolekce členů mají zcela odlišnou základní reprezentaci, nejsou implicitně převoditelné.</span><span class="sxs-lookup"><span data-stu-id="30b2b-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="30b2b-140">To znamená, že kód jako následující nebude zkompilován:</span><span class="sxs-lookup"><span data-stu-id="30b2b-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="30b2b-141">Je nutné porovnávání vzorů u jedné řazené kolekce členů a vytvořit druhé s částmi prvků.</span><span class="sxs-lookup"><span data-stu-id="30b2b-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="30b2b-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30b2b-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="30b2b-143">Kompilovaná forma řazených kolekcí členů odkazu</span><span class="sxs-lookup"><span data-stu-id="30b2b-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="30b2b-144">Tato část vysvětluje formu řazených kolekcí členů při jejich kompilaci.</span><span class="sxs-lookup"><span data-stu-id="30b2b-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="30b2b-145">Pokud necílíte .NET Framework 3,5 nebo nižší, nemusíte informace číst.</span><span class="sxs-lookup"><span data-stu-id="30b2b-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="30b2b-146">Řazené kolekce členů jsou kompilovány do objektů jednoho z několika obecných typů, `System.Tuple`všech pojmenovaných, které jsou přetíženy na aritou nebo podle počtu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="30b2b-147">Typy řazené kolekce členů se zobrazí v tomto formuláři, když je zobrazíte z C# jiného jazyka, jako je například nebo Visual Basic, nebo pokud používáte nástroj, který F# nemá informace o konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="30b2b-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="30b2b-148">`Tuple` Typy byly představeny v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="30b2b-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="30b2b-149">Pokud cílíte na starší verzi .NET Framework, kompilátor používá verze [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2,0 F# základní knihovny.</span><span class="sxs-lookup"><span data-stu-id="30b2b-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="30b2b-150">Typy v této knihovně jsou používány pouze pro aplikace, které cílí na verze .NET Framework 2,0, 3,0 a 3,5.</span><span class="sxs-lookup"><span data-stu-id="30b2b-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="30b2b-151">Přesměrování typu se používá k zajištění binární kompatibility mezi .NET Framework 2,0 a .NET Framework 4 F# komponentami.</span><span class="sxs-lookup"><span data-stu-id="30b2b-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="30b2b-152">Kompilovaná forma řazených kolekcí členů struktury</span><span class="sxs-lookup"><span data-stu-id="30b2b-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="30b2b-153">Řazené kolekce členů struktury (například `struct (x, y)`) jsou zásadním rozdílem od řazených kolekcí členů odkazu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="30b2b-154">Jsou zkompilovány do <xref:System.ValueTuple> typu, přetíženy pomocí aritou nebo počtu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="30b2b-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="30b2b-155">Jsou ekvivalentní k [ C# 7,0 řazených kolekcí členů](../../csharp/tuples.md) a [Visual Basic 2017 řazené kolekce členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a spolupracují obousměrně.</span><span class="sxs-lookup"><span data-stu-id="30b2b-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="30b2b-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30b2b-156">See also</span></span>

- [<span data-ttu-id="30b2b-157">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="30b2b-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="30b2b-158">Typy F#</span><span class="sxs-lookup"><span data-stu-id="30b2b-158">F# Types</span></span>](fsharp-types.md)
