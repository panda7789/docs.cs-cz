---
title: Práce s jazykem LINQ
description: V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, Zapsat metody pro použití v dotazech LINQ a rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086749"
---
# <a name="working-with-linq"></a>Práce s jazykem LINQ

## <a name="introduction"></a>Úvod

V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core. Získáte informace:

*   Jak vygenerovat pořadí s jazykem LINQ
*   Jak napsat metody, které můžete snadno použít v dotazech LINQ.
*   Jak rozlišovat mezi nemůžou dočkat, až a opožděné vyhodnocení.

Vytvořením aplikace, která ukazuje jednu základní dovednosti jakékoli magician dozvíte těchto technik: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Stručně řečeno náhodně faro je technika, kde rozdělit karet přesně na polovinu a pak shuffle předřadí jednotlivých karet z každého půl k opětovnému sestavení z původního balíčku.

Magicians tento postup použít, protože všechny karty je v zadaném umístění po jednotlivých shuffle a pořadí je s opakováním vzoru. 

Pro naše účely je slabá hearted podívejte se na zpracování data sekvencí. Aplikace, kterou vytvoříte bude sestavení karet a pak proveďte posloupnost podle okolí posouvá, zápis si pokaždé, když je pořadí. Budete také porovnat aktualizované aby původní pořadí.

V tomto kurzu má několik kroků. Po provedení každého kroku můžete spustit aplikaci a sledovat průběh. Můžete zobrazit také [úplnou vzorovou](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) v úložišti dotnet/samples GitHub. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejneru Dockeru. Bude potřeba nainstalovat váš oblíbený editor kódu. Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru. Ale můžete použít jakýkoli nástroje jste obeznámeni.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ujistěte se, že do aktuálního adresáře. Zadejte příkaz `dotnet new console` příkazového řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Pokud jste nikdy C#, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v jazyce C#. Může číst a pak se sem vraťte pro další informace o jazyku LINQ. 

## <a name="creating-the-data-set"></a>Vytvoření datové sady

Začněme vytvořením balíčku karet. Můžete udělat pomocí dotazu LINQ, který má dva zdroje (jeden pro čtyři vyhovuje, jeden pro třináct hodnoty). Tyto zdroje budete zkombinovat do 52 karet. A `Console.WriteLine` výroku uvnitř `foreach` smyčky zobrazí karty.

Tady je dotaz:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Násobek `from` klauzule vytvářejí `SelectMany`, vytváří jeden pořadí z kombinace každý prvek v první řadě se každý prvek v druhé pořadí. Pořadí je důležité pro naše účely. První prvek v první zdrojové sekvence (barvy) číslo zkombinuje s každý prvek v druhé pořadí (hodnoty). Tímto se vytvoří všechny karty třináct první barvy. Tento proces se opakuje ke každému elementu v první řadě (barvy). Konečný výsledek je balíčku karet seřazené podle barvy, za nímž následuje hodnoty.

V dalším kroku budete muset sestavit Suits() a Ranks() metody. Začneme velmi jednoduchou sadu *iterátory* generují sekvenci, jako Výčtový objekt řetězce:

```csharp
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

Tyto dvě metody jak využívat `yield return` syntaxi pro vytvoření sekvence za běhu. Kompilátor vytvoří objekt, který implementuje `IEnumerable<T>` a generuje posloupnost řetězců, jako jsou požadovány.

Pro tuto kompilaci je potřeba na začátek souboru přidejte následující dva řádky:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

Pokračujte a spusťte ukázku, kterou jste vytvořili v tomto okamžiku. Zobrazí se všechny 52 karty z balíčku. Může být pro vás velmi užitečné v ladicím programu sledovat tuto ukázku spustit jak `Suits()` a `Values()` provedení metody. Je jasně vidět, že každého řetězce v každé pořadí se vygeneruje pouze dle potřeby.

![Okno konzoly aplikace výpisu 52 karet](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulace s pořadí

V dalším kroku Vytvořme nástroj metodu, která můžete provést náhodné. Prvním krokem je rozdělit z balíčku ve dvou. `Take()` a `Skip()` metody, které jsou součástí rozhraní API LINQ poskytují tuto funkci pro nás:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Proto budete muset napsat vlastní metodou shuffle neexistuje ve standardní knihovně. Tato nová metoda ukazuje několik technik, které budete používat s aplikacemi na základě LINQ, můžeme vysvětlit jednotlivých součástí metodu v krocích.

Podpis metody vytvoří *– metoda rozšíření*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Metody rozšíření je zvláštní účely *statické metody.* Zobrazí se přidání `this` modifikátor v prvním argumentu k metodě. To znamená, že volání metody, jako by šlo o metodu člen typu prvního argumentu.

Metody rozšíření lze deklarovat pouze uvnitř `static` třídy, můžeme vytvořit novou statickou třídu s názvem `extensions` pro tuto funkci. Přidejte další metody rozšíření budete pokračovat v tomto kurzu, a ty budou umístěny ve stejné třídě.

Tato metoda také následuje po deklaraci standardní idiom kde vstupní a výstupní typy jsou `IEnumerable<T>`. Že postup umožňuje metody LINQ na možné zřetězit dohromady a provádět složitější dotazy.

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

Budete výčet obou pořadí najednou, prokládání prvky a vytvoření jednoho objektu.  Zápis LINQ metodu, která funguje s dvěma sekvencemi vyžaduje pochopit, jak `IEnumerable` funguje.

`IEnumerable` Rozhraní má jednu metodu: `GetEnumerator()`. Objekt vrácený rutinou `GetEnumerator()` má metodu pro přesun na další prvek a vlastnost, která načte aktuální prvek v sekvenci. Tyto dva členy použije k vytvoření výčtu kolekce a vrátí prvky. Tato metoda prokládání bude metodu iterátoru, místo vytváření kolekce a vrátí kolekci, které použijete `yield return` syntaxe uvedené výše. 

Tady je implementace této metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a shuffle jednou z balíčku:

```csharp
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

Podívejme se, kolik podle okolí posouvá trvá, než k nastavení z balíčku zpět do její původní pořadí. Musíte se napíše metoda, která určuje, jestli dvě sekvence jsou stejné. Jakmile budete mít tuto metodu, budete muset umístěte kód, který posouvá z balíčku ve smyčce a zkontrolujte, pokud je balíček zpět v pořadí.

Zápis metodou ke zjištění, jestli dané dvě sekvence jsou stejné by měl být jednoduché. Je podobné struktury metody, který jste napsali přesouvat z balíčku. Jenom tento čas namísto yield vrácení každého prvku, budete porovnáte odpovídajících prvků každé posloupnosti. Když celé sekvenci vytvoření výčtu, pokud každý prvek odpovídá, sekvencí jsou stejné:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Zobrazí se druhé idiom Linq: terminálu metody. Přijmout sekvenci jako vstup (nebo v tomto případě dvou sekvencí) a vrátí jednu skalární hodnotu. Tyto metody, když se používají, jsou vždy poslední metodu dotazu. (Tedy název). 

Vidíte to v akci při použití pro určení, kdy z balíčku je zpět do její původní pořadí. Shuffle kód uvnitř smyčky a zastavit, když sekvence je zpět do její původní pořadí s použitím `SequenceEquals()` metody. Vidíte, že by měl být vždy finální metoda každého dotazu, protože se vrací jedinou hodnotu místo sekvenci:

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

Spusťte ukázku a zjistěte, jak z balíčku uspořádá na každý shuffle, dokud se vrátí do původní konfigurace po 8 iteracích.

## <a name="optimizations"></a>Optimalizace

Ukázka, začlenění zatím provede *si shuffle*, kde horní a dolní části karty zůstat stejná při každém běhu. Pojďme si ho změnit a spusťte *v shuffle*, kde všechny 52 karty změní pozici. Pro v náhodně, můžete prokládání z balíčku tak, aby první karta v dolní polovině stane první karta balíčku. To znamená, že poslední karty v horní polovině stane dolní části karty. To je jen jeden řádek změnit. Volání přesouvat, chcete-li změnit pořadí horní a dolní polovinami z balíčku aktualizace:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Spusťte program znovu, a uvidíte, že trvá 52 iterací z balíčku můžete změnit pořadí samotný. Budete také začít Všimněte si, že některé jak výkon jako program nadále běží.

Existuje několik důvodů. Pojďme zodpovědět jednou z hlavních příčin: neefektivní používání šablon *opožděné vyhodnocení*.

Laxně vyhodnocují dotazů LINQ. Sekvence jsou generovány pouze v případě, že prvky jsou požadovány. Který je obvykle hlavní výhodou LINQ. Ale používá jako je například tento program, to způsobí, že exponenciální růst v čase spuštění.

Z původního balíčku byl vygenerován pomocí dotazu LINQ. Každý shuffle je generována pomocí provádí tři LINQ dotazy na předchozí balíčku. Všechny tyto laxně probíhají. To také znamená, že se že provádějí se znovu pokaždé, když je požadováno sekvence. Podle času, který jste získali 52nd iteraci můžete se znova se generuje z původního balíčku mnoho, v mnoha případech. Napíšeme protokolu demonstrují toto chování. Nakonec vám to vyřešíme.

Tady je protokol metody, která může být přidán do jakéhokoli dotazu k označení, že dotaz proveden.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

V dalším kroku instrumentace definici každého dotazu s zprávu protokolu:

```csharp
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
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
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

Všimněte si, že není přihlásíte pokaždé, když se přístup k dotazu. Přihlášení jenom při vytváření původního dotazu. Program stále trvá dlouhou dobu pro spuštění, ale teď se zobrazí důvod, proč. Pokud spustíte navýšení kapacity o trpělivost spuštění vnitřního shuffle s zapnout protokolování, přepněte zpátky na vnější náhodně. Dál uvidíte účinky opožděné vyhodnocení. Během jednoho spuštění se provede 2592 dotazů, včetně všech generování hodnoty a barvy.

Je snadný způsob, jak aktualizovat, aby všechny tyto spuštění tohoto programu. Způsoby LINQ `ToArray()` a `ToList()` , který způsobit spustit dotaz a výsledky uložíme v poli, nebo seznam, v uvedeném pořadí. Pomocí těchto metod místo znovu provést dotaz na zdroj dat výsledků dotazu do mezipaměti.  Připojit dotazy, které generují balíčky karet pomocí volání `ToArray()` a spusťte dotaz znovu:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Spusťte znovu a vnější shuffle je až 30 dotazy. Spusťte znovu s vnitřní shuffle a zobrazí se vám podobná vylepšení. (Je nyní spuštěn 162 dotazy).

V tomto příkladu není interpretuje důkladným, který by měly být například spuštěny všechny dotazy. V tomto příkladu je navržen pro zvýraznění případy použití, pokud opožděné vyhodnocení může způsobit potíže s výkonem. Důvodem je, každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání. Použití opožděné vyhodnocení znamená každou novou konfiguraci balíčku je sestaven z původního balíčku, i spouští kód, který založená `startingDeck`. Který způsobí, že velké množství práce navíc. 

V praxi některé algoritmy spustit mnohem lepší pomocí nemůžou dočkat, až hodnocení a jiné systém mnohem lepší pomocí opožděné vyhodnocení. (Obecně platí, opožděné vyhodnocení je mnohem lepší volbou, pokud je zdroj dat jako samostatný proces, jako je databázový stroj. V takových případech opožděné vyhodnocení umožňuje složitější dotazy provádět jenom jednu výměnu zpráv pro proces databáze.) LINQ umožňuje opožděné a nemůžou dočkat, až hodnocení. Měřte a vybrat nejlepší volbou.

## <a name="preparing-for-new-features"></a>Příprava pro nové funkce

Kód, který jste zadali pro tuto ukázku je příklad vytvoření jednoduchého prototyp, která provádí úlohy. To je skvělý způsob, jak prozkoumat problém místa, a pro mnoho funkcí, může být nejlepším řešením trvalé. Jste využít *anonymní typy* pro karty a každá karta představuje řetězce.

*Anonymní typy* mají mnoho výhod produktivitu. Není nutné definovat třídu sami sebe k reprezentaci úložiště. Kompilátor generuje typ za vás. Typ generovaný kompilátorem využívá mnoho osvědčených postupů pro jednoduché datové objekty. Má *neměnné*, což znamená, že žádná z její vlastnosti lze změnit poté, co byl vytvořen. Anonymní typy jsou interní v sestavení, takže nejsou uvedené jako součást veřejné rozhraní API pro toto sestavení. Anonymní typy také obsahují přepsání `ToString()` metodu, která vrací formátovaný řetězec s všechny hodnoty.

Anonymní typy mají také nevýhody. Nemají dostupné názvy, abyste je nelze používat jako návratové hodnoty nebo argumenty. Můžete si všimnout, že všechny metody výše, které používají tyto anonymní typy jsou obecné metody. Přepsané `ToString()` nemusí být žádoucí podle rozšiřování aplikace přidané další funkce. 

Ukázka také používá řetězce pro barvu a řazení jednotlivé karty. Který je poměrně otevřete byl ukončen. Systém typů jazyka C# nám můžete pomoct dokumenty lepší kód s využitím `enum` typy pro tyto hodnoty.

Začněte barvy. To je ten správný čas určený `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Metoda také změní typ a implementace:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

V dalším kroku proveďte stejnou změnu s pořadí karet:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

A metoda, která generuje je:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Jako jeden konečný vyčištění vytvoříme typ pro reprezentaci karty, aniž byste museli spoléhat na anonymního typu. Anonymní typy se skvěle hodí pro lightweight, místní typy, ale v tomto příkladu hrací karty je jedním z hlavní koncepty. Ji by měl být konkrétního typu implementujícího typ.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Tento typ používá *automaticky implementované vlastnosti jen pro čtení* se nastavují v konstruktoru a následně nelze upravit. Je také využívá [interpolace](../language-reference/tokens/interpolated.md) funkce, která usnadňuje výstupní řetězec formátu.

Aktualizujte dotaz, který generuje výchozí balíček použít nový typ:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Zkompilujte a spusťte znovu. Výstup je trochu čisticího modulu a kód je o něco trochu objasnit a je možné snadno rozšířit.

## <a name="conclusion"></a>Závěr

Tuto ukázku jsme si ukázali, můžete některé z metod používaných v LINQ, jak vytvořit vlastní metody, které se snadno používat s dotazy LINQ povoleno kódu. Je také ukázal rozdíly mezi opožděné a nemůžou dočkat, až hodnocení a rozhodnutí může mít na výkon vliv.

Jste se dozvěděli něco o jedné magician technika. Magicians faro shuffle použít, protože můžete určit, kde prochází všechny karty z balíčku. V některé tipy magician má členem cílové skupiny umístit karta na balíčku a uspořádá několikrát, znalost, kdy dostane tuto kartu. Další illusions vyžadovat z balíčku sady určitým způsobem. Magician nastaví z balíčku před provedením zdvih. Pak si bude náhodně z balíčku pomocí 5krát vnější shuffle. Na fázi může zobrazit, jak vypadá náhodné balíčku, náhodný výběr 3 víckrát a z balíčku nastavte přesně jak chce mít.
