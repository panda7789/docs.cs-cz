---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, Zapsat metody pro použití v dotazech LINQ a rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: b7faa75234dec62be63e96c0f15f97c6d2aa4c99
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170805"
---
# <a name="working-with-linq"></a>Práce s jazykem LINQ

## <a name="introduction"></a>Úvod

V tomto kurzu se naučíte, funkce v .NET Core a C# jazyka. Získáte informace:

*   Jak vygenerovat pořadí pomocí jazyka LINQ.
*   Jak napsat metody, které můžete snadno použít v dotazech LINQ.
*   Jak rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.

Vytvořením aplikace, která ukazuje jednu základní dovednosti jakékoli magician dozvíte těchto technik: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Stručně řečeno náhodně faro je technika, kde rozdělit karet přesně na polovinu a pak shuffle předřadí jednotlivých karet z každého půl k opětovnému sestavení z původního balíčku.

Magicians tento postup použít, protože všechny karty je v zadaném umístění po jednotlivých shuffle a pořadí je s opakováním vzoru. 

Pro účely je slabá hearted podívejte se na zpracování data sekvencí. Aplikace, kterou vytvoříte bude sestavení karet a pak proveďte posloupnost podle okolí posouvá, zápis si pokaždé, když je pořadí. Budete také porovnat aktualizované aby původní pořadí.

V tomto kurzu má několik kroků. Po provedení každého kroku můžete spustit aplikaci a sledovat průběh. Můžete zobrazit také [úplnou vzorovou](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti dotnet/samples GitHub. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejneru Dockeru. Bude potřeba nainstalovat váš oblíbený editor kódu. Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru. Ale můžete použít jakýkoli nástroje jste obeznámeni.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ujistěte se, že do aktuálního adresáře. Zadejte příkaz `dotnet new console` příkazového řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Pokud jste nikdy C#, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v jazyce C#. Může číst a pak se sem vraťte pro další informace o jazyku LINQ. 

## <a name="creating-the-data-set"></a>Vytvoření datové sady

Než začnete, ujistěte se, že v horní části jsou následující řádky `Program.cs` soubor generovaný nástrojem `dotnet new console`:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Pokud tyto tři řádky (`using` příkazy) nejsou v horní části souboru, nebude kompilovat náš program.

Teď, když máte všechny odkazy, které budete potřebovat, vezměte v úvahu informace o tom, co balíčku karet. Běžně balíčku hracích kartách obsahuje čtyři barvy a každou barvu má třináct hodnoty. Za normálních okolností zvažte vytvoření `Card` třídy přímo vypnuto bat a naplnění kolekce `Card` objekty ručně. S dotazy LINQ může být stručnější než obvyklým způsobem řešení problémů s vytvořením balíčku karet. Místo vytváření `Card` třídy, můžete vytvořit dvěma sekvencemi k reprezentaci sady a pořadí, v uvedeném pořadí. Vytvoříte opravdu jednoduchý dvojici [ *iterátory* ](../iterators.md#enumeration-sources-with-iterator-methods) , který bude generovat pořadí a barvy jako <xref:System.Collections.Generic.IEnumerable%601>s řetězců:

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
Tyto pod umístit `Main` metoda ve vaší `Program.cs` souboru. Tyto dvě metody jak využívat `yield return` syntaxi pro vytvoření sekvence za běhu. Kompilátor vytvoří objekt, který implementuje <xref:System.Collections.Generic.IEnumerable%601> a generuje posloupnost řetězců, jako jsou požadovány.

Tyto metody iterátoru teď použijte k vytvoření balíčku karet. Umístíte dotazu LINQ v našich `Main` metody. Tady se můžete podívat na to:

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

Násobek `from` klauzule vytvářejí <xref:System.Linq.Enumerable.SelectMany%2A>, vytváří jeden pořadí z kombinace každý prvek v první řadě se každý prvek v druhé pořadí. Pořadí je důležité pro naše účely. První prvek v první zdrojové sekvence (barvy) číslo zkombinuje s každý prvek v druhé pořadí (pořadí). Tímto se vytvoří všechny karty třináct první barvy. Tento proces se opakuje ke každému elementu v první řadě (barvy). Konečný výsledek je balíčku karet seřazené podle barvy, za nímž následuje hodnoty.

Je důležité mít na paměti, že ať rozhodnout pro zápis LINQ v syntaxi dotazů využité nad nebo použití syntaxe využívající metody místo toho, je vždy možné přejít z jednu formu syntaxe na druhý. Výše uvedené dotazy napsané v syntaxi dotazů je možné psát v syntaxe využívající metody jako:
```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```
Kompilátor překládá příkazy LINQ, které jsou napsané v syntaxi dotazů v syntaxi volání ekvivalentní metody. Bez ohledu na vaši volbu syntaxe proto dvě verze dotaz přinesou stejný výsledek. Zvolte, které syntaxe je nejvhodnější pro vaši situaci: pro instanci, pokud pracujete v týmu, kde některé členy mají potíže s syntaxe využívající metody, zkuste raději pomocí syntaxe dotazu.

Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto okamžiku. Zobrazí se všechny 52 karty z balíčku. Může být pro vás velmi užitečné v ladicím programu sledovat tuto ukázku spustit jak `Suits()` a `Ranks()` provedení metody. Je jasně vidět, že každého řetězce v každé pořadí se vygeneruje pouze dle potřeby.

![Okno konzoly aplikace výpisu 52 karet](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulace s pořadí

V dalším kroku se zaměřují na způsob se chystáte shuffle karty z balíčku. Prvním krokem při libovolné vhodné shuffle je rozdělit z balíčku ve dvou. <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> metody, které jsou součástí rozhraní API LINQ poskytují tuto funkci za vás. Je pod umístit `foreach` smyčka:

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

Neexistuje však žádná metoda shuffle výhod ve standardní knihovně, proto budete muset napsat vlastní. Shuffle metodu, kterou vytvoříte ukazuje několik technik, které budete používat s aplikací založených na LINQ, každá součást tohoto procesu bude popsanou v krocích.

Chcete-li přidat některé funkce, jak pracovat <xref:System.Collections.Generic.IEnumerable%601> získáte zpět z dotazů LINQ, budete muset napsat nějakou zvláštní druhy metod volá [rozšiřující metody](../../csharp/programming-guide/classes-and-structs/extension-methods.md). Stručně řečeno, rozšiřující metoda je zvláštní účely *statickou metodu* , který přidává nové funkce na typ, který již existuje bez nutnosti upravovat původní typ, který chcete přidat funkce.

Rozšiřující metody poskytují nový domov tak, že přidáte nový *statické* soubor třídy do vaší aplikace s názvem `Extensions.cs`a pak začít vytvářet out první – metoda rozšíření: 

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

Podívejte se na podpis metody na chvíli zastavíme, konkrétně parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Zobrazí se přidání `this` modifikátor v prvním argumentu k metodě. To znamená, že volání metody, jako by šlo o metodu člen typu prvního argumentu. Tato metoda také následuje po deklaraci standardní idiom kde vstupní a výstupní typy jsou `IEnumerable<T>`. Že postup umožňuje metody LINQ na možné zřetězit dohromady a provádět složitější dotazy.

Přirozeně protože rozdělení z balíčku na polovina se uloží, bude potřeba připojit k těmto polovina se uloží společně. V kódu, to znamená, že je budete výčet, obě sekvencí, které jste získali prostřednictvím <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> najednou, *`interleaving`* elementy a vytvoření jednoho pořadí: vaše nyní – které se náhodně pomíchají balíčku karet. Zápis LINQ metodu, která funguje s dvěma sekvencemi vyžaduje pochopit, jak <xref:System.Collections.Generic.IEnumerable%601> funguje.

<xref:System.Collections.Generic.IEnumerable%601> Rozhraní má jednu metodu: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. Objekt vrácený rutinou <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci. Tyto dva členy použije k vytvoření výčtu kolekce a vrátí prvky. Tato metoda prokládání bude metodu iterátoru, místo vytváření kolekce a vrátí kolekci, které použijete `yield return` syntaxe uvedené výše.

Tady je implementace této metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a shuffle jednou z balíčku:

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

Kolik podle okolí posouvá trvá, než k nastavení z balíčku zpět na jeho původní pořadí? Chcete-li zjistit, budete potřebovat napíše metoda, která určuje, jestli dvě sekvence jsou stejné. Jakmile budete mít tuto metodu, budete muset umístěte kód, který posouvá z balíčku ve smyčce a zkontrolujte, pokud je balíček zpět v pořadí.

Zápis metodou ke zjištění, jestli dané dvě sekvence jsou stejné by měl být jednoduché. Je podobné struktury metody, který jste napsali přesouvat z balíčku. Pouze to čas, namísto `yield return`ing každý prvek budete porovnávat odpovídajících prvků každé posloupnosti. Když celé sekvenci vytvoření výčtu, pokud každý prvek odpovídá, sekvencí jsou stejné:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Zobrazí se druhé idiom LINQ: terminálu metody. Přijmout sekvenci jako vstup (nebo v tomto případě dvou sekvencí) a vrátí jednu skalární hodnotu. Při použití terminálu metody, jsou vždy finální metoda v řetězci metody pro LINQ dotaz, tedy název "terminálu". 

Vidíte to v akci při použití pro určení, kdy z balíčku je zpět do její původní pořadí. Shuffle kód uvnitř smyčky a zastavit, když sekvence je zpět do její původní pořadí s použitím `SequenceEquals()` metody. Vidíte, že by měl být vždy finální metoda každého dotazu, protože se vrací jedinou hodnotu místo sekvenci:

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

Spusťte kód nechte zatím a poznamenejte si hodnotu jak z balíčku uspořádá na každý náhodně. Po 8 podle okolí posouvá (iterací provést-smyčku while), balíček vrátí původní konfiguraci, v jaké byl při jeho prvním vytvoření počátečního dotazu LINQ.

## <a name="optimizations"></a>Optimalizace

Ukázka, začlenění zatím provede *si shuffle*, kde horní a dolní části karty zůstat stejná při každém běhu. Vytvoříme jednu změnu: použijeme *v shuffle* místo, kde všechny 52 karty změní pozici. Pro v náhodně, můžete prokládání z balíčku tak, aby první karta v dolní polovině stane první karta balíčku. To znamená, že poslední karty v horní polovině stane dolní části karty. Jedná se o jednoduchou změnu singulární řádek kódu. Aktualizovat aktuální dotaz shuffle díky přepínání podle polohy <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>. Tím se změní pořadí horní a dolní polovinami z balíčku:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Spusťte program znovu, a uvidíte, že trvá 52 iterací z balíčku můžete změnit pořadí samotný. Budete také začít Všimněte si, že některé jak výkon jako program nadále běží.

Existuje několik důvodů. Můžete řešit jeden z hlavních příčin toto snížení výkonu: neefektivní používání šablon [ *opožděné vyhodnocení*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Stručně řečeno opožděné vyhodnocení uvádí, že se neprovádí vyhodnocení výrazu, dokud jeho hodnota je potřeba. Dotazy LINQ jsou příkazy, které jsou vyhodnocovány laxně. Sekvence jsou generovány pouze v případě, že prvky jsou požadovány. Který je obvykle hlavní výhodou LINQ. Ale používá jako je například tento program, to způsobí, že exponenciální růst v čase spuštění.

Mějte na paměti, že jsme generována z původního balíčku pomocí dotazu LINQ. Každý shuffle je generována pomocí provádí tři LINQ dotazy na předchozí balíčku. Všechny tyto laxně probíhají. To také znamená, že se že provádějí se znovu pokaždé, když je požadováno sekvence. Podle času, který jste získali 52nd iteraci můžete se znova se generuje z původního balíčku mnoho, v mnoha případech. Napíšeme protokolu demonstrují toto chování. Nakonec vám to vyřešíme.

Ve vaší `Extensions.cs` soubor, zadejte nebo zkopírujte následující metody. Tato metoda rozšíření vytvoří nový soubor s názvem `debug.log` v adresáři projektu a záznamů je právě prováděna jaký dotaz do souboru protokolu. Tato metoda rozšíření může být přidán k jakýkoli dotaz k označení, že dotaz proveden.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

V dalším kroku instrumentace definici každého dotazu s zprávu protokolu:

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

Všimněte si, že není přihlásíte pokaždé, když se přístup k dotazu. Přihlášení jenom při vytváření původního dotazu. Program stále trvá dlouhou dobu pro spuštění, ale teď se zobrazí důvod, proč. Pokud vyčerpáte trpělivost s protokolování zapnuté, přepínač mimo shuffle v náhodně. Dál uvidíte účinky opožděné vyhodnocení. Během jednoho spuštění se provede 2592 dotazů, včetně všech generování hodnoty a barvy.

Můžete zvýšit výkon kódu tady ke snížení počtu spuštění, které provedete. Můžete provést jednoduché opravy je *mezipaměti* výsledky původního dotazu LINQ, který Konstruuje balíčku karet. V současné době provedete dotazy znovu a znovu pokaždé, když-když smyčce prochází iterace, opětovné vytváření balíčku karet a resshuffling ho pokaždé, když. Pro ukládání do mezipaměti balíčku karet, můžete využít metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> a <xref:System.Linq.Enumerable.ToList%2A>; Pokud připojit dotazů, že budete provádět stejné akce, které jim má, ale teď budete ukládají výsledky v poli, nebo seznam, v závislosti na tom, jakou metodu můžete volat. Append – metoda LINQ <xref:System.Linq.Enumerable.ToArray%2A> na dotazy a znovu spustit program:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Nyní je mimo shuffle až 30 dotazy. Spusťte znovu s v shuffle a zobrazí se vám podobná vylepšení: teď provede 162 dotazy.

Upozorňujeme, že v tomto příkladu je **navržené** zvýrazněte případy použití, pokud opožděné vyhodnocení může způsobit potíže s výkonem. I když je důležité, pokud chcete zobrazit, pokud opožděné vyhodnocení může mít vliv na výkon kódu, je stejně důležité, abyste pochopili, že ne všechny dotazy vykonat například. Výkon přístupů, které se vám účtovat bez použití <xref:System.Linq.Enumerable.ToArray%2A> je vzhledem k tomu, že každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání. Použití opožděné vyhodnocení znamená každou novou konfiguraci balíčku je sestaven z původního balíčku, i spouští kód, který založená `startingDeck`. Který způsobí, že velké množství práce navíc. 

V praxi některé algoritmy spustit také pomocí nemůžou dočkat, až hodnocení a jiné systém dobře při používání opožděné vyhodnocení. Za denní využití opožděné vyhodnocení je obvykle lepší volbou, pokud je zdroj dat jako samostatný proces, jako je databázový stroj. Pro databáze opožděné vyhodnocení umožňuje vytvářet složitější dotazy spuštění pouze jedné odezvy k procesu databáze a zpět do zbytku kódu. LINQ je flexibilní, jestli rozhodnete využívat opožděné nebo nemůžou dočkat, až hodnocení, tak měření vašich procesů a vyberte si libovolný typ vyhodnocení poskytuje nejlepší výkon.

## <a name="conclusion"></a>Závěr

V tomto projektu pro vás řešení:
* pomocí dotazů LINQ pro agregovaná data na smysluplné sekvenci
* zápis rozšiřující metody pro přidání našich vlastních funkcí do dotazů LINQ
* Vyhledání oblastí v našem kódu, kde náš dotazů LINQ narazit na problémy s výkonem, jako je snížení rychlosti
* opožděné a nemůžou dočkat, až hodnocení související s dotazy LINQ a důsledky mohou mít na výkon dotazů

Kromě LINQ jste se dozvěděli něco o použití magicians techniku pro triky karty. Magicians Faro shuffle použít, protože můžete určit, kde prochází všechny karty z balíčku. Když teď víte, nemusíte ho znehodnotit pro všechny ostatní!

Další informace o LINQ naleznete v tématu:
* [LINQ (Language Integrated Query)](../programming-guide/concepts/linq/index.md)
    * [Úvod do jazyka LINQ](../programming-guide/concepts/linq/introduction-to-linq.md)
    * [Začínáme s dotazy LINQ vC#](../programming-guide/concepts/linq/getting-started-with-linq.md)
        - [Základní operace dotazů LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
        - [Transformace dat pomocí LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
        - [Syntaxe využívající dotazy a syntaxe využívající metody v technologii LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
        - [Funkce C# podporující LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
