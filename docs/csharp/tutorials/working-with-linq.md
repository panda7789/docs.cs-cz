---
title: Práce s jazykem LINQ
description: Tento kurz vás naučí, jak generovat sekvence s LINQ, psát metody pro použití v dotazech LINQ a rozlišovat mezi dychtivé a opožděné hodnocení.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240012"
---
# <a name="work-with-language-integrated-query-linq"></a>Práce s dotazem integrovaným jazykem (LINQ)

## <a name="introduction"></a>Úvod

Tento kurz vás naučí funkce v .NET Core a jazyk C#. Co se naučíte:

- Generovat sekvence s LINQ.
- Metody zápisu, které lze snadno použít v dotazech LINQ.
- Rozlišujte mezi dychtivým a líným hodnocením.

Naučíte se tyto techniky tím, že staví aplikace, která demonstruje jednu ze základních dovedností každého kouzelníka: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Stručně řečeno, faro shuffle je technika, kde si rozdělit kartu palubu přesně na polovinu, pak shuffle prolomení každé jedné karty z každé poloviny přestavět původní balíček.

Kouzelníci používají tuto techniku, protože každá karta je po každém náhodném přehrávání na známém místě a pořadí je opakující se vzor.

Pro vaše účely je to lehký pohled na manipulaci s sekvencemi dat. Aplikace, kterou budete stavět, vytvoří balíček karet a pak provede sekvenci zamíchání a pokaždé zapíše sekvenci. Budete také porovnávat aktualizované pořadí s původní objednávkou.

Tento kurz má několik kroků. Po každém kroku můžete spustit aplikaci a zobrazit průběh. Můžete také zobrazit [dokončenou ukázku](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti GitHub dotnet/samples. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění jádra .NET. Pokyny k instalaci naleznete na stránce [ke stažení jádra .NET.](https://dotnet.microsoft.com/download) Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux nebo OS X nebo v kontejneru Dockeru. Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code,](https://code.visualstudio.com/) který je open source, cross-platformní editor. Nicméně, můžete použít bez ohledu na nástroje, které jsou pohodlné s.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ať je to aktuální adresář. Zadejte `dotnet new console` příkaz na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".

Pokud jste nikdy nepoužívali C# dříve, [tento kurz](console-teleprompter.md) vysvětluje strukturu programu Jazyka C#. Můžete si přečíst, že a pak se vrátit sem se dozvíte více o LINQ.

## <a name="create-the-data-set"></a>Vytvoření sady dat

Než začnete, ujistěte se, že následující `Program.cs` řádky jsou `dotnet new console`v horní části souboru generovaného :

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Pokud tyto tři`using` řádky (příkazy) nejsou v horní části souboru, náš program nebude kompilovat.

Nyní, když máte všechny odkazy, které budete potřebovat, zvažte, co představuje balíček karet. Obvykle má balíček hracích karet čtyři barvy a každá barva má třináct hodnot. Za normálních okolností `Card` můžete zvážit vytvoření třídy hned bat `Card` a vyplnění kolekce objektů ručně. S LINQ, můžete být stručnější než obvyklý způsob, jak se vypořádat s vytvořením balíčku karet. Namísto vytvoření `Card` třídy můžete vytvořit dvě sekvence představující obleky a hodnosti. Vytvoříte opravdu jednoduchý pár [*iterátorových metod,*](../iterators.md#enumeration-sources-with-iterator-methods) které budou generovat <xref:System.Collections.Generic.IEnumerable%601>hodnosti a obleky jako s strun:

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

Umístěte je `Main` pod metodu do `Program.cs` souboru. Tyto dvě metody `yield return` oba využívají syntaxe k vytvoření sekvence při jejich spuštění. Kompilátor vytvoří objekt, který <xref:System.Collections.Generic.IEnumerable%601> implementuje a generuje posloupnost řetězců, jak jsou požadovány.

Nyní použijte tyto metody iterátoru k vytvoření balíčku karet. Dotaz LINQ umístíte do `Main` naší metody. Zde je pohled na to:

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

Více `from` klauzulí vytvořit <xref:System.Linq.Enumerable.SelectMany%2A>, který vytvoří jednu sekvenci z kombinování každý prvek v první sekvenci s každým prvkem v druhé sekvenci. Objednávka je důležitá pro naše účely. První prvek v první zdrojové sekvenci (Obleky) je kombinován s každým prvkem v druhé sekvenci (Ranky). Tím se vytvoří všech třináct karet první barvy. Tento proces se opakuje s každým prvkem v prvním pořadí (Obleky). Konečným výsledkem je balíček karet seřazených podle barev, následovaný hodnotami.

Je důležité mít na paměti, že ať už se rozhodnete napsat LINQ v syntaxi dotazu použité výše nebo použít syntaxi metody místo, je vždy možné přejít z jedné formy syntaxe do druhé. Výše uvedený dotaz napsaný v syntaxi dotazu lze zapsat v syntaxi metody jako:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Kompilátor přeloží linq příkazy napsané se syntaxí dotazu do syntaxe volání ekvivalentní metody. Proto bez ohledu na volbu syntaxe dvě verze dotazu vytvořit stejný výsledek. Zvolte, která syntaxe je pro vaši situaci nejvhodnější: například pokud pracujete v týmu, kde někteří členové mají potíže se syntaxí metody, zkuste dát přednost použití syntaxe dotazu.

Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto bodě. Zobrazí se všech 52 karet v balíčku. Může být velmi užitečné spustit tuto ukázku pod ladicím programem sledovat, jak `Suits()` a `Ranks()` metody spustit. Můžete jasně vidět, že každý řetězec v každé sekvenci je generován pouze podle potřeby.

![Okno konzoly zobrazující aplikaci, která vypisuje 52 karet.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Manipulujte s řádem

Dále se zaměřte na to, jak budete míchat karty v balíčku. Prvním krokem v každém dobrém shuffle je rozdělit palubu na dvě části. A <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> metody, které jsou součástí LINQ API poskytují tuto funkci pro vás. Umístěte je `foreach` pod smyčku:

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

Ve standardní knihovně však neexistuje žádná metoda náhodného přehrávání, takže budete muset napsat vlastní. Metoda náhodného přehrávání, kterou vytvoříte, ilustruje několik technik, které budete používat s programy založenými na LINQ, takže každá část tohoto procesu bude vysvětlena v krocích.

Chcete-li přidat některé funkce, jak <xref:System.Collections.Generic.IEnumerable%601> budete pracovat s dostanete zpět z linq dotazů, budete muset napsat některé speciální druhy metod nazývaných [metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md). Stručně řečeno, metoda rozšíření je speciální statický *způsob,* který přidává nové funkce již existující typ bez nutnosti měnit původní typ, který chcete přidat funkce.

Pojmenujte metody rozšíření novým domovem přidáním nového `Extensions.cs` *statického* souboru třídy do programu s názvem a začněte vytvářet první metodu rozšíření:

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

Podívejte se na podpis metody na chvíli, konkrétně parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Můžete vidět přidání modifikátoru `this` na první argument metody. To znamená, že volání metody, jako by byla člen metoda typu první argument. Tato deklarace metody také následuje standardní idiom, `IEnumerable<T>`kde jsou vstupní a výstupní typy . Tato praxe umožňuje LINQ metody, které mají být zřetězené dohromady provádět složitější dotazy.

Samozřejmě, protože jste rozdělili palubu na poloviny, budete muset spojit tyto poloviny dohromady. V kódu to znamená, že budete vyjmenovat obě sekvence, <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> které jste *`interleaving`* získali prostřednictvím a najednou, prvky a vytvořit jednu sekvenci: nyní zamíchaný balíček karet. Psaní LINQ metoda, která pracuje se dvěma <xref:System.Collections.Generic.IEnumerable%601> sekvencemi vyžaduje, abyste pochopili, jak funguje.

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> má jednu <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>metodu: . Objekt vrácený <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu přesunout na další prvek a vlastnost, která načte aktuální prvek v pořadí. Tyto dva členy použijete k vytvoření výčtu kolekce a vrácení prvků. Tato metoda Interleave bude metoda iterátoru, takže namísto vytváření kolekce a vrácení `yield return` kolekce použijete syntaxi uvedenou výše.

Zde je implementace této metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Nyní, když jste napsali tuto metodu, vraťte se k metodě `Main` a jednou zamíchejte balíček:

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

Kolik zamíchá, aby se paluba vrátila do původního pořadí? Chcete-li zjistit, budete muset napsat metodu, která určuje, zda jsou dvě sekvence stejné. Poté, co budete mít tuto metodu, budete muset umístit kód, který zamíchá palubu ve smyčce, a zkontrolujte, kdy je balíček zpět v pořádku.

Psaní metody k určení, pokud jsou dvě sekvence stejné by měly být jednoduché. Je to podobná struktura jako metoda, kterou jste napsali, abyste zamíchali palubu. Pouze tentokrát, namísto `yield return`ing každý prvek, budete porovnávat odpovídající prvky každé sekvence. Pokud byla celá sekvence výčtu, pokud každý prvek odpovídá, sekvence jsou stejné:

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

To ukazuje druhý LINQ idiom: terminálové metody. Vezmou sekvenci jako vstup (nebo v tomto případě dvě sekvence) a vrátí jednu skalární hodnotu. Při použití terminálových metod jsou vždy konečnou metodou v řetězci metod pro dotaz LINQ, odtud název "terminál".

Můžete to vidět v akci, když ji použijete k určení, kdy je balíček zpět v původním pořadí. Vložte kód náhodného přehrávání do smyčky a zastavte, když `SequenceEquals()` je sekvence zpět v původním pořadí použitím metody. Můžete vidět, že by vždy konečná metoda v libovolném dotazu, protože vrátí jednu hodnotu namísto sekvence:

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

Spusťte kód, který máte tak daleko, a vzít na vědomí, jak paluba přeskupí na každém shuffle. Po 8 shuffles (iterací do-while smyčky), balíček se vrátí do původní konfigurace, ve které byl při prvním vytvoření z počátečního dotazu LINQ.

## <a name="optimizations"></a>Optimalizace

Ukázka, kterou jste dosud vytvořili, provede *výběr*, kde horní a dolní karty zůstávají při každém běhu stejné. Udělejme jednu změnu: místo toho použijeme *zamíchanou,* kde změní pozici všech 52 karet. Pro shuffle, můžete proložit balíček tak, aby první karta v dolní polovině se stala první kartou v balíčku. To znamená, že poslední karta v horní polovině se stane spodní kartou. Jedná se o jednoduchou změnu jednotného řádku kódu. Aktualizujte aktuální zamíchací <xref:System.Linq.Enumerable.Take%2A> dotaz <xref:System.Linq.Enumerable.Skip%2A>přepnutím pozic a . Tím se změní pořadí horní a dolní poloviny paluby:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Spusťte program znovu a uvidíte, že trvá 52 iterací pro balíček, aby se přizpůsobil. Budete také začít všímat některé závažné snížení výkonu jako program nadále běžet.

Existuje pro to řada důvodů. Můžete řešit jednu z hlavních příčin tohoto poklesu výkonu: neefektivní použití [*opožděné hodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Stručně řečeno, opožděné vyhodnocení uvádí, že vyhodnocení příkazu není provedeno, dokud není potřeba jeho hodnota. LINQ dotazy jsou příkazy, které jsou vyhodnocovány líně. Sekvence jsou generovány pouze jako prvky jsou požadovány. Obvykle, to je hlavní výhodou LINQ. Však v použití, jako je tento program, to způsobí exponenciální růst v době provádění.

Nezapomeňte, že jsme vygenerovali původní balíček pomocí dotazu LINQ. Každý shuffle je generován provedením tří linq dotazů na předchozí palubě. Všechny tyto jsou prováděny líně. To také znamená, že jsou prováděny znovu pokaždé, když je požadována sekvence. V době, kdy se dostanete k 52. Pojďme napsat protokol demonstrovat toto chování. Tak to napravíš.

Do `Extensions.cs` souboru zadejte nebo zkopírujte níže uvedenou metodu. Tato metoda rozšíření vytvoří `debug.log` nový soubor svolaný v adresáři projektu a zaznamená, jaký dotaz je právě spuštěn do souboru protokolu. Tato metoda rozšíření lze připojit k libovolnému dotazu označit, že dotaz spuštěn.

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Uvidíte červenou vlnovku pod `File`, což znamená, že neexistuje. Nebude kompilovat, protože kompilátor neví, `File` co je. Chcete-li tento problém vyřešit, nezapomeňte přidat následující řádek `Extensions.cs`kódu pod úplně první řádek v :

```csharp
using System.IO;
```

To by mělo vyřešit problém a červená chyba zmizí.

Dále instrumentujte definici každého dotazu zprávou protokolu:

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

Všimněte si, že při každém přístupu k dotazu nezaznamenáváte. Protokolovat pouze při vytvoření původnídotaz. Spuštění programu stále trvá dlouho, ale nyní vidíte proč. Pokud vám dojde trpělivost při běhu s vypnutým protokolováním, přepněte zpět na out shuffle. Stále uvidíte opožděné efekty hodnocení. V jednom spuštění provede 2592 dotazů, včetně všech generování hodnoty a obleku.

Můžete zlepšit výkon kódu zde snížit počet spuštění provedete. Jednoduchá oprava, kterou můžete provést, je ukládat výsledky původního dotazu LINQ do *mezipaměti,* který vytváří balíček karet. V současné době provádíte dotazy znovu a znovu pokaždé, když smyčka do-while prochází iterace, re-constructing balíček karet a reshuffling pokaždé. Chcete-li uložit balíček karet do mezipaměti, můžete využít metody <xref:System.Linq.Enumerable.ToArray%2A> LINQ a <xref:System.Linq.Enumerable.ToList%2A>; Když je připojíte k dotazům, provedou stejné akce, které jste jim řekli, ale teď budou výsledky ukládat do pole nebo seznamu v závislosti na tom, kterou metodu se rozhodnete volat. Připojte metodu <xref:System.Linq.Enumerable.ToArray%2A> LINQ k oběma dotazům a znovu spusťte program:

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Nyní out shuffle je až 30 dotazů. Spusťte znovu s shuffle a uvidíte podobná vylepšení: nyní provádí 162 dotazů.

Vezměte prosím na vědomí, že tento příklad je **určen** ke zvýraznění případy použití, kde opožděné vyhodnocení může způsobit potíže s výkonem. I když je důležité zjistit, kde opožděné vyhodnocení může ovlivnit výkon kódu, je stejně důležité pochopit, že ne všechny dotazy by měly běžet dychtivě. Výkon hit vám vzniknou <xref:System.Linq.Enumerable.ToArray%2A> bez použití je proto, že každé nové uspořádání balíčku karet je postaven z předchozího uspořádání. Použití opožděné vyhodnocení znamená, že každá nová konfigurace balíčku je sestavena z původního balíčku, a to i při provádění kódu, který vytvořil `startingDeck`. To způsobuje velké množství práce navíc.

V praxi některé algoritmy běží dobře pomocí eager hodnocení a jiné spustit dobře pomocí opožděné hodnocení. Pro každodenní použití opožděné vyhodnocení je obvykle lepší volbou, pokud zdroj dat je samostatný proces, jako je databázový stroj. Pro databáze opožděné vyhodnocení umožňuje složitější dotazy spustit pouze jednu odezvu do procesu databáze a zpět do zbytku kódu. LINQ je flexibilní, ať už se rozhodnete využít líné nebo dychtivé hodnocení, takže změřte procesy a vyberte si, který druh hodnocení vám dává nejlepší výkon.

## <a name="conclusion"></a>Závěr

V tomto projektu jste se zabývali:

- použití dotazů LINQ k agregaci dat do smysluplné sekvence
- psaní rozšiřující metody přidat vlastní funkce linq dotazy
- lokalizace oblastí v našem kódu, kde naše linq dotazy mohou narazit na problémy s výkonem, jako je snížená rychlost
- líné a dychtivé hodnocení s ohledem na dotazy LINQ a důsledky, které mohou mít na výkon dotazu

Kromě LINQ, jste se dozvěděli něco o technice kouzelníci používají pro karetní triky. Kouzelníci používají Faro shuffle, protože mohou kontrolovat, kde se každá karta pohybuje v balíčku. Teď, když to víš, nezkaz to pro všechny ostatní!

Další informace o LINQ naleznete v následujících tématech:

- [LINQ (Language Integrated Query)](../programming-guide/concepts/linq/index.md)
- [Úvod do jazyka LINQ](../programming-guide/concepts/linq/index.md)
- [Základní operace dotazů LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Transformace dat s LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [Syntaxe využívající dotazy a syntaxe využívající metody v jazyce LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [Funkce C# podporující LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
