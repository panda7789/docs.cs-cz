---
title: Volba mezi anonymními a řazenými typy řazených kolekcí členů
description: Zjistěte, kdy je vhodné zvolit mezi anonymními typy a typem řazené kolekce členů.
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9140250ad1f48501bf1d2e53a1c179e6823f19cd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100961"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>Volba mezi anonymními a řazenými typy řazených kolekcí členů

Výběr vhodného typu zahrnuje zvážení jeho použitelnosti, výkonu a kompromisů v porovnání s jinými typy. Anonymní typy jsou k dispozici od C# 3,0, zatímco obecné <xref:System.Tuple%602?displayProperty=nameWithType> typy byly zavedeny s .NET Framework 4,0. Od té doby byly nové možnosti zavedeny s podporou na úrovni jazyka, jako je například <xref:System.ValueTuple%602?displayProperty=nameWithType> – což znamená, že jako název implikuje typ hodnoty s flexibilitou anonymních typů. V tomto článku se dozvíte, kdy je vhodné zvolit jeden typ přes druhý.

## <a name="usability-and-functionality"></a>Použitelnost a funkčnost

V jazyce C# 3,0 se výrazy LINQ (Language-Integrated Query) zavedly anonymní typy. Pomocí LINQ vývojáři často projektují výsledky z dotazů do anonymních typů, které obsahují několik vybraných vlastností z objektů, se kterými pracují. Vezměte v úvahu následující příklad, který vytvoří instanci pole <xref:System.DateTime> objektů a prochází jejich projekcí do anonymního typu se dvěma vlastnostmi.

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

Anonymní typy jsou vytvořeny pomocí [`new`](../../csharp/language-reference/operators/new-operator.md) operátoru a názvy vlastností a typy jsou odvozeny z deklarace. Pokud dva nebo více inicializátorů anonymních objektů ve stejném sestavení určují sekvenci vlastností, které jsou ve stejném pořadí a mají stejné názvy a typy, kompilátor považuje objekty za instance stejného typu. Sdílejí stejné informace typu vygenerované kompilátorem.

Předchozí fragment kódu jazyka C# je anonymní typ se dvěma vlastnostmi, podobně jako následující třída C# generovaná kompilátorem:

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

Další informace najdete v tématu [anonymní typy](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). Stejné funkce existují s řazenými kolekcemi členů při projekci do dotazů LINQ, můžete vybrat vlastnosti v řazených kolekcích členů. Tyto řazené kolekce členů procházejí dotazem stejně jako anonymní typy. Nyní vezměte v úvahu následující příklad pomocí `System.Tuple<string, long>` .

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

S rozhraním <xref:System.Tuple%602?displayProperty=nameWithType> zpřístupňuje instance vlastnosti číslovaných položek, například `Item1` a `Item2` . Tyto názvy vlastností mohou ztížit pochopení záměru hodnot vlastností, protože název vlastnosti poskytuje pouze ordinální číslo. Kromě toho `System.Tuple` typy jsou odkazové `class` typy. <xref:System.ValueTuple%602?displayProperty=nameWithType>Je však `struct` typ hodnoty. Následující fragment kódu jazyka C# používá `ValueTuple<string, long>` pro projekt do. V takovém případě přiřadí použití syntaxe literálu.

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

Jazyk C# poskytuje jazykovou podporu pro řazené kolekce členů s <xref:System.ValueTuple> typem a sémantikou pro:

- [Přiřazení řazené kolekce členů](../../csharp/tuples.md#assignment-and-tuples)
- [Dekonstrukce řazené kolekce členů](../../csharp/deconstruct.md) (neomezeno na řazené kolekce členů)
- [Kontroly rovnosti řazené kolekce členů](../../csharp/tuples.md#equality-and-tuples)
- [Inicializátory řazené kolekce členů](../../csharp/tuples.md#tuple-projection-initializers)

Předchozí příklady jsou všechny funkčně ekvivalentní, ale. Existují mírné rozdíly v jejich použitelnosti a jejich základní implementace.

## <a name="tradeoffs"></a>Kompromisy

Možná budete chtít vždycky používat <xref:System.ValueTuple> <xref:System.Tuple> i anonymní typy, ale měli byste zvážit kompromisy. <xref:System.ValueTuple>Typy jsou proměnlivé, zatímco <xref:System.Tuple> jsou jen pro čtení. Anonymní typy lze použít ve stromech výrazů, zatímco řazené kolekce členů nemůžou. Následující tabulka představuje přehled některých klíčových rozdílů.

### <a name="key-differences"></a>Klíčové rozdíly

| Name                     | Modifikátor přístupu | Typ     | Název vlastního člena | Podpora dekonstrukce | Podpora stromu výrazů |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| Anonymní typy          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>Serializace

Jedním z důležitých aspektů při výběru typu je, zda bude nutné jej serializovat. Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu. Další informace naleznete v tématu [serializace](../../csharp/programming-guide/concepts/serialization/index.md). Je-li serializace důležitá, je vytvoření `class` nebo `struct` upřednostňováno pro anonymní typy nebo typy řazené kolekce členů.

## <a name="performance"></a>Výkon

Výkon mezi těmito typy závisí na scénáři. Hlavní dopad zahrnuje kompromisy mezi přidělením a kopírováním. Ve většině scénářů je dopad malý. Pokud by mohlo dojít k velkým dopadům, měla by být provedena měření, aby se rozhodnutí informovalo.

## <a name="conclusion"></a>Závěr

Jako vývojář výběr mezi řazenými kolekcemi členů a anonymními typy je vhodné zvážit několik faktorů. Obecně řečeno, pokud nepracujete se [stromy výrazů](../../csharp/expression-trees.md)a Vy jste spokojeni s syntaxí řazené kolekce členů, zvolte <xref:System.ValueTuple> , protože poskytují typ hodnoty s flexibilitou pro pojmenování vlastností. Pokud pracujete se stromy výrazů a chcete nastavit název vlastností, vyberte anonymní typy. V opačném případě použijte <xref:System.Tuple> .

## <a name="see-also"></a>Viz také

- [Anonymní typy](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Stromy výrazů](../../csharp/expression-trees.md)
- [Typy řazené kolekce členů](../../csharp/tuples.md)
- [Pokyny k návrhu typu](../design-guidelines/type.md)
