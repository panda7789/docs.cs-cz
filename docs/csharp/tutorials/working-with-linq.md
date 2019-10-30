---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte generovat sekvence pomocí LINQ, metody zápisu pro použití v dotazech LINQ a rozlišovat mezi Eager a opožděným hodnocením.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: b25cd1763511f460537bccaf6011a3d23390ea72
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039176"
---
# <a name="working-with-linq"></a>Práce s jazykem LINQ

## <a name="introduction"></a>Úvod

V tomto kurzu se naučíte funkcemi v .NET Core a C# v jazyce. Naučíte se:

- Jak generovat sekvence pomocí LINQ.
- Jak zapisovat metody, které lze snadno použít v dotazech LINQ.
- Jak rozlišovat mezi Eager a opožděným hodnocením.

Tyto techniky se naučíte vytvořením aplikace, která předvádí jednu ze základních dovedností libovolného Magician: Faro se [náhodně](https://en.wikipedia.org/wiki/Faro_shuffle)rozhodnou. Stručně je Faro náhodné, když rozdělíte balíček karet přesně na polovinu, pak se náhodně ponechá každou jednu kartu od poloviny a znovu sestaví původní balíček.

Magicians tento postup použijte, protože každá karta je ve známém umístění po každém náhodném umístění a pořadí je opakující se vzor.

Pro vaše účely je to světle srdce, které se používá při manipulaci s sekvencemi dat. Aplikace, kterou sestavíte, vytvoří balíček karet a pak provede sekvenci přepisování a pokaždé zapíše sekvenci. Také porovnáte aktualizované pořadí s původní objednávkou.

V tomto kurzu se používá několik kroků. Po každém kroku můžete spustit aplikaci a zobrazit průběh. V úložišti GitHub/Samples můžete také zobrazit [ukázku dokončeno](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) . Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač, aby běžel .NET Core. Pokyny k instalaci najdete na stránce pro [stažení jádra .NET](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux, OS X nebo v kontejneru Docker. Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/) , což je Open Source Editor pro různé platformy. Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. Do příkazového řádku zadejte příkaz `dotnet new console`. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Pokud jste to ještě nikdy C# nepoužili, [Tento kurz](console-teleprompter.md) vysvětluje strukturu C# programu. Můžete si ho přečíst a pak se sem vrátit a získat další informace o LINQ.

## <a name="creating-the-data-set"></a>Vytvoření datové sady

Než začnete, ujistěte se, že jsou na začátku `Program.cs` souboru generovaného `dotnet new console`následující řádky:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Pokud tyto tři řádky (příkazy`using`) nejsou v horní části souboru, náš program nebude zkompilován.

Teď, když máte všechny odkazy, které budete potřebovat, zvažte, co představuje balíček karet. Balíčky hracích karet běžně obsahují čtyři barvy a každá z nich má třináct hodnot. Za normálních okolností můžete zvážit vytvoření `Card` třídy přímo z bat a naplnění kolekce objektů `Card` ručně. Pomocí LINQ můžete být výstižnější, než obvyklý způsob, jak řešit vytváření balíčku karet. Namísto vytváření `Card` třídy můžete vytvořit dvě sekvence, které reprezentují barvy a pořadí. Vytvoříte skutečně jednoduchý pár [*metod iterátoru*](../iterators.md#enumeration-sources-with-iterator-methods) , který bude generovat pořadí a obleky jako <xref:System.Collections.Generic.IEnumerable%601>s řetězců:

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

Umístěte je pod metodu `Main` do souboru `Program.cs`. Tyto dvě metody používají syntaxi `yield return` k vytvoření sekvence při jejich spuštění. Kompilátor vytvoří objekt, který implementuje <xref:System.Collections.Generic.IEnumerable%601> a generuje sekvenci řetězců, jak jsou požadovány.

Nyní tyto metody iterátoru použijte k vytvoření balíčku karet. Dotaz LINQ umístíte do naší `Main` metody. Tady se můžete podívat na:

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

Klauzule Multiple `from` vytvoří <xref:System.Linq.Enumerable.SelectMany%2A>, které vytvoří jednu sekvenci z kombinace každého elementu v první sekvenci s každým prvkem v druhé sekvenci. Pořadí je důležité pro naše účely. První prvek v první zdrojové sekvenci (barev) je kombinován s každým prvkem v druhé sekvenci (pořadí). Tím se vytvoří všechny třinácté karty první barvy. Tento proces se opakuje s každým prvkem v prvním pořadí (obleky). Konečný výsledek je balíček karet seřazený podle obleku a za ním hodnoty.

Je důležité mít na paměti, že pokud se rozhodnete napsat svůj LINQ v syntaxi dotazu použitou výše, nebo místo toho použít syntaxi metody, je vždy možné přejít z jedné formy syntaxe do druhé. Výše uvedený dotaz napsaný v syntaxi dotazu může být zapsaný v syntaxi metody jako:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Kompilátor překládá příkazy LINQ napsané pomocí syntaxe dotazu do ekvivalentní syntaxe volání metody. Bez ohledu na zvolenou syntaxi si proto dvě verze dotazu vytvoří stejný výsledek. Vyberte, která syntaxe je nejvhodnější pro vaši situaci: například pokud pracujete v týmu, kde někteří členové mají potíže se syntaxí metody, zkuste preferovat použití syntaxe dotazu.

Pokračujte a spusťte ukázku, kterou jste v tomto okamžiku vytvořili. V balíčku se zobrazí všechny karty 52. Je možné, že je velmi užitečné spustit tuto ukázku v ladicím programu, abyste zjistili, jak se metody `Suits()` a `Ranks()` spouštějí. Můžete jasně vidět, že každý řetězec v každé sekvenci je vygenerovaný pouze v případě potřeby.

![Okno konzoly zobrazující, že aplikace vypisuje 52 karet.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a>Manipulace s objednávkou

V dalším kroku se zaměřte na to, jak se budou karty v balíčku přemíchat. Prvním krokem v jakémkoli dobrým náhodném případě je rozdělení balíčku na dvě. Metody <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>, které jsou součástí rozhraní API LINQ, poskytují tuto funkci za vás. Umístěte je pod `foreach` smyčka:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

Neexistuje však žádná nepřesná metoda, která by se mohla využít ve standardní knihovně, takže budete muset napsat vlastní. Metoda náhodně, kterou budete vytvářet, znázorňuje několik postupů, které budete používat s aplikacemi založenými na technologii LINQ, takže všechny části tohoto procesu budou vysvětleny v krocích.

Aby bylo možné přidat některé funkce k interakci s <xref:System.Collections.Generic.IEnumerable%601> se vrátíte od dotazů LINQ, budete muset napsat některé speciální druhy metod označované jako [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md). Krátké metody rozšíření je *statická metoda* pro zvláštní účely, která přidává novou funkci do již existujícího typu bez nutnosti upravovat původní typ, do kterého chcete přidat funkci.

Poskytněte rozšiřující metody novému domů přidáním nového souboru *statické* třídy do programu s názvem `Extensions.cs`a poté začněte sestavovat první metodu rozšíření:

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

Podívejte se na signaturu metody za chvilku, konkrétně parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Můžete vidět Přidání modifikátoru `this` u prvního argumentu do metody. To znamená, že zavoláte metodu, jako by šlo o členskou metodu typu prvního argumentu. Tato deklarace metody také následuje po standardním idiom, kde jsou `IEnumerable<T>`vstupní a výstupní typy. Tento postup umožňuje zřetězení metod LINQ společně provádět složitější dotazy.

Přirozeně, vzhledem k tomu, že balíček rozdělíte na poloviny, budete muset spojit tyto poloviny dohromady. V kódu to znamená, že budete vytvářet výčet obou sekvencí, které jste získali prostřednictvím <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> najednou, *`interleaving`* prvky a vytvořit jednu sekvenci: nyní-náhodně vytvořená balíček karet. Zápis metody LINQ, která funguje se dvěma sekvencemi, vyžaduje, abyste porozuměli tomu, jak <xref:System.Collections.Generic.IEnumerable%601> funguje.

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> má jednu metodu: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. Objekt vrácený <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci. Tyto dva členy použijete k vytvoření výčtu kolekce a vrácení prvků. Tato metoda prokládání bude metodou iterátoru, takže nemusíte sestavovat kolekci a vracet kolekci, použijete výše uvedenou syntaxi `yield return`.

Toto je implementace této metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teď, když jste tuto metodu napsali, se vraťte k metodě `Main` a přemístěte balíček jednou:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>Porovnání

Kolik přeřazení trvá pro nastavení balíčku zpátky na původní objednávku? Chcete-li zjistit, je nutné napsat metodu, která určuje, zda jsou dvě sekvence stejné. Až tuto metodu použijete, budete muset umístit kód, který přeskočí balíček ve smyčce, a zkontrolujte, jestli je balíček zase v pořádku.

Zápis metody pro určení, zda jsou dvě sekvence stejné, by měly být jednoduché. Je to podobná struktura jako metoda, kterou jste napsali pro přemístění balíčku. Pouze tento čas, místo `yield return`z každého prvku, porovnáte vyhovující prvky každé sekvence. Po vytvoření výčtu celé sekvence, pokud každý prvek odpovídá, jsou sekvence stejné:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

To ukazuje druhou metodu LINQ idiom: Terminal. Přebírají sekvenci jako vstup (nebo v tomto případě dvě sekvence) a vrátí jednu skalární hodnotu. Při použití metod terminálu jsou vždy poslední metodou v řetězci metod pro dotaz LINQ, tedy název "Terminal".

Tuto akci můžete zobrazit v akci, když ji použijete k určení, kdy se balíček vrátí v původním pořadí. Vložte náhodně kód do smyčky a zastavte, pokud je sekvence vrácena zpět v původním pořadí pomocí metody `SequenceEquals()`. Můžete vidět, že by to byla vždy konečná metoda v jakémkoli dotazu, protože vrací jednu hodnotu namísto sekvence:

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Spusťte kód, který zatím máte, a poznamenejte si, jak se v každé náhodném uspořádání balíčku mění. Po osmi přesunech (iterace smyčky do-while) se balíček vrátí do původní konfigurace, ve které byl při prvním vytvoření dotazu LINQ.

## <a name="optimizations"></a>Optimalizace

Ukázka, kterou jste sestavili tak daleko, se vykoná *náhodně*, kde karty Top a Bottom zůstanou stejné při každém spuštění. Pojďme udělat jednu změnu: místo toho budeme používat *náhodně* , kde se na všech kartách 52 mění pozice. V případě náhodného seřadíte balíček tak, že první karta v dolní polovině se bude první kartou v balíčku. To znamená, že poslední karta v horní polovině se stala spodní kartou. Toto je jednoduchá změna v jednotném řádku kódu. Aktualizuje aktuální náhodný dotaz přepnutím pozic <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>. Tím se změní pořadí horních a dolních polovin balíčku:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Spusťte program znovu a uvidíte, že pro balíček bude trvat 52 iterací, aby se mohla změnit jejich uspořádání. Začnete také všimnout některých vážných snížení výkonu, protože program pokračuje v běhu.

To je několik důvodů. Jedním z hlavních příčin tohoto poklesu výkonu můžete řešit: neefektivní použití [*opožděného vyhodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Stručné a opožděné vyhodnocení uvádí, že vyhodnocení příkazu není provedeno, dokud není nutné zadat jeho hodnotu. Dotazy LINQ jsou příkazy, které jsou vyhodnocovány laxně vytvářená. Sekvence se generují pouze v případě, že jsou požadovány elementy. Obvykle je to hlavní výhodou LINQ. V takovém případě, jako je například tento program, způsobuje exponenciální nárůst v době spuštění.

Pamatujte na to, že jsme původní balíček vygenerovali pomocí dotazu LINQ. Každé náhodné volání je vygenerováno pomocí tří dotazů LINQ na předchozí palubě. Všechny tyto kroky jsou prováděny laxně vytvářená. To také znamená, že budou provedeny znovu při každém vyžádání sekvence. V době, kdy se dostanete k iteraci 52nd, znovu vygenerujete původní balíček spoustou mnohokrát. Pojďme napsat protokol, který demonstruje toto chování. Pak ho opravíte.

V souboru `Extensions.cs` zadejte nebo zkopírujte níže uvedenou metodu. Tato metoda rozšíření vytvoří nový soubor s názvem `debug.log` v adresáři projektu a zaznamená, který dotaz je aktuálně prováděn do souboru protokolu. Tato metoda rozšíření se dá připojit k libovolnému dotazu a označit tak, že se dotaz spustil.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Pod `File`se zobrazí červená vlnovka, což znamená, že neexistuje. Nebude zkompilován, protože kompilátor neví, co `File`. Chcete-li tento problém vyřešit, je třeba přidat následující řádek kódu do prvního řádku v `Extensions.cs`:

```csharp
using System.IO;
```

To by mělo vyřešit problém a červená chyba zmizí.

V dalším kroku Instrumentujte definici každého dotazu pomocí zprávy protokolu:

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

Všimněte si, že při každém přístupu k dotazu nechcete protokolovat. Protokolujte pouze v případě, že vytvoříte původní dotaz. Spuštění programu trvá delší dobu, ale nyní můžete zjistit, proč. Pokud vyčerpáte z služby trpělivost s zapnutým protokolováním, přepněte zpět na náhodné. Pořád se zobrazí efekty opožděného vyhodnocení. V jednom spuštění se spustí 2592 dotazů, včetně veškeré generace hodnot a barev.

Můžete zvýšit výkon kódu zde, abyste snížili počet provedených provedení. Jednoduchá oprava, kterou můžete udělat, je *Uložit do mezipaměti* výsledky původního dotazu LINQ, který sestaví balíček karet. V současné době spouštíte dotazy znovu a znovu pokaždé, když smyčka do-while projde iterací, znovu se vytvoří balíček karet a znovu se přeskočí. Pro ukládání balíčku karet do mezipaměti můžete využít metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> a <xref:System.Linq.Enumerable.ToList%2A>; Když je připojíte k dotazům, provedou stejné akce, které jste jim přihlásili, ale nyní budou výsledky ukládat do pole nebo seznamu v závislosti na metodě, kterou se rozhodnete volat. Přidejte do obou dotazů metodu LINQ <xref:System.Linq.Enumerable.ToArray%2A> a program spusťte znovu:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Teď je vypínání na více než 30 dotazů. Spusťte znovu s náhodným a uvidíte podobná vylepšení: teď spustí 162 dotazů.

Upozorňujeme, že tento příklad je **navržený** tak, aby zvýraznili případy použití, kdy může opožděné vyhodnocení způsobit problémy s výkonem. I když je důležité zjistit, kde opožděné hodnocení může ovlivnit výkon kódu, je stejně důležité pochopit, že ne všechny dotazy by měly běžet eagerly. Zvýšení výkonu, které jste provedete, můžete dosáhnout bez použití <xref:System.Linq.Enumerable.ToArray%2A> je, protože každé nové uspořádání balíčku karet je sestavené z předchozího uspořádání. Pomocí opožděného vyhodnocování znamená, že každá nová konfigurace balíčku je sestavena z původní balíčky, dokonce i v případě, že je spuštěn kód, který vytvořil `startingDeck`. To způsobuje velké množství dodatečné práce.

V praxi některé algoritmy dobře fungují s využitím vyhodnocení Eager a jiné fungují i s opožděným hodnocením. Pro každodenní použití je opožděné vyhodnocování obvykle lepší volbou, pokud je zdroj dat samostatným procesem, jako je databázový stroj. Pro databáze, opožděné vyhodnocení umožňuje složitějším dotazům spustit pouze jednu zpáteční cestu k procesu databáze a vrátit se do zbytku kódu. LINQ je flexibilní bez ohledu na to, jestli se rozhodnete používat opožděné nebo Eager vyhodnocení, takže Změřte své procesy a vyberte si, který typ hodnocení vám dává nejlepší výkon.

## <a name="conclusion"></a>Závěr

V tomto projektu jste pokryli:

- použití dotazů LINQ k agregaci dat do smysluplné sekvence
- zápis metod rozšíření pro přidání naší vlastní funkcionality do dotazů LINQ
- Vyhledání oblastí v našem kódu, kde se můžou dotazy LINQ povést k problémům s výkonem, jako je snížená rychlost
- opožděné a Eager vyhodnocení v souvislosti s dotazy LINQ a důsledky, které mohou mít při výkonu dotazů

Kromě technologie LINQ jste se dozvěděli o magicians techniky použití pro štychy karet. Magicians použít Faro náhodně, protože může určovat, kde se každá karta v balíčku pohybuje. Teď už víte, že si ho nevyřadíte pro všechny ostatní.

Další informace o LINQ najdete v těchto tématech:

- [LINQ (Language Integrated Query)](../programming-guide/concepts/linq/index.md)
  - [Úvod do jazyka LINQ](../programming-guide/concepts/linq/index.md)
  - [Základní operace dotazů LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [Transformace dat pomocí LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [Syntaxe dotazu a syntaxe metody v LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [Funkce C# podporující LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
