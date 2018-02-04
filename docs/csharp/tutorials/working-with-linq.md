---
title: "Práce s dotazy LINQ"
description: "V tomto kurzu se naučíte, jak vygenerovat pořadí s dotazy LINQ, zápis metody pro použití v dotazech LINQ a rozlišovat přes a opožděné vyhodnocení."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 3f0fcfebf37d9e6dad52c69111cc5e374ae27183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="working-with-linq"></a>Práce s dotazy LINQ

## <a name="introduction"></a>Úvod

V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#. Naučíte:

*   Jak vygenerovat pořadí s dotazy LINQ
*   Jak napsat metody, které lze snadno použít v dotazech LINQ.
*   Postup rozlišovat přes a opožděné vyhodnocení.

Tyto postupy získáte informace podle budovy aplikaci, která představuje jednu základní dovednosti žádné magician: [faro náhodně](https://en.wikipedia.org/wiki/Faro_shuffle). Stručně řečeno náhodně faro jde o techniku, kde rozdělení karet přesně v polovině a pak náhodně interleaves každou kartu jeden z každého půl znovu sestavit v původní podlaží.

Magicians použijte tento postup, protože každou kartu, je v zadaném umístění po každé náhodně a pořadí je opakující se vzorek. 

Pro naše účely je slabá hearted podívejte se na manipulace s posloupností data. Aplikace, kterou budete sestavení bude vytvořit karet a poté proveďte posloupnost podle okolí posouvá, zápis pořadí se pokaždé, když. Budete také porovnat aktualizované pořadí, které se původní pořadí.

V tomto kurzu má několik kroků. Po dokončení každého kroku můžete aplikaci spustit a sledovat průběh. Můžete také zjistit [hotová ukázka](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) v úložišti GitHub dotnet/docs. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, OS X nebo v kontejner Docker. Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Nastavit aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Pokud jste nepoužívali C# před, [v tomto kurzu](console-teleprompter.md) vysvětluje struktura programu v C#. Můžete číst a pak se vraťte sem Další informace o LINQ. 

## <a name="creating-the-data-set"></a>Vytváření v datové sadě

Začněme vytvořením balíčku karet. Můžete to udělat pomocí LINQ dotazu, který má dva zdroje (jeden pro čtyři vyhovuje, jeden pro třináct hodnoty). Tyto zdroje budete zkombinovat do 52 karet. A `Console.WriteLine` příkaz uvnitř `foreach` smyčky zobrazí kartách.

Zde je dotaz:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Násobek `from` klauzule vytvořit `SelectMany`, která vytvoří jeden pořadí z kombinace každý prvek v první pořadí s každý prvek v druhé pořadí. Pořadí je důležité pro naše účely. Prvním elementem v první zdrojové sekvence (sady) spolu s každý element v druhé pořadí (hodnoty). To vytváří všechny třináct karty první barvy. Tento postup se opakuje se každý prvek v první pořadí (sady). Konečný výsledek je balíčku karet seřazené podle sady, za nímž následuje hodnoty.

Potom budete muset vytvořit metody Suits() a Ranks(). Začneme skutečně jednoduchou sadou *iterator metody* , generovat pořadí, jako Výčtový řetězce:

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

Tyto dvě metody jak využívat `yield return` syntaxe vytvořit sekvenci při spuštění. Kompilátor vytvoří objekt, který implementuje `IEnumerable<T>` a generuje pořadí řetězce podle jejich požadavku.

Pokračovat a spustit ukázku, kterou jste vytvořili v tomto okamžiku. Zobrazí všechny 52 karet z balíčku. Může být velmi užiteční při spuštění této ukázce v rámci ladicího sledovat jak `Suits()` a `Values()` spuštění metody. Uvidíte je zřejmé, že každý řetězec v každé pořadí je vygenerováno, pouze když jej potřebuje.

![Okno konzoly zobrazující aplikace zápis se 52 karet](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulace s pořadí

V dalším kroku Vytvořme nástroj metodu, která můžete provádět náhodně. Prvním krokem je rozdělit podlaží vede ke dvěma. `Take()` a `Skip()` metody, které jsou součástí rozhraní API LINQ zadejte tuto funkci pro nás:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Metoda náhodně neexistuje v knihovně standardní, budete muset napsat vlastní. Tato nová metoda znázorňuje několik technik, které budete používat s aplikací založených na LINQ můžeme vysvětlují jednotlivých součástí metodu v krocích.

Vytvoří podpis metody *metoda rozšíření*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Metody rozšíření je zvláštní účely *statickou metodu.* Uvidíte přidání `this` modifikátor na první argument pro metodu. To znamená, že zavoláte metodu, jako by šlo metodou member typu prvního argumentu.

Rozšiřující metody lze deklarovat pouze uvnitř `static` třídy, takže umožňuje vytvořit novou statickou třídu s názvem `extensions` pro tuto funkci. Jak budete pokračovat v tomto kurzu, a ty budou umístěny ve stejné třídě přidáte další metody rozšíření.

Následuje také tuto deklaraci metoda standardní stylu, kde jsou typy vstupní a výstupní `IEnumerable<T>`. Aby postup umožňuje LINQ metody možné zřetězit dohromady a provádět složitější dotazy.

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

Budete se vytváření výčtu obě pořadí najednou, prokládání elementy a jeden objekt pro vytváření.  Zápis LINQ metoda, která funguje s dvěma pořadí vyžaduje, že chápete, jak `IEnumerable` funguje.

`IEnumerable` Rozhraní má jedno z těchto metod: `GetEnumerator()`. Objekt vrácený `GetEnumerator()` má metodu pro přesun na další prvek a vlastnosti, která načte aktuálního elementu v pořadí. Tyto dva členy použije výčet kolekce a vrátíte se elementy. Tato metoda prokládání bude metodu iterator tak místo vytváření kolekce a vrácení kolekce, které budete používat `yield return` syntaxe uvedené výše. 

Tady je implementace této metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teď, když jste napsali tuto metodu, vraťte se `Main` metoda a náhodně jednou z balíčku:

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

Podívejme se, kolik podle okolí posouvá trvá nastavit z balíčku zpět na jeho původní pořadí. Budete potřebovat napíše metoda, která určuje, jestli jsou dvě pořadí stejné. Až budete mít dané metody, musíte umístit kód, který posouvá podlaží v smyčky a zkontrolujte, pokud je balíček zpět v pořadí.

Zápis metoda k určení, jestli jsou stejné dvě pořadí by měl být přehledné. Je podobnou strukturou metodě, který jste napsali náhodný výběr balíčku. Pouze tentokrát místo yield vrácení každý prvek, je budete porovnat odpovídající elementy každé sekvence. Když byl výčet celého pořadí, pokud odpovídá každý element, pořadí jsou stejné:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Zobrazí se druhé stylu Linq: terminálu metody. Trvat pořadí jako vstup (nebo v tomto případě dvě pořadí) a vrátí jednu skalární hodnotu. Tyto metody, pokud se používají, jsou vždy poslední metodu dotazu. (Proto název). 

Uvidíte to v praxi při použití k určení, kdy je z balíčku zpět v jeho původní pořadí. Vložte kód náhodně uvnitř smyčky a zastavit, když je pořadí je zpět v jeho původní pořadí s použitím `SequenceEquals()` metoda. Vidíte, že by měl být vždy poslední metodu ve všech dotazu, protože vrátí jednu hodnotu namísto sekvenci:

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

Spustit ukázku a v tématu jak z balíčku Přeuspořádá na každý náhodně, dokud se vrátí do původní konfigurace po 8 iterací.

## <a name="optimizations"></a>Optimalizace

Ukázka, když jste sestavili dosavadní provede *v náhodně*, kde karty horní a dolní zůstaly stejné při každém spuštění. Pojďme si ho změnit a spusťte *se náhodně*, kde všechny 52 karty změní pozici. Pro mimo náhodného, můžete interleave z balíčku tak, aby první karty v dolní polovinu stane první karty v balíčku. To znamená, že poslední karty v horní polovině se změní na spodní kartu. To je právě změnu jeden řádek. Volání náhodný výběr chcete-li změnit pořadí horní a dolní polovina podlaží aktualizace:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Program spusťte znovu a uvidíte, že trvá 52 iterace pro balíček ke změně pořadí sám sebe. Budete také spustit Všimněte některé závažné výkonu degradations program stále spouštět.

Existuje několik důvodů pro tento. Pojďme jednou z hlavních příčin tohoto problému: neefektivní používání *opožděné vyhodnocení*.

LINQ dotazů jsou vyhodnocovány líné. Pořadí jsou generovány pouze jako elementy jsou požadovány. Obvykle, který je hlavní výhodou LINQ. Ale používá jako je tento program, to způsobí, že exponenciální růst v dobu provádění.

Původní podlaží byl vygenerován pomocí dotaz LINQ. Každý náhodně je generován provádění tři dotazů LINQ v předchozí podlaží. Všechny tyto líné probíhají. To také znamená, že je prováděna znovu pokaždé, když je požadovaný sekvenci. Podle času, které máte k 52nd iterace můžete se znovu vygenerovat. původní podlaží mnoho, kolikrát. Můžete napsat protokolu k předvedení toto chování. Budete pak, opravte ji.

Zde je metoda protokolu, která může být přidán k jakýkoli dotaz k označení, že dotaz spustit.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

V dalším kroku instrumentace definici každý dotaz s zprávu protokolu:

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

Všimněte si, že nemáte protokolu pokaždé, když přistupujete k dotazu. Přihlášení jenom v případě, že vytvoříte původní dotaz. Program stále trvá dlouhou dobu spuštění, ale nyní můžete zobrazit důvod, proč. Pokud spouštíte systému trpělivost systémem vnější náhodně s zapnout protokolování, přepněte zpět na vnitřní náhodně. Stále se zobrazí důsledky opožděné vyhodnocení. V prvního spuštění se provede 2592 dotazů, včetně všech generování hodnota a barvy.

Je snadný způsob, jak aktualizovat Vyhněte se všechny tyto spuštění tohoto programu. Způsoby LINQ `ToArray()` a `ToList()` , způsobit dotaz pro spouštění a ukládání výsledků do pole nebo seznam, v uvedeném pořadí. Tyto metody slouží k mezipaměti dat výsledků dotazu než zdrojový dotaz spustit znovu.  Připojit dotazy, které generují balíčky karet pomocí volání `ToArray()` a spusťte dotaz znovu:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Spusťte znovu a vnitřní náhodně je dolů 30 dotazy. Znovu spustit s vnější náhodně a zobrazí se podobné vylepšení. (Je nyní provádí 162 dotazy).

Nemáte nesprávně interpretovat v tomto příkladu důkladným, který by se měl například spouštět všechny dotazy. V tomto příkladu je určena pro zvýrazněte případy použití, kde opožděné vyhodnocení může způsobit problémy s výkonem. Je to způsobeno každý nový uspořádání balíčku karet je sestaven z předchozí uspořádání. Pomocí opožděné vyhodnocení znamená každou novou konfiguraci podlaží vychází z původní balíčku, i provádění kódu, který postavený `startingDeck`. Které způsobí, že velké množství další práci. 

V praxi některé algoritmy spustit mnohem lepší pomocí přes vyhodnocení a jiné systém mnohem lepší pomocí opožděné vyhodnocení. (Obecně platí, opožděné vyhodnocení je mnohem lepší volbou, pokud zdroj dat je samostatný proces, jako je databázový stroj. V takových případech opožděné vyhodnocení umožňuje složitější dotazy provést pouze jednu dobu odezvy pro proces databáze.) LINQ umožňuje opožděné i přes vyhodnocení. Měření a vybrat nejlepší volbou.

## <a name="preparing-for-new-features"></a>Příprava pro nové funkce

Kód, které jste vytvořili pro tato ukázka je příklad vytvoření jednoduchého prototyp, která provádí úlohy. Toto je skvělý způsob, jak prozkoumat problém místa, a pro mnoho funkcí, může být nejlepším řešením trvalé. Jste využít *anonymní typy* pro kartách a každou kartu je reprezentována řetězce.

*Anonymní typy* mají mnoho výhod produktivitu. Nemusíte definovat třídu sami, abyste představují úložiště. Kompilátor generuje typ za vás. Typ kompilátoru generované využívá řadu osvědčené postupy pro jednoduché datové objekty. Má *neměnné*, což znamená, že žádný z jeho vlastnosti lze změnit po byla vytvořená. Anonymní typy jsou interní sestavení, takže nevidí jako součást veřejné rozhraní API pro toto sestavení. Anonymní typy také obsahují přepsání `ToString()` metoda, která vrací řetězec formátovaný s jednotlivých hodnot.

Anonymní typy mít také nevýhody. Nemají přístupné názvy, takže je nejde používat jako návratové hodnoty nebo argumenty. Můžete si všimnout, že obecné metody, které všechny metody vyšší použít tyto anonymní typy jsou. Přepsané `ToString()` nemusí být co chcete použít víc funkcí růstem aplikace. 

Ukázka také používá řetězce pro barvy a pořadí každou kartu. Které je poměrně otevřít zakončeno. Systém typů jazyka C# můžete Pomozte nám lepší kód s využitím `enum` typy pro tyto hodnoty.

Začněte sady. Toto je ideální čas sloužící `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Metoda také změní typ a implementace:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

V dalším kroku stejné změnit s pořadí karet:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

A metoda, která generuje je:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Jako jeden konečné čištění provedeme typu představují karty, aniž byste museli spoléhat na anonymního typu. Anonymní typy jsou velmi vhodné pro typy lightweight, místní, ale v tomto příkladu herní karta je jedním z hlavní koncepty. To by měla být konkrétní typ.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Tento typ používá *automaticky implementované vlastnosti jen pro čtení* které se nastavují v konstruktoru a pak nemůže být upraven. Je také využívá nové *řetězec interpolace* funkce, která usnadňuje výstupní řetězec formátu.

Aktualizace dotazu, který generuje počáteční podlaží používat nový typ:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Kompilace a znovu spusťte. Výstupem je trochu čisticí a kód je trochu trochu objasnit a lze snadno rozšířit.

## <a name="conclusion"></a>Závěr

Tato ukázka vám ukázal, můžete některé metody použité v technologii LINQ, jak vytvořit vlastní metody, které se snadno používat s dotazy LINQ povoleno kódu. Je také ukázal rozdíly mezi opožděné a přes vyhodnocení a o tom, že rozhodnutí může mít na výkon.

Jste se dozvěděli o něco o jeden magician techniku. Magicians pomocí náhodně faro, protože můžou řídit, kdy každou kartu přesune z balíčku. V některých triky magician má člena cílové skupiny umístit karty nad z balíčku a posouvá několikrát, zároveň budete vědět, kde přejde karty. Další illusions vyžadují z balíčku nastavte určitým způsobem. Magician nastaví podlaží před provedením podvodné. Pak se bude náhodně podlaží 5krát pomocí vnitřní náhodně. Na fázi Jana můžete zobrazit, jak vypadá náhodných balíčku, náhodný výběr 3 vícekrát a mít podlaží nastavit, přesně jak chce.
