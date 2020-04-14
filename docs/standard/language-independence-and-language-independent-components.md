---
title: Jazyková nezávislost a jazykově nezávislé komponenty
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
ms.openlocfilehash: 725884d8ab6d6d9009ad1cdd7bc185889cd5e485
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243060"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

Rozhraní .NET Framework je nezávislé na jazyce. To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na rozhraní .NET Framework, jako je například C#, C++/CLI, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL a Windows PowerShell. Můžete přistupovat k typům a členům knihoven tříd vyvinutých pro rozhraní .NET Framework, aniž byste museli znát jazyk, ve kterém byly původně napsány, a aniž byste museli dodržovat některé z konvencí původního jazyka. Pokud jste vývojář komponent, vaše komponenta může přistupovat libovolnou aplikací rozhraní .NET Framework bez ohledu na její jazyk.

> [!NOTE]
> Tato první část tohoto článku popisuje vytváření komponent nezávislých na jazyce – to znamená, že součásti, které mohou být spotřebovány aplikacemi, které jsou napsány v libovolném jazyce. Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného ve více jazycích. viz [Interoperabilita mezi jazyky](#CrossLang) v druhé části tohoto článku.

Chcete-li plně pracovat s jinými objekty napsanými v libovolném jazyce, musí objekty vystavit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která platí pro vygenerovaná sestavení. Specifikace společného jazyka je definována v oddílu I, větách 7 až 11 [normy ECMA-335: Společná jazyková infrastruktura](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Pokud vaše součást odpovídá specifikaci společného jazyka, je zaručeno, že je kompatibilní se specifikací CLS a je přístupná z kódu v sestaveních napsaných v libovolném programovacím jazyce, který podporuje cls. Můžete určit, zda vaše součást odpovídá specifikaci společného <xref:System.CLSCompliantAttribute> jazyka v době kompilace použitím atributu ve zdrojovém kódu. Další informace naleznete [v tématu Atribut CLSCompliantAttribute](#CLSAttribute).

V tomto článku:

- [Pravidla dodržování předpisů CLS](#Rules)

  - [Typy a podpisy členů typu](#Types)

  - [Zásady vytváření názvů](#naming)

  - [Převod typů](#conversion)

  - [Pole](#arrays)

  - [Rozhraní](#Interfaces)

  - [Výčty](#enums)

  - [Typ členů obecně](#members)

  - [Přístupnost členů](#MemberAccess)

  - [Obecné typy a členy](#Generics)

  - [Konstruktory](#ctors)

  - [Vlastnosti](#properties)

  - [Události](#events)

  - [Přetížení](#overloads)

  - [Výjimky](#exceptions)

  - [Atributy](#attributes)

- [Atribut CLSCompliantAttribute](#CLSAttribute)

- [Vzájemná funkční spolupráce mezi jazyky](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů CLS

Tato část popisuje pravidla pro vytvoření součásti kompatibilní se standardem CLS. Úplný seznam pravidel naleznete v oddílu I, článku 11 [normy ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specifikace společného jazyka popisuje každé pravidlo pro dodržování specifikace CLS, protože se vztahuje na spotřebitele (vývojáři, kteří programově přistupují k součásti, která je kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytvoření knihoven kompatibilních se specifikací CLS) a extendery (vývojáři, kteří vytvářejí nástroj, jako je kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty kompatibilní se specifikací CLS). Tento článek se zaměřuje na pravidla, která se vztahují na rámce. Všimněte si však, že některá pravidla, která platí pro rozšiřující zařízení, se mohou vztahovat také na sestavení, která jsou vytvořena pomocí reflection.emit.

Chcete-li navrhnout komponentu, která je jazykově nezávislá, stačí použít pravidla pro dodržování předpisů CLS na veřejné rozhraní komponenty. Vaše soukromá implementace nemusí odpovídat specifikaci.

> [!IMPORTANT]
> Pravidla pro dodržování předpisů cls se vztahují pouze na veřejné rozhraní komponenty, nikoli na její privátní implementaci.

Například nepodepsaná celá čísla <xref:System.Byte> jiná než nejsou kompatibilní se standardem CLS. Vzhledem `Person` k tomu, že `Age` třída v <xref:System.UInt16>následujícím příkladu zpřístupňuje vlastnost typu , zobrazí se v následujícím kódu upozornění kompilátoru.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Třídu `Person` cls můžete provést změnou typu `Age` vlastnosti z <xref:System.UInt16> <xref:System.Int16>na , což je 16bitové podepsané číslo cls. Není třeba měnit typ soukromého `personAge` pole.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Veřejné rozhraní knihovny se skládá z následujících:

- Definice veřejných tříd.

- Definice veřejné členy veřejné třídy a definice členů přístupných odvozené třídy (to znamená, chráněné členy).

- Parametry a návratové typy veřejných metod veřejných tříd a parametry a návratové typy metod přístupných odvozeným třídám.

Pravidla pro dodržování předpisů cls jsou uvedeny v následující tabulce. Znění pravidel je převzato doslovně z [normy ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je autorská práva 2012 od ecma International. Podrobnější informace o těchto pravidlech naleznete v následujících částech.

|Kategorie|Seznamte se s |Pravidlo|Číslo pravidla|
|--------------|---------|----------|-----------------|
|Usnadnění|[Přístupnost členů](#MemberAccess)|Usnadnění přístupu se nesmí změnit při přepsání zděděných metod, s `family-or-assembly`výjimkou přepsání metody zděděné z jiného sestavení s usnadněním přístupu . V tomto případě musí mít `family`přepsání přístupnost .|10|
|Usnadnění|[Přístupnost členů](#MemberAccess)|Viditelnost a přístupnost typů a členů musí být takové, aby typy v podpisu kteréhokoli člena byly viditelné a přístupné vždy, když je člen sám viditelný a přístupný. Například veřejná metoda, která je viditelná mimo jeho sestavení, nesmí mít argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typů tvořících instanci obecný typ použitý v podpisu každého člena musí být viditelná a přístupná vždy, když je člen sám viditelný a přístupný. Například instance obecný typ přítomný v podpisu člena, který je viditelný mimo jeho sestavení nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení.|12|
|Pole|[Pole](#arrays)|Pole musí mít prvky s typem kompatibilním se standardem CLS a všechny rozměry pole musí mít dolní hranice nula. Pouze skutečnost, že položka je pole a typ prvku pole musí být nutné rozlišovat mezi přetížení. Při přetížení je založena na dvou nebo více typů pole typy prvků musí být pojmenovány typy.|16|
|Atributy|[Atributy](#attributes)|Atributy musí být <xref:System.Attribute?displayProperty=nameWithType>typu nebo typu, který z něj dědí.|41|
|Atributy|[Atributy](#attributes)|Cls umožňuje pouze podmnožinu kódování vlastní atributy. V těchto kódováních se zobrazí pouze typy (viz <xref:System.Type?displayProperty=nameWithType>oddíl <xref:System.String?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType>IV): <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType> <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType> <xref:System.Int16?displayProperty=nameWithType>, , , , , , , a jakýkoli typ výčtu založený na typu základního celočíselné číslo cls.|34|
|Atributy|[Atributy](#attributes)|Cls neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz Oddíl II),`modopt`ale umožňuje volitelné modifikátory ( , viz Oddíl II), kterému nerozumí.|35|
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu musí volat některé instance konstruktor jeho základní třídy před dojde k přístupu k datzitý instance. (To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)|21|
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu nesmí být volán s výjimkou součásti vytvoření objektu a objekt nesmí být inicializován dvakrát.|22|
|Výčty|[Výčty](#enums)|Základní typ výčtu musí být vestavěný typ celého čísla CLS, název pole bude "value__" a `RTSpecialName`toto pole bude označeno .|7|
|Výčty|[Výčty](#enums)|Existují dva různé druhy výčtů, označené přítomností nebo <xref:System.FlagsAttribute?displayProperty=nameWithType> nepřítomností vlastního atributu (viz Partition IV Library). Jeden představuje pojmenované celé číslo hodnoty; ostatní představuje pojmenované bitové příznaky, které lze kombinovat pro generování nepojmenované hodnoty. Hodnota an `enum` není omezena na zadané hodnoty.|8|
|Výčty|[Výčty](#enums)|Literálová statická pole výčtu musí mít typ výčtu samotného.|9|
|Události|[Události](#events)|Metody, které implementují `SpecialName` událost, musí být označeny v metadatech.|29|
|Události|[Události](#events)|Přístupnost události a jejích přistupujících objektů musí být totožná.|30|
|Události|[Události](#events)|Metody `add` `remove` a metody události musí být buď přítomny, nebo chybí.|31|
|Události|[Události](#events)|Metody `add` `remove` a pro událost musí mít jeden parametr, jehož typ definuje typ události <xref:System.Delegate?displayProperty=nameWithType>a který musí být odvozen od písmene a).|32|
|Události|[Události](#events)|Události musí dodržovat konkrétní vzor pojmenování. Atribut `SpecialName` uvedený v pravidle CLS 29 se při porovnávání názvů ignoruje a musí dodržovat pravidla identifikátorů.|33|
|Výjimky|[Výjimky](#exceptions)|Objekty, které jsou vyvolány musí být typu <xref:System.Exception?displayProperty=nameWithType> nebo typu dědit z něj. Metody kompatibilní se standardem CLS však nejsou nutné k blokování šíření jiných typů výjimek.|40|
|Obecné|[Dodržování předpisů CLS: pravidla](#Rules)|Pravidla CLS platí pouze pro ty části typu, které jsou přístupné nebo viditelné mimo definující sestavu.|1|
|Obecné|[Dodržování předpisů CLS: pravidla](#Rules)|Členové typů, které nejsou kompatibilní se standardem CLS, nesmějí být označeni jako kompatibilní se standardem CLS.|2|
|Obecné typy|[Obecné typy a členy](#Generics)|Vnořené typy musí mít alespoň tolik obecných parametrů jako ohraničující typ. Obecné parametry v nosného typu odpovídají podle pozice obecným parametrům v jeho ohraničujícím typu.|42|
|Obecné typy|[Obecné typy a členy](#Generics)|Název obecného typu musí kódovat počet parametrů typu deklarovaných na nevnořeném typu nebo nově zaváděných do typu, pokud je vnořen, podle výše definovaných pravidel.|43|
|Obecné typy|[Obecné typy a členy](#Generics)|Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že všechna omezení základního typu nebo rozhraní budou splněna omezeními obecného typu.|4444|
|Obecné typy|[Obecné typy a členy](#Generics)|Typy používané jako omezení obecných parametrů musí být samy o sobě kompatibilní se standardem CLS.|45|
|Obecné typy|[Obecné typy a členy](#Generics)|Viditelnost a přístupnost členů (včetně vnořených typů) v instanovaném obecném typu se považuje spíše za vymezenou podle konkrétní instance než za obecné prohlášení typu jako celek. Za tímto podmínek stále platí pravidla viditelnosti a usnadnění pravidla CLS 12.|46|
|Obecné typy|[Obecné typy a členy](#Generics)|Pro každou abstraktní nebo virtuální obecnou metodu musí být výchozí konkrétní (neabstraktní) implementace.|47|
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní kompatibilní s cls nesmějí k jejich provádění vyžadovat definici metod, které nejsou kompatibilní se standardem CLS.|18|
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní kompatibilní s CLS nesmějí definovat statické metody ani pole.|19|
|Členové|[Typ členů obecně](#members)|Globální statická pole a metody nejsou kompatibilní se standardem CLS.|36|
|Členové|--|Hodnota literálu statické je určena pomocí metadat inicializace pole. Literál kompatibilní se standardem CLS musí mít hodnotu zadanou v metadatech inicializace pole, která je přesně `enum`stejného typu jako literál (nebo základního typu, pokud je tento literál ).|13|
|Členové|[Typ členů obecně](#members)|Omezení vararg není součástí cls a pouze konvence volání podporované CLS je standardní spravované volání konvence.|15|
|Zásady vytváření názvů|[Zásady vytváření názvů](#naming)|Sestavy se řídí přílohou 7 technické zprávy 15 standardu Unicode Standard3.0, kterými se řídí soubor <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>znaků, které mohou začínat a být zahrnuty do identifikátorů dostupných online na adrese . Identifikátory musí být v kanonickém formátu definovaném normalizačním formulářem C kódování Unicode. Pro účely cls dva identifikátory jsou stejné, pokud jejich mapování malých písmen (jak je určeno unicode národní ho necitlivý, 1-1 malá písmena mapování) jsou stejné. To znamená, že pro dva identifikátory, které mají být považovány za odlišné podle CLS, které se liší ve více než jen jejich případě. Však za účelem přepsání zděděné definice CLI vyžaduje přesné kódování původní deklarace použít.|4|
|Přetížení|[Zásady vytváření názvů](#naming)|Všechny názvy zavedené v oblasti souladu se standardem CLS musí být odlišné nezávislé svého druhu, s výjimkou případů, kdy jsou názvy totožné a jsou vyřešeny přetížením. To znamená, že zatímco CTSumožňuje jeden typ použít stejný název pro metodu a pole, CLS není.|5|
|Přetížení|[Zásady vytváření názvů](#naming)|Pole a vnořené typy se odlišují pouze porovnáním identifikátorů, i když CTS umožňuje rozlišit odlišné podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů) se liší více než pouze návratový typ, s výjimkou, jak je uvedeno v pravidle CLS 39.|6|
|Přetížení|[Přetížení](#overloads)|Pouze vlastnosti a metody mohou být přetíženy.|37|
|Přetížení|[Přetížení](#overloads)|Vlastnosti a metody mohou být přetíženy pouze na základě počtu a `op_Implicit` typů `op_Explicit`jejich parametrů, s výjimkou operátorů převodu s názvem a , které mohou být také přetíženy na základě jejich návratového typu.|38|
|Přetížení|--|Mají-li dvě nebo více metod kompatibilních se standardem CLS deklarované v typu stejný název a pro určitou sadu instancí typu mají stejný parametr a návratové typy, musí být všechny tyto metody sémanticky rovnocenné při těchto instancích typu.|48|
|Typy|[Typ a typ podpisy členů](#Types)|<xref:System.Object?displayProperty=nameWithType>je kompatibilní se standardem CLS. Všechny ostatní třídy kompatibilní se standardem CLS dědí z třídy kompatibilní se standardem CLS.|23|
|Vlastnosti|[Vlastnosti](#properties)|Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech.|24|
|Vlastnosti|[Vlastnosti](#properties)|Všechny přistupující objekty vlastnosti musí být statické, všechny virtuální nebo všechny instance.|26|
|Vlastnosti|[Vlastnosti](#properties)|Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro getter a typy všech, kromě konečného parametru setteru. Všechny tyto typy musí být kompatibilní se standardem CLS a nesmí být spravovány ukazateli (tj. nesmí být předávány odkazem).|27|
|Vlastnosti|[Vlastnosti](#properties)|Vlastnosti musí splňovat konkrétní vzor pojmenování. Atribut `SpecialName` uvedený v pravidle CLS 24 se při porovnávání názvů ignoruje a musí dodržovat pravidla identifikátorů. Vlastnost musí mít getter metoda, setter metoda nebo obojí.|28|
|Převod typů|[Převod typů](#conversion)|Je-li `op_Explicit` k dispozici nebo `op_Implicit` je-li poskytnut, musí být poskytnut alternativní způsob zajištění nátlaku.|39|
|Typy|[Typ a typ podpisy členů](#Types)|Typy hodnot v rámečku nejsou kompatibilní se standardem CLS.|3|
|Typy|[Typ a typ podpisy členů](#Types)|Všechny typy uvedené v podpisu musí být kompatibilní se standardem CLS. Všechny typy, které tvoří typ typu instanovaného obecného typu, musí být kompatibilní se standardem CLS.|11|
|Typy|[Typ a typ podpisy členů](#Types)|Zadané odkazy nejsou kompatibilní se standardem CLS.|14|
|Typy|[Typ a typ podpisy členů](#Types)|Nespravované typy ukazatelů nejsou kompatibilní se standardem CLS.|17|
|Typy|[Typ a typ podpisy členů](#Types)|Třídy, typy hodnot a rozhraní kompatibilní se standardem CLS nevyžadují implementaci členů, kteří nejsou kompatibilní se standardem CLS.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Typy a podpisy členů typu

Typ <xref:System.Object?displayProperty=nameWithType> je kompatibilní se systémem CLS a je základním typem všech typů objektů v systému typu rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je <xref:System.String> implicitní (například <xref:System.Object> třída implicitně dědí z <xref:System.Globalization.CultureNotFoundException> třídy) nebo <xref:System.ArgumentException> explicitní (například třída <xref:System.SystemException> explicitně dědí z <xref:System.Exception> třídy, která explicitně dědí z třídy, která explicitně dědí z třídy). Aby byl odvozený typ kompatibilní se standardem CLS, musí být jeho základní typ také kompatibilní se standardem CLS.

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se standardem CLS. Definuje základní `Counter` třídu, která používá nepodepsané 32bitové celé číslo jako čítač. Vzhledem k tomu, že třída poskytuje funkci čítače zabalením nepodepsaného celého čísla, je třída označena jako nekompatibilní se souborem CLS. V důsledku toho odvozené `NonZeroCounter`třídy , také není kompatibilní se seznamem CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se standardem CLS. Kromě toho pro obecné typy:

- Všechny typy, které tvoří instanci obecný typ musí být kompatibilní se standardem CLS.

- Všechny typy používané jako omezení obecných parametrů musí být kompatibilní se standardem CLS.

Systém [běžného typu](../../docs/standard/base-types/common-type-system.md) rozhraní .NET Framework obsahuje řadu předdefinovaných typů, které jsou podporovány přímo modulem RUNTIME společného jazyka a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se standardem CLS.

|Typ kompatibilní se standardem CLS|Popis|
|-------------------------|-----------------|
|<xref:System.Byte>|Osmibitové celé číslo bez znaménka|
|<xref:System.Int16>|16bitové podepsané celé číslo|
|<xref:System.Int32>|32bitové podepsané celé číslo|
|<xref:System.Int64>|64bitové podepsané celé číslo|
|<xref:System.Single>|Hodnota s plovoucí desetinnou desetinnou s jednou přesností|
|<xref:System.Double>|Hodnota s dvojitou přesností s plovoucí desetinnou desetinnou desetinnou hodnotou|
|<xref:System.Boolean>|`true`nebo `false` typ hodnoty|
|<xref:System.Char>|Jednotka kódovaného kódu UTF-16|
|<xref:System.Decimal>|Desítkové číslo bez plovoucí desetinné čárky|
|<xref:System.IntPtr>|Ukazatel nebo úchyt definované platformou|
|<xref:System.String>|Kolekce nulových, jednoho <xref:System.Char> nebo více objektů|

Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se standardem CLS.

|Nevyhovující typ|Popis|Alternativa odpovídající specifikaci CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|Osmibitový podepsaný celočíselný datový typ|<xref:System.Int16>|
|<xref:System.TypedReference>|Ukazatel na objekt a jeho typ běhu|Žádný|
|<xref:System.UInt16>|16bitové celé celé číslo bez znaménka|<xref:System.Int32>|
|<xref:System.UInt32>|32bitové celé celé číslo bez znaménka|<xref:System.Int64>|
|<xref:System.UInt64>|64bitové celé celé číslo bez znaménka|<xref:System.Int64>(může přetékat), <xref:System.Numerics.BigInteger>nebo<xref:System.Double>|
|<xref:System.UIntPtr>|Nepodepsaný ukazatel nebo popisovač|<xref:System.IntPtr>|

Knihovna tříd rozhraní .NET Framework nebo jakákoli jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se standardem CLS. například:

- Typy hodnot v rámečku. Následující příklad jazyka C# vytvoří třídu, `int*` která `Value`má veřejnou vlastnost typu s názvem . Vzhledem `int*` k tomu, že je zabalený typ hodnoty, kompilátor jej označí jako nekompatibilní se souborem CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Zadané odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ. Zadané odkazy jsou reprezentovány v rozhraní <xref:System.TypedReference> .NET Framework třídou.

Pokud typ není kompatibilní se standardem CLS, měli byste použít <xref:System.CLSCompliantAttribute> atribut s hodnotou. `isCompliant` `false` Další informace naleznete v části [atributu CLSCompliantAttribute.](#CLSAttribute)

Následující příklad ilustruje problém dodržování cls v podpisu metody a v obecném typu instanování. Definuje třídu `InvoiceItem` s vlastností <xref:System.UInt32>typu , vlastností typu `Nullable(Of UInt32)`a konstruktorem <xref:System.UInt32> s `Nullable(Of UInt32)`parametry typu a . Při pokusu o kompilaci v tomto příkladu se zobrazí čtyři upozornění kompilátoru.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Chcete-li odstranit upozornění kompilátoru, nahraďte `InvoiceItem` typy, které nejsou kompatibilní se standardem CLS ve veřejném rozhraní, kompatibilními typy:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Kromě konkrétních uvedených typů nejsou některé kategorie typů kompatibilní se standardem CLS. Patří mezi ně nespravované typy ukazatelů a typy ukazatelů funkce. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo k vytvoření pole celá čísla.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Pro abstraktní třídy kompatibilní se seznamem `abstract` CLS (to `MustInherit` znamená třídy označené jako v jazyce C# nebo jako v jazyce Visual Basic) musí být všichni členové třídy také kompatibilní se seznamem CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Zásady vytváření názvů

Vzhledem k tomu, že některé programovací jazyky nerozlišují malá a velká písmena, identifikátory (například názvy oborů názvů, typů a členů) se musí lišit o více než malá a velká písmena. Dva identifikátory jsou považovány za rovnocenné, pokud jejich mapování s nižšími písmeny jsou stejné. Následující příklad jazyka C# definuje `Person` dvě `person`veřejné třídy a . Vzhledem k tomu, že se liší pouze podle případu, kompilátor Jazyka C# je označí jako nekompatibilní se seznamem CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Identifikátory programovacích jazyků, jako jsou názvy jmenných prostorů, typů a členů, musí odpovídat [normě Unicode 3.0, Technické zprávě 15, příloha 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

- Prvním znakem identifikátoru může být libovolné velké písmeno Unicode, malé písmeno, písmeno nadpisu, modifikační písmeno, jiné písmeno nebo písmeno. Informace o kategoriích znaků Unicode naleznete ve výčtu. <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType>

- Následující znaky mohou být z libovolné z kategorií jako první znak a mohou také obsahovat značky bez mezer, mezery kombinující značky, desetinná čísla, interpunkce spojnice a formátovací kódy.

Před porovnáním identifikátorů byste měli odfiltrovat formátovací kódy a převést identifikátory na formulář C normalizace kódování Unicode, protože jeden znak může být reprezentován více jednotkami kódu kódovaných UTF-16. Posloupnosti znaků, které vytvářejí stejné jednotky kódu ve formuláři C normalizace kódování Unicode, nejsou kompatibilní se seznamem CLS. Následující příklad definuje vlastnost `Å`s názvem , která se skládá z znaku ANGSTROM sign (U + 212B) a druhé vlastnosti s názvem `Å`, která se skládá ze znaku latinka velké písmeno a s kroužkem nad (U + 00C5). Kompilátory jazyka C# i Visual Basic označí zdrojový kód jako nekompatibilní se souborem CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou vyřešeny přetížením. Tento požadavek je přísnější než u běžného systému typů, který umožňuje více členů v rámci oboru mít stejné názvy, pokud se jedná o různé druhy členů (například jeden je metoda a jeden je pole). Zejména pro členy typu:

- Pole a vnořené typy se rozlišují podle názvu samotného.

- Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouze návratový typ.

Následující příklad ilustruje požadavek, že názvy členů musí být jedinečné v rámci jejich oboru. Definuje třídu s `Converter` názvem, která `Conversion`zahrnuje čtyři členy s názvem . Tři jsou metody a jedna je vlastnost. Metoda, která <xref:System.Int64> obsahuje parametr, je jednoznačně pojmenována, <xref:System.Int32> ale dvě metody s parametrem nejsou, protože vrácená hodnota není považována za součást podpisu člena. Vlastnost `Conversion` také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na běžný jazyk runtime, musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v jazyce C# a jazyka Visual Basic. Následující příklad jazyka však je schopen rozptýlit třídu `case` pojmenovanou z klíčového `case` slova pomocí počáteční a uzavírací závorky. V opačném případě by v příkladu vytvořit chybovou zprávu , "Klíčové slovo není platný jako identifikátor" a nepodaří zkompilovat.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Následující příklad jazyka C# je schopen `case` vytvořit instanci třídy pomocí symbolu `@` k rozdvojení identifikátoru z klíčového slova jazyka. Bez něj by kompilátor Jazyka C# zobrazil dvě chybové zprávy"Type expected" a "Invalid expression term 'case'."

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Převod typů

Specifikace společného jazyka definuje dva operátory převodu:

- `op_Implicit`, který se používá pro rozšíření převody, které nevedou ke ztrátě dat nebo přesnosti. <xref:System.Decimal> Například struktura obsahuje přetížený `op_Implicit` operátor převést hodnoty <xref:System.Char> integrální typy a hodnoty na <xref:System.Decimal> hodnoty.

- `op_Explicit`, který se používá pro zúžení převody, které mohou mít za následek ztrátu velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. <xref:System.Decimal> Struktura například obsahuje přetížený `op_Explicit` operátor <xref:System.Double> <xref:System.Single> převést <xref:System.Decimal> a hodnoty <xref:System.Decimal> a převést <xref:System.Double> <xref:System.Single>hodnoty <xref:System.Char>na integrální hodnoty , , a .

Však ne všechny jazyky podporují přetížení operátoru nebo definice vlastní operátory. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob provedení převodu. Doporučujeme zadat `From` *xxx* `To`a *xxx* metody.

Následující příklad definuje implicitní a explicitní převody kompatibilní se standardem CLS. Vytvoří třídu, `UDouble` která představuje podepsané číslo s dvojitou přesností s plovoucí desetinnou desetinnou hlavou. Poskytuje implicitní převody `UDouble` <xref:System.Double> z a pro `UDouble` explicitní <xref:System.Single> <xref:System.Double> převody <xref:System.Single> z `UDouble`, do `UDouble`, a na . Definuje také `ToDouble` metodu jako alternativu k implicitnímu operátoru převodu a metodě `ToSingle`, `FromDouble`a `FromSingle` metody jako alternativy k operátorům explicitního převodu.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Pole

Pole kompatibilní se standardem CLS splňují následující pravidla:

- Všechny dimenze pole musí mít dolní mez nula. Následující příklad vytvoří pole, které není kompatibilní se standardem CLS, s dolní mez jednoho. Všimněte si, že <xref:System.CLSCompliantAttribute> i přes přítomnost atributu kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metodou není kompatibilní se seznamem CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Všechny prvky pole se musí skládat z typů kompatibilních se standardem CLS. Následující příklad definuje dvě metody, které vracejí pole, která nejsou kompatibilní se standardem CLS. První vrátí pole <xref:System.UInt32> hodnot. Druhý vrátí <xref:System.Object> pole, <xref:System.Int32> které <xref:System.UInt32> obsahuje a hodnoty. Přestože kompilátor identifikuje první pole jako nekompatibilní z důvodu jeho <xref:System.UInt32> typu, nedokáže rozpoznat, že druhé pole obsahuje prvky, které nejsou kompatibilní se standardem CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Řešení přetížení pro metody, které mají parametry pole je založena na skutečnosti, že jsou pole a na jejich typu prvku. Z tohoto důvodu je následující definice `GetSquares` přetížené metody kompatibilní se standardem CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Rozhraní

Rozhraní kompatibilní se standardem CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace). Rozhraní kompatibilní se standardem CLS nemůže obsahovat některou z následujících možností:

- Statické metody nebo statická pole. Kompilátory jazyka C# i Visual Basic generují chyby kompilátoru, pokud definujete statický člen v rozhraní.

- Pole. Kompilátory jazyka C# i Visual Basic generují chyby kompilátoru, pokud definujete pole v rozhraní.

- Metody, které nejsou kompatibilní se standardem CLS. Například následující definice rozhraní obsahuje `INumber.GetUnsigned`metodu , která je označena jako nekompatibilní se souborem CLS. Tento příklad generuje upozornění kompilátoru.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Z důvodu tohoto pravidla nejsou typy kompatibilní se standardem CLS nutné implementovat členy, které nejsou kompatibilní se standardem CLS. Pokud rozhraní kompatibilní se standardem CLS zveřejňuje třídu, která implementuje rozhraní kompatibilní se standardem CLS, měla by také poskytovat konkrétní implementace všech členů, které nejsou kompatibilní se standardem CLS.

Kompilátory jazyka kompatibilní se seznamem CLS musí také umožnit třídě poskytovat samostatné implementace členů, které mají stejný název a podpis ve více rozhraních.  C# a Visual Basic podporují [explicitní implementace rozhraní](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) poskytovat různé implementace identicky pojmenované metody. Visual Basic také `Implements` podporuje klíčové slovo, které umožňuje explicitně určit, které rozhraní a člen konkrétní člen implementuje. Následující příklad ilustruje tento scénář definováním `Temperature` třídy, `ICelsius` `IFahrenheit` která implementuje rozhraní a jako explicitní implementace rozhraní.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Výčty

Výčty kompatibilní se standardem CLS se musí řídit těmito pravidly:

- Základní typ výčtu musí být vnitřní cls kompatibilní s celočíselným <xref:System.Int16> <xref:System.Int32>číslem <xref:System.Int64>(<xref:System.Byte>, , , nebo ). Například následující kód se pokusí definovat výčtu, <xref:System.UInt32> jehož základní typ je a generuje upozornění kompilátoru.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Typ výčtu musí mít jedno `Value__` pole instance s <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> názvem atributem. To umožňuje implicitně odkazovat na hodnotu pole.

- Výčet zahrnuje literálová statická pole, jejichž typy odpovídají typu samotného výčtu. Například pokud definujete `State` výčet s `State.On` hodnotami `State.On` `State.Off` a `State.Off`, a jsou oba `State`literál statická pole, jejichž typ je .

- Existují dva druhy výčtů:

  - Výčet, který představuje sadu vzájemně se vylučujících, pojmenovaných celé hodnoty. Tento typ výčtu je označen absencí vlastního atributu. <xref:System.FlagsAttribute?displayProperty=nameWithType>

  - Výčet, který představuje sadu bitových příznaků, které lze kombinovat generovat nepojmenovanou hodnotu. Tento typ výčtu je označen přítomností <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastní atribut.

  Další informace naleznete v dokumentaci ke <xref:System.Enum> struktuře.

- Hodnota výčtu není omezena na rozsah jeho zadané hodnoty. Jinými slovy rozsah hodnot ve výčtu je rozsah jeho základní hodnotu. Metodu <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> můžete použít k určení, zda je zadaná hodnota členem výčtu.

<a name="members"></a>

### <a name="type-members-in-general"></a>Typ členů obecně

Specifikace společného jazyka vyžaduje, aby všechna pole a metody byly přístupné jako členové určité třídy. Globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány na rozdíl od typu) proto nejsou kompatibilní se standardem CLS. Pokud se pokusíte zahrnout globální pole nebo metodu do zdrojového kódu, kompilátory jazyka C# i Visual Basic vygenerují chybu kompilátoru.

Specifikace společného jazyka podporuje pouze standardní konvence spravovaných volání. Nepodporuje nespravované konvence volání a metody s proměnnými `varargs` argumenty označenými klíčovým slovem. Pro seznamy proměnných argumentů, které jsou <xref:System.ParamArrayAttribute> kompatibilní se standardní spravovanou konvencí volání, použijte atribut nebo implementaci jednotlivého jazyka, jako je například `params` klíčové slovo v jazyce C# a `ParamArray` klíčové slovo v jazyce Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Přístupnost členů

Přepsání zděděného člena nemůže změnit přístupnost tohoto člena. Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě. Existuje jedna výjimka: a `protected internal` (v `Protected Friend` jazyce C#) nebo (v jazyce Visual Basic) člen v jednom sestavení, který je přepsán typem v jiném sestavení. V takovém případě je `Protected`přístupnost přepsání .

Následující příklad ilustruje chybu, která je <xref:System.CLSCompliantAttribute> generována při `true`atribut `Human`je nastaven na , `Animal`a , což je `Species` třída odvozená z , pokusí se změnit přístupnost vlastnosti z veřejné na soukromé. Příklad se úspěšně zkompiluje, pokud je jeho usnadnění přístupu změněno na veřejné.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Typy v podpisu člena musí být přístupné vždy, když je tento člen přístupný. Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je soukromý, chráněný nebo interní. Následující příklad ilustruje chybu kompilátoru, `StringWrapper` která je výsledkem, když konstruktor třídy zpřístupní hodnotu vnitřního `StringOperationType` výčtu, která určuje, jak by měla být zabalena hodnota řetězce.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Obecné typy a členy

Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich ohraničující typ. Ty odpovídají podle pozice obecných parametrů v ohraničujícím typu. Obecný typ může také obsahovat nové obecné parametry.

Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořených typů může být skryt syntaxí jednotlivých jazyků. V následujícím příkladu obecný `Outer<T>` typ obsahuje dvě `Inner1A` `Inner1B<U>`vnořené třídy a . Volání `ToString` metody, ze které každá třída <xref:System.Object.ToString%2A?displayProperty=nameWithType>dědí , ukazují, že každá vnořená třída obsahuje parametry typu její obsahující třídy.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Obecné názvy typů jsou kódovány v *názvu\`* formuláře n \` , kde *název* je název typu, je literál znaku a *n* je počet parametrů deklarovaných na typu nebo, pro vnořené obecné typy, počet nově zavedených parametrů typu. Toto kódování obecných názvů typů je primárně zajímavé pro vývojáře, kteří používají reflexe pro přístup k obecným typům stížností CLS v knihovně.

Pokud jsou použita omezení pro obecný typ, všechny typy používané jako omezení musí být také kompatibilní se standardem CLS. Následující příklad definuje třídu `BaseClass` s názvem, která není kompatibilní `BaseCollection` se standardem CLS, a obecnou třídu s názvem, jejíž parametr typu musí být odvozen z `BaseClass`. Ale `BaseClass` protože není kompatibilní se standardem CLS, kompilátor vydává upozornění.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Pokud obecný typ je odvozen od obecného základního typu, musí znovu deklarovat všechna omezení tak, aby může zaručit, že omezení na základní typ jsou také splněny. Následující příklad definuje, `Number<T>` který může představovat libovolný číselný typ. Také definuje třídu, `FloatingPoint<T>` která představuje hodnotu s plovoucí desetinnou tácek. Zdrojový kód se však nepodaří zkompilovat, `Number<T>` protože nepoužije omezení (že `FloatingPoint<T>`T musí být typ hodnoty) na .

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Příklad se úspěšně zkompiluje, `FloatingPoint<T>` pokud je omezení přidáno do třídy.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Specifikace společného jazyka ukládá konzervativní model instance pro vnořené typy a chráněné členy. Otevřené obecné typy nemohou vystavit pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného chráněného obecného typu. Neobecné typy, které rozšiřují konkrétní konkretizovat obecnou základní třídu nebo rozhraní, nemohou vystavit pole nebo členy s podpisy, které obsahují jinou instanci vnořeného chráněného obecného typu.

Následující příklad definuje obecný typ `C1<T>` (nebo `C1(Of T)` v jazyce Visual `C1<T>.N` Basic) `C1(Of T).N` a chráněnou třídu (nebo v jazyce Visual Basic). `C1<T>`má dvě `M1` metody `M2`a . Však `M1` není kompatibilní se standardem CLS, `C1(Of Integer).N`protože se pokusí\<vrátit `C1<int>.N` (nebo ) objekt z C1 T> (nebo `C1(Of T)`). Druhá třída `C2`, je odvozena `C1<long>` `C1(Of Long)`od (nebo ). Má dvě metody `M3` `M4`a . `M3`není kompatibilní se sítí CLS, `C1<int>.N` protože `C1(Of Integer).N`se pokusí vrátit (nebo ) objekt z podtřídy . `C1<long>` Všimněte si, že kompilátory jazyka může být ještě více omezující. V tomto příkladu visual basic zobrazí chybu `M4`při pokusu o kompilaci .

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Konstruktory

Konstruktory ve třídách a strukturách kompatibilních se standardem CLS se musí řídit těmito pravidly:

- Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy předtím, než přistupuje k datům zděděné instance. Tento požadavek je způsoben skutečností, že konstruktory základní třídy nejsou zděděny jejich odvozené třídy. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.

  Kompilátory obvykle vynucují toto pravidlo nezávisle na dodržování předpisů cls, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je `Person` odvozena z `Doctor` třídy, `Person` ale třída se nezdaří volat konstruktor třídy inicializovat zděděná pole instance.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Konstruktor objektu nelze volat s výjimkou vytvoření objektu. Kromě toho objekt nelze inicializovat dvakrát. Například to znamená, že <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> a metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> deserializace, jako je například nesmí volat konstruktory.

<a name="properties"></a>

### <a name="properties"></a>Vlastnosti

Vlastnosti v typech kompatibilních se standardem CLS se musí řídit těmito pravidly:

- Vlastnost musí mít setter, getter nebo obojí. V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí `get_`jako samostatné metody `set_`(getter se nazývá *propertyname* a setter je *propertyname*) označené jako `SpecialName` v metadatech sestavení. Kompilátory jazyka C# a Visual Basic vynucují toto pravidlo automaticky bez nutnosti použití atributu. <xref:System.CLSCompliantAttribute>

- Typ vlastnosti je návratový typ vlastnosti getter a poslední argument setter. Tyto typy musí být kompatibilní se standardem CLS a argumenty nelze přiřadit k vlastnosti odkazem (to znamená, že nemohou být spravovány ukazatele).

- Pokud vlastnost má getter a setter, musí být oba virtuální, statické nebo obě instance. Kompilátory jazyka C# a Visual Basic automaticky vynucují toto pravidlo prostřednictvím syntaxe definice vlastnosti.

<a name="events"></a>

### <a name="events"></a>Události

Událost je definována svým názvem a typem. Typ události je delegát, který se používá k označení události. Například <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost je typu <xref:System.ResolveEventHandler>. Kromě samotné události poskytují implementaci události tři metody s názvy založenými na `SpecialName` názvu události a jsou označeny jako v metadatech sestavení:

- Metoda pro přidání obslužné rutiny události s názvem `add_` *EventName*. Například metoda odběru události <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pro událost `add_AssemblyResolve`je pojmenována .

- Metoda odebrání obslužné `remove_`rutiny události s názvem *EventName*. Například metoda odebrání pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost `remove_AssemblyResolve`je pojmenována .

- Metoda označující, že došlo k `raise_`události s názvem *EventName*.

> [!NOTE]
> Většina pravidel společné jazykové specifikace týkající se událostí je implementována kompilátory jazyka a je transparentní pro vývojáře komponent.

Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost. Musí být také všechny statické, instance nebo virtuální. Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události. Metody add a remove musí být přítomny nebo obě chybí.

Následující příklad definuje třídu kompatibilní se `Temperature` seznamem `TemperatureChanged` CLS s názvem, která vyvolá událost, pokud se změna teploty mezi dvěma hodnotami rovná nebo překročí prahovou hodnotu. Třída `Temperature` explicitně definuje `raise_TemperatureChanged` metodu tak, aby mohla selektivně spouštět obslužné rutiny událostí.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Přetížení

Specifikace společného jazyka ukládá přetíženým členům následující požadavky:

- Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru. Volání konvence, návratový typ, vlastní modifikátory použité na metodu nebo její parametr a zda parametry jsou předány hodnotou nebo odkazem nejsou považovány při rozlišování mezi přetížení. Příklad naleznete v kódu požadavku, že názvy musí být jedinečné v rámci oboru v části [Konvence pojmenování.](#naming)

- Pouze vlastnosti a metody mohou být přetíženy. Pole a události nemohou být přetíženy.

- Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.

> [!NOTE]
> A `op_Explicit` `op_Implicit` operátory jsou výjimky z pravidla, že vrácená hodnota není považována za součást podpisu metody pro řešení přetížení. Tyto dva operátory mohou být přetíženy na základě jejich parametry a jejich vrácená hodnota.

<a name="exceptions"></a>

### <a name="exceptions"></a>Výjimky

Objekty výjimek <xref:System.Exception?displayProperty=nameWithType> musí být odvozeny <xref:System.Exception?displayProperty=nameWithType>z jiného typu odvozeného z . Následující příklad ilustruje chybu kompilátoru, která `ErrorClass` se vynaložit při vlastní třídy s názvem se používá pro zpracování výjimek.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Chcete-li opravit `ErrorClass` tuto chybu, <xref:System.Exception?displayProperty=nameWithType>třída musí dědit z . Kromě toho `Message` musí být vlastnost přepsána. Následující příklad opravuje tyto chyby definovat třídu, `ErrorClass` která je kompatibilní se standardem CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Atributy

In.NET framework sestavení, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody. Vlastní atributy musí <xref:System.Attribute?displayProperty=nameWithType> být odvozeny z <xref:System.Attribute?displayProperty=nameWithType>nebo z typu odvozeného z .

Následující příklad porušuje toto pravidlo. Definuje třídu, `NumericAttribute` která není <xref:System.Attribute?displayProperty=nameWithType>odvozena z . Všimněte si, že chyba kompilátoru výsledky pouze v případě, že je použit atribut nekompatibilní se standardem CLS, nikoli při definování třídy.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

Konstruktor nebo vlastnosti atributu kompatibilního se standardem CLS mohou vystavit pouze následující typy:

- <xref:System.Boolean>

- <xref:System.Byte>

- <xref:System.Char>

- <xref:System.Double>

- <xref:System.Int16>

- <xref:System.Int32>

- <xref:System.Int64>

- <xref:System.Single>

- <xref:System.String>

- <xref:System.Type>

- Libovolný typ výčtu, <xref:System.Byte>jehož <xref:System.Int32>základní <xref:System.Int64>typ je , <xref:System.Int16>, , nebo .

Následující příklad definuje `DescriptionAttribute` třídu, která <xref:System.Attribute>je odvozena od . Konstruktor třídy má parametr `Descriptor`typu , takže třída není kompatibilní se seznamem CLS. Všimněte si, že kompilátor Jazyka C# vydává upozornění, ale úspěšně zkompiluje, zatímco kompilátor jazyka visual basic nevydává upozornění ani chybu.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Atribut CLSCompliantAttribute

Atribut <xref:System.CLSCompliantAttribute> se používá k označení, zda prvek programu je v souladu se specifikací společného jazyka. Konstruktor <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29> obsahuje jeden povinný `isCompliant`parametr , který označuje, zda je prvek programu kompatibilní se standardem CLS.

V době kompilace kompilátor zjistí nekompatibilní prvky, které jsou považovány za kompatibilní se standardem CLS a vydává upozornění. Kompilátor nevydává upozornění pro typy nebo členy, které jsou explicitně deklarovány jako nekompatibilní.

Vývojáři komponent <xref:System.CLSCompliantAttribute> mohou atribut použít dvěma způsoby:

- Chcete-li definovat části veřejného rozhraní vystavené komponenty, které jsou kompatibilní se seznamem CLS a součásti, které nejsou kompatibilní se standardem CLS. Pokud se atribut používá k označení určitých prvků programu jako kompatibilní se standardem CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na rozhraní .NET Framework.

- Chcete-li zajistit, že veřejné rozhraní knihovny komponent zpřístupňuje pouze prvky programu, které jsou kompatibilní se standardem CLS. Pokud prvky nejsou kompatibilní se seznamem CLS, kompilátory obecně vydá upozornění.

> [!WARNING]
> V některých případech kompilátory jazyka vynucovat cls kompatibilní pravidla bez ohledu na to, zda se používá <xref:System.CLSCompliantAttribute> atribut. Například definování statického člena v rozhraní porušuje pravidlo CLS. V tomto ohledu pokud `static` definujete (v `Shared` jazyce C#) nebo (v jazyce Visual Basic) člen v rozhraní, c# a visual basic kompilátory zobrazit chybovou zprávu a nepodaří zkompilovat aplikaci.

Atribut <xref:System.CLSCompliantAttribute> je označen <xref:System.AttributeUsageAttribute> atributem, který <xref:System.AttributeTargets.All?displayProperty=nameWithType>má hodnotu . Tato hodnota umožňuje použít <xref:System.CLSCompliantAttribute> atribut pro libovolný prvek programu, včetně sestavení, modulů, typů (třídy, struktury, výčty, rozhraní a delegáty), členů typu (konstruktory, metody, vlastnosti, pole a události), parametry, obecné parametry a vrácené hodnoty. V praxi byste však měli atribut použít pouze pro sestavení, typy a členy typu. V opačném případě kompilátory ignorovat atribut a nadále generovat upozornění kompilátoru vždy, když narazí na nekompatibilní parametr, obecný parametr nebo vrácenou hodnotu ve veřejné rozhraní knihovny.

Hodnota atributu <xref:System.CLSCompliantAttribute> je zděděna obsaženými prvky programu. Například pokud je sestavení označeno jako kompatibilní se standardem CLS, jeho typy jsou také kompatibilní se standardem CLS. Pokud je typ označen jako kompatibilní se seznamem CLS, jeho vnořené typy a členy jsou také kompatibilní se standardem CLS.

Zděděnou dodržování předpisů můžete explicitně přepsat použitím atributu <xref:System.CLSCompliantAttribute> na prvek obsaženého programu. Můžete například použít <xref:System.CLSCompliantAttribute> atribut s `isCompliant` hodnotou k definování nekompatibilního `false` typu v kompatibilním sestavení a `isCompliant` můžete `true` použít atribut s hodnotou k definování kompatibilního typu v nekompatibilním sestavení. Můžete také definovat nekompatibilní členy v kompatibilním typu. Nekompatibilní typ však nemůže mít kompatibilní členy, takže nelze `isCompliant` použít `true` atribut s hodnotou k přepsání dědičnosti z nekompatibilního typu.

Při vývoji součástí byste měli vždy <xref:System.CLSCompliantAttribute> použít atribut k označení, zda vaše sestavení, jeho typy a jeho členy jsou kompatibilní se seznamem CLS.

Vytvoření součástí kompatibilních se standardem CLS:

1. Použijte <xref:System.CLSCompliantAttribute> k označení sestavení jako kompatibilní se standardem CLS.

2. Označte všechny veřejně exponované typy v sestavení, které nejsou kompatibilní se standardem CLS jako nekompatibilní.

3. Označte všechny veřejně exponované členy v typech kompatibilních se standardem CLS jako nekompatibilní.

4. Poskytněte alternativu kompatibilní se standardem CLS pro členy, kteří nejsou kompatibilní se standardem CLS.

Pokud jste úspěšně označili všechny nekompatibilní typy a členy, kompilátor by neměl vyzařovat žádná upozornění na nedodržování předpisů. Měli byste však určit, které členy nejsou kompatibilní se standardem CLS, a v dokumentaci k produktu uvést jejich alternativy kompatibilní se standardem CLS.

Následující příklad používá <xref:System.CLSCompliantAttribute> atribut k definování sestavení kompatibilního se `CharacterUtilities`seznamem CLS a typu , který má dva členy, které nesplňují požadavky cls. Vzhledem k tomu, `CLSCompliant(false)` že oba členy jsou označeny atributem, kompilátor nevytváří žádná upozornění. Třída také poskytuje alternativu kompatibilní se standardem CLS pro obě metody. Obvykle bychom jen přidat dvě přetížení `ToUTF16` metody poskytnout alternativy kompatibilní se standardem CLS. Protože však metody nemohou být přetíženy na základě vrácené hodnoty, názvy metod kompatibilních se standardem CLS se liší od názvů nekompatibilních metod.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Pokud vyvíjíte aplikaci, nikoli knihovnu (to znamená, že nevystavujete typy nebo členy, které můžou využívat jiní vývojáři aplikací), je dodržování předpisů cls pro prvky programu, které vaše aplikace využívá, zajímavé pouze v případě, že je váš jazyk nepodporuje. V takovém případě kompilátor jazyka vygeneruje chybu při pokusu o použití prvku, který není kompatibilní se standardem CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden význam, který je popsán v článku [Jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md), zahrnuje bezproblémové náročné typy napsané v jednom jazyce z aplikace napsané v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro StringUtil.vb, který obsahuje jeden člen, `ToTitleCase`, ve své třídě `StringLib`.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů. Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:

```console
vbc /t:module StringUtil.vb
```

Další informace o syntaxi příkazového řádku kompilátoru jazyka Visual Basic naleznete [v tématu Building from the Command Line](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:

```console
csc /t:module NumberUtil.cs
```

Další informace o syntaxi příkazového řádku kompilátoru jazyka C# naleznete v [tématu Vytváření příkazového řádku s csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Potom pomocí [propojovacího nástroje možnosti](/cpp/build/reference/linker-options) zkompilovat dva moduly do sestavení:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`. Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:

```console
vbc example.vb /r:UtilityLib.dll
```

Chcete-li zkompilovat pomocí jazyka C#, změňte název kompilátoru z **vbc** na **csc**a změňte příponu souboru z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Viz také

- <xref:System.CLSCompliantAttribute>
