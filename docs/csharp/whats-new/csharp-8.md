---
title: Co je nového v C# 8.0 - C# Guide
description: Získejte přehled o nových funkcích dostupných v c# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: 1a005750751129969f2d1e9caf156330dbe61cb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989204"
---
# <a name="whats-new-in-c-80"></a>Co je nového v C# 8.0

C# 8.0 přidává do jazyka C# následující funkce a vylepšení:

- [Členové pouze pro čtení](#readonly-members)
- [Výchozí metody rozhraní](#default-interface-methods)
- [Vylepšení porovnávání vzorů](#more-patterns-in-more-places):
  - [Přepnutí výrazů](#switch-expressions)
  - [Vzory vlastností](#property-patterns)
  - [Řazené kolekce členů](#tuple-patterns)
  - [Poziční vzory](#positional-patterns)
- [Použití deklarací](#using-declarations)
- [Statické místní funkce](#static-local-functions)
- [Jednorázové ref struktury](#disposable-ref-structs)
- [Odkazové typy s možnou hodnotou null](#nullable-reference-types)
- [Asynchronní datové proudy](#asynchronous-streams)
- [Asynchronní jednorázové](#asynchronous-disposable)
- [Indexy a rozsahy](#indices-and-ranges)
- [Přiřazení null-coalescing](#null-coalescing-assignment)
- [Nespravované konstruované typy](#unmanaged-constructed-types)
- [Stackalloc ve vnořených výrazech](#stackalloc-in-nested-expressions)
- [Vylepšení interpolovaných doslovných řetězců](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 je podporován na **rozhraních .NET Core 3.x** a **.NET Standard 2.1**. Další informace naleznete v [tématu C# language versioning](../language-reference/configure-language-version.md).

Zbývající část tohoto článku stručně popisuje tyto funkce. Pokud jsou k dispozici podrobné články, jsou k dispozici odkazy na tyto kurzy a přehledy. Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:

1. Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Nastavte aktuální adresář do podadresáře *csharp8* pro úložiště *try-samples.*
1. Spusťte `dotnet try`.

## <a name="readonly-members"></a>Členové pouze pro čtení

`readonly` Modifikátor můžete použít na členy struktury. Označuje, že člen nemění stav. Je podrobnější než použití `readonly` modifikátoru `struct` na deklaraci.  Zvažte následující proměnlivou strukturu:

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

Stejně jako většina `ToString()` struktur, metoda nemění stav. Můžete to označit přidáním modifikátoru `readonly` do deklarace `ToString()`:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Předchozí změna generuje upozornění kompilátoru, `ToString` protože `Distance` přistupuje `readonly`k vlastnosti, která není označena :

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilátor vás upozorní, když potřebuje vytvořit obrannou kopii.  Vlastnost `Distance` nezmění stav, takže můžete opravit toto upozornění `readonly` přidáním modifikátor u deklarace:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Všimněte `readonly` si, že modifikátor je nezbytné pro vlastnost jen pro čtení. Kompilátor nepředpokládá, `get` že přístupové objektů nemění stav; musíte deklarovat `readonly` explicitně. Automaticky implementované vlastnosti jsou výjimkou; kompilátor bude považovat všechny automaticky implementované gettery za jen pro čtení, takže zde není nutné přidávat `readonly` modifikátor do vlastností `X` a. `Y`

Kompilátor vynucuje pravidlo, že `readonly` členové nemění stav. Následující metoda nebude kompilovat, `readonly` pokud odebrat modifikátor:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Tato funkce umožňuje určit záměr návrhu, aby ho kompilátor mohl vynutit, a provést optimalizace na základě tohoto záměru. Další informace o členech readonly se [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)dozvíte v článku s odkazy na jazyk na .

## <a name="default-interface-methods"></a>Výchozí metody rozhraní

Nyní můžete přidat členy do rozhraní a poskytnout implementaci pro tyto členy. Tato jazyková funkce umožňuje autorům rozhraní API přidávat metody do rozhraní v novějších verzích bez přerušení zdrojové nebo binární kompatibility s existujícími implementacemi tohoto rozhraní. Existující implementace *dědí* výchozí implementaci. Tato funkce také umožňuje C# spolupracovat s api, která cílí na Android nebo Swift, které podporují podobné funkce. Výchozí metody rozhraní také umožňují scénáře podobné funkci jazyka "vlastnosti".

Výchozí metody rozhraní ovlivňují mnoho scénářů a prvků jazyka. Náš první výukový program se zabývá [aktualizací rozhraní s výchozími implementacemi](../tutorials/default-interface-methods-versions.md). Další výukové programy a referenční aktualizace přicházejí včas pro obecné vydání.

## <a name="more-patterns-in-more-places"></a>Více vzorů na více místech

**Porovnávání vzorů** poskytuje nástroje pro poskytování funkcí závislých na tvarech napříč souvisejícími, ale různými druhy dat. C# 7.0 zavedlsyntaxi pro vzory typu a [`is`](../language-reference/keywords/is.md) konstantní vzorky pomocí výrazu a příkazu. [`switch`](../language-reference/keywords/switch.md) Tyto funkce představovaly první předběžné kroky směrem k podpoře programovacích paradigmat, kde data a funkce žijí odděleně. Vzhledem k tomu, že se odvětví posune směrem k více mikroslužbám a dalším cloudovým architekturám, jsou potřeba další jazykové nástroje.

C# 8.0 rozšiřuje tento slovník, takže můžete použít více vzor výrazy na více místech v kódu. Zvažte tyto funkce, když jsou vaše data a funkce oddělené. Zvažte porovnávání vzorů, když vaše algoritmy závisí na skutečnosti, než je typ runtime objektu. Tyto techniky poskytují další způsob, jak vyjádřit návrhy.

Kromě nových vzorů na nových místech c# 8.0 přidává **rekurzivní vzory**. Výsledkem libovolného výrazu vzoru je výraz. Rekurzivní vzorek je jednoduše výraz vzorku aplikovaný na výstup jiného výrazu vzorku.

### <a name="switch-expressions"></a>Přepnutí výrazů

Často příkaz [`switch`](../language-reference/keywords/switch.md) vytvoří hodnotu v každém `case` z jeho bloků. **Přepínací výrazy** umožňují používat stručnější syntaxi výrazů. Existuje méně opakujících se `case` `break` a klíčových slov a méně složených závorek.  Jako příklad zvažte následující výčet, který uvádí barvy duhy:

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

Pokud `RGBColor` aplikace definovala `R`typ, který je `G` `B` vytvořen z , a `Rainbow` komponenty, můžete převést hodnotu na jeho hodnoty RGB pomocí následující metody obsahující výraz přepínače:

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

Existuje zde několik vylepšení syntaxe:

- Proměnná předchází klíčovému slovu. `switch` Různé pořadí umožňuje vizuálně snadno odlišit výraz přepínače od příkazu switch.
- `case` Prvky `:` a jsou `=>`nahrazeny písmenem . Je to stručnější a intuitivnější.
- Pouzdro `default` je nahrazeno `_` výmětem.
- Těla jsou výrazy, ne příkazy.

Kontrast, že s ekvivalentní `switch` kód pomocí klasické hopříkaz:

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

**Vzor vlastnosti** umožňuje shodovat s vlastnostmi zkoumaného objektu. Zvažte web elektronického obchodu, který musí vypočítat DPH na základě adresy kupujícího. Tento výpočt není hlavní odpovědností `Address` třídy. To se bude měnit v průběhu času, pravděpodobně častěji než změny formátu adresy. Částka DPH závisí na `State` vlastnosti adresy. Následující metoda používá vlastnost vzor pro výpočet DPH z adresy a ceny:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Porovnávání vzorů vytvoří stručnou syntaxi pro vyjádření tohoto algoritmu.

### <a name="tuple-patterns"></a>Řazené kolekce členů

Některé algoritmy závisí na více vstupech. **Vzorky n-tice** umožňují přepínat na základě více hodnot vyjádřených jako [řazená kolekce členů](../tuples.md).  Následující kód ukazuje výraz přepínače pro hru *rock, papír, nůžky*:

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

Zprávy označují vítěze. Zahození případu představuje tři kombinace pro vazby nebo jiné textové vstupy.

### <a name="positional-patterns"></a>Poziční vzory

Některé typy `Deconstruct` zahrnují metodu, která dekonstruuje jeho vlastnosti do diskrétní proměnné. Pokud `Deconstruct` je metoda přístupná, můžete použít **poziční vzorky** ke kontrole vlastností objektu a použít tyto vlastnosti pro vzorek.  Zvažte `Point` následující třídu, která obsahuje metodu `Deconstruct` `X` pro `Y`vytvoření diskrétních proměnných pro a:

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

Kromě toho zvažte následující výčt, který představuje různé pozice kvadrantu:

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

Následující metoda používá **poziční vzor** `x` extrahovat hodnoty a `y`. Potom používá klauzuli `when` k `Quadrant` určení bodu:

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

Vzorek zahození v předchozím přepínači odpovídá, když buď `x` nebo `y` je 0, ale ne obojí. Výraz přepínače musí buď vytvořit hodnotu nebo vyvolat výjimku. Pokud žádný z případů shodují, výraz přepínač vyvolá výjimku. Kompilátor vygeneruje upozornění pro vás, pokud nechcete pokrýt všechny možné případy ve výrazu přepínač.

Můžete prozkoumat techniky porovnávání vzorů v tomto [pokročilém kurzu o porovnávání vzorů](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Použití deklarací

Deklarace **using** je deklarace proměnné, které předchází `using` klíčové slovo. Říká kompilátoru, že proměnná deklarovaná by měla být uvolněna na konci ohraničujícího oboru. Zvažte například následující kód, který zapisuje textový soubor:

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

V předchozím příkladu je soubor uvolněn při dosažení uzavírací složená závorka pro metodu. To je konec oboru, ve `file` kterém je deklarována. Předchozí kód je ekvivalentní následující kód, který používá klasický [using příkaz](../language-reference/keywords/using-statement.md):

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

V předchozím příkladu je soubor uvolněn při dosažení uzavírací složená závorka přidružená k příkazu. `using`

V obou případech kompilátor generuje `Dispose()`volání . Kompilátor generuje chybu, pokud výraz `using` v příkazu není na jedno použití.

## <a name="static-local-functions"></a>Statické místní funkce

Nyní můžete přidat `static` modifikátor do místních funkcí, abyste zajistili, že místní funkce nezachytí (neodkazuje) žádné proměnné z ohraničujícího oboru. Tím se `CS8421`vygeneruje , "Statické místní funkce \<nemůže obsahovat odkaz na proměnné>."

Zvažte následující kód. Místní funkce `LocalFunction` přistupuje k proměnné `y`, deklarované v ohraničující mašká (metoda). `M` `LocalFunction` Proto nelze deklarovat `static` pomocí modifikátoru:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Následující kód obsahuje statickou místní funkci. Může být statický, protože nemá přístup k žádné proměnné v ohraničujícím oboru:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Jednorázové ref struktury

`struct` Deklarované `ref` s modifikátorem nemusí implementovat <xref:System.IDisposable>žádná rozhraní, a proto nelze implementovat . Proto povolit `ref struct` likvidaci, musí mít přístupnou `void Dispose()` metodu. Tato funkce platí `readonly ref struct` také pro deklarace.

## <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

Uvnitř kontextu poznámky s možnou hodnotou null je jakákoli proměnná typu odkazu považována za **nenulný typ odkazu**. Pokud chcete označit, že proměnná může být null, je `?` nutné připojit název typu s deklarovat proměnnou jako **typ odkazu s možnou hodnotou null**.

Pro neplatné typy odkazů kompilátor používá analýzu toku k zajištění, že místní proměnné jsou inicializovány na hodnotu bez nuly při deklarování. Pole musí být během výstavby inicializována. Kompilátor generuje upozornění, pokud proměnná není nastavena voláním některého z dostupných konstruktorů nebo inicializátorem. Kromě toho nelze zrušitelné typy odkazů nelze přiřadit hodnotu, která může být null.

Typy odkazů s možnou hodnotou Null nejsou kontrolovány, aby bylo zajištěno, že nejsou přiřazeny nebo inicializovány na hodnotu null. Kompilátor však používá analýzu toku k zajištění, že všechny proměnné typu odkazu s možnou hodnotou null je zkontrolována proti hodnotě null před tím, než je přístupná nebo přiřazena k neplatnému typu odkazu.

Další informace o této funkci naleznete v přehledu [typů odkazů s možnou hodnotou null](../nullable-references.md). Vyzkoušejte si to sami v nové aplikaci v tomto [kurzu s nulovatelnými typy odkazů](../tutorials/nullable-reference-types.md). Informace o krocích migrace existujícího základu kódu pro použití typů odkazů s možnou hodnotou null v [kurzu migrace aplikace k použití typů odkazů s možnou hodnotou null](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Asynchronní datové proudy

Počínaje C# 8.0, můžete vytvořit a využívat datové proudy asynchronně. Metoda, která vrací asynchronní datový proud, má tři vlastnosti:

1. Je to deklarováno modifikátorem. `async`
1. Vrátí . <xref:System.Collections.Generic.IAsyncEnumerable%601>
1. Metoda obsahuje `yield return` příkazy vrátit po sobě jdoucích prvků v asynchronní datový proud.

Náročné asynchronní datový proud vyžaduje, `await` abyste přidat `foreach` klíčové slovo před klíčové slovo při výčet prvků datového proudu. Přidání `await` klíčového slova vyžaduje metodu, která vyjmenovává asynchronní datový proud, který má být deklarován pomocí `async` modifikátoru, a vrátí typ povolený pro metodu. `async` Obvykle to znamená vrácení <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>nebo . To může být <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>také nebo . Metoda může spotřebovávat a vytvářet asynchronní datový <xref:System.Collections.Generic.IAsyncEnumerable%601>proud, což znamená, že vrátí . Následující kód generuje sekvenci od 0 do 19, čekání 100 ms mezi generování každé číslo:

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

Byste výčet sekvence pomocí příkazu: `await foreach`

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Můžete zkusit asynchronní proudy sami v našem kurzu o [vytváření a využívání asynchronních proudů](../tutorials/generate-consume-asynchronous-stream.md). Ve výchozím nastavení jsou prvky datového proudu zpracovány v zachyceném kontextu. Pokud chcete zakázat zachycení kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zachycení aktuálního kontextu naleznete v článku o [využití asynchronního vzoru založeného na úlohách](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="asynchronous-disposable"></a>Asynchronní jednorázové

Počínaje C# 8.0 jazyk podporuje asynchronní jednorázové typy, které implementují <xref:System.IAsyncDisposable?displayProperty=nameWithType> rozhraní. Operand výrazu `using` může implementovat buď <xref:System.IDisposable> nebo <xref:System.IAsyncDisposable>. `IAsyncDisposable`V případě , kompilátor generuje `await` kód <xref:System.Threading.Tasks.Task> vrácené z <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>. Další informace naleznete v [ `using` prohlášení](../language-reference/keywords/using-statement.md).

## <a name="indices-and-ranges"></a>Indexy a rozsahy

Indexy a rozsahy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.

Tato jazyková podpora závisí na dvou nových typech a dvou nových operátorech:

- <xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.
- Index z koncového operátoru `^`, který určuje, že index je relativní ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.
- Operátor `..`rozsahu , který určuje začátek a konec rozsahu jako jeho operandy.

Začněme s pravidly pro indexy. Zvažte `sequence`pole . Index `0` je stejný `sequence[0]`jako . Index `^0` je stejný `sequence[sequence.Length]`jako . Všimněte `sequence[^0]` si, že se `sequence[sequence.Length]` vyvolat výjimku, stejně jako dělá. Pro libovolné `n`číslo `^n` je index `sequence.Length - n`stejný jako .

Rozsah určuje *začátek* *a* konec rozsahu. Začátek rozsahu je včetně, ale konec rozsahu je exkluzivní, což znamená, že *začátek* je součástí rozsahu, ale *konec* není součástí rozsahu. Rozsah `[0..^0]` představuje celý rozsah, `[0..sequence.Length]` stejně jako představuje celý rozsah.

Podívejme se na několik příkladů. Zvažte následující pole s poznámkami s jeho indexem od začátku a od konce:

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

Můžete načíst poslední slovo `^1` s indexem:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Následující kód vytvoří podrozsah se slovy "quick", "brown" a "fox". To `words[1]` zahrnuje `words[3]`prostřednictvím . Prvek `words[4]` není v rozsahu.

```csharp
var quickBrownFox = words[1..4];
```

Následující kód vytvoří podrozsah s "líný" a "pes". To `words[^2]` zahrnuje `words[^1]`a . Koncový index `words[^0]` není zahrnut:

```csharp
var lazyDog = words[^2..^0];
```

Následující příklady vytvářejí oblasti, které jsou otevřené pro začátek, konec nebo obojí:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Rozsahy můžete také deklarovat jako proměnné:

```csharp
Range phrase = 1..4;
```

Rozsah pak lze použít `[` uvnitř `]` znaky a:

```csharp
var text = words[phrase];
```

Nejen pole podporují indexy a rozsahy. Můžete také použít indexy a rozsahy <xref:System.Span%601>s <xref:System.ReadOnlySpan%601> [řetězcem](../language-reference/builtin-types/reference-types.md#the-string-type), nebo . Další informace naleznete [v tématu Typ podpory pro indexy a rozsahy](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Další informace o indexech a rozsahech můžete prozkoumat v kurzu o [indexech a rozsahech](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Přiřazení null-coalescing

C# 8.0 zavádí operátor `??=`přiřazení null-coalescing . `??=` Operátor můžete použít k přiřazení hodnoty jeho pravostranného operandu jeho levostranné operandu pouze `null`v případě, že se levá operand vyhodnotí na .

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Pro více informací, viz [?? a ?? = článek operátorů.](../language-reference/operators/null-coalescing-operator.md)

## <a name="unmanaged-constructed-types"></a>Nespravované konstruované typy

V C# 7.3 a starší, konstruované typu (typ, který obsahuje alespoň jeden argument typu) nemůže být [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md). Počínaje C# 8.0, početný typ hodnoty je nespravovaný, pokud obsahuje pouze pole nespravovaných typů.

Například s ohledem na následující `Coords<T>` definici obecného typu:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>` typ je nespravovaný typ v C# 8.0 a novější. Stejně jako u všech nespravovaných typů můžete vytvořit ukazatel na proměnnou tohoto typu nebo [přidělit blok paměti v zásobníku](../language-reference/operators/stackalloc.md) pro instance tohoto typu:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Další informace naleznete v tématu [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc ve vnořených výrazech

Počínaje C# 8.0, pokud je výsledek výrazu [stackalloc](../language-reference/operators/stackalloc.md) typu <xref:System.Span%601?displayProperty=nameWithType> nebo, <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> můžete použít `stackalloc` výraz v jiných výrazech:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Vylepšení interpolovaných doslovných řetězců

Pořadí `$` a `@` tokeny v [interpolovaných](../language-reference/tokens/interpolated.md) doslovných řetězců může `$@"..."` být `@$"..."` libovolné: oba a jsou platné interpolované doslovné řetězce. V dřívějších verzích `$` jazyka C# `@` token musí zobrazit před token.
