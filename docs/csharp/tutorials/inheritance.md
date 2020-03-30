---
title: 'Dědičnost v C #'
description: Naučte se používat dědičnost v knihovnách a aplikacích jazyka C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 78833110db0e4f0382e5c0c6de7c6c8be9a16c8d
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391146"
---
# <a name="inheritance-in-c-and-net"></a>Dědičnost v jazyce C# a technologii .NET

Tento kurz vás seznámí s dědičností v c#. Dědičnost je funkce objektově orientovaných programovacích jazyků, která umožňuje definovat základní třídu, která poskytuje specifické funkce (data a chování) a definovat odvozené třídy, které tuto funkci dědí nebo převyšují.

## <a name="prerequisites"></a>Požadavky

Tento kurz předpokládá, že jste nainstalovali .NET Core SDK. Navštivte stránku [stahování jádra .NET a](https://dotnet.microsoft.com/download) stáhněte si ji. Potřebujete také editor kódu. Tento kurz používá [Visual Studio Code](https://code.visualstudio.com), i když můžete použít libovolný editor kódu podle vašeho výběru.

## <a name="running-the-examples"></a>Spuštění příkladů

Chcete-li vytvořit a spustit příklady v tomto kurzu, použijte nástroj [dotnet](../../core/tools/dotnet.md) z příkazového řádku. Pro každý příklad postupujte takto:

1. Vytvořte adresář pro uložení příkladu.
1. Zadejte příkaz [dotnet new console](../../core/tools/dotnet-new.md) na příkazovém řádku a vytvořte nový projekt .NET Core.
1. Zkopírujte a vložte kód z příkladu do editoru kódu.
1. Zadejte příkaz [dotnet restore](../../core/tools/dotnet-restore.md) z příkazového řádku, chcete-li načíst nebo obnovit závislosti projektu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Zadejte příkaz [dotnet run](../../core/tools/dotnet-run.md) pro kompilaci a provedení příkladu.

## <a name="background-what-is-inheritance"></a>Souvislosti: Co je dědictví?

*Dědičnost* je jedním ze základních atributů objektově orientovaného programování. Umožňuje definovat podřízenou třídu, která opakovaně používá (dědí), rozšiřuje nebo upravuje chování nadřazené třídy. Třída, jejíž členové jsou zděděni, se nazývá *základní třída*. Třída, která dědí členy základní třídy se nazývá *odvozené třídy*.

C# a .NET podporují pouze *jednu dědičnost.* To znamená, že třída může dědit pouze z jedné třídy. Dědičnost je však přenositelná, což umožňuje definovat hierarchii dědičnosti pro sadu typů. Jinými slovy, `D` typ může `C`dědit z `B`typu , který dědí `A`z typu , který dědí z typu základní třídy . Vzhledem k tomu, že dědičnost je přenositá, jsou členové typu `A` k dispozici pro typ `D`.

Ne všichni členové základní třídy jsou zděděni odvozenými třídami. Následující členové nejsou zděděni:

- [Statické konstruktory](../programming-guide/classes-and-structs/static-constructors.md), které inicializují statická data třídy.

- [Instance konstruktory](../programming-guide/classes-and-structs/constructors.md), které voláte k vytvoření nové instance třídy. Každá třída musí definovat své vlastní konstruktory.

- [Finalizační metody](../programming-guide/classes-and-structs/destructors.md), které jsou volány systémem uvolňování paměti za běhu ke zničení instancí třídy.

Zatímco všechny ostatní členy základní třídy jsou zděděny odvozené třídy, zda jsou viditelné nebo ne, závisí na jejich usnadnění přístupu. Usnadnění přístupu člena ovlivňuje jeho viditelnost pro odvozené třídy následujícím způsobem:

- [Soukromé](../language-reference/keywords/private.md) členy jsou viditelné pouze v odvozených třídách, které jsou vnořeny do své základní třídy. V opačném případě nejsou viditelné v odvozených třídách. V následujícím příkladu je `A.B` vnořená `A`třída, `C` která `A`je odvozena od , a pochází z . Soukromé `A.value` pole je viditelné v A.B. Pokud však odeberete `C.GetValue` komentáře z metody a pokusíte se zkompilovat příklad, vytvoří chybu kompilátoru CS0122: "'Hodnota' je nepřístupná z důvodu úrovně ochrany."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chráněné](../language-reference/keywords/protected.md) členy jsou viditelné pouze v odvozených třídách.

- [Vnitřní](../language-reference/keywords/internal.md) členy jsou viditelné pouze v odvozených třídách, které jsou umístěny ve stejném sestavení jako základní třída. Nejsou viditelné v odvozených třídách umístěných v jiném sestavení od základní třídy.

- [Veřejné](../language-reference/keywords/public.md) členy jsou viditelné v odvozené třídy a jsou součástí veřejné rozhraní odvozené třídy. Veřejné zděděné členy lze volat stejně jako pokud jsou definovány v odvozené třídě. V následujícím příkladu `A` třída definuje `Method1`metodu `B` s názvem `A`a třída dědí z třídy . Příklad pak `Method1` volá, jako by se `B`jednalo o metodu instance na .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Odvozené třídy můžete také *přepsat* zděděné členy poskytnutím alternativní implementace. Aby bylo možné přepsat člena, musí být člen v základní třídě označen [virtuálním](../language-reference/keywords/virtual.md) klíčovým slovem. Ve výchozím nastavení nejsou členové `virtual` základní třídy označeni jako a nelze je přepsat. Při pokusu o přepsání nevirtuálního člena, jak to dělá následující příklad,\<generuje chyba kompilátoru \<CS0506: " člen> nemůže přepsat zděděný člen> protože není označen virtuální, abstraktní nebo přepsání.

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

V některých případech *musí* odvozená třída přepsat implementaci základní třídy. Členové základní třídy označeni [abstraktním](../language-reference/keywords/abstract.md) klíčovým slovem vyžadují, aby je odvozené třídy přepsaly. Pokus o kompilaci následujícípříklad generuje chybu kompilátoru&lt;CS0534, " třída&gt; neimplementuje zděděný &lt;abstraktní člen&gt;", protože třída `B` poskytuje žádné implementace pro `A.Method1`.

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

Dědičnost platí pouze pro třídy a rozhraní. Jiné kategorie typů (struktury, delegáti a výčty) nepodporují dědičnost. Z důvodu těchto pravidel, pokus o kompilaci kódu, jako je následující příklad produkuje chybu kompilátoru CS0527: "Typ ValueType' v seznamu rozhraní není rozhraní." Chybová zpráva označuje, že i když můžete definovat rozhraní, která implementuje struktury, dědičnost není podporována.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Implicitní dědičnost

Kromě všech typů, které mohou dědit z prostřednictvím jedné dědičnosti, <xref:System.Object> všechny typy v systému typu .NET implicitně dědí z nebo typ odvozený z něj. Běžné funkce <xref:System.Object> je k dispozici pro všechny typy.

Chcete-li zjistit, co implicitní dědičnost `SimpleClass`znamená, definujme novou třídu , která je jednoduše prázdnou definicí třídy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Potom můžete použít reflexe (který umožňuje zkontrolovat metadata typu získat informace o tomto typu) získat seznam `SimpleClass` členů, které patří do typu. I když jste nedefinovali `SimpleClass` žádné členy ve vaší třídě, výstup z příkladu označuje, že ve skutečnosti má devět členů. Jeden z těchto členů je konstruktor bez parametrů (nebo `SimpleClass` výchozí), který je automaticky dodáván pro typ kompilátorem Jazyka C#. Zbývajících osm jsou <xref:System.Object>členy , typ, ze kterého všechny třídy a rozhraní v systému typu .NET nakonec implicitně dědí.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Implicitní dědičnost z třídy <xref:System.Object> `SimpleClass` zpřístupňuje tyto metody pro třídu:

- Veřejná `ToString` metoda, která `SimpleClass` převádí objekt na jeho řetězcovou reprezentaci, vrátí plně kvalifikovaný název typu. V tomto případě `ToString` metoda vrátí řetězec "SimpleClass".

- Tři metody, které testují rovnost dvou `Equals(Object)` objektů: metodu `Equals(Object, Object)` veřejné instance, `ReferenceEquals(Object, Object)` veřejnou statickou metodu a veřejnou statickou metodu. Ve výchozím nastavení tyto metody testují referenční rovnost; to znamená, že se rovná dvě proměnné objektu musí odkazovat na stejný objekt.

- Public `GetHashCode` Metoda, která vypočítá hodnotu, která umožňuje instanci typu, který má být použit v zachycované kolekce.

- Public `GetType` Metoda, která <xref:System.Type> vrátí objekt, `SimpleClass` který představuje typ.

- Chráněná <xref:System.Object.Finalize%2A> metoda, která je určena k uvolnění nespravovaných prostředků před uvolněním paměti objektu uvolněnou systémem uvolňování paměti.

- Chráněná <xref:System.Object.MemberwiseClone%2A> metoda, která vytvoří mělký klon aktuálního objektu.

Z důvodu implicitní dědičnosti můžete volat `SimpleClass` libovolný zděděný člen z objektu, stejně jako kdyby byl ve skutečnosti členem definovaným `SimpleClass` ve třídě. Například následující příklad volá `SimpleClass.ToString` metodu, `SimpleClass` která <xref:System.Object>dědí z .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

V následující tabulce jsou uvedeny kategorie typů, které můžete vytvořit v jazyce C# a typy, ze kterých implicitně dědí. Každý základní typ zpřístupňuje jinou sadu členů prostřednictvím dědičnosti implicitně odvozené typy.

| Kategorie typu | Implicitně dědí z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| třída         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegát      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dědičnost a vztah "je"

Dědičnost se obvykle používá k vyjádření vztahu "is a" mezi základní třídou a jednou nebo více odvozenými třídami, kde odvozené třídy jsou specializované verze základní třídy; odvozená třída je typ základní třídy. Například `Publication` třída představuje publikace jakéhokoli druhu a `Book` `Magazine` a třídy představují určité typy publikací.

> [!NOTE]
> Třída nebo struktura může implementovat jedno nebo více rozhraní. Zatímco implementace rozhraní je často prezentována jako řešení pro jednu dědičnost nebo jako způsob použití dědičnosti se strukturami, je určena k vyjádření jiného vztahu (vztah "může udělat") mezi rozhraním a jeho implementačním typem než Dědičnosti. Rozhraní definuje podmnožinu funkcí (například schopnost testovat rovnost, porovnávat nebo řadit objekty nebo podporovat analýzu a formátování zkoumaná jazykovou verzí), kterou rozhraní zpřístupní implementujícím typům.

Všimněte si, že "je a" také vyjadřuje vztah mezi typem a konkrétní konkretiace tohoto typu. V následujícím příkladu je třída, `Automobile` která má tři `Make`jedinečné vlastnosti jen pro čtení: , výrobce automobilu; `Model`, druh automobilu; a `Year`, rok výroby. Vaše `Automobile` třída má také konstruktor, jehož argumenty jsou přiřazeny <xref:System.Object.ToString%2A?displayProperty=nameWithType> k hodnotám vlastností a `Automobile` přepíše metodu k vytvoření řetězce, který jednoznačně identifikuje instanci spíše než třídu. `Automobile`

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

V tomto případě byste se neměli spoléhat na dědictví reprezentovat konkrétní auto dělá a modelů. Například není nutné definovat `Packard` typ představující automobily vyrobené packardovou společností. Místo toho je můžete reprezentovat `Automobile` vytvořením objektu s příslušnými hodnotami předanými jeho konstruktoru třídy, jak to dělá následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Vztah is-a založený na dědičnosti je nejlépe použita pro základní třídu a odvozené třídy, které přidávají další členy do základní třídy nebo které vyžadují další funkce, které nejsou k dispozici v základní třídě.

## <a name="designing-the-base-class-and-derived-classes"></a>Návrh základní třídy a odvozených tříd

Podívejme se na proces navrhování základní třídy a její odvozené třídy. V této části definujete základní třídu , `Publication`která představuje publikaci jakéhokoli druhu, například knihu, časopis, noviny, časopis, článek atd. Budete také definovat `Book` třídu, která `Publication`je odvozena od . Příklad můžete snadno rozšířit a definovat další odvozené `Journal` `Newspaper`třídy, například `Magazine`, , a `Article`.

### <a name="the-base-publication-class"></a>Základní třída Publication

Při navrhování `Publication` vaší třídy je třeba provést několik rozhodnutí o návrhu:

- Jaké členy zahrnout do `Publication` základní třídy `Publication` a zda členové `Publication` poskytují implementace metody nebo zda je abstraktní základní třída, která slouží jako šablona pro odvozené třídy.

  V tomto případě `Publication` bude třída poskytovat implementace metody. [Návrh abstraktní základní třídy a jejich odvozené třídy](#abstract) sekce obsahuje příklad, který používá abstraktní základní třídy definovat metody, které odvozené třídy musí přepsat. Odvozené třídy jsou zdarma poskytnout všechny implementace, která je vhodná pro odvozený typ.

  Schopnost znovu použít kód (to znamená, že více odvozených tříd sdílí deklaraci a implementaci metod základní třídy a není nutné je přepsat) je výhodou neabstraktních základních tříd. Proto byste měli přidat `Publication` členy, pokud jejich kód je pravděpodobně `Publication` sdílet některé nebo většina specializovaných typů. Pokud se vám nepodaří poskytnout implementace základní třídy efektivně, budete nakonec muset poskytnout do značné míry identické členské implementace v odvozených třídách spíše jednu implementaci v základní třídě. Potřeba udržovat duplicitní kód na více místech je potenciálním zdrojem chyb.

  Chcete-li maximalizovat opakované použití kódu a vytvořit logickou a intuitivní hierarchii `Publication` dědičnosti, měli byste mít jistotu, že do třídy zahrnete pouze data a funkce, které jsou společné pro všechny nebo pro většinu publikací. Odvozené třídy pak implementovat členy, které jsou jedinečné pro konkrétní druhy publikace, které představují.

- Jak daleko rozšířit hierarchii tříd. Chcete vytvořit hierarchii tří nebo více tříd, nikoli pouze základní třídy a jedné nebo více odvozených tříd? Může se `Publication` například jedná `Periodical`o základní třídu , `Magazine`která `Journal` `Newspaper`je zase základní třídou . a .

  V příkladu použijete malou hierarchii `Publication` třídy a jednu `Book`odvozenou třídu . Můžete snadno rozšířit příklad vytvořit řadu dalších tříd, které `Magazine` `Article`jsou odvozeny z `Publication`, například a .

- Zda má smysl vytvořit konkretizovat základní třídu. Pokud tomu tak není, měli byste použít [abstraktní](../language-reference/keywords/abstract.md) klíčové slovo na třídu. V opačném `Publication` případě může být vaše třída vytvořena instance voláním jeho konstruktoru třídy. Pokud je proveden pokus o vytvoření instance třídy označené `abstract` klíčovým slovem přímým voláním konstruktoru třídy, kompilátor Jazyka C# generuje chybu CS0144, "Nelze vytvořit instanci abstraktní třídy nebo rozhraní." Pokud je proveden pokus o vytvoření instance třídy pomocí reflexe, <xref:System.MemberAccessException>metoda odrazu vyvolá .

  Ve výchozím nastavení lze vytvořit instanci základní třídy voláním svého konstruktoru třídy. Není třeba explicitně definovat konstruktor třídy. Pokud jeden není k dispozici ve zdrojovém kódu základní třídy, kompilátor Jazyka C# automaticky poskytuje výchozí (parametrless) konstruktor.

  V příkladu označíte `Publication` třídu jako [abstraktní,](../language-reference/keywords/abstract.md) aby ji nebylo možné vytvořit.  Třída `abstract` bez `abstract` jakékoli metody označuje, že tato třída představuje abstraktní koncept, `Book` `Journal`který je sdílen mezi několik konkrétních tříd (například , ).

- Zda odvozené třídy musí dědit implementaci základní třídy konkrétní chčlenů, zda mají možnost přepsat implementaci základní třídy, nebo zda musí poskytnout implementaci. Pomocí [abstraktního](../language-reference/keywords/abstract.md) klíčového slova vynutíte odvozené třídy k poskytnutí implementace. Virtuální [klíčové](../language-reference/keywords/virtual.md) slovo slouží k povolení odvozených tříd přepsat metodu základní třídy. Ve výchozím nastavení metody definované v základní třídě *nejsou* overridable.

 Třída `Publication` nemá žádné `abstract` metody, ale třída `abstract`sama je .

- Zda odvozená třída představuje konečnou třídu v hierarchii dědičnosti a nemůže být sama použita jako základní třída pro další odvozené třídy. Ve výchozím nastavení může každá třída sloužit jako základní třída. Můžete použít [zapečetěné](../language-reference/keywords/sealed.md) klíčové slovo označující, že třída nemůže sloužit jako základní třída pro všechny další třídy. Pokus o odvození z zapečetěné třídy generované chyba kompilátoru CS0509, "nelze odvodit z zapečetěného typu \<typeName>".

  V příkladu označíte odvozenou `sealed`třídu jako .

Následující příklad ukazuje zdrojový kód `Publication` pro třídu, `PublicationType` stejně jako výčet, který je vrácen vlastností. `Publication.PublicationType` Kromě členů, které dědí <xref:System.Object>z `Publication` , třída definuje následující jedinečné členy a přepsání členů:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Vzhledem `Publication` k `abstract`tomu, že třída je , nelze vytvořit instanci přímo z kódu, jako je následující příklad:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Jeho instance konstruktor však může být volána přímo z konstruktorů `Book` odvozené třídy, jak ukazuje zdrojový kód pro třídu.

- Dvě vlastnosti související s publikací

  `Title`je vlastnost jen <xref:System.String> pro čtení, jejíž `Publication` hodnota je zadána voláním konstruktoru.

  `Pages`je vlastnost pro <xref:System.Int32> čtení a zápis, která označuje, kolik celkových stránek publikace má. Hodnota je uložena v `totalPages`soukromém poli s názvem . Musí to být kladné <xref:System.ArgumentOutOfRangeException> číslo nebo je hozen.

- Členové související s vydavatelem

  Dvě vlastnosti jen `Publisher` `Type`pro čtení a . Hodnoty jsou původně dodávány voláním konstruktoru `Publication` třídy.

- Členové související s publikováním

  Dvě metody `Publish` `GetPublicationDate`a , nastavte a vraťte datum publikování. Metoda `Publish` nastaví `published` soukromý `true` příznak, když je volána a přiřadí datum, `datePublished` které mu bylo předáno jako argument do soukromého pole. Metoda `GetPublicationDate` vrátí řetězec "NYP", `published` pokud `false`je příznak , `datePublished` a hodnota `true`pole, pokud je .

- Členové související s autorskými právy

  Metoda `Copyright` bere jméno držitele autorských práv a rok autorského práva jako `CopyrightName` argumenty a přiřazuje je k vlastnostem a. `CopyrightDate`

- Přepsání `ToString` metody

  Pokud typ nepřepíše <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu, vrátí plně kvalifikovaný název typu, který je málo použitelný při odlišení jedné instance od druhé. Třída `Publication` přepíše <xref:System.Object.ToString%2A?displayProperty=nameWithType> vrátit hodnotu `Title` vlastnosti.

Následující obrázek znázorňuje vztah `Publication` mezi základní třídou <xref:System.Object> a její implicitně zděděnou třídou.

![Třídy Object and Publication](media/publication-class.jpg)

### <a name="the-book-class"></a>Třída `Book`

Třída `Book` představuje knihu jako specializovaný typ publikace. Následující příklad ukazuje zdrojový kód `Book` pro třídu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Kromě členů, které dědí `Publication`z `Book` , třída definuje následující jedinečné členy a přepsání členů:

- Dva konstruktory

  Dva `Book` konstruktory sdílejí tři společné parametry. Dva, *název* a *vydavatel*, odpovídají `Publication` parametrům konstruktoru. Třetí je *autor*, který je uložen na `Author` veřejné neměnné vlastnosti. Jeden konstruktor obsahuje *isbn* parametr, který `ISBN` je uložen v auto-vlastnost.

  První konstruktor používá klíčové slovo [this](../language-reference/keywords/this.md) k volání jiného konstruktoru. Řetězení konstruktoru je běžný vzor při definování konstruktorů. Konstruktory s menším počtem parametrů poskytují výchozí hodnoty při volání konstruktoru s největším počtem parametrů.

  Druhý konstruktor používá [základní](../language-reference/keywords/base.md) klíčové slovo předat název a název vydavatele konstruktoru základní třídy. Pokud neprovedete explicitní volání konstruktoru základní třídy ve zdrojovém kódu, kompilátor Jazyka C# automaticky dodá volání výchozího konstruktoru základní třídy nebo konstruktoru bez parametrů.

- Vlastnost jen `ISBN` pro čtení, `Book` která vrací mezinárodní standardní číslo knihy objektu, jedinečné 10 nebo 13místné číslo. ISBN je dodáván jako argument jednomu `Book` z konstruktorů. ISBN je uložen v privátní záložní pole, které je automaticky generováno kompilátorem.

- Vlastnost jen `Author` pro čtení. Jméno autora je zadáno `Book` jako argument oběma konstruktorům a je uloženo ve vlastnosti.

- Dvě vlastnosti související s `Price` cenou `Currency`jen pro čtení a . Jejich hodnoty jsou uvedeny jako `SetPrice` argumenty v volání metody. Vlastnost `Currency` je třímístný symbol měny ISO (například USD pro americký dolar). Symboly měny ISO lze <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> načíst z vlastnosti. Obě tyto vlastnosti jsou externě jen pro čtení, `Book` ale obě lze nastavit podle kódu ve třídě.

- Metoda, `SetPrice` která nastaví hodnoty `Price` `Currency` vlastnosti a. Tyto hodnoty jsou vráceny stejnými vlastnostmi.

- Přepíše `ToString` metodu (zděděnou z) `Publication`a metody <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> a <xref:System.Object.GetHashCode%2A> (zděděné z). <xref:System.Object>

  Pokud není přepsána, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda testuje rovnost odkazů. To znamená, že dvě proměnné objektu jsou považovány za stejné, pokud odkazují na stejný objekt. Ve `Book` třídě, na druhé straně `Book` dva objekty by měly být stejné, pokud mají stejné ISBN.

  Při přepsání <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody, musíte také <xref:System.Object.GetHashCode%2A> přepsat metodu, která vrátí hodnotu, která runtime používá k ukládání položek v zachycované kolekce pro efektivní načítání. Kód hash by měl vrátit hodnotu, která je konzistentní s testem rovnosti. Vzhledem k tomu, že jste přepsáni <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> vrátit, `true` pokud ISBN vlastnosti dvou `Book` objektů <xref:System.String.GetHashCode%2A> jsou stejné, vrátíte hash kód vypočítaný voláním metody řetězce vrácené `ISBN` vlastností.

Následující obrázek znázorňuje `Book` vztah `Publication`mezi třídou a jeho základní třídou.

![Publikační a knižní třídy](media/book-class.jpg)

Nyní můžete vytvořit instanci objektu, `Book` vyvolat jeho jedinečné i zděděné členy a předat jej `Publication` jako argument `Book`metodě, která očekává parametr typu nebo typu , jak ukazuje následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Navrhování abstraktních základních tříd a jejich odvozených tříd
<a name="abstract"></a>

V předchozím příkladu jste definovali základní třídu, která poskytla implementaci pro řadu metod, které umožňují odvozeným třídám sdílet kód. V mnoha případech se však neočekává, že základní třída poskytuje implementaci. Místo toho základní třída je *abstraktní třída,* která deklaruje *abstraktní metody*; slouží jako šablona, která definuje členy, které musí každá odvozená třída implementovat. Obvykle v abstraktní základní třídy implementace každého odvozeného typu je jedinečný pro tento typ. Třídu jste označili abstraktním klíčovým slovem, protože `Publication` nemělo smysl vytvořit instanci objektu, i když třída poskytovala implementace funkcí, které jsou společné pro publikace.

Například každý uzavřený dvourozměrný geometrický tvar obsahuje dvě vlastnosti: oblast, vnitřní rozsah tvaru; a obvodu, nebo vzdálenost podél okrajů tvaru. Způsob výpočtu těchto vlastností však zcela závisí na konkrétním tvaru. Vzorec pro výpočet obvodu (nebo obvodu) kruhu se například liší od vzorce trojúhelníku. Třída `Shape` je `abstract` třída `abstract` s metodami. To znamená, že odvozené třídy sdílejí stejné funkce, ale tyto odvozené třídy implementují tuto funkci odlišně.

Následující příklad definuje abstraktní základní `Shape` třídu s názvem, která definuje dvě vlastnosti: `Area` a `Perimeter`. Kromě označení třídy [pomocí klíčového](../language-reference/keywords/abstract.md) slova abstract je každý člen instance také označen [abstraktním](../language-reference/keywords/abstract.md) klíčovým slovem. V tomto `Shape` případě také <xref:System.Object.ToString%2A?displayProperty=nameWithType> přepíše metodu vrátit název typu, spíše než jeho plně kvalifikovaný název. A definuje dva statické `GetArea` členy `GetPerimeter`a , které umožňují volajícím snadno načíst oblast a obvod instance libovolné odvozené třídy. Když předáte instanci odvozené třídy jedné z těchto metod, runtime volá přepsání metody odvozené třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Potom můžete odvodit některé třídy z, `Shape` které představují určité obrazce. Následující příklad definuje tři `Triangle`třídy , `Rectangle`, a `Circle`. Každý používá vzorec jedinečný pro daný obrazec k výpočtu plochy a obvodu. Některé odvozené třídy také definují vlastnosti, například `Rectangle.Diagonal` a `Circle.Diameter`, které jsou jedinečné pro obrazec, který představují.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Následující příklad používá objekty `Shape`odvozené z . Konkretizovat pole objektů odvozených z `Shape` a volá `Shape` statické metody třídy, která obtéká hodnoty vlastností vrátit. `Shape` Runtime načte hodnoty z přepsaných vlastností odvozených typů. Příklad také přetypuje každý `Shape` objekt v poli na jeho odvozený typ a pokud je `Shape`přetypovost úspěšná, načte vlastnosti této konkrétní podtřídy .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Viz také

- [Třídy a objekty](../tour-of-csharp/classes-and-objects.md)
- [Dědičnost (Průvodce programováním v C#)](../programming-guide/classes-and-structs/inheritance.md)
