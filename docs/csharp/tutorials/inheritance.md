---
title: Dědičnost v jazyce C#
description: Naučte se používat dědičnosti knihovny jazyka C# a v aplikacích.
author: rpetrusha
ms.author: ronpet
ms.date: 08/16/2017
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 1476425594e55531fdb56de531ee61808dccd7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365758"
---
# <a name="inheritance-in-c-and-net"></a>Dědičnost v C# a rozhraní .NET

Tento kurz vás seznámí s dědičnosti v jazyce C#. Dědičnost je funkce objektově orientované programovací jazyky, která vám umožní zadat základní třídu, která poskytuje konkrétní funkce (dat a chování) a definovat odvozené třídy, které dědí nebo přepsání této funkce.

## <a name="prerequisites"></a>Požadavky

Tento kurz předpokládá, že jste nainstalovali .NET Core. Pokyny k instalaci naleznete v tématu [Průvodce instalací .NET Core](https://www.microsoft.com/net/core). Musíte také editor kódu. Tento kurz používá [Visual Studio Code](https://code.visualstudio.com), přestože je možné použít libovolný editor kódu podle svého výběru.

## <a name="running-the-examples"></a>Spuštění příkladů

Chcete-li vytvořit a spustit v příkladech v tomto kurzu, je použít [dotnet](../../core/tools/dotnet.md) nástroj z příkazového řádku. Pomocí těchto kroků pro každý příklad:

1. Vytvořte adresář k uložení v příkladu.
1. Zadejte [novou konzolu pro dotnet](../../core/tools/dotnet-new.md) příkazu na příkazovém řádku k vytvoření nového projektu .NET Core.
1. Zkopírujte a vložte kód z příkladu do vašeho kódu editoru.
1. Zadejte [dotnet obnovení](../../core/tools/dotnet-restore.md) příkazu z příkazového řádku k načtení nebo obnovte závislosti projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Zadejte [dotnet spustit](../../core/tools/dotnet-run.md) příkaz pro zkompilování a spuštění v příkladu.


## <a name="background-what-is-inheritance"></a>Pozadí: Co je dědičnosti?

*Dědičnost* je jedním z základní atributy objektově orientované programování. Umožňuje definovat podřízené třídu, která opětovně používá (dědí), rozšiřuje nebo mění chování nadřazené třídy. Je volána třídu, jejíž členové jsou děděné *základní třída*. Třídu, která dědí členy základní třídy se nazývá *odvozené třídy*.

C# a rozhraní .NET podporují *jedna dědičnost* pouze. To znamená třídu může dědit vlastnosti pouze z jedné třídy. Dědičnost je však přenositelné, který umožňuje definovat hierarchie dědičnosti pro sadu typů. Jinými slovy, zadejte `D` může dědit vlastnosti z typu `C`, který dědí od typu `B`, který dědí od typu základní třídy `A`. Protože je dědičnosti přenositelné, členy typu `A` jsou k dispozici na typ `D`.

Ne všechny členy základní třídy jsou děděné odvozené třídy. Nejsou zděděné následující členy:

- [Statické konstruktory](../programming-guide/classes-and-structs/static-constructors.md), který inicializovat statických dat třídy.

- [Instance konstruktory](../programming-guide/classes-and-structs/constructors.md), která se volá vytvořit novou instanci třídy. Každá třída musí definovat vlastní konstruktory.

- [Finalizační metody](../programming-guide/classes-and-structs/destructors.md), které jsou volány uvolňování paměti modulu runtime zrušení instance třídy.

Při odvozené třídy dědí všechny ostatní členy základní třídy, bez ohledu na jejich, jestli jsou viditelné závisí na jejich usnadnění. Člen usnadnění ovlivňuje jeho viditelnost odvozené třídy následujícím způsobem:

- [Privátní](../language-reference/keywords/private.md) členové jsou viditelné pouze v odvozených třídách, které jsou vnořené v jejich základní třídy. Jinak nejsou viditelné v odvozených třídách. V následujícím příkladu `A.B` je vnořená třída odvozená z `A`, a `C` je odvozena z `A`. Privátní `A.value` pole je viditelné v A.B. Ale pokud odeberete komentářů ze `C.GetValue` metoda a pokus o zkompilování příkladu vyvolá chyba kompilátoru CS0122: "'A.value' je nedostupná v důsledku úrovně ochrany."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chráněné](../language-reference/keywords/protected.md) členové jsou viditelné pouze v odvozených třídách.

- [Interní](../language-reference/keywords/internal.md) členové jsou viditelné pouze v odvozených třídách, které se nacházejí ve stejném sestavení jako základní třídy. Nebyly viditelné v odvozených třídách umístěný v jiném sestavení ze základní třídy.

- [Veřejné](../language-reference/keywords/public.md) členové jsou viditelné v odvozených třídách a jsou součástí veřejné rozhraní odvozené třídy. Veřejné zděděné členy nelze volat, stejně, jako kdyby byly definovány v odvozené třídě. V následujícím příkladu třída `A` definuje metodu s názvem `Method1`a třída `B` dědí z třídy `A`. V příkladu pak zavolá `Method1` jako by šlo metodu instance na `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Odvozené třídy mohou také *přepsat* zděděné členy tím, že poskytuje alternativní implementace. Aby bylo možné přepsat členem, musí být označen člen v základní třídě [virtuální](../language-reference/keywords/virtual.md) – klíčové slovo. Ve výchozím nastavení, členy základní třídy nejsou označeny jako `virtual` a nelze ji přepsat. Probíhá pokus o přepsání nevirtuálních člena, stejně jako v následujícím příkladu, vygeneruje Chyba kompilátoru CS0506: "<member> nejde přepsat zděděného členu <member> protože není označena jako virtuální, abstraktní, nebo potlačit.

```csharp
public class A
{
    public void Method1()
    {
        // Do something.
    }
}

public class B : A
{
    public override void Method1() // Generates CS0506.
    {
        // Do something else.
    }
}
```

V některých případech odvozené třídě *musí* přepsat implementaci základní třídy. Členy třídy, které jsou označené jako základní [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo vyžadují, aby odvozené třídy nepřepíšete. Pokus o kompilovat v následujícím příkladu vygeneruje Chyba kompilátoru CS0534, "<class> neimplementuje zděděného členu abstraktní <member>', protože třída `B` poskytuje žádné implementaci pro `A.Method1`.

```csharp
public abstract class A
{
    public abstract void Method1();
}

public class B : A // Generates CS0534.
{
    public void Method3()
    {
        // Do something.
    }
}
```

Dědičnost platí jenom pro třídy a rozhraní. Další typ kategorie (struktury, delegáti a výčty) nepodporují dědičnosti. Z toho důvodu pokusu kompilace kódu takto vytváří Chyba kompilátoru CS0527: "Typ"typ hodnoty' v seznamu rozhraní není rozhraní." Chybová zpráva znamená, že i když můžete definovat rozhraní, která implementuje struktury, dědičnosti není podporovaný.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Implicitní dědičnosti

Kromě toho všechny typy, které mohou dědit z prostřednictvím jedna dědičnost, všechny typy v rozhraní .NET typ systému implicitně dědí z <xref:System.Object> nebo typ z něj odvozenou. To zajistí, že běžné funkce je k dispozici k libovolnému typu.

Pokud chcete zobrazit, jaké implicitní dědičnosti znamená, že umožňuje definovat novou třídu, `SimpleClass`, který je jednoduše definici prázdné třídy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Můžeme využít reflexe (které umožňují nám zkontrolovat typu metadat k načtení informací o typu) Chcete-li získat seznam členů, které patří do `SimpleClass` typu. I když jsme nebyly definovány žádné členy v našem `SimpleClass` třída, výstup z příkladu znamená, že je ve skutečnosti má devět členů. Jedním z nich je konstruktor bez parametrů (nebo výchozí), který automaticky poskytnutý `SimpleClass` typ kompilátorem C#. Zbývající osm jsou členy <xref:System.Object>, typ, ze kterého všechny třídy a rozhraní .NET systém typů nakonec implicitně dědit vlastnosti.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Implicitní dědění ze <xref:System.Object> třídu, můžete tyto metody `SimpleClass` třídy:

- Veřejnosti `ToString` metody, která převádí `SimpleClass` objektu na řetězcovou reprezentaci, vrátí typ plně kvalifikovaný název. V takovém případě `ToString` metoda vrátí řetězec "SimpleClass".

- Tři metody, které testování rovnosti dvou objektů: veřejné instance `Equals(Object)` metoda, veřejné statické `Equals(Object, Object)` metoda a veřejné statické `ReferenceEquals(Object, Object)` metoda. Ve výchozím nastavení tyto metody testování rovnosti odkazů; To znamená si rovny dvě proměnné objektu musí odkazovat na stejný objekt.

- Veřejnosti `GetHashCode` metodu, která vypočítá hodnotu, která umožňuje instanci typu, který se má použít v kolekcích hash.

- Veřejnosti `GetType` metoda, která vrátí hodnotu <xref:System.Type> objekt, který reprezentuje `SimpleClass` typu.

- Chráněného <xref:System.Object.Finalize%2A> metodu, která slouží k uvolnění nespravovaných prostředků, než je paměť objektu uvolnit modulem garbage collector.

- Chráněného <xref:System.Object.MemberwiseClone%2A> metodu, která vytvoří bez podstruktury klon aktuálního objektu.

Z důvodu implicitní dědičnosti říkáme žádné zděděného členu z `SimpleClass` stejně, jako by byl ve skutečnosti členem objektu je definována v `SimpleClass` třídy. Například v následujícím příkladu volání `SimpleClass.ToString` metoda, která `SimpleClass` dědí z <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Následující tabulka obsahuje seznam kategorií typů, které můžete vytvořit v jazyku C# a typy, ze kterých budou implicitně dědí. Každý základní typ zpřístupní jinou sadu členů prostřednictvím dědičnosti implicitně odvozené typy.

| Typ kategorie | Implicitně dědí z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| třída         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegát      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dědičnost a "je" relace

Obvykle se používá dědičnosti vyjádřit "je" vztah mezi základní třídou a jeden nebo více odvozené třídy, které jsou odvozené třídy specializované verze základní třídy; odvozená třída je typu základní třídy. Například `Publication` třída reprezentuje publikace libovolného typu a `Book` a `Magazine` třídy představují konkrétní typy publikací.

> [!NOTE]
> Třídě nebo struktuře můžete implementovat jednu další rozhraní. Při implementaci rozhraní se často zobrazí jako alternativní řešení pro jedna dědičnost nebo jako způsob použití dědičnosti struktury, je určena k jiné relace ("provést" vztah) mezi rozhraní a jeho implementující typ než express dědičnost. Rozhraní definuje podmnožinu funkcí (například možnost k testování rovnosti k porovnání řazení objektů, nebo pro podporu jazykovou analýzy a formátování), které typy jejího implementující zpřístupní rozhraní.

Všimněte si, že "je" také vyjadřuje vztah mezi typem a konkrétní instanci daného typu. V následujícím příkladu `Automobile` je třída, která má tři jedinečné vlastnosti jen pro čtení: `Make`, výrobce automobilu; `Model`, druh automobilu; a `Year`, jeho rok výroby. Naše `Automobile` třída také obsahuje konstruktor jejichž argumenty jsou přiřazeny k hodnoty vlastností a přepíše <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření řetězec, který jednoznačně identifikuje `Automobile` instance místo `Automobile` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

V takovém případě jsme neměli spoléhat na dědičnosti k reprezentaci značky konkrétní car a modelu. Například můžeme nemusíte definovat `Packard` typ, který má představovat automobilů pocházejí od společnosti Packard Motor Auto. Místo toho jsme může reprezentovat vytvořením `Automobile` objekt s příslušnými hodnotami předaný konstruktor třídy, stejně jako v následujícím příkladu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relace je a podle dědičnosti se nejlépe použije základní třída a odvozené třídy, přidejte další členy do základní třídu nebo, které vyžadují další funkce nejsou k dispozici v základní třídě.

## <a name="designing-the-base-class-and-derived-classes"></a>Navrhování základní třída a odvozené třídy

Podívejme se na vytváření základní třídy a jejich odvozené třídy. V této části se budeme definovat základní třídu, `Publication`, která představuje publikace libovolného typu, například knihy, časopise, novinách, deníku, článku atd. Budeme také definovat `Book` třídu odvozenou od `Publication`. Příklad můžete definovat další odvozené třídy, jako jsme může rozšířit snadno `Magazine`, `Journal`, `Newspaper`, a `Article`.

### <a name="the-base-publication-class"></a>Základní třída publikace

V návrhu naše `Publication` třídy, je třeba mít několik rozhodnutí o návrhu:

- Jaké členy pro zahrnutí do našich základní `Publication` třída a jestli `Publication` členy poskytovat metoda implementace, nebo jestli `Publication` je abstraktní základní třída, která slouží jako šablona pro jejich odvozené třídy.

  V takovém případě `Publication` třída bude poskytovat implementace metoda. [Navrhování abstraktní základní třídy a jejich odvozené třídy](#abstract) část obsahuje příklad, který se používá abstraktní základní třída pro definování metody, které odvozené třídy musí přepsat. Odvozené třídy mohou poskytnout žádnou implementaci, který je vhodný pro odvozený typ.

  Možnost pro opakované použití kódu (tedy více odvozené třídy sdílet deklarace a implementaci základní metody třídy a není potřeba nepřepíšete) je výhoda neabstraktní základní třídy. Proto měli přidávat členy do `Publication` Pokud svůj kód je pravděpodobně sdílí některé nebo nejvíce specializuje `Publication` typy. Pokud se nám nepovedlo Uděláte to tak efektivní, jsme nakonec se museli zadávat implementace z velké části identické člen v odvozených třídách místo jediná implementace v základní třídě. Je potřeba udržovat duplicitní kód v několika umístěních je potenciální příčinu chyby.

  Jak chcete maximalizovat kód opakované použití a vytvoření hierarchie dědičnosti logické a intuitivní, chceme mít jistotu, že jsme zahrnout do `Publication` třídy data a funkce, které jsou společné pro všechny nebo většinu publikace. Odvozené třídy pak implementovat členy, které jsou jedinečné pro konkrétní typy publikace, která představují.

- Jak daleko rozšířit naše hierarchie tříd. Chcete nám vyvíjet hierarchie tři nebo více tříd, nikoli jednoduše základní třída a jeden nebo více odvozené třídy? Například `Publication` může být základní třídě `Periodical`, který je zase základní třídě `Magazine`, `Journal` a `Newspaper`.

  Pro náš příklad použijeme jednoduché hierarchii `Publication` třída a jeden odvozené třídy `Book`. Jsme může snadno rozšířit příklad k vytvoření počet další třídy, které jsou odvozeny od `Publication`, jako například `Magazine` a `Article`.

- Jestli má smysl pro vytvoření instance základní třídy. Pokud ne, jsme by se měly používat [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo k třídě. Pokud je proveden pokus o vytvoření instance třídy označené jako `abstract` – klíčové slovo přímé volání konstruktoru třídy kompilátor jazyka C# generuje chyby CS0144, "Nelze vytvořit instanci abstraktní třídy nebo rozhraní". Pokud je k pokusu vytvořit instanci třídy pomocí reflexe, vrátí metoda reflexe <xref:System.MemberAccessException>. V opačném naše `Publication` může vytvořit instanci třídy voláním konstruktor třídy.

  Ve výchozím nastavení můžete vytvořit instanci základní třídu voláním konstruktor třídy. Všimněte si, že jsme není nutné explicitně definujte konstruktoru třídy. Pokud není přítomen ve zdrojovém kódu základní třídy, kompilátor jazyka C# automaticky poskytuje výchozí konstruktor (bez parametrů).

  Pro náš příklad jsme budete označit `Publication` třídy jako [abstraktní](../language-reference/keywords/abstract.md) tak, aby ji nelze vytvořit instanci.

- Jestli odvozené třídy musí dědit provádění konkrétní členy základní třídy, nebo jestli mají možnost přepsání implementaci základní třídy. Budeme muset použít [virtuální](../language-reference/keywords/virtual.md) – klíčové slovo umožňující odvozené třídy přepsat metodu základní třídy. Ve výchozím nastavení, jsou metody definované v základní třídě *není* přepisovatelné.

- Jestli odvozené třídě představuje poslední třídu v hierarchii dědičnosti a nelze samotné použít jako základní třída pro další odvozené třídy. Ve výchozím nastavení může jakákoli třída sloužit jako základní třída. Můžeme použít [zapečetěné](../language-reference/keywords/sealed.md) – klíčové slovo indikující, že třída nemůže sloužit jako základní třída pro všechny další třídy. Při pokusu o odvození z chyby kompilátoru zapečetěné třídy generované CS0509, "nelze odvodit z zapečetěné typ <typeName>".

  Pro náš příklad jsme budete označit naše odvozené třídy jako `sealed`.

Následující příklad ukazuje, zdrojový kód `Publication` třída, a také `PublicationType` výčet, který je vrácen rutinou `Publication.PublicationType` vlastnost. Kromě členů, které dědí z <xref:System.Object>, `Publication` třída definuje následující členy jedinečný a člen přepisuje:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Protože `Publication` třída je `abstract`, nelze vytvořit instanci přímo z kódu takto:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Však lze volat jeho konstruktoru instance přímo z konstruktorů v odvozené třídě, jako zdrojový kód `Book` třídy ukazuje.

- Dvě vlastnosti související s publikace

  `Title` jen pro čtení <xref:System.String> vlastnost, jehož hodnota je poskytnuta voláním `Publication` konstruktor.

  `Pages` je pro čtení a zápis <xref:System.Int32> má vlastnost, která určuje, kolik celkem stránky publikace. Hodnota je uložena v soukromé pole s názvem `totalPages`. Musí být kladné číslo nebo <xref:System.ArgumentOutOfRangeException> je vyvolána výjimka.

- Související vydavatele členy

  Dvě vlastnosti jen pro čtení, `Publisher` a `Type`. Hodnoty jsou původně poskytl volání `Publication` konstruktoru třídy.

- Publikování související členy

  Dvě metody, `Publish` a `GetPublicationDate`, nastavení a vracení datum publikace. `Publish` Metoda nastaví privátního `published` příznak, který `true` kdy se nazývá a přiřadí datum do ní předán jako argument pro privátní `datePublished` pole. `GetPublicationDate` Metoda vrátí řetězec "NYP", pokud `published` příznak je `false`a hodnota `datePublished` pole, pokud je `true`.

- Copyright související členy

  `Copyright` Metoda přebírá název držitel autorských právech a rok copyrightu jako argumenty a přiřazuje jim `CopyrightName` a `CopyrightDate` vlastnosti.

- Přepsání `ToString` – metoda

  Pokud typ nepřepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda, vrátí plně kvalifikovaný název typu, který je málo použití v rozlišení jednu instanci z jiné. `Publication` Třídy přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> vrátit hodnotu `Title` vlastnost.

Následující obrázek ukazuje vztah mezi naše základní `Publication` třídy a jeho implicitně zděděné <xref:System.Object> třídy.

![Třídy objektu a publikace](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` – Třída

`Book` Třída reprezentuje knihy jako specializované typ publikace. Následující příklad ukazuje, zdrojový kód `Book` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Kromě členů, které dědí z `Publication`, `Book` třída definuje následující členy jedinečný a člen přepisuje:

- Dva konstruktory

  Dva `Book` konstruktory sdílet tři společné parametry. Dva, *název* a *vydavatele*, odpovídají parametry `Publication` konstruktor. Je třetí *Autor*, které se ukládají do privátního `authorName` pole. Obsahuje jeden konstruktor *isbn* parametr, který je uložen v `ISBN` vlastnost automaticky.

  První konstruktor používá [to](../language-reference/keywords/this.md) – klíčové slovo volat jiné konstruktoru. Toto je běžný vzor k definování konstruktory. Konstruktory s méně parametry zadejte výchozí hodnoty při volání metody konstruktor s největší počet parametrů.

  Druhý konstruktor používá [základní](../language-reference/keywords/base.md) – klíčové slovo předat a vydavateli názvu konstruktor základní třídy. Pokud neprovedete explicitní volání konstruktoru základní třídy ve zdrojovém kódu, kompilátor jazyka C# automaticky poskytuje volání výchozí základní třídu nebo konstruktor bez parametrů.

- Jen pro čtení `ISBN` vlastnost, která vrací `Book` objektu mezinárodní standardní číslo knihy, jedinečné nebo 1310místné číslo. ISBN je zadaný jako argument pro jednu z `Book` konstruktory. V poli privátní zálohování, které je automaticky generované kompilátorem je uložený ISBN.

- Jen pro čtení `Author` vlastnost. Jméno autora je zadaný jako argument pro obě `Book` konstruktory a je uložen v privátní `authorName` pole.

- Dvě jen pro čtení související s cenami vlastnosti, `Price` a `Currency`. Jejich hodnoty jsou uvedeny jako argumentů `SetPrice` volání metody. Ceny je uložen v soukromé pole `bookPrice`. `Currency` Vlastnost je symbolu měny ISO třímístné (například USD dolaru USA) a je uložen v privátní `ISOCurrencySymbol` pole. Symboly ISO měny je možné načíst z <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> vlastnost.

- A `SetPrice` metoda, která nastavuje hodnoty `bookPrice` a `ISOCurrencySymbol` pole. Jedná se o hodnoty vrácené `Price` a `Currency` vlastnosti.

- Přepsání `ToString` – metoda (zděděno z `Publication`) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> a <xref:System.Object.GetHashCode%2A> metody (zděděno z <xref:System.Object>).

  Pokud není přepsána, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda testování rovnosti odkazů. Dvě proměnné objektu to znamená, se považují za rovna Pokud odkazují na stejný objekt. U `Book` třídy, na druhé straně dva `Book` objekty by měly být shodné v případě, že mají stejný ISBN.

  Při přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda, je nutné také přepsat <xref:System.Object.GetHashCode%2A> metoda, která vrátí hodnotu, která používá modul runtime ukládá položky do kolekce hash pro efektivní načtení. Hodnota hash by měl vrátit hodnotu, která je konzistentní s testování rovnosti. Vzhledem k tomu, že jsme jste přepsat <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> vrátit `true` Pokud ISBN vlastnosti dva `Book` objekty jsou stejné, se vrací hodnota hash vypočítaného voláním <xref:System.String.GetHashCode%2A> metoda řetězec vrácený `ISBN` vlastnost.

Následující obrázek ukazuje vztah mezi `Book` třídy a `Publication`, jeho základní třída.

![Třídy publikace a adresáře](media/book-class.jpg)

Nyní jsme můžete vytvořit instanci `Book` objektu vyvolání její jedinečný a zděděné členy a předat jako argument pro metodu, která očekává parametr typu `Publication` nebo typu `Book`, jak ukazuje následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Navrhování abstraktní základní třídy a jejich odvozené třídy
<a name="abstract"></a>

V předchozím příkladu jsme definovali základní třídu, která poskytuje implementaci pro počet metody, které umožňují sdílet kód odvozené třídy. V mnoha případech ale základní třída není očekáván poskytnout implementaci. Místo toho je základní třída *abstraktní třída*; slouží jako šablonu, která definuje členy, že všechny odvozené třídy musí implementovat. V případě abstraktní základní třídu, je obvykle jedinečné pro daný typ provádění jednotlivých odvozeného typu.

Například každý uzavřený obrazec dvourozměrná geometrickou obsahuje dvě vlastnosti: oblasti, vnitřní rozsah tvaru; a hraniční, nebo vzdálenosti na okrajů tvaru. Způsob, ve kterém jsou vypočítávány tyto vlastnosti, ale závisí zcela na konkrétní tvaru. Vzorec pro výpočet hraniční (nebo obvodu) kruh, například je příliš neliší od trojúhelníku.

V následujícím příkladu definuje abstraktní základní třídu s názvem `Shape` , který definuje dvě vlastnosti: `Area` a `Perimeter`. Všimněte si, že, kromě třídu označit pomocí [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo, každý člen instance je také označené jako [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo. V takovém případě `Shape` také přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda vrátí název typu, nikoli plně kvalifikovaným názvem. A definuje dvě statické členy `GetArea` a `GetPerimeter`, které umožňují volající k snadnému načtení oblasti a hraniční instance všechny odvozené třídy. Když jsme instanci odvozené třídy předat do jedné z těchto metod, modul runtime volá přepsání metody odvozené třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Jsme můžete pak odvozovat některé z `Shape` které představují konkrétní obrazce. V následujícím příkladu definuje tři třídy `Triangle`, `Rectangle`, a `Circle`. Vzorec pro tento konkrétní tvar jedinečné každá používá k výpočtu oblasti a hraniční. Některé z odvozené třídy definovat také vlastnosti, jako například `Rectangle.Diagonal` a `Circle.Diameter`, které jsou jedinečné pro obrazec, který představují.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Následující příklad používá objekty, které jsou odvozené z `Shape`. Vytvoření instance pole objektů, které jsou odvozené z `Shape` a volání statických metod `Shape` třídy, která zabalí vrátit `Shape` hodnot vlastností. Všimněte si, že modul runtime načítá hodnoty ze přepsané vlastnosti u odvozeného typu. Tento příklad také vrhá každý `Shape` objekt v poli, aby jeho odvozený typ a pokud přetypování úspěšné, načte vlastnosti této konkrétní podtřídou třídy `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Viz také

[Třídy a objekty](../tour-of-csharp/classes-and-objects.md)   
[Dědičnost (C# Průvodce programováním)](../programming-guide/classes-and-structs/inheritance.md)
