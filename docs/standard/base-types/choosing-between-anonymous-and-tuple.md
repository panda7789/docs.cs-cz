---
title: Volba mezi anonymními a řazenými typy řazených kolekcí členů
description: Zjistěte, kdy je vhodné zvolit mezi anonymními typy a typem řazené kolekce členů.
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 2f927b59d7206dd0f405c11529f93b56a1c778a0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052075"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="82c7d-103">Volba mezi anonymními a řazenými typy řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="82c7d-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="82c7d-104">Výběr vhodného typu zahrnuje zvážení jeho použitelnosti, výkonu a kompromisů v porovnání s jinými typy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="82c7d-105">Anonymní typy jsou k dispozici od C# 3,0, zatímco obecné <xref:System.Tuple%602?displayProperty=nameWithType> typy byly zavedeny s .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="82c7d-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="82c7d-106">Od té doby byly nové možnosti zavedeny s podporou na úrovni jazyka, jako je například <xref:System.ValueTuple%602?displayProperty=nameWithType> – což znamená, že jako název implikuje typ hodnoty s flexibilitou anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="82c7d-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="82c7d-107">V tomto článku se dozvíte, kdy je vhodné zvolit jeden typ přes druhý.</span><span class="sxs-lookup"><span data-stu-id="82c7d-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="82c7d-108">Použitelnost a funkčnost</span><span class="sxs-lookup"><span data-stu-id="82c7d-108">Usability and functionality</span></span>

<span data-ttu-id="82c7d-109">V jazyce C# 3,0 se výrazy LINQ (Language-Integrated Query) zavedly anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="82c7d-110">Pomocí LINQ vývojáři často projektují výsledky z dotazů do anonymních typů, které obsahují několik vybraných vlastností z objektů, se kterými pracují.</span><span class="sxs-lookup"><span data-stu-id="82c7d-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="82c7d-111">Vezměte v úvahu následující příklad, který vytvoří instanci pole <xref:System.DateTime> objektů a prochází jejich projekcí do anonymního typu se dvěma vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="82c7d-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="82c7d-112">Anonymní typy jsou vytvořeny pomocí [`new`](../../csharp/language-reference/operators/new-operator.md) operátoru a názvy vlastností a typy jsou odvozeny z deklarace.</span><span class="sxs-lookup"><span data-stu-id="82c7d-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="82c7d-113">Pokud dva nebo více inicializátorů anonymních objektů ve stejném sestavení určují sekvenci vlastností, které jsou ve stejném pořadí a mají stejné názvy a typy, kompilátor považuje objekty za instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="82c7d-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="82c7d-114">Sdílejí stejné informace typu vygenerované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="82c7d-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="82c7d-115">Předchozí fragment kódu jazyka C# je anonymní typ se dvěma vlastnostmi, podobně jako následující třída C# generovaná kompilátorem:</span><span class="sxs-lookup"><span data-stu-id="82c7d-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="82c7d-116">Další informace najdete v tématu [anonymní typy](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="82c7d-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="82c7d-117">Stejné funkce existují s řazenými kolekcemi členů při projekci do dotazů LINQ, můžete vybrat vlastnosti v řazených kolekcích členů.</span><span class="sxs-lookup"><span data-stu-id="82c7d-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="82c7d-118">Tyto řazené kolekce členů procházejí dotazem stejně jako anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="82c7d-119">Nyní vezměte v úvahu následující příklad pomocí `System.Tuple<string, long>` .</span><span class="sxs-lookup"><span data-stu-id="82c7d-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="82c7d-120">S rozhraním <xref:System.Tuple%602?displayProperty=nameWithType> zpřístupňuje instance vlastnosti číslovaných položek, například `Item1` a `Item2` .</span><span class="sxs-lookup"><span data-stu-id="82c7d-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="82c7d-121">Tyto názvy vlastností mohou ztížit pochopení záměru hodnot vlastností, protože název vlastnosti poskytuje pouze ordinální číslo.</span><span class="sxs-lookup"><span data-stu-id="82c7d-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="82c7d-122">Kromě toho `System.Tuple` typy jsou odkazové `class` typy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="82c7d-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>Je však `struct` typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="82c7d-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="82c7d-124">Následující fragment kódu jazyka C# používá `ValueTuple<string, long>` pro projekt do.</span><span class="sxs-lookup"><span data-stu-id="82c7d-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="82c7d-125">V takovém případě přiřadí použití syntaxe literálu.</span><span class="sxs-lookup"><span data-stu-id="82c7d-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="82c7d-126">Jazyk C# poskytuje jazykovou podporu pro řazené kolekce členů s <xref:System.ValueTuple> typem a sémantikou pro:</span><span class="sxs-lookup"><span data-stu-id="82c7d-126">C# provides language support of tuples with the <xref:System.ValueTuple> type, and semantics for:</span></span>

- [<span data-ttu-id="82c7d-127">Přiřazení řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="82c7d-127">Tuple assignment</span></span>](../../csharp/tuples.md#assignment-and-tuples)
- <span data-ttu-id="82c7d-128">[Dekonstrukce řazené kolekce členů](../../csharp/deconstruct.md) (neomezeno na řazené kolekce členů)</span><span class="sxs-lookup"><span data-stu-id="82c7d-128">[Tuple deconstruction](../../csharp/deconstruct.md) (not limited to tuples)</span></span>
- [<span data-ttu-id="82c7d-129">Kontroly rovnosti řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="82c7d-129">Tuple equality checks</span></span>](../../csharp/tuples.md#equality-and-tuples)
- [<span data-ttu-id="82c7d-130">Inicializátory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="82c7d-130">Tuple projection initializers</span></span>](../../csharp/tuples.md#tuple-projection-initializers)

<span data-ttu-id="82c7d-131">Předchozí příklady jsou všechny funkčně ekvivalentní, ale. Existují mírné rozdíly v jejich použitelnosti a jejich základní implementace.</span><span class="sxs-lookup"><span data-stu-id="82c7d-131">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="82c7d-132">Kompromisy</span><span class="sxs-lookup"><span data-stu-id="82c7d-132">Tradeoffs</span></span>

<span data-ttu-id="82c7d-133">Možná budete chtít vždycky používat <xref:System.ValueTuple> <xref:System.Tuple> i anonymní typy, ale měli byste zvážit kompromisy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-133">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="82c7d-134"><xref:System.ValueTuple>Typy jsou proměnlivé, zatímco <xref:System.Tuple> jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="82c7d-134">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="82c7d-135">Anonymní typy lze použít ve stromech výrazů, zatímco řazené kolekce členů nemůžou.</span><span class="sxs-lookup"><span data-stu-id="82c7d-135">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="82c7d-136">Následující tabulka představuje přehled některých klíčových rozdílů.</span><span class="sxs-lookup"><span data-stu-id="82c7d-136">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="82c7d-137">Klíčové rozdíly</span><span class="sxs-lookup"><span data-stu-id="82c7d-137">Key differences</span></span>

| <span data-ttu-id="82c7d-138">Name</span><span class="sxs-lookup"><span data-stu-id="82c7d-138">Name</span></span>                     | <span data-ttu-id="82c7d-139">Modifikátor přístupu</span><span class="sxs-lookup"><span data-stu-id="82c7d-139">Access modifier</span></span> | <span data-ttu-id="82c7d-140">Typ</span><span class="sxs-lookup"><span data-stu-id="82c7d-140">Type</span></span>     | <span data-ttu-id="82c7d-141">Název vlastního člena</span><span class="sxs-lookup"><span data-stu-id="82c7d-141">Custom member name</span></span> | <span data-ttu-id="82c7d-142">Podpora dekonstrukce</span><span class="sxs-lookup"><span data-stu-id="82c7d-142">Deconstruction support</span></span> | <span data-ttu-id="82c7d-143">Podpora stromu výrazů</span><span class="sxs-lookup"><span data-stu-id="82c7d-143">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="82c7d-144">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="82c7d-144">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="82c7d-145">✔️</span><span class="sxs-lookup"><span data-stu-id="82c7d-145">✔️</span></span>                   | ❌                     | <span data-ttu-id="82c7d-146">✔️</span><span class="sxs-lookup"><span data-stu-id="82c7d-146">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="82c7d-147">✔️</span><span class="sxs-lookup"><span data-stu-id="82c7d-147">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="82c7d-148">✔️</span><span class="sxs-lookup"><span data-stu-id="82c7d-148">✔️</span></span>                   | <span data-ttu-id="82c7d-149">✔️</span><span class="sxs-lookup"><span data-stu-id="82c7d-149">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="82c7d-150">Serializace</span><span class="sxs-lookup"><span data-stu-id="82c7d-150">Serialization</span></span>

<span data-ttu-id="82c7d-151">Jedním z důležitých aspektů při výběru typu je, zda bude nutné jej serializovat.</span><span class="sxs-lookup"><span data-stu-id="82c7d-151">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="82c7d-152">Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu.</span><span class="sxs-lookup"><span data-stu-id="82c7d-152">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="82c7d-153">Další informace naleznete v tématu [serializace](../../csharp/programming-guide/concepts/serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="82c7d-153">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="82c7d-154">Je-li serializace důležitá, je vytvoření `class` nebo `struct` upřednostňováno pro anonymní typy nebo typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="82c7d-154">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="82c7d-155">Výkon</span><span class="sxs-lookup"><span data-stu-id="82c7d-155">Performance</span></span>

<span data-ttu-id="82c7d-156">Výkon mezi těmito typy závisí na scénáři.</span><span class="sxs-lookup"><span data-stu-id="82c7d-156">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="82c7d-157">Hlavní dopad zahrnuje kompromisy mezi přidělením a kopírováním.</span><span class="sxs-lookup"><span data-stu-id="82c7d-157">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="82c7d-158">Ve většině scénářů je dopad malý.</span><span class="sxs-lookup"><span data-stu-id="82c7d-158">In most scenarios, the impact is small.</span></span> <span data-ttu-id="82c7d-159">Pokud by mohlo dojít k velkým dopadům, měla by být provedena měření, aby se rozhodnutí informovalo.</span><span class="sxs-lookup"><span data-stu-id="82c7d-159">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="82c7d-160">Závěr</span><span class="sxs-lookup"><span data-stu-id="82c7d-160">Conclusion</span></span>

<span data-ttu-id="82c7d-161">Jako vývojář výběr mezi řazenými kolekcemi členů a anonymními typy je vhodné zvážit několik faktorů.</span><span class="sxs-lookup"><span data-stu-id="82c7d-161">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="82c7d-162">Obecně řečeno, pokud nepracujete se [stromy výrazů](../../csharp/expression-trees.md)a Vy jste spokojeni s syntaxí řazené kolekce členů, zvolte <xref:System.ValueTuple> , protože poskytují typ hodnoty s flexibilitou pro pojmenování vlastností.</span><span class="sxs-lookup"><span data-stu-id="82c7d-162">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="82c7d-163">Pokud pracujete se stromy výrazů a chcete nastavit název vlastností, vyberte anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="82c7d-163">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="82c7d-164">V opačném případě použijte <xref:System.Tuple> .</span><span class="sxs-lookup"><span data-stu-id="82c7d-164">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="82c7d-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="82c7d-165">See also</span></span>

- [<span data-ttu-id="82c7d-166">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="82c7d-166">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="82c7d-167">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="82c7d-167">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="82c7d-168">Typy řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="82c7d-168">Tuple types</span></span>](../../csharp/tuples.md)
- [<span data-ttu-id="82c7d-169">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="82c7d-169">Type design guidelines</span></span>](../design-guidelines/type.md)
