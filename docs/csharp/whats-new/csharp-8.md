---
title: Co je nového v C# 8,0 – příručka C#
description: Získejte přehled o nových funkcích dostupných v C# 8,0.
ms.date: 04/07/2020
ms.openlocfilehash: 14df381e17fe89bd862f97522c7efd814857e71e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309401"
---
# <a name="whats-new-in-c-80"></a>Co je nového v C# 8,0

C# 8,0 přidává následující funkce a vylepšení jazyka C#:

- [Členové jen pro čtení](#readonly-members)
- [Výchozí metody rozhraní](#default-interface-methods)
- [Vylepšení porovnávání vzorů](#more-patterns-in-more-places):
  - [Výrazy Switch](#switch-expressions)
  - [Vzory vlastností](#property-patterns)
  - [Vzory řazené kolekce členů](#tuple-patterns)
  - [Poziční vzory](#positional-patterns)
- [Používání deklarací](#using-declarations)
- [Statické místní funkce](#static-local-functions)
- [Struktury odkazů na jedno použití](#disposable-ref-structs)
- [Odkazové typy s možnou hodnotou null](#nullable-reference-types)
- [Asynchronní proudy](#asynchronous-streams)
- [Asynchronní na jedno použití](#asynchronous-disposable)
- [Indexy a rozsahy](#indices-and-ranges)
- [Přiřazení slučování s hodnotou null](#null-coalescing-assignment)
- [Nespravované konstruované typy](#unmanaged-constructed-types)
- [Stackalloc ve vnořených výrazech](#stackalloc-in-nested-expressions)
- [Vylepšení interpolované doslovného řetězce](#enhancement-of-interpolated-verbatim-strings)

C# 8,0 se podporuje v **.NET Core 3. x** a **.NET Standard 2,1**. Další informace najdete v tématu [Správa verzí jazyka C#](../language-reference/configure-language-version.md).

Zbývající část tohoto článku stručně popisuje tyto funkce. Kde jsou k dispozici podrobné články, jsou uvedeny odkazy na tyto kurzy a přehledy. Pomocí globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí `dotnet try` :

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp8* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="readonly-members"></a>Členové jen pro čtení

Můžete použít `readonly` modifikátor u členů struktury. Indikuje, že člen nemění stav. Je lépe podrobnější než použití `readonly` modifikátoru na `struct` deklaraci.  Vezměte v úvahu následující proměnlivou strukturu:

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

Podobně jako u většiny struktur `ToString()` Metoda nemění stav. Můžete určit, že přidáním `readonly` modifikátoru k deklaraci `ToString()` :

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Předchozí změna vygeneruje upozornění kompilátoru, protože `ToString` přistupuje k `Distance` vlastnosti, která není označena jako `readonly` :

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilátor vás upozorní, když potřebuje vytvořit obrannou linií kopii.  `Distance`Vlastnost nemění stav, takže můžete toto upozornění opravit přidáním `readonly` modifikátoru k deklaraci:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Všimněte si, že `readonly` Modifikátor je nutný pro vlastnost, která je jen pro čtení. Kompilátor nepředpokládá `get` , že přistupující objekty nemění stav. musíte deklarovat `readonly` explicitně. Automaticky implementované vlastnosti představují výjimku. Kompilátor bude zacházet se všemi automaticky implementovanými metodami getter `readonly` , takže zde není nutné přidávat `readonly` modifikátor do `X` `Y` vlastností a.

Kompilátor vynutil pravidlo, že `readonly` Členové nemění stav. Následující metoda nebude zkompilována, dokud neodeberete `readonly` Modifikátor:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Tato funkce umožňuje určit záměr návrhu, aby ho kompilátor mohl vynutit a na základě tohoto záměru provádět optimalizace.

Další informace naleznete v oddílu [ `readonly` instance členů](../language-reference/builtin-types/struct.md#readonly-instance-members) článku [typy struktury](../language-reference/builtin-types/struct.md) .

## <a name="default-interface-methods"></a>Výchozí metody rozhraní

Nyní můžete přidat členy do rozhraní a poskytnout implementaci pro tyto členy. Tato funkce jazyka umožňuje autorům rozhraní API přidávat metody do rozhraní v pozdějších verzích bez narušení zdrojové nebo binární kompatibility se stávajícími implementacemi tohoto rozhraní. Stávající implementace *dědí* výchozí implementaci. Tato funkce také umožňuje jazyku C# spolupracovat s rozhraními API, která cílí na Android nebo SWIFT, což podporuje podobné funkce. Výchozí metody rozhraní také umožňují scénáře podobně jako funkce jazyka "vlastnosti".

Výchozí metody rozhraní ovlivňují mnoho scénářů a prvků jazyka. Náš první kurz popisuje [aktualizaci rozhraní s výchozími implementacemi](../tutorials/default-interface-methods-versions.md). Další kurzy a referenční aktualizace jsou k disčase pro obecné vydání.

## <a name="more-patterns-in-more-places"></a>Další vzory na více místech

**Porovnávání vzorů** poskytuje nástrojům poskytování funkcionality závislé na tvaru v rámci souvisejících, ale různých druhů dat. C# 7,0 představil Syntax pro vzory typů a konstantní vzorce pomocí [`is`](../language-reference/keywords/is.md) výrazu a [`switch`](../language-reference/keywords/switch.md) příkazu. Tyto funkce představovaly první nezávazné kroky směrem k podpoře programovacích paradigmat, ve kterých jsou data a funkce živě oddělené. Vzhledem k tomu, že se odvětví pohybuje k většímu mikroslužbám a dalším cloudovým architekturám, jsou potřeba jiné jazykové nástroje.

C# 8,0 rozšiřuje tento slovník, takže můžete použít více výrazů vzoru ve více místech kódu. Tyto funkce zvažte, když jsou vaše data a funkce oddělené. Zvažte porovnávání vzorů, pokud jsou algoritmy závislé na jiném faktě, než je typ modulu runtime objektu. Tyto techniky poskytují jiný způsob, jak vyjádřit návrhy.

Kromě nových vzorů na nových místech C# 8,0 přidává **rekurzivní vzory**. Výsledek jakéhokoli výrazu vzoru je výraz. Rekurzivní vzorek je pouze výraz vzoru aplikovaný na výstup jiného výrazu vzoru.

### <a name="switch-expressions"></a>Výrazy Switch

[`switch`](../language-reference/keywords/switch.md)Příkaz často v každém z jeho bloků vytvoří hodnotu `case` . **Výrazy Switch** umožňují použít stručnější syntaxi výrazů. K dispozici jsou méně opakující se `case` a `break` klíčová slova a méně složené závorky.  Podívejte se například na následující výčet, který obsahuje seznam barev duha:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

Pokud vaše aplikace definovala `RGBColor` typ, který je vytvořen z rozhraní `R` , `G` a `B` , mohli byste převést `Rainbow` hodnotu na její hodnoty RGB pomocí následující metody, která obsahuje výraz Switch:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Tady je několik vylepšení syntaxe:

- Proměnná se nachází před `switch` klíčovým slovem. V jiném pořadí je vizuálně snadné odlišit výraz přepínače od příkazu switch.
- `case`Prvky a `:` jsou nahrazeny `=>` . Je výstižnější a intuitivní.
- `default`Případ je nahrazen `_` zahozením.
- Tělo jsou výrazy, nikoli příkazy.

Kontrast se stejným kódem pomocí `switch` příkazu Classic:

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>Vzory vlastností

**Vzor vlastnosti** umožňuje porovnávat vlastnosti objektu, který je zkontrolován. Vezměte v úvahu web elektronického obchodování, který musí počítat DPH na základě adresy kupujícího. Tento výpočet není základní zodpovědností `Address` třídy. Změní se v průběhu času, nejspíš častěji než změny formátu adresy. Částka DPH závisí na `State` vlastnosti adresy. Následující metoda používá vzorek vlastností k výpočtu DPH z adresy a ceny:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Porovnávání vzorů vytvoří stručnou syntaxi pro vyjádření tohoto algoritmu.

### <a name="tuple-patterns"></a>Vzory řazené kolekce členů

Některé algoritmy závisí na více vstupech. **Vzorce řazené kolekce členů** umožňují přepínat na základě více hodnot vyjádřených jako [řazené kolekce členů](../language-reference/builtin-types/value-tuples.md).  Následující kód ukazuje výraz přepínače pro herní *rock, papír, nůžky*:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

Zprávy indikují vítěze. Případ zahození představuje tři kombinace pro vazby nebo jiné textové vstupy.

### <a name="positional-patterns"></a>Poziční vzory

Některé typy obsahují `Deconstruct` metodu, která dekonstruuje své vlastnosti do diskrétních proměnných. Když `Deconstruct` je metoda přístupná, můžete použít **poziční vzory** pro kontrolu vlastností objektu a použít tyto vlastnosti pro vzor.  Vezměte v úvahu následující `Point` třídu, která obsahuje `Deconstruct` metodu pro vytvoření diskrétních proměnných pro `X` a `Y` :

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

Navíc zvažte následující výčet, který představuje různé pozice kvadrantu:

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

Následující metoda používá **poziční vzor** k extrakci hodnot `x` a `y` . Pak pomocí `when` klauzule určíte `Quadrant` bod:

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

Vzor zahození v předchozím přepínači odpovídá, pokud buď `x` nebo `y` je 0, ale ne obojí. Výraz přepínače musí buď vytvořit hodnotu, nebo vyvolat výjimku. Pokud žádný z případů neodpovídá, výraz přepínače vyvolá výjimku. Kompilátor vygeneruje upozornění, pokud nepokrýváte všechny možné případy ve výrazu přepínače.

Techniky porovnávání vzorů můžete prozkoumat v tomto [pokročilém kurzu o porovnávání vzorů](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Používání deklarací

**Deklarace using** je deklarace proměnné před `using` klíčovým slovem. Dává kompilátoru pokyn, že proměnná, která má být deklarována, by měla být uvolněna na konci ohraničujícího oboru. Zvažte například následující kód, který zapisuje textový soubor:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

V předchozím příkladu je soubor zlikvidován při dosažení uzavírací závorky pro metodu. To je konec oboru, ve kterém `file` je deklarováno. Předchozí kód je ekvivalentní následujícímu kódu, který používá [příkaz Classic using](../language-reference/keywords/using-statement.md):

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

V předchozím příkladu je soubor zlikvidován při dosažení uzavírací závorky přidružené k `using` příkazu.

V obou případech kompilátor vygeneruje volání `Dispose()` . Kompilátor vygeneruje chybu, pokud výraz v `using` příkazu není jednorázově.

## <a name="static-local-functions"></a>Statické místní funkce

Nyní můžete přidat `static` Modifikátor k místním funkcím, aby se zajistilo, že lokální funkce nebude zachytit (odkaz) jakékoli proměnné z ohraničujícího oboru. Tím se vygeneruje `CS8421` "statická místní funkce nemůže obsahovat odkaz na \<variable> ."

Vezměte v úvahu následující kód. Místní funkce `LocalFunction` přistupuje k proměnné `y` deklarované v ohraničujícím oboru (metoda `M` ). Proto `LocalFunction` nelze deklarovat s `static` modifikátorem:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Následující kód obsahuje statickou místní funkci. Může být statický, protože nemá přístup k žádným proměnným v ohraničujícím oboru:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Struktury odkazů na jedno použití

`struct`Deklarace s `ref` modifikátorem nesmí implementovat žádná rozhraní, a proto nemůže implementovat <xref:System.IDisposable> . Proto aby bylo možné `ref struct` Odstranit, musí mít přístupnou `void Dispose()` metodu. Tato funkce se vztahuje také na `readonly ref struct` deklarace.

## <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

V kontextu anotace s možnou hodnotou null je jakákoli proměnná typu odkazu považována za **typ odkazu**, který není null. Pokud chcete označit, že proměnná může mít hodnotu null, je nutné připojit název typu `?` k deklaraci proměnné jako **typ odkazu s možnou hodnotou null**.

Pro nehodnotový odkazový typ kompilátor používá analýzu toků k zajištění, že lokální proměnné jsou inicializovány na hodnotu, která není null, je-li deklarována. Pole musí být inicializována během konstrukce. Kompilátor vygeneruje upozornění, pokud proměnná není nastavena voláním žádné z dostupných konstruktorů nebo inicializátoru. Kromě toho nemůžete přiřadit typy odkazů, které mohou mít hodnotu null.

Typy odkazů s možnou hodnotou null nejsou kontrolovány, aby se zajistilo, že nejsou přiřazeny nebo inicializovány Kompilátor však používá analýzu toků k zajištění toho, aby byla jakákoli proměnná typu odkazu s možnou hodnotou null zkontrolována před tím, než bude k dispozici nebo přiřazena k neprázdnému typu odkazu.

Další informace o této funkci najdete v přehledu [typů odkazů s možnou hodnotou null](../nullable-references.md). Zkuste to sami v nové aplikaci v tomto [kurzu odkazové typy s možnou hodnotou null](../tutorials/nullable-reference-types.md). Přečtěte si o krocích k migraci existujícího základu kódu, aby bylo možné používat v [migraci aplikace na použití typů odkazů s možnou hodnotou null v kurzu](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Asynchronní proudy

Počínaje jazykem C# 8,0 můžete vytvářet a spotřebovávat streamy asynchronně. Metoda, která vrací asynchronní datový proud má tři vlastnosti:

1. Je deklarována s `async` modifikátorem.
1. Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601> .
1. Metoda obsahuje `yield return` příkazy pro vrácení po sobě jdoucích prvků v asynchronním datovém proudu.

Spotřebovávání asynchronního datového proudu vyžaduje, abyste `await` před `foreach` klíčovým slovem při vytváření výčtu prvků v datovém proudu přidali klíčové slovo. Přidání `await` klíčového slova vyžaduje metodu, která vytvoří výčet asynchronního datového proudu, který má být deklarován s `async` modifikátorem a vrátí typ povolený pro `async` metodu. Obvykle to znamená, že vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> . Může to být také <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601> . Metoda může spotřebovávat a vytvořit asynchronní datový proud, což znamená, že by vrátilo <xref:System.Collections.Generic.IAsyncEnumerable%601> . Následující kód vygeneruje sekvenci od 0 do 19, čekání 100 MS mezi vygenerováním každého čísla:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Vyčíslení sekvence pomocí `await foreach` příkazu:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Asynchronní streamy si můžete vyzkoušet sami v našem kurzu [vytváření a využívání asynchronních datových proudů](../tutorials/generate-consume-asynchronous-stream.md). Ve výchozím nastavení jsou prvky Stream zpracovávány v zachyceném kontextu. Pokud chcete zakázat zachycování kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zaznamenávání aktuálního kontextu naleznete v článku o [využívání asynchronního vzoru založeného na úlohách](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="asynchronous-disposable"></a>Asynchronní na jedno použití

Počínaje jazykem C# 8,0 podporuje jazyk asynchronní typy v případě, které implementují <xref:System.IAsyncDisposable?displayProperty=nameWithType> rozhraní. Použijete `await using` příkaz pro práci s asynchronním objektem na jedno. Další informace najdete v článku [implementace metody DisposeAsync](../../standard/garbage-collection/implementing-disposeasync.md) .

## <a name="indices-and-ranges"></a>Indexy a rozsahy

Indexy a rozsahy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.

Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:

- <xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.
- Index z operátoru End `^` , který určuje, že index je relativní ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.
- Operátor rozsahu `..` , který určuje začátek a konec rozsahu jako jeho operandy.

Pojďme začít s pravidly pro indexy. Zvažte pole `sequence` . `0`Index je stejný jako `sequence[0]` . `^0`Index je stejný jako `sequence[sequence.Length]` . Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]` . Pro jakékoli číslo `n` `^n` je index stejný jako `sequence.Length - n` .

Rozsah Určuje *začátek* a *konec* rozsahu. Začátek rozsahu je včetně, ale konec rozsahu je exkluzivní, což znamená, že *začátek* je zahrnutý v rozsahu, ale *konec* není zahrnutý v rozsahu. Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah.

Podívejme se na několik příkladů. Vezměte v úvahu následující pole s poznámkou s jeho indexem od začátku do konce:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Poslední slovo můžete načíst s `^1` indexem:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Následující kód vytvoří dílčí rozsah s slovy "quick", "brown" a "fox". Zahrnuje vše mezi `words[1]` `words[3]` . Element `words[4]` není v rozsahu.

```csharp
var quickBrownFox = words[1..4];
```

Následující kód vytvoří dílčí rozsah s "lazy" a "dog". Zahrnuje vše mezi `words[^2]` a `words[^1]` . Koncový index `words[^0]` není zahrnutý:

```csharp
var lazyDog = words[^2..^0];
```

V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Rozsahy můžete deklarovat také jako proměnné:

```csharp
Range phrase = 1..4;
```

Rozsah lze použít v rámci `[` `]` znaků a:

```csharp
var text = words[phrase];
```

Pouze pole podporují indexy a rozsahy. Můžete také použít indexy a rozsahy s [řetězcem](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> . Další informace najdete v tématu [Podpora typů pro indexy a rozsahy](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Můžete prozkoumat další informace o indexech a oblastech v kurzu týkající se [indexů a rozsahů](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Přiřazení slučování s hodnotou null

Jazyk C# 8,0 zavádí operátor přiřazení s hodnotou null `??=` . Operátor můžete použít `??=` k přiřazení hodnoty jeho pravého operandu jeho levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` .

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Další informace najdete v tématu [?? a?? =](../language-reference/operators/null-coalescing-operator.md) – článek o operátorech

## <a name="unmanaged-constructed-types"></a>Nespravované konstruované typy

V jazyce C# 7,3 a starším je konstruovaný typ (typ, který obsahuje alespoň jeden argument typu) [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md). Počínaje jazykem C# 8,0 je typ konstruované hodnoty nespravovaný, pokud obsahuje pouze pole nespravovaných typů.

Například s ohledem na následující definice obecného `Coords<T>` typu:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>`typ je nespravovaný typ v jazyce C# 8,0 a novějším. Podobně jako u jakéhokoli nespravovaného typu můžete vytvořit ukazatel na proměnnou tohoto typu nebo [přidělit blok paměti v zásobníku](../language-reference/operators/stackalloc.md) pro instance tohoto typu:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Další informace naleznete v tématu [nespravované typy](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc ve vnořených výrazech

Počínaje jazykem C# 8,0, pokud výsledek [stackalloc](../language-reference/operators/stackalloc.md) výrazu je <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> typu nebo, můžete použít `stackalloc` výraz v jiných výrazech:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Vylepšení interpolované doslovného řetězce

Pořadí `$` a `@` tokeny v [interpolované](../language-reference/tokens/interpolated.md) doslovném řetězci mohou být libovolné: `$@"..."` a `@$"..."` jsou platné interpolované řetězce. V dřívějších verzích C# se `$` token musí vyskytovat před `@` tokenem.
