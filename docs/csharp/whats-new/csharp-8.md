---
title: Co je nového v C# 8.0 – C# Průvodce
description: Získejte přehled o nových funkcí dostupných v C# 8.0. V tomto článku je aktuální verze Preview 5.
ms.date: 02/12/2019
ms.openlocfilehash: dd4aca99a19134ed3ffff859c9c9554d4d480816
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557151"
---
# <a name="whats-new-in-c-80"></a>Co je nového v C# 8.0

Existuje mnoho vylepšení C# jazyk, který můžete vyzkoušet již. 

- [Členy jen pro čtení](#readonly-members)
- [Výchozí členy rozhraní](#default-interface-members)
- [Porovnávání vzorů vylepšení](#more-patterns-in-more-places):
  * [Přepnout výrazy](#switch-expressions)
  * [Vlastnost vzory](#property-patterns)
  * [Vzory řazené kolekce členů](#tuple-patterns)
  * [Poziční vzory](#positional-patterns)
- [Pomocí deklarace](#using-declarations)
- [Statická lokální funkce](#static-local-functions)
- [Struktury ref uvolnitelné](#disposable-ref-structs)
- [Odkazové typy s možnou hodnotou null](#nullable-reference-types)
- [Asynchronní datové proudy](#asynchronous-streams)
- [Indexy a rozsahy](#indices-and-ranges)

> [!NOTE]
> Tento článek byl naposledy aktualizován pro C# 8.0 ve verzi preview 5.

Zbývající část tohoto článku stručně popisuje tyto funkce. Pokud podrobné články jsou k dispozici, jsou k dispozici odkazy na tyto kurzy a přehledy.

## <a name="readonly-members"></a>Členy jen pro čtení

Můžete použít `readonly` modifikátor k libovolnému členovi struktury. Znamená to, že člen neprovede žádné změny stavu. Je podrobnější než použití `readonly` modifikátor `struct` deklarace.  Vezměte v úvahu následující proměnlivé struktury:

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

Většina struktury, jako jsou `ToString()` metoda neprovede žádné změny stavu. Který může znamenat tak, že přidáte `readonly` modifikátoru deklarace `ToString()`:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Předchozí změny generuje upozornění kompilátoru, protože `ToString` přistupuje `Distance` vlastnost, která není označena `readonly`:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Kompilátor vás upozorní, když je potřeba vytvořit obranná kopie.  `Distance` Vlastnost nedojde ke změně stavu, takže toto upozornění můžete vyřešit tak, že přidáte `readonly` modifikátoru deklarace:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Všimněte si, že `readonly` Modifikátor je nezbytné na vlastnost jen pro čtení. Kompilátor nepředpokládá `get` přistupující objekty neprovádějte žádné změny stavu, je třeba deklarovat `readonly` explicitně. Kompilátor vynucuje pravidla, která `readonly` členy neprovádějte žádné změny stavu. Následující metoda nebude kompilovat, dokud neodeberete `readonly` modifikátor:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Tato funkce vám umožní zadat máte v úmyslu návrhu tak, aby kompilátor může vynutit a ujistěte se, optimalizace podle tohoto záměru.

## <a name="default-interface-members"></a>Výchozí členy rozhraní

Teď můžete přidat členy do rozhraní a poskytnout implementaci pro ty členy. Této funkci jazyka umožňuje autorům rozhraní API přidat metody do rozhraní v pozdějších verzích bez narušení zdroje nebo binární kompatibilitu s existující implementace rozhraní. Existujících implementací *dědit* výchozí implementaci. Tato funkce také umožňuje C# pro spolupráci s rozhraní API, která cílí na Android nebo Swift, které podporují podobné funkce. Výchozí členy rozhraní také povolit scénáře podobné funkci jazyka "vlastnosti".

Výchozí členy rozhraní ovlivňuje mnoho scénářů a prvky jazyka. Naše první kurz se zabývá [aktualizace pomocí výchozí implementace rozhraní](../tutorials/default-interface-members-versions.md). Další kurzy a referenční aktualizace se chystají v čase pro obecné verze.

## <a name="more-patterns-in-more-places"></a>Další vzory na více místech

**Porovnávání vzorů** poskytuje nástroje k zajištění funkce závislé na tvar v souvisejících, ale různé druhy dat. C#7.0 vytvořit pomocí syntaxe pro typ vzory a konstantní vzory [ `is` ](../language-reference/keywords/is.md) výraz a [ `switch` ](../language-reference/keywords/switch.md) příkazu. Tyto funkce jsou reprezentovány první nezávazně postup směrem k podpoře programovací modely, kde data a funkce live od sebe. Jak se v oboru blíží další mikroslužby a další cloudové architektury, jsou potřeba další nástroje jazyka.

C#8.0 rozšiřuje tento slovník tak další vzorek výrazy můžete použít na více místech ve vašem kódu. Pokud vaše data a funkce jsou oddělené vezměte v úvahu tyto funkce. Vezměte v úvahu porovnávání vzorů při algoritmy závisí na skutečnost než objekt typu modulu runtime. Tyto postupy zadejte jiný způsob, jak vyjádřit návrhy.

Kromě nové vzory v nových místech C# 8.0 přidá **rekurzivní vzory**. Výsledek výrazu jakékoli vzor je výraz. Rekurzivní vzor je jednoduše vzor výraz použitý pro výstup jiný výraz vzoru.

### <a name="switch-expressions"></a>Přepnout výrazy

Často [ `switch` ](../language-reference/keywords/switch.md) příkaz vytvoří hodnotu ve všech jeho `case` bloky. **Přepnout výrazy** vám umožní používat stručnější syntaxi výrazu. Existují méně opakované `case` a `break` klíčová slova a méně složených závorek.  Jako příklad vezměte v úvahu následující výčtového typu, který obsahuje seznam barvy rainbow:

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

Pokud vaše aplikace definované `RGBColor` typ, který je vytvořen z `R`, `G` a `B` součásti, můžete převést `Rainbow` hodnotu na jeho hodnoty RGB pomocí následující metody, který obsahuje výraz přepínače:

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

Existuje několik vylepšení syntaxe tady:

- Proměnná byla zaslána před `switch` – klíčové slovo. Jiné pořadí vizuálně usnadňuje rozlišit výraz přepínače z příkazu switch.
- `case` a `:` prvky jsou nahrazeny `=>`. Je stručnějším a intuitivní.
- `default` Případ je nahrazen `_` zahodit.
- Subjekty jsou výrazy, nikoli příkazy.

Oproti, který odpovídá kódu pomocí klasického `switch` – příkaz:

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

### <a name="property-patterns"></a>Vlastnost vzory

**Vlastnost vzor** umožňuje tak, aby odpovídala na vlastnosti objektu prověřit. Vezměte v úvahu elektronického obchodování webu, který musí vypočítat na základě adresy odběratele DPH. Výpočet není základní působnosti `Address` třídy. Se změní v čase, pravděpodobně častěji než změny formátu adresy. Množství DPH závisí `State` vlastnost adresy. Následující metoda používá vzor pro vlastnost pro výpočet DPH z adresy a cena:

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

Porovnávání vzorů vytvoří stručnější syntaxe pro vyjádření tento algoritmus.

### <a name="tuple-patterns"></a>Vzory řazené kolekce členů

Některé algoritmy závisí na více vstupů. **Vzory řazené kolekce členů** bylo možné přepnout na základě více hodnot, vyjádřené jako [řazené kolekce členů](../tuples.md).  Následující kód ukazuje výraz přepínače hry *rock, dokument, nůžek*:

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

Zprávy určit vítěze. Případ zahození představuje tři kombinace pro vazby nebo další textovými vstupy.

### <a name="positional-patterns"></a>Poziční vzory

Některé typy zahrnují `Deconstruct` metodu, která do proměnných diskrétního deconstructs její vlastnosti. Když `Deconstruct` metoda je přístupná, můžete použít **poziční vzory** ke kontrole vlastností objektu a použijte tyto vlastnosti pro vzor.  Vezměte v úvahu následující `Point` třídu, která zahrnuje `Deconstruct` metodu pro vytvoření proměnné diskrétního pro `X` a `Y`:

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

Kromě toho zvažte následující výčtového typu, který představuje různé pozic kvadrantu:

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

Používá následující metodu **poziční vzor** k extrakci hodnot z `x` a `y`. Potom použije `when` klauzule určit `Quadrant` bodu:

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

Vzor zrušení v předchozím přepínače odpovídá při buď `x` nebo `y` je 0, ale ne obojí. Výraz přepínače musíte vytvořit hodnotu nebo vyvolat výjimku. Výraz přepínače vyvolá výjimku, pokud neodpovídá žádná případů. Kompilátor vygeneruje upozornění za vás, pokud jste ve výrazu přepínače nepokrývají všechny možné případy.

Můžete prozkoumat porovnávání vzorů postupy v tomto [Upřesnit kurz o porovnávání vzorů](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Pomocí deklarace

A **using – deklarace** deklaraci proměnné předchází `using` – klíčové slovo. To sděluje kompilátoru, že by mělo být uvolněno deklarované proměnné na konci nadřazeném oboru. Zvažte například následující kód, který zapisuje do textového souboru:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

V předchozím příkladu je soubor odstraněn po dosažení pravou složenou závorku v případě metody. Který je koncem objektu oboru, ve kterém `file` je deklarována. Předchozí kód je ekvivalentní následujícímu kódu pomocí klasického [příkazy using](../language-reference/keywords/using-statement.md) – příkaz:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

V předchozím příkladu je soubor uvolněno při přidružené pravou složenou závorku `using` je dosažen příkaz.

V obou případech platí, kompilátor vygeneruje volání `Dispose()`. Kompilátor vygeneruje chybu, pokud výraz v pomocí příkazu není na jedno použití.

## <a name="static-local-functions"></a>Statická lokální funkce

Teď můžete přidávat `static` modifikátor lokální funkce zajistit, že místní funkce nezachytí (referenční dokumentace) všechny proměnné v ohraničujícím oboru. Tím se vygeneruje `CS8421`, "statické lokální funkce nesmí obsahovat odkaz na \<proměnná >." 

Uvažujme následující kód. Lokální funkce `LocalFunction` přistupuje k proměnné `y`, které jsou deklarovány v ohraničujícím oboru (metoda `M`). Proto `LocalFunction` se nedá deklarovat pomocí `static` modifikátor:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Následující kód obsahuje statické lokální funkce. Může být statická, protože nemá přístup k žádné proměnné v ohraničujícím oboru:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Struktury ref uvolnitelné

A `struct` deklarované s `ref` modifikátor nemusí implementovat jakékoli rozhraní a proto nemůže implementovat <xref:System.IDisposable>. Proto aby `ref struct` odstraněn, musí mít k dispozici přístup `void Dispose()` metoda. To platí i pro `readonly ref struct` deklarace.

## <a name="nullable-reference-types"></a>Typy s možnou hodnotou Null odkazů

V kontextu poznámky s možnou hodnotou Null, všechny proměnné typu odkazu se považuje za **nonnullable odkazový typ**. Pokud chcete určit, že proměnná může mít hodnotu null, musí připojit k názvu typu `?` deklarovat jako proměnnou **typ s možnou hodnotou Null odkazu**.

Pro typy odkazů nemá kompilátor používá k zajištění, že místní proměnné jsou inicializovány na hodnotu než null při deklaraci analýzy toku. Pole musí být inicializován během konstrukce. Kompilátor generuje upozornění, pokud proměnná není nastavená voláním kterýkoli z konstruktorů k dispozici nebo inicializátor. Kromě toho nemá odkazové typy nelze přiřadit hodnotu, která může mít hodnotu null.

Typy odkazů s možnou hodnotou Null nejsou kontrola nejsou přiřazen nebo inicializován na hodnotu null. Však kompilátor používá k zajištění, že všechny proměnné typu odkazu s možnou hodnotou null je porovnány s hodnotou null, předtím, než má získat přístup nebo přiřazený k typu odkazu nonnullable analýzy toku.

Další informace o funkci v přehledu [typy s možnou hodnotou Null odkazů](../nullable-references.md). Vyzkoušejte si to sami v nové aplikaci v tomto [kurzu typy s možnou hodnotou Null reference](../tutorials/nullable-reference-types.md). Seznamte se s kroky při migraci z existujícího základu kódu, aby použití typů s povolenou hodnotou Null odkazu v [migrace aplikace pro použití s možnou hodnotou NULL referenční typy kurzu](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Asynchronní datové proudy

Počínaje C# 8.0, lze vytvářet a využívat datové proudy asynchronně. Metodu vracející asynchronní datový proud má tři vlastnosti:

1. Je deklarována s `async` modifikátor.
1. Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Metoda obsahuje `yield return` příkazy vrátit po sobě jdoucí prvky v asynchronního datového proudu.

Použití asynchronního datového proudu je potřeba přidat `await` – klíčové slovo před `foreach` – klíčové slovo při výčtu prvky datového proudu. Přidání `await` – klíčové slovo vyžaduje metodu, která vytvoří výčet asynchronního datového proudu deklarován s `async` modifikátor a návratový typ povolené pro `async` metoda. Obvykle to znamená, že vrácení <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Může být <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601>. Metoda může současně využívají a produkují asynchronní datový proud, což znamená, že by měla vrátit <xref:System.Collections.Generic.IAsyncEnumerable%601>. Následující kód generuje sekvenci od 0 do 19 čekání na 100 ms mezi generování každé číslo:

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

By výčet pomocí pořadí `await foreach` – příkaz:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Můžete zkusit asynchronními datovými proudy sami v našem kurzu [vytváření a používání asynchronních streamů](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručné syntaxe pro zadání podrozsahů v poli, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.

Tato podpora jazyka spoléhá na dva nové typy a dvou nových operátorů.
- <xref:System.Index?displayProperty=nameWithType> představuje index na sekvenci.
- `^` Operátor, který určuje, že je index vzhledem ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType> představuje rozsah dílčí sekvenci.
- Operátor rozsahu (`..`), který určuje začátek a konec rozsahu, jako je operandy.

Začněme s pravidly pro indexy. Vezměte v úvahu pole `sequence`. `0` Index je stejný jako `sequence[0]`. `^0` Index je stejný jako `sequence[sequence.Length]`. Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]` nepodporuje. Pro libovolný počet `n`, index `^n` je stejný jako `sequence.Length - n`.

Určuje oblast *start* a *koncové* rozsahu. Rozsahy jsou výhradní, to znamená *end* není zahrnutý v rozsahu. Rozsah `[0..^0]` představuje celou oblast, stejně jako `[0..sequence.Length]` představuje celou oblast. 

Podívejme se na několik příkladů. Vezměte v úvahu následující pole označena s jeho index od samého začátku a konci:

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

Můžete načíst poslední slovo s `^1` indexu:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox". Zahrnuje `words[1]` prostřednictvím `words[3]`. Element `words[4]` není v rozsahu.

```csharp
var quickBrownFox = words[1..4];
```

Následující kód vytvoří podrozsahu "opožděné" a "pes". Zahrnuje `words[^2]` a `words[^1]`. Koncová hodnota `words[^0]` nezahrnuje:

```csharp
var lazyDog = words[^2..^0];
```

Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

Rozsahy můžete také deklarovat jako proměnné:

```csharp
Range phrase = 1..4;
```

Rozsah je pak možné uvnitř `[` a `]` znaků:

```csharp
var text = words[phrase];
```

Další informace o indexy a rozsahy můžete prozkoumat v tomto kurzu na [indexy a rozsahy adres](../tutorials/ranges-indexes.md).
