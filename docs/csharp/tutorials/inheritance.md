---
title: Dědičnost v jazyce C#
description: Naučte se používat dědičnosti v C# knihovny a aplikace.
author: rpetrusha
ms.author: ronpet
ms.date: 07/05/2018
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 942950570253b73cfb9896117bd22189e56389ea
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836640"
---
# <a name="inheritance-in-c-and-net"></a>Dědičnost v jazyce C# a .NET

Tento kurz vás seznámí s dědičnosti v C#. Dědičnost je funkce objektově orientované programovací jazyky, které vám umožní definovat základní třídu, která poskytuje konkrétní funkci (data a chování) a definovat odvozené třídy, které dědí nebo přepsání, které tuto funkci.

## <a name="prerequisites"></a>Požadavky

Tento kurz předpokládá, že jste nainstalovali .NET Core. Pokyny k instalaci, naleznete v tématu [Průvodce instalací rozhraní .NET Core](https://www.microsoft.com/net/core). Budete také potřebovat editor kódu. Tento kurz používá [Visual Studio Code](https://code.visualstudio.com), i když můžete použít libovolný editor kódu podle vašeho výběru.

## <a name="running-the-examples"></a>Spuštění příkladů

Vytvoření a spuštění příkladů v tomto kurzu, můžete použít [dotnet](../../core/tools/dotnet.md) nástroje z příkazového řádku. Postupujte podle těchto kroků pro každý příklad:

1. Vytvořte adresář pro uložení v příkladu.
1. Zadejte [nové konzoly dotnet](../../core/tools/dotnet-new.md) příkazu na příkazovém řádku k vytvoření nového projektu .NET Core.
1. Zkopírujte a vložte kód z příkladu do editoru kódu.
1. Zadejte [dotnet restore](../../core/tools/dotnet-restore.md) příkazu z příkazového řádku k načtení nebo obnovte závislosti projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Zadejte [dotnet spustit](../../core/tools/dotnet-run.md) příkazu zkompilovat a spustit v příkladu.

## <a name="background-what-is-inheritance"></a>Na pozadí: Co je dědičnost?

*Dědičnost* je jednou ze základních atributů objektově orientované programování. Umožňuje definovat podřízenou třídu, která se použije znovu (dědí), rozšiřuje nebo upravuje chování nadřazené třídy. Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*. Třída, která dědí členy základní třídy se nazývá *odvozené třídy*.

Podpora jazyka C# a .NET *jednoduché dědičnosti* pouze. To znamená třída může dědit pouze z jedné třídy. Dědičnost je však tranzitivní, který umožňuje definovat hierarchie dědičnosti pro sadu typů. Jinými slovy, zadejte `D` může dědit z typu `C`, která dědí z typu `B`, která dědí ze základní třídy typu `A`. Vzhledem k tomu, že dědičnost je přenosné členy typu `A` jsou k dispozici na typ `D`.

Ne všechny členy základní třídy jsou zděděny z odvozených tříd. Nejsou děděna následující členy:

- [Statické konstruktory](../programming-guide/classes-and-structs/static-constructors.md), který inicializace statických dat třídy.

- [Konstruktory instancí](../programming-guide/classes-and-structs/constructors.md), kterou zavoláte vytvořit novou instanci třídy. Každá třída musí definovat vlastní konstruktory.

- [Finalizační metody](../programming-guide/classes-and-structs/destructors.md), které se nazývají uvolňováním paměti modulu runtime ke zničení instance třídy.

Přestože všechny členy základní třídy jsou zděděny z odvozených tříd, určuje, zda jsou viditelné nebo ne závisí na jejich přístupnost. Usnadnění přístupu člena ovlivňuje jeho viditelnost odvozené třídy následujícím způsobem:

- [Privátní](../language-reference/keywords/private.md) členy jsou viditelné pouze v odvozených třídách, které jsou vnořené v jejich základní třídy. V opačném případě nebyly viditelné v odvozených třídách. V následujícím příkladu `A.B` je vnořená třída, která je odvozena z `A`, a `C` je odvozena z `A`. Privátní `A.value` je pole viditelné v A.B. Ale pokud odeberete případnými poznámkami od `C.GetValue` metoda a pokusíte se zkompilovat v příkladu, vytvoří Chyba kompilátoru CS0122: "" A.value"je vzhledem k úrovni ochrany nepřístupný."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chráněné](../language-reference/keywords/protected.md) členy jsou viditelné pouze v odvozených třídách.

- [Interní](../language-reference/keywords/internal.md) členy jsou viditelné pouze v odvozených třídách, které se nacházejí ve stejném sestavení jako základní třídy. Nebyly viditelné v odvozených třídách, které jsou umístěné v jiném sestavení ze základní třídy.

- [Veřejné](../language-reference/keywords/public.md) členy jsou viditelné v odvozených třídách a jsou součástí veřejného rozhraní odvozené třídy. Veřejné členy zděděné lze volat, jakoby jsou definovány v odvozené třídě. V následujícím příkladu třída `A` definuje metodu s názvem `Method1`a třídy `B` dědí z třídy `A`. Příklad poté volá `Method1` jako by šlo o metodu instance na `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Odvozené třídy lze také *přepsat* zděděné členy tím, že poskytuje alternativní implementace. Aby bylo možné přepsat členy, musí být označeny člena základní třídy [virtuální](../language-reference/keywords/virtual.md) – klíčové slovo. Ve výchozím nastavení, členy základní třídy nejsou označeny jako `virtual` a nedají se přepsat. Pokus přepsat nevirtuální člen, stejně jako v následujícím příkladu, vygeneruje chybu kompilátoru CS0506: "<member> nejde přepsat zděděný člen <member> protože není označena jako virtuální, abstraktní nebo přepis.

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

V některých případech se v odvozené třídě *musí* přepsat implementaci základní třídy. Členy základní třídy označené [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo vyžaduje, že je odvozeným třídám přepsat. Při pokusu o kompilaci následující příklad vygeneruje chybu kompilátoru CS0534, "&lt;třídy&gt; neimplementuje zděděný abstraktní člen &lt;člen&gt;", protože třída `B` poskytuje ne implementace `A.Method1`.

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

Dědičnost platí jenom pro třídy a rozhraní. Další kategorie typů (struktury, delegátů a výčty) nepodporují dědičnosti. Protože tato pravidla pokusu o kompilaci kódu, jako je následující příklad generuje chybu kompilátoru CS0527: "Typ 'ValueType' v seznamu rozhraní není rozhraní." Chybová zpráva znamená, že i když můžete definovat rozhraní, která implementuje strukturu, dědičnosti, není podporovaný.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Implicitní dědičnosti

Kromě všechny typy, které může dědit z přes jednoduchá dědičnost, všechny typy v systému typů .NET implicitně dědí z <xref:System.Object> nebo typ odvozený z něj. Běžné funkce <xref:System.Object> je k dispozici pro libovolného typu.

Pokud chcete zobrazit, jaké implicitní dědičnosti znamená, že umožňuje definovat novou třídu `SimpleClass`, je jednoduše prázdnou definici třídy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Reflexe (čímž získáte kontrolu typu metadat k získání informací o typu) pak můžete použít k získání seznamu členů, které patří do `SimpleClass` typu. I když nejsou definované žádné členy v vaše `SimpleClass` třídy výstup z příkladu označuje, že ve skutečnosti obsahuje devět členů. Jeden z těchto členů je konstruktor bez parametrů (nebo výchozí), který automaticky poskytnutý `SimpleClass` typ kompilátoru jazyka C#. Zbývající 8 jsou členy <xref:System.Object>, typ, ze kterého všechny třídy a rozhraní v rozhraní .NET systém typů nakonec implicitně dědí.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Implicitní dědičnosti z <xref:System.Object> třídy zpřístupní tyto metody `SimpleClass` třídy:

- Veřejná `ToString` metody, která převádí `SimpleClass` objektu na jeho řetězcovou reprezentaci vrátí plně kvalifikovaného názvu. V takovém případě `ToString` metoda vrátí řetězec "SimpleClass".

- Tři metody, které testují rovnost dvou objektů: veřejné instanci `Equals(Object)` metody, veřejné statické `Equals(Object, Object)` metoda a veřejných statických `ReferenceEquals(Object, Object)` metoda. Ve výchozím nastavení tyto metody testovat rovnost reference; se rovná, tedy dvě proměnné objektu musí odkazovat na stejný objekt.

- Veřejná `GetHashCode` metodu, která vypočítá hodnotu, která umožňuje instance typu použitého v kolekcích hodnoty hash.

- Veřejná `GetType` metoda, která vrátí <xref:System.Type> objekt, který reprezentuje `SimpleClass` typu.

- Chráněný <xref:System.Object.Finalize%2A> metodu, která slouží k uvolnění nespravovaných prostředků, než paměti objektu je uvolněn systémem uvolňování paměti.

- Chráněný <xref:System.Object.MemberwiseClone%2A> metodu, která vytvoří klon bez podstruktury aktuálního objektu.

Z důvodu implicitní dědičnosti, můžete volat všechny zděděného členu z `SimpleClass` stejně, jako by byl ve skutečnosti člen objekt definovaný v `SimpleClass` třídy. Například následující příklad volá `SimpleClass.ToString` metoda, která `SimpleClass` dědí z <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Následující tabulka obsahuje seznam kategorií typů, které můžete vytvořit v jazyce C# a typů, ze kterých implicitně dědí. Jednotlivých základních typů provede různé sady členů k dispozici prostřednictvím dědičnosti na implicitně odvozené typy.

| Typ kategorie | Implicitně dědí z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| třída         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegát      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dědičnost a "je" relace

Obvykle se používá dědičnosti vyjádřit "je" vztah mezi základní třídu a jeden nebo více odvozené třídy, kde odvozené třídy jsou speciální verze základní třídy; odvozená třída je typ základní třídy. Například `Publication` třída reprezentuje publikace jakéhokoli druhu a `Book` a `Magazine` třídy představují konkrétní typy publikací.

> [!NOTE]
> Třídy nebo struktury může implementovat jedno nebo více rozhraní. Při implementaci rozhraní často prezentována jako alternativní řešení pro jednoduchou dědičnost nebo jako způsob, jak pomocí struktury dědičnosti, je určena k jiné relaci ("lze provádět" relace) mezi rozhraní a jeho implementující typ než express dědičnost. Rozhraní definuje podmnožinu funkcí (jako je například možnost testovat rovnost pro porovnání nebo řazení objektů, nebo pro podporu zohledňující jazykovou verzi, analýzy a formátování), který rozhraní zpřístupní pro jeho implementaci typů.

Všimněte si, že "je" také vyjadřují vztah mezi typem a konkrétní instanci daného typu. V následujícím příkladu `Automobile` je třída, která má tři jedinečné vlastnosti jen pro čtení: `Make`, výrobce automobile; `Model`, druh automobile; a `Year`, jeho rok výroby. Vaše `Automobile` třída také obsahuje konstruktor, jehož argumenty jsou přiřazeny hodnoty vlastností a přepíše <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu za účelem vytvoření řetězec, který jednoznačně identifikuje `Automobile` instance místo `Automobile` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

V takovém případě byste neměli vycházet dědičnosti představující konkrétní automobil značky a modelu. Například nemusíte definovat `Packard` typ představující automobily pocházejí od společnosti Packard Motor auta. Místo toho vám mohou představovat vytvořením `Automobile` objektu s příslušnými hodnotami předaný konstruktoru třídy stejně jako v následujícím příkladu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Relace je a podle dědičnosti nejlépe platí na základní třídu a pro odvozené třídy, která přidat další členy základní třídy nebo které vyžadují další funkce není k dispozici v základní třídě.

## <a name="designing-the-base-class-and-derived-classes"></a>Navrhování základní třída a odvozené třídy

Podívejme se na proces návrhu základní třída a odvozené třídy. V této části budete definovat základní třídy `Publication`, která představuje publikace jakéhokoli druhu, jako jsou knihy, časopisy, novinových, deníku, článku, atd. Budete také definovat `Book` třídu odvozenou od `Publication`. Může snadno rozšířit příklad na definovat další odvozené třídy, jako například `Magazine`, `Journal`, `Newspaper`, a `Article`.

### <a name="the-base-publication-class"></a>Základní třída publikace

Při navrhování vaší `Publication` třídy, je třeba provést několik rozhodnutí týkající se návrhu:

- Jaké členy mají být zahrnuty v základním `Publication` třídy a zda `Publication` členy poskytují implementace metody nebo zda `Publication` je abstraktní základní třída, která slouží jako šablona pro její odvozené třídy.

  V takovém případě `Publication` třídy bude poskytovat implementace metody. [Návrh abstraktní základní třídy a jejich odvozené třídy](#abstract) oddíl obsahuje příklad, který používá abstraktní základní třída pro definování metod, které odvozené třídy musí přepsat. Odvozené třídy je zdarma k dispozici žádné implementace, která je vhodná pro odvozeného typu.

  Možnosti opakovaně používat kód (to znamená více odvozených tříd sdílet deklaraci a implementaci základní třídy, metody třídy a není nutné k jejich přepsání) je výhodné z neabstraktní základní třídy. Proto by měl přidat členy do `Publication` pokud jejich kód je pravděpodobné, že některé sdílí nebo nejvíce specializované `Publication` typy. Pokud nedodržíte poskytují efektivní implementace základní třídy, budete mít nakonec nebudete muset zadávat implementací velké části stejný jako člena v odvozených třídách spíše jedna implementace v základní třídě. Je potřeba udržovat duplicitním kódem v několika umístěních je možným zdrojem chyb.

  Jak maximalizovat opakované použití kódu a vytvoření hierarchie dědičnosti logické a intuitivní, chcete mít jistotu, že složku zahrnujete v `Publication` třídy data a funkce, které jsou společné pro všechny nebo Většina publikací. Odvozené třídy pak implementovat členy, které jsou jedinečné pro konkrétní druhy publikace, která představují.

- Jak daleko k rozšíření vaší hierarchie tříd. Chcete rozvíjet hierarchie tři nebo více tříd, spíše než pouze základní třídu a jeden nebo více odvozených tříd? Například `Publication` může být základní třídou `Periodical`, který je zase základní třídou `Magazine`, `Journal` a `Newspaper`.

  Příklad, budete používat malé hierarchii `Publication` třídy a jedné odvozené třídy `Book`. Může snadno rozšířit příklad na vytvořit počet další třídy, které jsou odvozeny z `Publication`, jako například `Magazine` a `Article`.

- Určuje, zda je vhodné pro vytvoření instance základní třídy. Pokud tomu tak není, měli byste použít [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo do třídy. Jinak vaše `Publication` třída může být tvořena voláním konstruktoru třídy. Pokud je proveden pokus o vytvoření instance třídy označené `abstract` – klíčové slovo pomocí přímého volání konstruktoru třídy, kompilátor jazyka C# vygeneruje chybu CS0144 "Nelze vytvořit instanci abstraktní třídy nebo rozhraní." Pokud je proveden pokus o vytvoření instance třídy pomocí reflexe, vyvolá metoda výjimku reflexe <xref:System.MemberAccessException>.

  Ve výchozím nastavení můžete vytvořit instanci základní třídy pomocí volání konstruktoru třídy. Není nutné explicitně definovat konstruktor třídy. Pokud není k dispozici ve zdrojovém kódu základní třídu, kompilátor jazyka C# automaticky poskytne výchozí konstruktor (bez parametrů).

  Pro příklad, budete označíte `Publication` třídy jako [abstraktní](../language-reference/keywords/abstract.md) tak, aby se nedá vytvořit instance.  `abstract` Třídy bez `abstract` metody Určuje, že tato třída představuje abstraktní koncept, který je sdílen mezi několika konkrétní třídy (podobně jako `Book`, `Journal`).

- Určuje, zda odvozené třídy musí dědit provádění konkrétní členy základní třídy, určuje, zda mají možnost přepsat implementaci základní třídy nebo zda musí poskytnout implementaci. Můžete použít [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo chcete vynutit odvozené třídy, které poskytují implementace. Můžete použít [virtuální](../language-reference/keywords/virtual.md) – klíčové slovo umožňuje odvozeným třídám přepsat metodu základní třídy. Ve výchozím nastavení, jsou metody definované v základní třídě *není* overridable.

 `Publication` Třída nemá žádné `abstract` metody, ale samotné třídě je `abstract`.

- Určuje, zda odvozená třída představuje poslední třídy v hierarchii dědičnosti a samotné nelze zadat jako základní třída pro další odvozené třídy. Ve výchozím nastavení jakákoli třída může sloužit jako základní třídu. Můžete použít [zapečetěné](../language-reference/keywords/sealed.md) – klíčové slovo k označení, že třída nemůže sloužit jako základní třída pro všechny další třídy. Při pokusu o odvození z zapečetěnou třídu vygeneruje chybu kompilátoru CS0509, "se nemůže odvozovat ze zapečetěného typu <typeName>".

  Pro příklad, budete označit odvozené třídy jako `sealed`.

Následující příklad ukazuje, zdrojový kód `Publication` třídy, a také `PublicationType` výčet, který je vrácený `Publication.PublicationType` vlastnost. Kromě členy, které dědí z <xref:System.Object>, `Publication` třída definuje následující členy jedinečný a člen přepisuje:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Vzhledem k tomu, `Publication` třída je `abstract`, nelze vytvořit instanci přímo z kódu jako v následujícím příkladu:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Však lze volat jeho konstruktor instance přímo z konstruktory odvozené třídy jako zdrojový kód `Book` třídy ukazuje.

- Dvě vlastnosti související s publikace

  `Title` je jen pro čtení <xref:System.String> vlastnost, jejíž hodnota je poskytnuta voláním `Publication` konstruktoru.

  `Pages` je pro čtení i zápis <xref:System.Int32> má vlastnost, která označuje, kolik celkem stránek publikace. Hodnota je uložena v privátní pole s názvem `totalPages`. Musí být kladné číslo nebo <xref:System.ArgumentOutOfRangeException> je vyvolána výjimka.

- Související vydavatele členy

  Dvě vlastnosti jen pro čtení, `Publisher` a `Type`. Hodnoty jsou původně zadaný ve volání `Publication` konstruktoru třídy.

- Publikování související členy

  Dvě metody, `Publish` a `GetPublicationDate`, nastavení a vracení datum publikace. `Publish` Metoda nastaví privátní `published` příznak `true` když je volána a přiřadí data do něho předaný jako argument pro privátní `datePublished` pole. `GetPublicationDate` Metoda vrátí řetězec "NYP", pokud `published` příznak je `false`a hodnota `datePublished` pole, pokud je `true`.

- Copyright související členy

  `Copyright` Metoda přijímá jméno vlastníka autorských práv a roku autorská práva jako argumenty a přiřazuje jim `CopyrightName` a `CopyrightDate` vlastnosti.

- Přepsání `ToString` – metoda

  Pokud typ nepřepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, vrátí plně kvalifikovaný název typu, což je malý použití ve firmách jednu instanci od druhé. `Publication` Třídy přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> k vrácení hodnoty `Title` vlastnost.

Následující obrázek ukazuje vztah mezi základním `Publication` třídy a jeho implicitně zděděné <xref:System.Object> třídy.

![Třídy objektu a publikování](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` Třídy

`Book` Třída reprezentuje knihy jako speciální typ publikace. Následující příklad ukazuje, zdrojový kód `Book` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Kromě členy, které dědí z `Publication`, `Book` třída definuje následující členy jedinečný a člen přepisuje:

- Dva konstruktory

  Dva `Book` konstruktory sdílet tři společných parametrů. Dva, *title* a *vydavatele*, odpovídají parametry `Publication` konstruktoru. Je třetí *Autor*, které je uložený na veřejnou neměnné `Author` vlastnost. Zahrnuje jeden konstruktor *isbn* parametr, který je uložený v `ISBN` automatickou vlastnost.

  První konstruktor používá [to](../language-reference/keywords/this.md) – klíčové slovo k volání jiných konstruktoru. Řetězení konstruktor je běžný vzor při definování konstruktory. Konstruktory s parametry méně zadat výchozí hodnoty při volání konstruktoru s největší počet parametrů.

  Druhý konstruktor používá [základní](../language-reference/keywords/base.md) – klíčové slovo a vydavatel názvu předat konstruktoru základní třídy. Pokud neprovedete explicitní volání konstruktoru základní třídy ve zdrojovém kódu, kompilátor jazyka C# automaticky poskytuje volání konstruktoru základní třídy výchozí nebo konstruktor bez parametrů.

- Jen pro čtení `ISBN` vlastnost, která vrací `Book` objektu mezinárodní Standard číslo knihy, číslo jedinečný nebo 13 – 10místné. ISBN je předána jako argument jeden z `Book` konstruktory. ISBN je uložena v privátní pomocným polem, které je automaticky generovaný kompilátorem.

- Jen pro čtení `Author` vlastnost. Jméno autora je předána jako argument pro obě `Book` konstruktory a je uložená ve vlastnosti.

- Dvě vlastnosti jen pro čtení související s cenami, `Price` a `Currency`. Jejich hodnoty jsou k dispozici jako argumenty v `SetPrice` volání metody. `Currency` Vlastnost má tři číslice symbolem měny ISO (například USD za americký dolar). Symboly měny ISO můžete získat z <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> vlastnost. Obě tyto vlastnosti jsou externě jen pro čtení, ale i lze nastavit pomocí kódu v `Book` třídy.

- A `SetPrice` metodu, která nastavuje hodnoty `Price` a `Currency` vlastnosti. Tyto hodnoty jsou vráceny podle stejné vlastností.

- Přepsání `ToString` – metoda (zděděno z `Publication`) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> a <xref:System.Object.GetHashCode%2A> metody (zděděno z <xref:System.Object>).

  Pokud nepřepíšete, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> testy metoda rovnosti odkazů. To znamená, že dvě proměnné objektu jsou považovány za rovny, pokud odkazují na stejný objekt. V `Book` třídy, na druhé straně dvě `Book` objekty by měly být shodné, pokud mají stejné ISBN.

  Při přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda, je nutné také přepsat <xref:System.Object.GetHashCode%2A> metoda, která vrátí hodnotu, která používá modul runtime ukládá položky do kolekce hodnotu hash pro efektivní načtení. Hodnota hash by měla vrátit hodnotu, která je konzistentní s testování rovnosti. Protože jste přepsat <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> vrátit `true` Pokud vlastnosti ISBN dvou `Book` objekty rovnají, vrátí kód hash počítají tak, že volání <xref:System.String.GetHashCode%2A> metoda řetězec vrácený funkcí `ISBN` vlastnost.

Následující obrázek ukazuje vztah mezi `Book` třídy a `Publication`, její základní třídy.

![Třídy publikace a knihy](media/book-class.jpg)

Nyní můžete vytvořit instanci `Book` objektu, vyvolání jeho jedinečné a zděděné členy a předat jako argument pro metodu, která očekává parametr typu `Publication` nebo typu `Book`, jak ukazuje následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Návrh abstraktní základní třídy a jejich odvozené třídy
<a name="abstract"></a>

V předchozím příkladu jste definovali základní třídu, která poskytuje implementaci pro celou řadou metody, které umožňují sdílení kódu odvozené třídy. V mnoha případech se však základní třídy se neočekává poskytnout implementaci. Místo toho je základní třídy *abstraktní třídu* , který deklaruje *abstraktní metody*; slouží jako šablony, která definuje členy, že každý odvozené třídy musí implementovat. Abstraktní základní třídy, je obvykle jedinečné pro daný typ provádění jednotlivých odvozeného typu. Je označen atributem class s abstract – klíčové slovo, protože nevytváří žádné vhodné vytvořit instanci `Publication` objekt, ačkoli třída poskytují implementace funkčnost společnou pro publikace.

Například všechny uzavřené dvojrozměrné geometrické obrazce obsahuje dvě vlastnosti: oblasti, vnitřního rozsahu tvaru; a hraniční, nebo vzdálenost podél okrajů tvaru. Způsob, ve kterém se počítají těchto vlastností, ale závisí zcela na konkrétní tvar. Vzorec pro výpočet hraniční (nebo obvodu) kruh, například se liší od trojúhelník. `Shape` Třída je `abstract` třídy s `abstract` metody. Který označuje odvozené třídy sdílejí stejné funkce, ale tyto odvozené třídy, které tuto funkci implementovat odlišně.

Následující příklad definuje abstraktní základní třídu s názvem `Shape` , který definuje dvě vlastnosti: `Area` a `Perimeter`. Kromě třídu označit pomocí [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo, každý člen instance je také označena [abstraktní](../language-reference/keywords/abstract.md) – klíčové slovo. V takovém případě `Shape` přepíše také <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda vrátí název typu, nikoli jeho plně kvalifikovaný název. A definuje dvě statické členy `GetArea` a `GetPerimeter`, které umožňují volajícím snadno načíst obsah a obvod instance všechny odvozené třídy. Pokud předáte instanci odvozené třídy pro žádnou z těchto metod, modul runtime volá přepsání metody odvozené třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Pak lze odvodit z některé třídy `Shape` , které představují konkrétní obrazce. Následující příklad definuje tři třídy `Triangle`, `Rectangle`, a `Circle`. Každá jedinečný pro tento konkrétní tvar vzorec používá k výpočtu obsah a obvod. Některé z odvozených tříd také definovat vlastnosti, jako například `Rectangle.Diagonal` a `Circle.Diameter`, které jsou jedinečné pro obrazec, který představují.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Následující příklad používá objekty odvozené z `Shape`. Vytvoření instance pole objektů, které jsou odvozeny z `Shape` a volání statické metody `Shape` třída, která zabalí vrátit `Shape` hodnot vlastností. Modul runtime načítá hodnoty ze přepsané vlastnosti odvozených typů. V příkladu také přetypování každý `Shape` objekt v poli na jeho odvozený typ. a pokud je přetypování úspěšné, načte vlastnosti této konkrétní podtřídy `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Viz také:

- [Třídy a objekty](../tour-of-csharp/classes-and-objects.md)
- [Dědičnost (C# Programming Guide)](../programming-guide/classes-and-structs/inheritance.md)
