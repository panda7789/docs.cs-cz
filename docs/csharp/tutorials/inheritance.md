---
title: Dědičnost vC#
description: Naučte se používat dědičnost C# v knihovnách a aplikacích.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: b69da841c7c7a2e518191ad34f2ff5b368899728
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120136"
---
# <a name="inheritance-in-c-and-net"></a>Dědičnost v jazyce C# a technologii .NET

V tomto kurzu se seznámíte s C#děděním v. Dědičnost je funkcí objektově orientovaných programovacích jazyků, které umožňují definovat základní třídu, která poskytuje konkrétní funkce (data a chování) a definovat odvozené třídy, které obě tyto funkce dědí nebo přepíší.

## <a name="prerequisites"></a>Požadavky

V tomto kurzu se předpokládá, že jste nainstalovali .NET Core SDK. Navštivte stránku [ke stažení pro .NET Core](https://dotnet.microsoft.com/download) , kterou si můžete stáhnout. Budete také potřebovat Editor kódu. V tomto kurzu se používá [Visual Studio Code](https://code.visualstudio.com), i když můžete použít libovolný editor kódu, který si vyberete.

## <a name="running-the-examples"></a>Spuštění příkladů

Chcete-li vytvořit a spustit příklady v tomto kurzu, použijte nástroj [dotnet](../../core/tools/dotnet.md) z příkazového řádku. Pro každý příklad použijte tento postup:

1. Vytvořte adresář, do kterého chcete příklad Uložit.
1. Chcete-li vytvořit nový projekt .NET Core, zadejte do příkazového řádku příkaz [dotnet New Console](../../core/tools/dotnet-new.md) .
1. Zkopírujte a vložte kód z příkladu do editoru kódu.
1. Zadejte příkaz [dotnet Restore](../../core/tools/dotnet-restore.md) z příkazového řádku, aby se načetly nebo obnovily závislosti projektu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Zadejte příkaz [dotnet Run](../../core/tools/dotnet-run.md) pro zkompilování a spuštění příkladu.

## <a name="background-what-is-inheritance"></a>Pozadí: co je dědičnost?

*Dědičnost* je jedním ze základních atributů objektově orientovaného programování. Umožňuje definovat podřízenou třídu, která znovu používá (dědí), rozšiřuje nebo upravuje chování nadřazené třídy. Třída, jejíž členové jsou zděděni, se nazývají *základní třídy*. Třída, která dědí členy základní třídy, se nazývá *odvozená třída*.

C#a podpora rozhraní .NET podporuje pouze *jedinou dědičnost* . To znamená, že třída může dědit pouze z jedné třídy. Dědičnost je však tranzitivní, což umožňuje definovat hierarchii dědičnosti pro sadu typů. Jinými slovy typ `D` může dědit z typu `C`, který dědí z typu `B`, který dědí ze `A`typu základní třídy. Vzhledem k tomu, že dědičnost je tranzitivní, jsou členy typu `A` k dispozici pro typ `D`.

Ne všichni členové základní třídy jsou děděni odvozenými třídami. Následující členové nejsou děděni:

- [Statické konstruktory](../programming-guide/classes-and-structs/static-constructors.md), které inicializují statická data třídy.

- [Konstruktory instancí](../programming-guide/classes-and-structs/constructors.md), které zavoláte k vytvoření nové instance třídy. Každá třída musí definovat vlastní konstruktory.

- [Finalizační metody](../programming-guide/classes-and-structs/destructors.md), které jsou volány uvolňováním paměti modulu runtime pro zničení instancí třídy.

Zatímco všichni ostatní členové základní třídy jsou děděni odvozenými třídami, ať už jsou viditelné, nebo nejsou závislé na jejich přístupnost. Přístupnost člena má vliv na jeho viditelnost pro odvozené třídy následujícím způsobem:

- [Soukromé](../language-reference/keywords/private.md) členy jsou viditelné pouze v odvozených třídách, které jsou vnořeny do jejich základní třídy. V opačném případě nejsou viditelné v odvozených třídách. V následujícím příkladu je `A.B` vnořená třída, která je odvozena z `A`a `C` je odvozena z `A`. Soukromé `A.value` pole je viditelné v A.B. Pokud však odeberete komentáře z metody `C.GetValue` a pokusíte se zkompilovat příklad, vyvolá chybu kompilátoru CS0122: A. Value je nepřístupný z důvodu úrovně ochrany. "

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chránění](../language-reference/keywords/protected.md) členové jsou viditelné pouze v odvozených třídách.

- [Interní](../language-reference/keywords/internal.md) členy jsou viditelné pouze v odvozených třídách, které jsou umístěny ve stejném sestavení jako základní třída. Nejsou viditelné v odvozených třídách, které jsou umístěny v jiném sestavení ze základní třídy.

- [Veřejné](../language-reference/keywords/public.md) členy jsou viditelné v odvozených třídách a jsou součástí veřejného rozhraní odvozené třídy. Veřejné zděděné členy mohou být volány stejně, jako kdyby byly definovány v odvozené třídě. V následujícím příkladu třída `A` definuje metodu nazvanou `Method1`a třída `B` dědí ze třídy `A`. Příklad poté volá `Method1`, jako by šlo o metodu instance v `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Odvozené třídy mohou také *přepsat* zděděné členy poskytnutím alternativní implementace. Aby bylo možné přepsat člena, musí být člen v základní třídě označený klíčovým slovem [Virtual](../language-reference/keywords/virtual.md) . Ve výchozím nastavení nejsou členy základní třídy označeny jako `virtual` a nelze je přepsat. Při pokusu o přepsání nevirtuálního člena, jak je znázorněno v následujícím příkladu, vygeneruje chybu kompilátoru CS0506: "\<členský > nemůže přepsat zděděný člen > \<členů, protože není označen jako virtuální, abstraktní nebo přepsání.

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

V některých případech *musí* odvozená třída přepsat implementaci základní třídy. Členy základní třídy označené pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) vyžadují, aby je přepsaly odvozené třídy. Při pokusu o zkompilování následujícího příkladu dojde k chybě kompilátoru CS0534, "&lt;&gt; třídy neimplementuje zděděný abstraktní člen &lt;member&gt;", protože třída `B` neposkytuje žádnou implementaci pro `A.Method1`.

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

Dědičnost se vztahuje pouze na třídy a rozhraní. Jiné kategorie typů (struktury, delegáti a výčty) nepodporují dědění. Z důvodu těchto pravidel se při pokusu o zkompilování kódu, jako je následující příklad, vytvoří Chyba kompilátoru CS0527: "Type ' ValueType ' v seznamu rozhraní není rozhraní." Chybová zpráva označuje, že i když můžete definovat rozhraní implementující strukturou, dědičnost není podporována.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Implicitní dědičnost

Kromě jakýchkoli typů, které mohou dědit prostřednictvím jedné dědičnosti, všechny typy v systému typů .NET implicitně dědí z <xref:System.Object> nebo z něj odvozený typ. Běžné funkce <xref:System.Object> jsou k dispozici pro libovolný typ.

Chcete-li zjistit, co implicitní dědičnost znamená, definujte novou třídu, `SimpleClass`, která je jednoduše definicí prázdné třídy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Pak můžete použít reflexi (což vám umožní zkontrolovat metadata typu a získat informace o tomto typu) a získat tak seznam členů, kteří patří do typu `SimpleClass`. I když jste nedefinovali žádné členy ve třídě `SimpleClass`, výstup z příkladu označuje, že ve skutečnosti má devět členů. Jeden z těchto členů je konstruktor bez parametrů (nebo výchozí), který je automaticky dodán pro `SimpleClass` typ C# kompilátorem. Zbývající osm jsou členy <xref:System.Object>, typ, ze kterého všechny třídy a rozhraní v systému typů .NET jsou nakonec implicitně děděny.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Implicitní dědění z <xref:System.Object> třídy zpřístupňuje tyto metody pro `SimpleClass` třídy:

- Metoda Public `ToString`, která převede `SimpleClass` objektu na jeho řetězcovou reprezentaci, vrátí název plně kvalifikovaného typu. V tomto případě metoda `ToString` vrátí řetězec "SimpleClass".

- Tři metody, které testují rovnost dvou objektů: veřejné instance `Equals(Object)` metodu, veřejnou statickou `Equals(Object, Object)` metodou a veřejnou statickou `ReferenceEquals(Object, Object)` metodou. Ve výchozím nastavení tyto metody test rovnosti referencí; To znamená, že dva objektové proměnné musí odkazovat na stejný objekt.

- Metoda Public `GetHashCode`, která vypočítá hodnotu, která umožňuje použití instance typu v kolekcích s algoritmem hash.

- Metoda Public `GetType`, která vrací objekt <xref:System.Type>, který představuje typ `SimpleClass`.

- Chráněná <xref:System.Object.Finalize%2A> metoda, která je navržena pro uvolnění nespravovaných prostředků před tím, než je paměť objektu uvolněna systémem uvolňování paměti.

- Chráněná <xref:System.Object.MemberwiseClone%2A> metoda, která vytvoří neomezený klon aktuálního objektu.

Z důvodu implicitní dědičnosti můžete volat všechny zděděné členy z objektu `SimpleClass` stejným způsobem, jako kdyby byl ve skutečnosti člen definován ve třídě `SimpleClass`. Například následující příklad volá metodu `SimpleClass.ToString`, která `SimpleClass` dědí z <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

V následující tabulce jsou uvedeny kategorie typů, které lze vytvořit v C# a typy, ze kterých jsou implicitně děděny. Každý základní typ zpřístupňuje jinou sadu členů prostřednictvím dědičnosti implicitně odvozeným typům.

| Kategorie typu | Implicitně dědí z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| třída         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType><xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType><xref:System.Object>             |
| delegát      | <xref:System.MulticastDelegate>, <xref:System.Delegate><xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dědičnost a "je" relace

Obvykle se dědičnost používá k vyjádření vztahu "je" vztah mezi základní třídou a jednou nebo více odvozenými třídami, kde jsou odvozenými třídami specializované verze základní třídy; odvozená třída je typem základní třídy. Například třída `Publication` představuje publikaci jakéhokoli druhu a třídy `Book` a `Magazine` představují konkrétní typy publikací.

> [!NOTE]
> Třída nebo struktura může implementovat jedno nebo více rozhraní. I když je implementace rozhraní často prezentována jako alternativní řešení pro jednoduchou dědičnost nebo jako způsob použití dědičnosti s strukturami, je určena k vyjádření odlišné relace (relace "může provádět") mezi rozhraním a jeho implementující typ než dědičnost. Rozhraní definuje podmnožinu funkcí (například možnost testování rovnosti, pro porovnání nebo řazení objektů nebo pro podporu analýzy a formátování zohledňující jazykovou verzi), že rozhraní zpřístupňuje své implementující typy.

Všimněte si, že "je" také vyjadřuje vztah mezi typem a specifickou instancí tohoto typu. V následujícím příkladu je `Automobile` třída, která má tři jedinečné vlastnosti jen pro čtení: `Make`, výrobce automobilu; `Model`druh automobilu; a `Year`rok výroby. Vaše třída `Automobile` má také konstruktor, jehož argumenty jsou přiřazeny hodnotám vlastností, a přepisuje metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType> k vytvoření řetězce, který jedinečně identifikuje instanci `Automobile` spíše než `Automobile` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

V takovém případě byste neměli spoléhat na dědění, která představuje konkrétní automobilové a modely. Například nemusíte definovat typ `Packard`, který bude reprezentovat Automobiles vyráběná společností Packard motorového automobilu. Místo toho je lze reprezentovat vytvořením objektu `Automobile` s odpovídajícími hodnotami předanými do svého konstruktoru třídy, jak je uvedeno v následujícím příkladu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Je relace založená na dědičnosti nejvhodnější pro základní třídu a na odvozené třídy, které přidávají další členy do základní třídy nebo které vyžadují další funkce, které nejsou k dispozici v základní třídě.

## <a name="designing-the-base-class-and-derived-classes"></a>Návrh základní třídy a odvozených tříd

Pojďme se podívat na postup navrhování základní třídy a jejích odvozených tříd. V této části definujete základní třídu, `Publication`, která představuje publikaci libovolného druhu, jako je kniha, časopis, Magazine, novinka, článek atd. Definujete také třídu `Book`, která je odvozena od `Publication`. Můžete snadno roztáhnout příklad pro definování dalších odvozených tříd, například `Magazine`, `Journal`, `Newspaper`a `Article`.

### <a name="the-base-publication-class"></a>Základní třída publikace

Při navrhování `Publication` třídy je potřeba provést několik rozhodnutí o návrhu:

- Jaké členy mají být zahrnuty do základní třídy `Publication` a zda `Publication` členy poskytují implementace metod nebo zda je `Publication` abstraktní základní třída, která slouží jako šablona pro odvozené třídy.

  V tomto případě bude třída `Publication` poskytovat implementace metod. Oddíl [navrhování abstraktních základních tříd a jejich odvozené třídy](#abstract) obsahuje příklad, který používá abstraktní základní třídu k definování metod, které musí přepsat odvozené třídy. Odvozené třídy jsou bezplatné k poskytnutí libovolné implementace, která je vhodná pro odvozený typ.

  Možnost opětovného použití kódu (to znamená, že více odvozených tříd sdílí deklaraci a implementaci metod základní třídy a není nutné je přepsat) je výhodou neabstraktních základních tříd. Proto byste měli přidat členy do `Publication`, pokud je jejich kód pravděpodobně sdílen některými nebo nejvíce specializovanými typy `Publication`. Pokud nebudete moci efektivně poskytovat implementace základní třídy, bude nutné, abyste v odvozených třídách poskytovali v podstatě identické implementace členů, nikoli na jednu implementaci v základní třídě. Nutnost udržovat duplicitní kód ve více umístěních je potenciální zdrojem chyb.

  Jak maximalizovat opětovné použití kódu a vytvořit logickou a intuitivní hierarchii dědičnosti, chcete mít jistotu, že zahrnete do `Publication` třídy jenom data a funkce, které jsou společné pro všechny nebo na většinu publikací. Odvozené třídy potom implementují členy, které jsou jedinečné pro konkrétní druhy publikace, které představují.

- Jak daleko se rozšířila vaše hierarchie tříd. Chcete vytvořit hierarchii tří nebo více tříd, nikoli jednoduše základní třídu a jednu nebo více odvozených tříd? Například `Publication` může být základní třídou `Periodical`, která je zase základní třídou `Magazine`, `Journal` a `Newspaper`.

  Pro váš příklad budete používat malou hierarchii `Publication` třídy a jednu odvozenou třídu, `Book`. Příklad můžete snadno zvětšit a vytvořit tak mnoho dalších tříd, které jsou odvozeny od `Publication`, například `Magazine` a `Article`.

- Zda má smysl vytvořit instanci základní třídy. Pokud tomu tak není, měli byste použít klíčové slovo [abstract](../language-reference/keywords/abstract.md) pro třídu. V opačném případě může být vytvořena instance třídy `Publication` voláním svého konstruktoru třídy. Pokud je proveden pokus o vytvoření instance třídy označené klíčovým slovem `abstract` přímým voláním konstruktoru třídy, C# kompilátor vygeneruje chybu CS0144, "nemůže vytvořit instanci abstraktní třídy nebo rozhraní". Pokud je proveden pokus o vytvoření instance třídy pomocí reflexe, vyvolá metoda Reflection <xref:System.MemberAccessException>.

  Ve výchozím nastavení lze vytvořit instanci základní třídy voláním svého konstruktoru třídy. Nemusíte explicitně definovat konstruktor třídy. Pokud není k dispozici ve zdrojovém kódu základní třídy, C# kompilátor automaticky poskytne výchozí konstruktor (bez parametrů).

  Pro váš příklad označíte třídu `Publication` jako [abstraktní](../language-reference/keywords/abstract.md) , takže nelze vytvořit instanci.  Třída `abstract` bez jakýchkoli metod `abstract` označuje, že tato třída představuje abstraktní koncept, který je sdílen mezi několika konkrétními třídami (například `Book`, `Journal`).

- Zda odvozené třídy musí dědit implementaci základní třídy konkrétních členů, zda mají možnost přepsat implementaci základní třídy nebo zda musí poskytovat implementaci. Pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) vynutíte odvozené třídy pro zajištění implementace. Použijete klíčové slovo [Virtual](../language-reference/keywords/virtual.md) k povolení odvozených tříd pro přepsání metody základní třídy. Ve výchozím nastavení nejsou metody definované v základní *třídě přepsatelné* .

 Třída `Publication` neobsahuje žádné metody `abstract`, ale samotná třída je `abstract`.

- Zda odvozená třída představuje konečnou třídu v hierarchii dědičnosti a nemůže být použita jako základní třída pro další odvozené třídy. Ve výchozím nastavení může kterákoli třída sloužit jako základní třída. Můžete použít [zapečetěné](../language-reference/keywords/sealed.md) klíčové slovo k označení, že třída nemůže sloužit jako základní třída pro žádné další třídy. Došlo k pokusu o odvození od zapečetěné třídy s chybou kompilátoru CS0509, "nelze odvozovat od zapečetěného typu \<typeName >".

  Jako příklad označíte svou odvozenou třídu jako `sealed`.

Následující příklad ukazuje zdrojový kód pro třídu `Publication` a také výčet `PublicationType`, který je vrácen vlastností `Publication.PublicationType`. Kromě členů, které dědí z <xref:System.Object>, třída `Publication` definuje následující jedinečné členy a přepsání členů:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Vzhledem k tomu, že třída `Publication` je `abstract`, nelze vytvořit instanci přímo z kódu, podobně jako v následujícím příkladu:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Nicméně jeho konstruktor instance lze volat přímo z konstruktorů odvozené třídy, jak ukazuje zdrojový kód třídy `Book`.

- Dvě vlastnosti týkající se publikace

  `Title` je vlastnost <xref:System.String> jen pro čtení, jejíž hodnota je dodána voláním konstruktoru `Publication`.

  `Pages` je vlastnost pro čtení i zápis <xref:System.Int32>, která určuje, kolik celkových stránek publikace má. Hodnota je uložena v soukromém poli s názvem `totalPages`. Musí se jednat o kladné číslo, nebo je vyvolána <xref:System.ArgumentOutOfRangeException>.

- Členové související s vydavatelem

  Dvě vlastnosti, `Publisher` a `Type`jen pro čtení. Hodnoty jsou původně poskytnuty voláním konstruktoru třídy `Publication`.

- Členové související s publikováním

  Existují dvě metody, `Publish` a `GetPublicationDate`, nastavení a vrácení data publikace. Metoda `Publish` nastaví příznak Private `published` na `true` při volání a přiřadí k němu datum předané jako argument pro pole private `datePublished`. Metoda `GetPublicationDate` vrátí řetězec "NYP", pokud je příznak `published` `false`, a hodnotu `datePublished` pole, pokud je `true`.

- Členové související s copyrightem

  Metoda `Copyright` přebírá jméno vlastníka autorského práva a rok copyrightu jako argumenty a přiřazuje je k vlastnostem `CopyrightName` a `CopyrightDate`.

- Přepsání metody `ToString`

  Pokud typ nepřepisuje metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType>, vrátí plně kvalifikovaný název typu, který je malý použití při odlišení jedné instance od druhé. Třída `Publication` Přepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby vracela hodnotu vlastnosti `Title`.

Následující obrázek znázorňuje vztah mezi základní třídou `Publication` a implicitně děděnou <xref:System.Object> třídou.

![Třídy objektu a publikace](media/publication-class.jpg)

### <a name="the-book-class"></a>Třída `Book`

Třída `Book` představuje knihu jako specializovaný typ publikace. Následující příklad ukazuje zdrojový kód pro třídu `Book`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Kromě členů, které dědí z `Publication`, třída `Book` definuje následující jedinečné členy a přepsání členů:

- Dva konstruktory

  Dva konstruktory `Book` sdílejí tři společné parametry. Dva, *název* a *Vydavatel*odpovídají parametrům `Publication` konstruktoru. Třetí je *Autor*, který je uložený do veřejné vlastnosti neměnného `Author`. Jeden konstruktor obsahuje parametr *ISBN* , který je uložený v `ISBN` automatické vlastnosti.

  První konstruktor používá klíčové slovo [This](../language-reference/keywords/this.md) k volání druhého konstruktoru. Řetězení konstruktorů je běžným vzorem v definování konstruktorů. Konstruktory s menšími parametry poskytují výchozí hodnoty při volání konstruktoru s největším počtem parametrů.

  Druhý konstruktor používá klíčové slovo [Base](../language-reference/keywords/base.md) k předání názvu a názvu vydavatele konstruktoru základní třídy. Pokud neprovedete explicitní volání konstruktoru základní třídy ve zdrojovém kódu, C# kompilátor automaticky dodá volání výchozí třídy Base nebo konstruktoru bez parametrů.

- Vlastnost `ISBN` jen pro čtení, která vrací číslo mezinárodní knihy standardního objektu `Book`, jedinečné číslo s 10 nebo 13 číslicemi. ISBN je zadáno jako argument jednoho z `Book` konstruktorů. ISBN je uložen v soukromém zálohovacím poli, které je automaticky generováno kompilátorem.

- Vlastnost `Author` jen pro čtení. Jméno autora je zadáno jako argument pro oba konstruktory `Book` a je uloženo ve vlastnosti.

- Dvě vlastnosti `Price` a `Currency`s cenami jen pro čtení. Jejich hodnoty jsou k dispozici jako argumenty ve volání metody `SetPrice`. Vlastnost `Currency` je třímístný symbol měny ISO (například USD za americký dolar). Z vlastnosti <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> lze načíst symboly ISO měny. Obě tyto vlastnosti jsou externě jen pro čtení, ale obě lze nastavit pomocí kódu ve třídě `Book`.

- `SetPrice` metoda, která nastavuje hodnoty vlastností `Price` a `Currency`. Tyto hodnoty jsou vraceny pomocí stejných vlastností.

- Přepíše metodu `ToString` (zděděná z `Publication`) a metody <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> a <xref:System.Object.GetHashCode%2A> (zděděné z <xref:System.Object>).

  Pokud není přepsán, metoda <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> testuje referenční rovnost. To znamená, že dvě proměnné objektu jsou považovány za stejné, pokud odkazují na stejný objekt. Ve třídě `Book`, na druhé straně by měly být dva objekty `Book` stejné, pokud mají stejné ISBN.

  Pokud přepíšete metodu <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>, je nutné také přepsat metodu <xref:System.Object.GetHashCode%2A>, která vrací hodnotu, kterou modul runtime používá k ukládání položek v kolekcích hash pro efektivní načtení. Kód hash by měl vracet hodnotu, která je konzistentní s testem pro rovnost. Vzhledem k tomu, že jste přepsali <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> pro návrat `true` Pokud jsou vlastnosti ISBN dvou `Book` objektů stejné, vrátíte kód hash vypočítaný voláním metody <xref:System.String.GetHashCode%2A> řetězce vráceného vlastností `ISBN`.

Následující obrázek znázorňuje vztah mezi `Book` třídou a `Publication`, její základní třídou.

![Třídy publikace a knihy](media/book-class.jpg)

Nyní můžete vytvořit instanci objektu `Book`, vyvolat jeho jedinečné i zděděné členy a předat jej jako argument metodě, která očekává parametr typu `Publication` nebo typu `Book`, jak ukazuje následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Navrhování abstraktních základních tříd a jejich odvozených tříd
<a name="abstract"></a>

V předchozím příkladu jste definovali základní třídu, která poskytuje implementaci pro určitý počet metod, který umožňuje odvozeným třídám sdílet kód. V mnoha případech však neočekáváme, že základní třída poskytuje implementaci. Místo toho je základní třídou *abstraktní třída* , která deklaruje *abstraktní metody*; slouží jako šablona definující členy, které musí implementovat jednotlivé odvozené třídy. Obvykle v abstraktní základní třídě je implementace každého odvozeného typu pro tento typ jedinečná. Označili jste třídu pomocí klíčového slova abstract, protože nevytvořila žádné smysly pro vytvoření instance objektu `Publication`, i když třída poskytovala implementace funkcí běžných pro publikace.

Každý uzavřený 2D tvar obsahuje například dvě vlastnosti: oblast, vnitřní rozsah tvaru; a obvodu nebo vzdálenost podél okrajů obrazce. Způsob, jakým jsou tyto vlastnosti vypočítávány, však závisí zcela na konkrétním tvaru. Vzorec pro výpočet hraničního (nebo obvodu) kružnice, například se liší od trojúhelníku. Třída `Shape` je `abstract` třída s metodami `abstract`. Který označuje, že odvozené třídy mají stejné funkce, ale tyto odvozené třídy implementují tuto funkčnost jinak.

Následující příklad definuje abstraktní základní třídu s názvem `Shape`, která definuje dvě vlastnosti: `Area` a `Perimeter`. Kromě označení třídy pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) je každý člen instance označen také pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) . V tomto případě `Shape` také přepíše metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType>, aby vrátila název typu, nikoli jeho plně kvalifikovaný název. A definuje dva statické členy `GetArea` a `GetPerimeter`, které umožňují volajícíům snadno načíst oblast a obvod instance jakékoli odvozené třídy. Pokud předáte instanci odvozené třídy jedné z těchto metod, modul runtime zavolá metodu přepsání odvozené třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Pak můžete odvodit některé třídy z `Shape`, které reprezentují konkrétní tvary. Následující příklad definuje tři třídy, `Triangle`, `Rectangle`a `Circle`. Každá z nich používá vzorec jedinečný pro konkrétní obrazec k výpočtu oblasti a hraničního prostředí. Některé odvozené třídy také definují vlastnosti, například `Rectangle.Diagonal` a `Circle.Diameter`, které jsou jedinečné pro tvar, který představují.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Následující příklad používá objekty odvozené z `Shape`. Vytvoří instanci pole objektů odvozených od `Shape` a zavolá statické metody třídy `Shape`, která zabalí návratové hodnoty vlastností `Shape`. Modul runtime načítá hodnoty z potlačených vlastností odvozených typů. Příklad také přetypování každého objektu `Shape` v poli na jeho odvozený typ a, pokud je přetypování úspěšné, načte vlastnosti této konkrétní podtřídy `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Viz také:

- [Třídy a objekty](../tour-of-csharp/classes-and-objects.md)
- [Dědičnost (C# Průvodce programováním)](../programming-guide/classes-and-structs/inheritance.md)
