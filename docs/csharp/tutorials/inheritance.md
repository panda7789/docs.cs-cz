---
title: 'Dědičnost v jazyce C #'
description: Naučte se používat dědičnost v knihovnách a aplikacích C#.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 70db8716bea84984ad56d79fa9e26aab3a8182fa
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063507"
---
# <a name="inheritance-in-c-and-net"></a>Dědičnost v jazyce C# a technologii .NET

V tomto kurzu se seznámíte s děděním v jazyce C#. Dědičnost je funkcí objektově orientovaných programovacích jazyků, které umožňují definovat základní třídu, která poskytuje konkrétní funkce (data a chování) a definovat odvozené třídy, které obě tyto funkce dědí nebo přepíší.

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

C# a .NET podporují jenom *jednu dědičnost* . To znamená, že třída může dědit pouze z jedné třídy. Dědičnost je však tranzitivní, což umožňuje definovat hierarchii dědičnosti pro sadu typů. Jinými slovy typ `D` může dědit z typu `C` , který dědí z typu `B` , který dědí z typu základní třídy `A` . Vzhledem k tomu, že dědičnost je tranzitivní, `A` jsou členové typu k dispozici pro typ `D` .

Ne všichni členové základní třídy jsou děděni odvozenými třídami. Následující členové nejsou děděni:

- [Statické konstruktory](../programming-guide/classes-and-structs/static-constructors.md), které inicializují statická data třídy.

- [Konstruktory instancí](../programming-guide/classes-and-structs/constructors.md), které zavoláte k vytvoření nové instance třídy. Každá třída musí definovat vlastní konstruktory.

- [Finalizační metody](../programming-guide/classes-and-structs/destructors.md), které jsou volány uvolňováním paměti modulu runtime pro zničení instancí třídy.

Zatímco všichni ostatní členové základní třídy jsou děděni odvozenými třídami, ať už jsou viditelné, nebo nejsou závislé na jejich přístupnost. Přístupnost člena má vliv na jeho viditelnost pro odvozené třídy následujícím způsobem:

- [Soukromé](../language-reference/keywords/private.md) členy jsou viditelné pouze v odvozených třídách, které jsou vnořeny do jejich základní třídy. V opačném případě nejsou viditelné v odvozených třídách. V následujícím příkladu `A.B` je vnořená třída, která je odvozena z `A` a je `C` odvozena z `A` . Soukromé `A.value` pole je viditelné v A.B. Pokud však odeberete komentáře z `C.GetValue` metody a pokusíte se zkompilovat příklad, vyvolá chybu kompilátoru CS0122: "' A. Value ' je z důvodu úrovně ochrany nepřístupná."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Chránění](../language-reference/keywords/protected.md) členové jsou viditelné pouze v odvozených třídách.

- [Interní](../language-reference/keywords/internal.md) členy jsou viditelné pouze v odvozených třídách, které jsou umístěny ve stejném sestavení jako základní třída. Nejsou viditelné v odvozených třídách, které jsou umístěny v jiném sestavení ze základní třídy.

- [Veřejné](../language-reference/keywords/public.md) členy jsou viditelné v odvozených třídách a jsou součástí veřejného rozhraní odvozené třídy. Veřejné zděděné členy mohou být volány stejně, jako kdyby byly definovány v odvozené třídě. V následujícím příkladu třída `A` definuje metodu s názvem `Method1` a třídy `B` dědí z třídy `A` . Příklad pak volá `Method1` , jako by šlo o metodu instance v `B` .

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Odvozené třídy mohou také *přepsat* zděděné členy poskytnutím alternativní implementace. Aby bylo možné přepsat člena, musí být člen v základní třídě označený klíčovým slovem [Virtual](../language-reference/keywords/virtual.md) . Ve výchozím nastavení nejsou členy základní třídy označeny jako `virtual` a nelze je přepsat. Pokus o přepsání nevirtuálního člena, jak je znázorněno v následujícím příkladu, vygeneruje chybu kompilátoru CS0506: " \<member> nemůže přepsat zděděný člen, \<member> protože není označen jako virtuální, abstraktní nebo přepsání.

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

V některých případech *musí* odvozená třída přepsat implementaci základní třídy. Členy základní třídy označené pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) vyžadují, aby je přepsaly odvozené třídy. Při pokusu o zkompilování následujícího příkladu dojde k chybě kompilátoru CS0534, " &lt; Třída &gt; neimplementuje zděděný abstraktní člen &lt; &gt; ", protože třída `B` neposkytuje žádnou implementaci pro `A.Method1` .

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

Kromě jakýchkoli typů, které mohou dědit prostřednictvím jedné dědičnosti, všechny typy v systému typů .NET implicitně dědí z <xref:System.Object> nebo z typu odvozeného z něj. Společná funkce nástroje <xref:System.Object> je k dispozici pro libovolný typ.

Chcete-li zjistit, co implicitní dědičnost znamená, definujte novou třídu, `SimpleClass` , která je jednoduše prázdnou definicí třídy:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Pak můžete použít reflexi (což vám umožní zkontrolovat metadata typu a získat informace o tomto typu) a získat tak seznam členů, kteří patří do daného `SimpleClass` typu. I když jste nedefinovali žádné členy ve `SimpleClass` třídě, výstup z příkladu označuje, že ve skutečnosti má devět členů. Jeden z těchto členů je konstruktor bez parametrů (nebo výchozí), který je automaticky dodán pro `SimpleClass` typ kompilátorem jazyka C#. Zbývajících osm jsou členové <xref:System.Object> , typ, ze kterého všechny třídy a rozhraní v systému typů .NET jsou nakonec implicitně děděny.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Implicitní dědění z <xref:System.Object> třídy zpřístupňuje tyto metody pro `SimpleClass` třídu:

- Veřejná `ToString` metoda, která převede `SimpleClass` objekt na jeho řetězcovou reprezentaci, vrátí plně kvalifikovaný název typu. V tomto případě `ToString` Metoda vrátí řetězec "SimpleClass".

- Tři metody, které testují rovnost dvou objektů: metodu veřejné instance `Equals(Object)` , veřejnou statickou `Equals(Object, Object)` metodu a veřejnou statickou `ReferenceEquals(Object, Object)` metodu. Ve výchozím nastavení tyto metody test rovnosti referencí; To znamená, že dva objektové proměnné musí odkazovat na stejný objekt.

- Veřejná `GetHashCode` metoda, která vypočítá hodnotu, která umožňuje použití instance typu v kolekcích s algoritmem hash.

- Veřejná `GetType` metoda, která vrací <xref:System.Type> objekt, který představuje `SimpleClass` typ.

- Chráněná <xref:System.Object.Finalize%2A> metoda, která je navržena pro uvolnění nespravovaných prostředků před tím, než je paměť objektu uvolněna systémem uvolňování paměti.

- Chráněná <xref:System.Object.MemberwiseClone%2A> metoda, která vytvoří neomezený klon aktuálního objektu.

Z důvodu implicitní dědičnosti můžete volat všechny zděděné členy z `SimpleClass` objektu stejným způsobem, jako by byl ve skutečnosti člen definovaný ve `SimpleClass` třídě. Například následující příklad volá `SimpleClass.ToString` metodu, která `SimpleClass` dědí z <xref:System.Object> .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

V následující tabulce jsou uvedeny kategorie typů, které lze vytvořit v jazyce C#, a typy, ze kterých jsou implicitně děděny. Každý základní typ zpřístupňuje jinou sadu členů prostřednictvím dědičnosti implicitně odvozeným typům.

| Kategorie typu | Implicitně dědí z                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| třída         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| delegát      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Dědičnost a "je" relace

Obvykle se dědičnost používá k vyjádření vztahu "je" vztah mezi základní třídou a jednou nebo více odvozenými třídami, kde jsou odvozenými třídami specializované verze základní třídy; odvozená třída je typem základní třídy. Například `Publication` Třída představuje publikaci libovolného druhu a `Book` `Magazine` třídy a představují konkrétní typy publikací.

> [!NOTE]
> Třída nebo struktura může implementovat jedno nebo více rozhraní. I když je implementace rozhraní často prezentována jako alternativní řešení pro jednoduchou dědičnost nebo jako způsob použití dědičnosti s strukturami, má vyjadřovat jiný vztah ("může provádět" vztah) mezi rozhraním a jeho implementací typu než dědění. Rozhraní definuje podmnožinu funkcí (například možnost testování rovnosti, pro porovnání nebo řazení objektů nebo pro podporu analýzy a formátování zohledňující jazykovou verzi), že rozhraní zpřístupňuje své implementující typy.

Všimněte si, že "je" také vyjadřuje vztah mezi typem a specifickou instancí tohoto typu. V následujícím příkladu `Automobile` je třída, která má tři jedinečné vlastnosti jen pro čtení: `Make` , výrobce automobilu `Model` , druh automobilu a `Year` rok výroby. Vaše `Automobile` Třída má také konstruktor, jehož argumenty jsou přiřazeny hodnotám vlastností a Přepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření řetězce, který jedinečně identifikuje `Automobile` instanci namísto `Automobile` třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

V takovém případě byste neměli spoléhat na dědění, která představuje konkrétní automobilové a modely. Například nemusíte definovat `Packard` typ pro reprezentaci Automobiles vyráběných společností společnosti Packard motorových automobilů. Místo toho je lze reprezentovat vytvořením `Automobile` objektu s příslušnými hodnotami předaných konstruktoru třídy, jak je uvedeno v následujícím příkladu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Je relace založená na dědičnosti nejvhodnější pro základní třídu a na odvozené třídy, které přidávají další členy do základní třídy nebo které vyžadují další funkce, které nejsou k dispozici v základní třídě.

## <a name="designing-the-base-class-and-derived-classes"></a>Návrh základní třídy a odvozených tříd

Pojďme se podívat na postup navrhování základní třídy a jejích odvozených tříd. V této části definujete základní třídu, `Publication` která představuje publikaci libovolného druhu, jako je kniha, časopis, novinka, deník, článek atd. Také definujete `Book` třídu, která je odvozena z `Publication` . Můžete snadno zvětšit příklad pro definování dalších odvozených tříd, například `Magazine` , `Journal` , `Newspaper` a `Article` .

### <a name="the-base-publication-class"></a>Základní třída publikace

Při navrhování vaší `Publication` třídy je potřeba provést několik rozhodnutí o návrhu:

- Jaké členy mají být zahrnuty do základní `Publication` třídy a zda `Publication` členy poskytují implementace metod nebo zda `Publication` je abstraktní základní třída, která slouží jako šablona pro odvozené třídy.

  V tomto případě `Publication` Třída nabídne implementace metod. Oddíl [navrhování abstraktních základních tříd a jejich odvozené třídy](#abstract) obsahuje příklad, který používá abstraktní základní třídu k definování metod, které musí přepsat odvozené třídy. Odvozené třídy jsou bezplatné k poskytnutí libovolné implementace, která je vhodná pro odvozený typ.

  Možnost opětovného použití kódu (to znamená, že více odvozených tříd sdílí deklaraci a implementaci metod základní třídy a není nutné je přepsat) je výhodou neabstraktních základních tříd. Proto byste měli přidat členy do, `Publication` Pokud je jejich kód pravděpodobně sdílen některými nebo nejvíce specializovanými `Publication` typy. Pokud nebudete moci efektivně poskytovat implementace základní třídy, bude nutné, abyste v odvozených třídách poskytovali v podstatě identické implementace členů, nikoli na jednu implementaci v základní třídě. Nutnost udržovat duplicitní kód ve více umístěních je potenciální zdrojem chyb.

  Jak maximalizovat opětovné použití kódu a vytvořit logickou a intuitivní hierarchii dědičnosti, chcete mít jistotu, že zahrnete do `Publication` třídy pouze data a funkce, které jsou společné pro všechny nebo pro většinu publikací. Odvozené třídy potom implementují členy, které jsou jedinečné pro konkrétní druhy publikace, které představují.

- Jak daleko se rozšířila vaše hierarchie tříd. Chcete vytvořit hierarchii tří nebo více tříd, nikoli jednoduše základní třídu a jednu nebo více odvozených tříd? Například `Publication` může být základní třída `Periodical` , která je zase základní třídou třídy `Magazine` , `Journal` a `Newspaper` .

  Pro váš příklad budete používat malou hierarchii `Publication` třídy a jednu odvozenou třídu `Book` . Příklad lze snadno zvětšit a vytvořit tak mnoho dalších tříd, které jsou odvozeny z `Publication` , například `Magazine` a `Article` .

- Zda má smysl vytvořit instanci základní třídy. Pokud tomu tak není, měli byste použít klíčové slovo [abstract](../language-reference/keywords/abstract.md) pro třídu. V opačném případě `Publication` může být vytvořena instance třídy voláním svého konstruktoru třídy. Pokud se provede pokus o vytvoření instance třídy označené `abstract` klíčovým slovem přímým voláním konstruktoru třídy, kompilátor C# vygeneruje chybu CS0144, "nemůže vytvořit instanci abstraktní třídy nebo rozhraní." Pokud je proveden pokus o vytvoření instance třídy pomocí reflexe, metoda Reflection vyvolá <xref:System.MemberAccessException> .

  Ve výchozím nastavení lze vytvořit instanci základní třídy voláním svého konstruktoru třídy. Nemusíte explicitně definovat konstruktor třídy. Pokud není k dispozici ve zdrojovém kódu základní třídy, kompilátor jazyka C# automaticky poskytuje výchozí konstruktor (bez parametrů).

  Jako příklad označíte `Publication` třídu jako [abstraktní](../language-reference/keywords/abstract.md) , aby se nedá vytvořit instance.  `abstract`Třída bez `abstract` metod označuje, že tato třída představuje abstraktní koncept, který je sdílen mezi několika konkrétními třídami (například `Book` , `Journal` ).

- Zda odvozené třídy musí dědit implementaci základní třídy konkrétních členů, zda mají možnost přepsat implementaci základní třídy nebo zda musí poskytovat implementaci. Pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) vynutíte odvozené třídy pro zajištění implementace. Použijete klíčové slovo [Virtual](../language-reference/keywords/virtual.md) k povolení odvozených tříd pro přepsání metody základní třídy. Ve výchozím nastavení nejsou metody definované v základní *třídě přepsatelné* .

  `Publication`Třída nemá žádné `abstract` metody, ale samotná třída je `abstract` .

- Zda odvozená třída představuje konečnou třídu v hierarchii dědičnosti a nemůže být použita jako základní třída pro další odvozené třídy. Ve výchozím nastavení může kterákoli třída sloužit jako základní třída. Můžete použít [zapečetěné](../language-reference/keywords/sealed.md) klíčové slovo k označení, že třída nemůže sloužit jako základní třída pro žádné další třídy. Došlo k pokusu o odvození z zapečetěné třídy s chybou kompilátoru CS0509, "nemůže odvozovat z zapečetěného typu \<typeName> ".

  Jako příklad označíte svou odvozenou třídu jako `sealed` .

Následující příklad ukazuje zdrojový kód pro `Publication` třídu a také `PublicationType` výčet, který je vrácen `Publication.PublicationType` vlastností. Kromě členů, které dědí z <xref:System.Object> , `Publication` Třída definuje následující jedinečné členy a přepsání členů:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Konstruktor

  Vzhledem k tomu `Publication` , že třída je `abstract` , nemůže být vytvořena instance přímo z kódu, jako v následujícím příkladu:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Nicméně jeho konstruktor instance lze volat přímo z konstruktorů odvozené třídy, jak ukazuje zdrojový kód `Book` třídy.

- Dvě vlastnosti týkající se publikace

  `Title`je vlastnost jen pro čtení <xref:System.String> , jejíž hodnota je dodána voláním `Publication` konstruktoru.

  `Pages`je vlastnost pro čtení a zápis <xref:System.Int32> , která určuje, kolik celkových stránek publikace má. Hodnota je uložena v soukromém poli s názvem `totalPages` . Musí se jednat o kladné číslo nebo <xref:System.ArgumentOutOfRangeException> je vyvolána výjimka.

- Členové související s vydavatelem

  Dvě vlastnosti jen pro čtení `Publisher` a `Type` . Hodnoty jsou původně poskytnuty voláním `Publication` konstruktoru třídy.

- Členové související s publikováním

  Dvě metody `Publish` a `GetPublicationDate` nastavte a vraťte datum publikování. `Publish`Metoda nastaví `published` příznak Private na `true` hodnotu při volání a přiřadí k němu datum předané jako argument privátního `datePublished` pole. `GetPublicationDate`Metoda vrátí řetězec "NYP", pokud je `published` příznak `false` , a hodnotu `datePublished` pole, pokud je `true` .

- Členové související s copyrightem

  `Copyright`Metoda vezme jméno vlastníka autorského práva a rok autorského práva jako argumenty a přiřadí je k `CopyrightName` `CopyrightDate` vlastnostem a.

- Přepsání `ToString` metody

  Pokud typ nepřepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu, vrátí plně kvalifikovaný název typu, který je malý použití při odlišení jedné instance od druhé. `Publication`Třída Přepisuje, <xref:System.Object.ToString%2A?displayProperty=nameWithType> aby vracela hodnotu `Title` Vlastnosti.

Následující obrázek znázorňuje vztah mezi základní `Publication` třídou a implicitně zděděnou <xref:System.Object> třídou.

![Třídy objektu a publikace](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book`Třída

`Book`Třída představuje knihu jako specializovaný typ publikace. Následující příklad ukazuje zdrojový kód pro `Book` třídu.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Kromě členů, které dědí z `Publication` , `Book` Třída definuje následující jedinečné členy a přepsání členů:

- Dva konstruktory

  Dva `Book` konstruktory sdílejí tři společné parametry. Dva, *název* a *Vydavatel*odpovídají parametrům `Publication` konstruktoru. Třetí je *Autor*, který je uložený do veřejné neměnné `Author` Vlastnosti. Jeden konstruktor obsahuje parametr *ISBN* , který je uložený v `ISBN` Automatické vlastnosti.

  První konstruktor používá klíčové slovo [This](../language-reference/keywords/this.md) k volání druhého konstruktoru. Řetězení konstruktorů je běžným vzorem v definování konstruktorů. Konstruktory s menšími parametry poskytují výchozí hodnoty při volání konstruktoru s největším počtem parametrů.

  Druhý konstruktor používá klíčové slovo [Base](../language-reference/keywords/base.md) k předání názvu a názvu vydavatele konstruktoru základní třídy. Pokud neprovedete explicitní volání konstruktoru základní třídy ve zdrojovém kódu, kompilátor jazyka C# automaticky dodá volání výchozího nebo bezparametrů konstruktoru základní třídy.

- Vlastnost jen pro čtení `ISBN` , která vrací `Book` číslo mezinárodní knihy standardního standardního objektu, jedinečné číslo na 10 nebo 13 číslic. ISBN je zadáno jako argument pro jeden z `Book` konstruktorů. ISBN je uložen v soukromém zálohovacím poli, které je automaticky generováno kompilátorem.

- Vlastnost jen pro čtení `Author` . Jméno autora je zadáno jako argument pro oba `Book` konstruktory a je uloženo ve vlastnosti.

- Dvě vlastnosti týkající se cen jen pro čtení `Price` a `Currency` . Jejich hodnoty jsou zadány jako argumenty ve `SetPrice` volání metody. `Currency`Vlastnost je třímístný symbol měny ISO (například USD za americký dolar). Z vlastnosti lze načíst symboly ISO měny <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> . Obě tyto vlastnosti jsou externě jen pro čtení, ale obě lze nastavit pomocí kódu ve `Book` třídě.

- `SetPrice`Metoda, která nastavuje hodnoty `Price` `Currency` vlastností a. Tyto hodnoty jsou vraceny pomocí stejných vlastností.

- Přepíše `ToString` metodu (zděděnou z `Publication` ) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object.GetHashCode%2A> metody a (zděděné z <xref:System.Object> ).

  Pokud není přepsán, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metoda Testuje referenční rovnost. To znamená, že dvě proměnné objektu jsou považovány za stejné, pokud odkazují na stejný objekt. Ve `Book` třídě na druhé straně `Book` by měly být dva objekty stejné, pokud mají stejné ISBN.

  Při přepsání metody je <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> nutné také přepsat <xref:System.Object.GetHashCode%2A> metodu, která vrací hodnotu, kterou modul runtime používá k ukládání položek v kolekcích s algoritmem hash pro efektivní načtení. Kód hash by měl vracet hodnotu, která je konzistentní s testem pro rovnost. Vzhledem k tomu, že jste přepsali <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> `true` , že pokud jsou vlastnosti ISBN dvou `Book` objektů stejné, vrátíte kód hash vypočítaný voláním <xref:System.String.GetHashCode%2A> metody řetězce vráceného `ISBN` vlastností.

Následující obrázek znázorňuje vztah mezi `Book` třídou a `Publication` , její základní třídou.

![Třídy publikace a knihy](media/book-class.jpg)

Nyní můžete vytvořit instanci `Book` objektu, vyvolat jeho jedinečné i zděděné členy a předat jej jako argument metodě, která očekává parametr typu `Publication` nebo typu `Book` , jak ukazuje následující příklad.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Navrhování abstraktních základních tříd a jejich odvozených tříd
<a name="abstract"></a>

V předchozím příkladu jste definovali základní třídu, která poskytuje implementaci pro určitý počet metod, který umožňuje odvozeným třídám sdílet kód. V mnoha případech však neočekáváme, že základní třída poskytuje implementaci. Místo toho je základní třídou *abstraktní třída* , která deklaruje *abstraktní metody*; slouží jako šablona definující členy, které musí implementovat jednotlivé odvozené třídy. Obvykle v abstraktní základní třídě je implementace každého odvozeného typu pro tento typ jedinečná. Označili jste třídu pomocí klíčového slova abstract, protože nemá žádný smysl pro vytvoření instance `Publication` objektu, i když třída poskytovala implementace funkcí běžných pro publikace.

Každý uzavřený 2D tvar obsahuje například dvě vlastnosti: oblast, vnitřní rozsah tvaru; a obvodu nebo vzdálenost podél okrajů obrazce. Způsob, jakým jsou tyto vlastnosti vypočítávány, však závisí zcela na konkrétním tvaru. Vzorec pro výpočet hraničního (nebo obvodu) kružnice, například se liší od trojúhelníku. `Shape`Třída je `abstract` Třída s `abstract` metodami. Který označuje, že odvozené třídy mají stejné funkce, ale tyto odvozené třídy implementují tuto funkčnost jinak.

Následující příklad definuje abstraktní základní třídu s názvem `Shape` , která definuje dvě vlastnosti: `Area` a `Perimeter` . Kromě označení třídy pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) je každý člen instance označen také pomocí klíčového slova [abstract](../language-reference/keywords/abstract.md) . V tomto případě `Shape` přepíše také metodu, <xref:System.Object.ToString%2A?displayProperty=nameWithType> která vrátí název typu, nikoli jeho plně kvalifikovaný název. A definuje dva statické členy `GetArea` a `GetPerimeter` , které umožňují volajícím snadno načíst oblast a obvod instance jakékoli odvozené třídy. Pokud předáte instanci odvozené třídy jedné z těchto metod, modul runtime zavolá metodu přepsání odvozené třídy.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Pak můžete odvodit některé třídy z `Shape` , které představuje konkrétní tvary. Následující příklad definuje tři třídy, `Triangle` , a `Rectangle` `Circle` . Každá z nich používá vzorec jedinečný pro konkrétní obrazec k výpočtu oblasti a hraničního prostředí. Některé odvozené třídy také definují vlastnosti, například `Rectangle.Diagonal` a `Circle.Diameter` , které jsou jedinečné pro tvar, který představují.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Následující příklad používá objekty odvozené z `Shape` . Vytvoří instanci pole objektů odvozených z `Shape` a zavolá statické metody `Shape` třídy, které zalomí hodnoty vrácených `Shape` vlastností. Modul runtime načítá hodnoty z potlačených vlastností odvozených typů. Příklad také přetypování každý `Shape` objekt v poli na odvozený typ a, pokud je přetypování úspěšné, načte vlastnosti této konkrétní podtřídy `Shape` .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Viz také

- [Dědičnost (Průvodce programováním v C#)](../programming-guide/classes-and-structs/inheritance.md)
