---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: Zjistěte, jak můžete vyvíjet v jednom z mnoha podporovaných jazyků v rozhraní .NET, jako je například C#, C++/CLI, F#, IronPython, VB, Visual COBOL a PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 03751fa3758c239cb9eea5fe826dff66c1c1605b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249575"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

.NET je jazykově nezávislý. To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na implementace rozhraní .NET, například C#, F# a Visual Basic. Můžete přistupovat k typům a členům knihoven tříd vyvinutých pro implementace rozhraní .NET, aniž byste museli znát jazyk, ve kterém byly původně napsány, a aniž byste museli dodržovat některé z konvencí původního jazyka. Pokud jste vývojář komponent, vaše komponenta může přistupovat libovolnou aplikací .NET bez ohledu na její jazyk.

> [!NOTE]
> Tato první část tohoto článku popisuje vytváření součásti nezávislé na jazyce - to znamená, že součásti, které mohou být spotřebovány aplikace, které jsou napsány v libovolném jazyce. Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného ve více jazycích. viz [Interoperabilita mezi jazyky](#cross-language-interoperability) v druhé části tohoto článku.

Chcete-li plně pracovat s jinými objekty napsanými v libovolném jazyce, musí objekty vystavit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která platí pro vygenerovaná sestavení. Specifikace společného jazyka je definována v oddílu I, větách 7 až 11 [normy ECMA-335: Společná jazyková infrastruktura](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Pokud vaše součást odpovídá specifikaci společného jazyka, je zaručeno, že je kompatibilní se specifikací CLS a je přístupná z kódu v sestaveních napsaných v libovolném programovacím jazyce, který podporuje cls. Můžete určit, zda vaše součást odpovídá specifikaci společného jazyka v době kompilace použitím atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) na zdrojový kód. Další informace naleznete v [tématu Atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

V tomto článku:

* [Pravidla dodržování předpisů CLS](#cls-compliance-rules)

  * [Typy a podpisy členů typu](#types-and-type-member-signatures)

  * [Zásady vytváření názvů](#naming-conventions)

  * [Převod typů](#type-conversion)

  * [Pole](#arrays)

  * [Rozhraní](#interfaces)

  * [Výčty](#enumerations)

  * [Typ členů obecně](#type-members-in-general)

  * [Přístupnost členů](#member-accessibility)

  * [Obecné typy a členy](#generic-types-and-members)

  * [Konstruktory](#constructors)

  * [Vlastnosti](#properties)

  * [Události](#events)

  * [Přetížení](#overloads)

  * [Výjimky](#exceptions)

  * [Atributy](#attributes)

* [Atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute)

* [Vzájemná funkční spolupráce mezi jazyky](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů CLS

Tato část popisuje pravidla pro vytvoření součásti kompatibilní se standardem CLS. Úplný seznam pravidel naleznete v oddílu I, článku 11 [normy ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specifikace společného jazyka popisuje každé pravidlo pro dodržování specifikace CLS, protože se vztahuje na spotřebitele (vývojáři, kteří programově přistupují k součásti, která je kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytvoření Knihovny kompatibilní se standardem CLS) a rozšiřující zařízení (vývojáři, kteří vytvářejí nástroj, jako je například kompilátor jazyka nebo analyzátor kódu, který vytváří součásti kompatibilní se standardem CLS). Tento článek se zaměřuje na pravidla, která se vztahují na rámce. Všimněte si však, že některá pravidla, která platí pro rozšiřující zařízení, se mohou vztahovat také na sestavení, která jsou vytvořena pomocí [funkce Reflection.Emit](xref:System.Reflection.Emit).

Chcete-li navrhnout komponentu, která je jazykově nezávislá, stačí použít pravidla pro dodržování předpisů CLS na veřejné rozhraní komponenty. Vaše soukromá implementace nemusí odpovídat specifikaci.

> [!IMPORTANT]
> Pravidla pro dodržování předpisů cls se vztahují pouze na veřejné rozhraní komponenty, nikoli na její privátní implementaci.

Například nepodepsaná celá čísla než [Byte](xref:System.Byte) nejsou kompatibilní se smlouvou CLS. Vzhledem `Person` k tomu, že `Age` třída v následujícím příkladu zpřístupňuje vlastnost typu [UInt16](xref:System.UInt16), zobrazí se v následujícím kódu upozornění kompilátoru.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

Třídu Person CLS můžete provést změnou `Age` typu `UInt16` vlastnosti z [Int16](xref:System.Int16), což je 16bitové podepsané číslo cls. Není třeba měnit typ soukromého `personAge` pole.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

Veřejné rozhraní knihovny se skládá z následujících:

* Definice veřejných tříd.

* Definice veřejné členy veřejné třídy a definice členů přístupných odvozené třídy (to znamená, chráněné členy).

* Parametry a návratové typy veřejných metod veřejných tříd a parametry a návratové typy metod přístupných odvozeným třídám.

Pravidla pro dodržování předpisů cls jsou uvedeny v následující tabulce. Znění pravidel je převzato doslovně z [normy ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je autorská práva 2012 od ecma International. Podrobnější informace o těchto pravidlech naleznete v následujících částech.

Kategorie | Seznamte se s  | Pravidlo | Číslo pravidla
-------- | --- | ---- | -----------
Přístupnost | [Přístupnost členů](#member-accessibility) | Usnadnění přístupu se nesmí změnit při přepsání zděděných metod, s `family-or-assembly`výjimkou přepsání metody zděděné z jiného sestavení s usnadněním přístupu . V tomto případě musí mít `family`přepsání přístupnost . | 10
Přístupnost | [Přístupnost členů](#member-accessibility) | Viditelnost a přístupnost typů a členů musí být takové, aby typy v podpisu kteréhokoli člena byly viditelné a přístupné vždy, když je člen sám viditelný a přístupný. Například veřejná metoda, která je viditelná mimo jeho sestavení, nesmí mít argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typů tvořících instanci obecný typ použitý v podpisu každého člena musí být viditelná a přístupná vždy, když je člen sám viditelný a přístupný. Například instance obecný typ přítomný v podpisu člena, který je viditelný mimo jeho sestavení nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení. | 12
Pole | [Pole](#arrays) | Pole musí mít prvky s typem kompatibilním se standardem CLS a všechny rozměry pole musí mít dolní hranice nula. Pouze skutečnost, že položka je pole a typ prvku pole musí být nutné rozlišovat mezi přetížení. Při přetížení je založena na dvou nebo více typů pole typy prvků musí být pojmenovány typy. | 16
Atributy | [Atributy](#attributes) | Atributy musí být typu [System.Attribute](xref:System.Attribute)nebo typu dědícího z něj. | 41
Atributy | [Atributy](#attributes) | Cls umožňuje pouze podmnožinu kódování vlastní atributy. V těchto kódováních se zobrazí pouze typy (viz oddíl IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double)a jakýkoli typ výčtu založený na typu základního celého čísla kompatibilního se standardem CLS. | 34
Atributy | [Atributy](#attributes) | Cls neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz Oddíl II),`modopt`ale umožňuje volitelné modifikátory ( , viz Oddíl II), kterému nerozumí. | 35
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu musí volat některé instance konstruktor jeho základní třídy před dojde k přístupu k datzitý instance. (To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)  | 21
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu nesmí být volán s výjimkou součásti vytvoření objektu a objekt nesmí být inicializován dvakrát. | 22
Výčty | [Výčty](#enumerations) | Základní typ výčtu musí být vestavěný typ celého čísla CLS, název pole bude "value__" a `RTSpecialName`toto pole bude označeno . |  7
Výčty | [Výčty](#enumerations) | Existují dva odlišné druhy výčtů, označené přítomností nebo nepřítomností vlastního atributu [System.FlagsAttribute](xref:System.FlagsAttribute) (viz Knihovna oddílu IV). Jeden představuje pojmenované celé číslo hodnoty; ostatní představuje pojmenované bitové příznaky, které lze kombinovat pro generování nepojmenované hodnoty. Hodnota an `enum` není omezena na zadané hodnoty. |  8
Výčty | [Výčty](#enumerations) | Literálová statická pole výčtu musí mít typ výčtu samotného. |  9
Události | [Události](#events) | Metody, které implementují `SpecialName` událost, musí být označeny v metadatech. |29
Události | [Události](#events) | Přístupnost události a jejích přistupujících objektů musí být totožná. |30
Události | [Události](#events) | Metody `add` `remove` a metody události musí být buď přítomny, nebo chybí. |31
Události | [Události](#events) | Metody `add` `remove` a pro událost musí mít jeden parametr, jehož typ definuje typ události a který musí být odvozen od [System.Delegate](xref:System.Delegate). |32
Události | [Události](#events) | Události musí dodržovat konkrétní vzor pojmenování. Atribut SpecialName uvedený v pravidle CLS 29 bude při porovnávání příslušných názvů ignorován a musí dodržovat pravidla identifikátorů.  |33
Výjimky | [Výjimky](#exceptions) | Objekty, které jsou vyvolány musí být typu [System.Exception](xref:System.Exception) nebo typu dědit z něj. Metody kompatibilní se standardem CLS však nejsou nutné k blokování šíření jiných typů výjimek. | 40
Obecné | [Pravidla dodržování předpisů CLS](#cls-compliance-rules) | Pravidla CLS platí pouze pro ty části typu, které jsou přístupné nebo viditelné mimo definující sestavu. | 1
Obecné | [Pravidla dodržování předpisů CLS](#cls-compliance-rules) | Členové typů, které nejsou kompatibilní se standardem CLS, nesmějí být označeni jako kompatibilní se standardem CLS. | 2
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Vnořené typy musí mít alespoň tolik obecných parametrů jako ohraničující typ. Obecné parametry v nosného typu odpovídají podle pozice obecným parametrům v jeho ohraničujícím typu.  | 42
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Název obecného typu musí kódovat počet parametrů typu deklarovaných na nevnořeném typu nebo nově zaváděných do typu, pokud je vnořen, podle výše definovaných pravidel. | 43
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že všechna omezení základního typu nebo rozhraní budou splněna omezeními obecného typu. | 44
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Typy používané jako omezení obecných parametrů musí být samy o sobě kompatibilní se standardem CLS. | 45
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Viditelnost a přístupnost členů (včetně vnořených typů) v instanovaném obecném typu se považuje spíše za vymezenou podle konkrétní instance než za obecné prohlášení typu jako celek. Za tímto podmínek stále platí pravidla viditelnosti a usnadnění pravidla CLS 12. | 46
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Pro každou abstraktní nebo virtuální obecnou metodu musí být k dispozici výchozí konkrétní (neabstraktní) implementace | 47
Rozhraní | [Rozhraní](#interfaces) | Rozhraní kompatibilní s cls nesmějí k jejich provádění vyžadovat definici metod, které nejsou kompatibilní se standardem CLS. | 18
Rozhraní | [Rozhraní](#interfaces) | Rozhraní kompatibilní s CLS nesmějí definovat statické metody ani pole. | 19
Členové | [Typ členů obecně](#type-members-in-general) | Globální statická pole a metody nejsou kompatibilní se standardem CLS. | 36
Členové | -- | Hodnota literálu statické je určena pomocí metadat inicializace pole. Literál kompatibilní se standardem CLS musí mít hodnotu zadanou v metadatech inicializace pole, která je přesně `enum`stejného typu jako literál (nebo základního typu, pokud je tento literál ). | 13
Členové | [Typ členů obecně](#type-members-in-general) | Omezení vararg není součástí cls a pouze konvence volání podporované CLS je standardní spravované volání konvence. | 15
Zásady vytváření názvů | [Zásady vytváření názvů](#naming-conventions) | Sestavy se řídí přílohou 7 technické zprávy 15 standardu Unicode Standard3.0, kterými se řídí soubor znaků povolených pro spuštění a zahrnutí do identifikátorů, které jsou k dispozici online na [formulářích normalizace Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identifikátory musí být v kanonickém formátu definovaném normalizačním formulářem C kódování Unicode. Pro účely cls dva identifikátory jsou stejné, pokud jejich mapování malých písmen (jak je určeno unicode národní ho necitlivý, 1-1 malá písmena mapování) jsou stejné. To znamená, že pro dva identifikátory, které mají být považovány za odlišné podle CLS, které se liší ve více než jen jejich případě. Však za účelem přepsání zděděné definice CLI vyžaduje přesné kódování původní deklarace použít. | 4
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Všechny názvy zavedené v oblasti souladu se standardem CLS musí být odlišné nezávislé svého druhu, s výjimkou případů, kdy jsou názvy totožné a jsou vyřešeny přetížením. To znamená, že zatímco CTS umožňuje jeden typ použít stejný název pro metodu a pole, CLS není. | 5
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Pole a vnořené typy se odlišují pouze porovnáním identifikátorů, i když CTS umožňuje rozlišit odlišné podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů), se musí lišit o více než jen návratový typ, s výjimkou případů uvedených v pravidle CLS 39 | 6
Přetížení | [Přetížení](#overloads) | Pouze vlastnosti a metody mohou být přetíženy. | 37
Přetížení | [Přetížení](#overloads) |Vlastnosti a metody mohou být přetíženy pouze na základě počtu a `op_Implicit` typů `op_Explicit`jejich parametrů, s výjimkou operátorů převodu s názvem a , které mohou být také přetíženy na základě jejich návratového typu. | 38
Přetížení | -- | Mají-li dvě nebo více metod kompatibilních se standardem CLS deklarované v typu stejný název a pro určitou sadu instancí typu mají stejný parametr a návratové typy, musí být všechny tyto metody sémanticky rovnocenné při těchto instancích typu. | 48
Vlastnosti | [Vlastnosti](#properties) | Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech. | 24
Vlastnosti | [Vlastnosti](#properties) | Všechny přistupující objekty vlastnosti musí být statické, všechny virtuální nebo všechny instance. | 26
Vlastnosti | [Vlastnosti](#properties) | Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro getter a typy všech, kromě konečného parametru setteru. Všechny tyto typy musí být kompatibilní se standardem CLS a nesmí být spravovány ukazatele (to znamená, nesmí být předány odkazem). | 27
Vlastnosti | [Vlastnosti](#properties) | Vlastnosti musí splňovat konkrétní vzor pojmenování. Atribut `SpecialName` uvedený v pravidle CLS 24 se při porovnávání názvů ignoruje a musí dodržovat pravidla identifikátorů. Vlastnost musí mít getter metoda, setter metoda nebo obojí. | 28
Převod typů | [Převod typů](#type-conversion) | Je-li k dispozici op_Implicit nebo op_Explicit, musí být poskytnuty alternativní prostředky pro zajištění nátlaku. | 39
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | Typy hodnot v rámečku nejsou kompatibilní se standardem CLS. | 3
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | Všechny typy uvedené v podpisu musí být kompatibilní se standardem CLS. Všechny typy, které tvoří typ typu instanovaného obecného typu, musí být kompatibilní se standardem CLS. | 11
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | Zadané odkazy nejsou kompatibilní se standardem CLS. | 14
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | Nespravované typy ukazatelů nejsou kompatibilní se standardem CLS. | 17
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | Třídy, typy hodnot a rozhraní kompatibilní se standardem CLS nevyžadují implementaci členů, kteří nejsou kompatibilní se standardem CLS. | 20
Typy | [Typy a podpisy členů typu](#types-and-type-member-signatures) | [System.Object](xref:System.Object) je kompatibilní se systémem CLS. Všechny ostatní třídy kompatibilní se standardem CLS dědí z třídy kompatibilní se standardem CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy a podpisy členů typu

Typ [System.Object](xref:System.Object) je kompatibilní se systémem CLS a je základním typem všech typů objektů v systému typu rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je [String](xref:System.String) implicitní (například třída `Object` String implicitně dědí z třídy) nebo explicitní (například třída [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) explicitně dědí z třídy [ArgumentException,](xref:System.ArgumentException) která explicitně dědí z třídy [Exception.](xref:System.Exception) Aby byl odvozený typ kompatibilní se standardem CLS, musí být jeho základní typ také kompatibilní se standardem CLS.

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se standardem CLS. Definuje základní `Counter` třídu, která používá nepodepsané 32bitové celé číslo jako čítač. Vzhledem k tomu, že třída poskytuje funkci čítače zabalením nepodepsaného celého čísla, je třída označena jako nekompatibilní se souborem CLS. V důsledku toho odvozené `NonZeroCounter`třídy , také není kompatibilní se seznamem CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se standardem CLS. Kromě toho pro obecné typy:

* Všechny typy, které tvoří instanci obecný typ musí být kompatibilní se standardem CLS.

* Všechny typy používané jako omezení obecných parametrů musí být kompatibilní se standardem CLS.

[Systém běžného typu](common-type-system.md) .NET obsahuje řadu předdefinovaných typů, které jsou podporovány přímo modulem COMMON Language runtime a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se standardem CLS.

Typ kompatibilní se standardem CLS | Popis
------------------ | -----------
[Byte](xref:System.Byte) | Osmibitové celé číslo bez znaménka
[Int16](xref:System.Int16) | 16bitové podepsané celé číslo
[Int32](xref:System.Int32) | 32bitové podepsané celé číslo
[Int64](xref:System.Int64) | 64bitové podepsané celé číslo
[Single](xref:System.Single) | Hodnota s plovoucí desetinnou desetinnou s jednou přesností
[Dvojité](xref:System.Double) | Hodnota s dvojitou přesností s plovoucí desetinnou desetinnou desetinnou hodnotou
[Logická hodnota](xref:System.Boolean) | typ hodnoty true nebo false
[Char](xref:System.Char) | Jednotka kódovaného kódu UTF-16
[Desetinných](xref:System.Decimal) | Desítkové číslo bez plovoucí desetinné čárky
[Intptr](xref:System.IntPtr) | Ukazatel nebo úchyt definované platformou
[Řetězec](xref:System.String) | Kolekce objektů s nulou, jedním nebo více char

Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se standardem CLS.

Nevyhovující typ | Popis | Alternativa odpovídající specifikaci CLS
------------------ | ----------- | -------------------------
[Sbyte](xref:System.SByte) | Osmibitový podepsaný celočíselný datový typ | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16bitové celé celé číslo bez znaménka | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32bitové celé celé číslo bez znaménka | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64bitové celé celé číslo bez znaménka | [Int64](xref:System.Int64) (může přetečení), [BigInteger](xref:System.Numerics.BigInteger), nebo [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Nepodepsaný ukazatel nebo popisovač | [Intptr](xref:System.IntPtr)

Knihovna tříd rozhraní .NET Framework nebo jakákoli jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se standardem CLS. například:

* Typy hodnot v rámečku. Následující příklad jazyka C# vytvoří třídu, `int`která `Value`má veřejnou vlastnost typu * s názvem . Vzhledem `int`k tomu, že * je zabalený typ hodnoty, kompilátor jej označí jako nekompatibilní se souborem CLS.

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* Zadané odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ.

Pokud typ není kompatibilní se souborem CLS, měli byste použít atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) s parametrem *isCompliant* s jeho hodnotou. `false` Další informace naleznete v části [atributu CLSCompliantAttribute.](#the-clscompliantattribute-attribute)

Následující příklad ilustruje problém dodržování cls v podpisu metody a v obecném typu instanování. Definuje třídu `InvoiceItem` s vlastností typu [UInt32](xref:System.UInt32), vlastnost typu [Nullable(Of UInt32)](xref:System.Nullable%601)a konstruktor `UInt32` `Nullable(Of UInt32)`s parametry typu a . Při pokusu o kompilaci v tomto příkladu se zobrazí čtyři upozornění kompilátoru.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

Chcete-li odstranit upozornění kompilátoru, nahraďte `InvoiceItem` typy, které nejsou kompatibilní se standardem CLS ve veřejném rozhraní, kompatibilními typy:

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

Kromě konkrétních uvedených typů nejsou některé kategorie typů kompatibilní se standardem CLS. Patří mezi ně nespravované typy ukazatelů a typy ukazatelů funkce. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo k vytvoření pole celá čísla.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

Pro abstraktní třídy kompatibilní se seznamem `abstract` CLS (to znamená třídy označené jako v c#) musí být všichni členové třídy také kompatibilní se seznamem CLS.

### <a name="naming-conventions"></a>Zásady vytváření názvů

Vzhledem k tomu, že některé programovací jazyky nerozlišují malá a velká písmena, identifikátory (například názvy oborů názvů, typů a členů) se musí lišit o více než malá a velká písmena. Dva identifikátory jsou považovány za rovnocenné, pokud jejich mapování s nižšími písmeny jsou stejné. Následující příklad jazyka C# definuje `Person` dvě `person`veřejné třídy a . Vzhledem k tomu, že se liší pouze podle případu, kompilátor Jazyka C# je označí jako nekompatibilní se seznamem CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

Identifikátory programovacích jazyků, jako jsou názvy jmenných prostorů, typů a členů, musí odpovídat [normě Unicode 3.0, Technické zprávě 15, příloha 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

* Prvním znakem identifikátoru může být libovolné velké písmeno Unicode, malé písmeno, písmeno nadpisu, modifikační písmeno, jiné písmeno nebo písmeno. Informace o kategoriích znaků Unicode naleznete ve výčtu [System.Globalization.UnicodeCategory.](xref:System.Globalization.UnicodeCategory)

* Následující znaky mohou být z libovolné z kategorií jako první znak a mohou také obsahovat značky bez mezer, mezery kombinující značky, desetinná čísla, interpunkce spojnice a formátovací kódy.

Před porovnáním identifikátorů byste měli odfiltrovat formátovací kódy a převést identifikátory na formulář C normalizace kódování Unicode, protože jeden znak může být reprezentován více jednotkami kódu kódovaných UTF-16. Posloupnosti znaků, které vytvářejí stejné jednotky kódu ve formuláři C normalizace kódování Unicode, nejsou kompatibilní se seznamem CLS. Následující příklad definuje vlastnost `Å`s názvem , která se skládá z znaku ANGSTROM sign (U + 212B) a druhá vlastnost s názvem, `Å` která se skládá ze znaku latinka velké písmeno a s kroužkem nad (U + 00C5). Kompilátor Jazyka C# označí zdrojový kód jako nekompatibilní se souborem CLS.

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou vyřešeny přetížením. Tento požadavek je přísnější než u běžného systému typů, který umožňuje více členů v rámci oboru mít stejné názvy, pokud se jedná o různé druhy členů (například jeden je metoda a jeden je pole). Zejména pro členy typu:

* Pole a vnořené typy se rozlišují podle názvu samotného.

* Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouze návratový typ.

Následující příklad ilustruje požadavek, že názvy členů musí být jedinečné v rámci jejich oboru. Definuje třídu s `Converter` názvem, která `Conversion`zahrnuje čtyři členy s názvem . Tři jsou metody a jedna je vlastnost. Metoda, která `Int64` obsahuje parametr, je jednoznačně pojmenována, `Int32` ale dvě metody s parametrem nejsou, protože vrácená hodnota není považována za součást podpisu člena. Vlastnost `Conversion` také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na běžný jazyk runtime, musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v jazyce C# a jazyka Visual Basic. Následující příklad jazyka však je schopen rozptýlit třídu `case` pojmenovanou z klíčového `case` slova pomocí počáteční a uzavírací závorky. V opačném případě by v příkladu vytvořit chybovou zprávu , "Klíčové slovo není platný jako identifikátor" a nepodaří zkompilovat.

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

Následující příklad jazyka C# je schopen `case` vytvořit instanci třídy pomocí symbolu @ k rozdvojení identifikátoru z klíčového slova jazyka. Bez něj by kompilátor Jazyka C# zobrazil dvě chybové zprávy"Type expected" a "Invalid expression term 'case'."

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a>Převod typů

Specifikace společného jazyka definuje dva operátory převodu:

* `op_Implicit`, který se používá pro rozšíření převody, které nevedou ke ztrátě dat nebo přesnosti. Například [desítkové](xref:System.Decimal) struktury obsahuje přetížené `op_Implicit` operátor převést hodnoty integrální typy a [Char](xref:System.Char) hodnoty. `Decimal`

* `op_Explicit`, který se používá pro zúžení převody, které mohou mít za následek ztrátu velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. `Decimal` Struktura například obsahuje přetížený `op_Explicit` operátor převést [Double](xref:System.Double) `Decimal` a Single `Decimal` hodnoty a `Double`převést hodnoty na integrální hodnoty , `Single`, a `Char`. [Single](xref:System.Single)

Však ne všechny jazyky podporují přetížení operátoru nebo definice vlastní operátory. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob provedení převodu. Doporučujeme zadat `From`xxx `To`a xxx metody.

Následující příklad definuje implicitní a explicitní převody kompatibilní se standardem CLS. Vytvoří třídu, `UDouble` která představuje podepsané číslo s dvojitou přesností s plovoucí desetinnou desetinnou hlavou. Poskytuje implicitní převody `UDouble` `Double` z a pro `UDouble` explicitní `Single` `Double` převody `Single` z `UDouble`, do `UDouble`, a na . Definuje také `ToDouble` metodu jako alternativu k implicitnímu operátoru převodu a metodě `ToSingle`, `FromDouble`a `FromSingle` metody jako alternativy k operátorům explicitního převodu.

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a>Pole

Pole kompatibilní se standardem CLS splňují následující pravidla:

* Všechny dimenze pole musí mít dolní mez nula. Následující příklad vytvoří pole, které není kompatibilní se standardem CLS, s dolní mez jednoho. Všimněte si, že i přes přítomnost [clscompliantattribute](xref:System.CLSCompliantAttribute) atribut kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metodou není kompatibilní se seznamem CLS.

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* Všechny prvky pole se musí skládat z typů kompatibilních se standardem CLS. Následující příklad definuje dvě metody, které vracejí pole, která nejsou kompatibilní se standardem CLS. První vrátí pole [hodnot UInt32.](xref:System.UInt32) Druhý vrátí [object](xref:System.Object) pole, které obsahuje `UInt32` [Int32](xref:System.Int32) a hodnoty. Přestože kompilátor identifikuje první pole jako nekompatibilní z důvodu jeho `UInt32` typu, nedokáže rozpoznat, že druhé pole obsahuje prvky, které nejsou kompatibilní se standardem CLS.

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* Řešení přetížení pro metody, které mají parametry pole je založena na skutečnosti, že jsou pole a na jejich typu prvku. Z tohoto důvodu je následující definice `GetSquares` přetížené metody kompatibilní se standardem CLS.

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a>Rozhraní

Rozhraní kompatibilní se standardem CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace). Rozhraní kompatibilní se standardem CLS nemůže obsahovat některou z následujících možností:

* Statické metody nebo statická pole. Kompilátor Jazyka C# generuje chyby kompilátoru, pokud definujete statický člen v rozhraní.

* Pole. C# kompilátor generuje chyby kompilátoru, pokud definujete pole v rozhraní.

* Metody, které nejsou kompatibilní se standardem CLS. Například následující definice rozhraní obsahuje `INumber.GetUnsigned`metodu , která je označena jako nekompatibilní se souborem CLS. Tento příklad generuje upozornění kompilátoru.

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  Z důvodu tohoto pravidla nejsou typy kompatibilní se standardem CLS nutné implementovat členy, které nejsou kompatibilní se standardem CLS. Pokud rozhraní kompatibilní se standardem CLS zveřejňuje třídu, která implementuje rozhraní kompatibilní se standardem CLS, měla by také poskytovat konkrétní implementace všech členů, které nejsou kompatibilní se standardem CLS.

Kompilátory jazyka kompatibilní se seznamem CLS musí také umožnit třídě poskytovat samostatné implementace členů, které mají stejný název a podpis ve více rozhraních. C# podporuje explicitní implementace rozhraní poskytovat různé implementace identicky pojmenované metody. Následující příklad ilustruje tento scénář definováním `Temperature` třídy, `ICelsius` `IFahrenheit` která implementuje rozhraní a jako explicitní implementace rozhraní.

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a>Výčty

Výčty kompatibilní se standardem CLS se musí řídit těmito pravidly:

* Základní typ výčtu musí být vnitřní cls kompatibilní celé číslo ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)nebo [Int64](xref:System.Int64)). Například následující kód se pokusí definovat výčtu, jehož základní typ je [UInt32](xref:System.UInt32) a generuje upozornění kompilátoru.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* Typ výčtu musí mít jedno `Value__` pole instance s `FieldAttributes.RTSpecialName` názvem atributem. To umožňuje implicitně odkazovat na hodnotu pole.

* Výčet zahrnuje literálová statická pole, jejichž typy odpovídají typu samotného výčtu. Například pokud definujete `State` výčet s `State.On` hodnotami `State.On` `State.Off` a `State.Off`, a jsou oba `State`literál statická pole, jejichž typ je .

* Existují dva druhy výčtů:

  * Výčet, který představuje sadu vzájemně se vylučujících, pojmenovaných celé hodnoty. Tento typ výčtu je označen absencí vlastního atributu [System.FlagsAttribute.](xref:System.FlagsAttribute)

  * Výčet, který představuje sadu bitových příznaků, které lze kombinovat generovat nepojmenovanou hodnotu. Tento typ výčtu je označen přítomností vlastního atributu [System.FlagsAttribute.](xref:System.FlagsAttribute)

Další informace naleznete v dokumentaci ke struktuře [výčtu.](xref:System.Enum)

* Hodnota výčtu není omezena na rozsah jeho zadané hodnoty. Jinými slovy rozsah hodnot ve výčtu je rozsah jeho základní hodnotu. Metodu `Enum.IsDefined` můžete použít k určení, zda je zadaná hodnota členem výčtu.

### <a name="type-members-in-general"></a>Typ členů obecně

Specifikace společného jazyka vyžaduje, aby všechna pole a metody byly přístupné jako členové určité třídy. Globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány na rozdíl od typu) proto nejsou kompatibilní se standardem CLS. Pokud se pokusíte zahrnout globální pole nebo metodu do zdrojového kódu, kompilátor Jazyka C# vygeneruje chybu kompilátoru.

Specifikace společného jazyka podporuje pouze standardní konvence spravovaných volání. Nepodporuje nespravované konvence volání a metody s proměnnými `varargs` argumenty označenými klíčovým slovem. Pro seznamy proměnných argumentů, které jsou kompatibilní se standardní konvencí spravovaných `params` volání, použijte atribut `ParamArray` [ParamArrayAttribute](xref:System.ParamArrayAttribute) nebo implementaci jednotlivého jazyka, například klíčové slovo v jazyce C# a klíčové slovo v jazyce Visual Basic.

### <a name="member-accessibility"></a>Přístupnost členů

Přepsání zděděného člena nemůže změnit přístupnost tohoto člena. Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě. Existuje jedna výjimka: a `protected internal` (v `Protected Friend` jazyce C#) nebo (v jazyce Visual Basic) člen v jednom sestavení, který je přepsán typem v jiném sestavení.  V takovém případě je `Protected`přístupnost přepsání .

Následující příklad ilustruje chybu, která je generována při [clsCompliantAttribute](xref:System.CLSCompliantAttribute) atribut je nastaven `true`na , a `Person`, což je třída odvozená z `Animal`, pokusí se změnit usnadnění `Species` přístupu vlastnosti z veřejné na soukromé. Příklad se úspěšně zkompiluje, pokud je jeho usnadnění přístupu změněno na veřejné.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

Typy v podpisu člena musí být přístupné vždy, když je tento člen přístupný. Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je soukromý, chráněný nebo interní. Následující příklad ilustruje chybu kompilátoru, `StringWrapper` která je výsledkem, když konstruktor třídy zpřístupní hodnotu vnitřního `StringOperationType` výčtu, která určuje, jak by měla být zabalena hodnota řetězce.

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a>Obecné typy a členy

Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich ohraničující typ. Ty odpovídají podle pozice obecných parametrů v ohraničujícím typu. Obecný typ může také obsahovat nové obecné parametry.

Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořených typů může být skryt syntaxí jednotlivých jazyků. V následujícím příkladu obecný `Outer<T>` typ obsahuje dvě `Inner1A` `Inner1B<U>`vnořené třídy a . Volání `ToString` metody, ze které každá třída `Object.ToString`dědí , ukazují, že každá vnořená třída obsahuje parametry typu její obsahující třídy.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

Obecné názvy typů jsou kódovány v *názvu*formuláře*n*, *`* kde *název* je název typu, je literál znaku a *n* je počet parametrů deklarovaných na typu nebo, pro vnořené obecné typy, počet nově zavedených parametrů typu. Toto kódování obecných názvů typů je primárně zajímavé pro vývojáře, kteří používají reflexe pro přístup k obecným typům stížností CLS v knihovně.

Pokud jsou použita omezení pro obecný typ, všechny typy používané jako omezení musí být také kompatibilní se standardem CLS. Následující příklad definuje třídu `BaseClass` s názvem, která není kompatibilní `BaseCollection` se standardem CLS, a obecnou třídu s názvem, jejíž parametr typu musí být odvozen z `BaseClass`. Ale `BaseClass` protože není kompatibilní se standardem CLS, kompilátor vydává upozornění.

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

Pokud obecný typ je odvozen od obecného základního typu, musí znovu deklarovat všechna omezení tak, aby může zaručit, že omezení na základní typ jsou také splněny. Následující příklad definuje, `Number<T>` který může představovat libovolný číselný typ. Také definuje třídu, `FloatingPoint<T>` která představuje hodnotu s plovoucí desetinnou tácek. Zdrojový kód se však nepodaří zkompilovat, `Number<T>` protože nepoužije omezení (že `FloatingPoint<T>`T musí být typ hodnoty) na .

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

Příklad se úspěšně zkompiluje, `FloatingPoint<T>` pokud je omezení přidáno do třídy.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

Specifikace společného jazyka ukládá konzervativní model instance pro vnořené typy a chráněné členy. Otevřené obecné typy nemohou vystavit pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného chráněného obecného typu. Neobecné typy, které rozšiřují konkrétní konkretizovat obecnou základní třídu nebo rozhraní, nemohou vystavit pole nebo členy s podpisy, které obsahují jinou instanci vnořeného chráněného obecného typu.

Následující příklad definuje obecný typ `C1<T>`a chráněnou `C1<T>.N`třídu . `C1<T>`má dvě `M1` metody `M2`a . Však `M1` není kompatibilní se standardem CLS, protože se pokusí vrátit `C1<int>.N` objekt z `C1<T>`. Druhá třída `C2`, je odvozena od `C1<long>`. Má dvě metody `M3` `M4`a . `M3`není kompatibilní se sítí CLS, `C1<int>.N` protože se pokusí `C1<long>`vrátit objekt z podtřídy rozhraní . Všimněte si, že kompilátory jazyka může být ještě více omezující. V tomto příkladu visual basic zobrazí chybu `M4`při pokusu o kompilaci .

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a>Konstruktory

Konstruktory ve třídách a strukturách kompatibilních se standardem CLS se musí řídit těmito pravidly:

* Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy předtím, než přistupuje k datům zděděné instance. Tento požadavek je způsoben skutečností, že konstruktory základní třídy nejsou zděděny jejich odvozené třídy. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.

  Kompilátory obvykle vynucují toto pravidlo nezávisle na dodržování předpisů cls, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je `Person` odvozena z `Doctor` třídy, `Person` ale třída se nezdaří volat konstruktor třídy inicializovat zděděná pole instance.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* Konstruktor objektu nelze volat s výjimkou vytvoření objektu. Kromě toho objekt nelze inicializovat dvakrát. Například to znamená, že `Object.MemberwiseClone` nesmí volat konstruktory.

### <a name="properties"></a>Vlastnosti

Vlastnosti v typech kompatibilních se standardem CLS se musí řídit těmito pravidly:

* Vlastnost musí mít setter, getter nebo obojí. V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí `get` \_jako samostatné metody (getter se `SpecialName` nazývá *propertyname* a setter je `set` \_ *propertyname*) označené jako v metadatech sestavení. Kompilátor Jazyka C# vynucuje toto pravidlo automaticky bez nutnosti <xref:System.CLSCompliantAttribute> použít atribut.

* Typ vlastnosti je návratový typ vlastnosti getter a poslední argument setter. Tyto typy musí být kompatibilní se standardem CLS a argumenty nelze přiřadit k vlastnosti odkazem (to znamená, že nemohou být spravovány ukazatele).

* Pokud vlastnost má getter a setter, musí být oba virtuální, statické nebo obě instance. Kompilátor Jazyka C# automaticky vynucuje toto pravidlo prostřednictvím syntaxe definice vlastnosti.

### <a name="events"></a>Události

Událost je definována svým názvem a typem. Typ události je delegát, který se používá k označení události. Například `DbConnection.StateChange` událost je typu `StateChangeEventHandler`. Kromě samotné události poskytují implementaci události tři metody s názvy založenými na `SpecialName` názvu události a jsou označeny jako v metadatech sestavení:

* Metoda pro přidání obslužné rutiny události s názvem `add`_*EventName*. Například metoda odběru události `DbConnection.StateChange` pro událost `add_StateChange`je pojmenována .

* Metoda odebrání obslužné `remove`rutiny události s názvem _*EventName*. Například metoda odebrání pro `DbConnection.StateChange` událost `remove_StateChange`je pojmenována .

* Metoda označující, že došlo k `raise` \_události s názvem *EventName*.

> [!NOTE]
> Většina pravidel společné jazykové specifikace týkající se událostí je implementována kompilátory jazyka a je transparentní pro vývojáře komponent.

Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost. Musí být také všechny statické, instance nebo virtuální. Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události. Metody add a remove musí být přítomny nebo obě chybí.

Následující příklad definuje třídu kompatibilní se `Temperature` seznamem `TemperatureChanged` CLS s názvem, která vyvolá událost, pokud se změna teploty mezi dvěma hodnotami rovná nebo překročí prahovou hodnotu. Třída `Temperature` explicitně definuje `raise_TemperatureChanged` metodu tak, aby mohla selektivně spouštět obslužné rutiny událostí.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a>Přetížení

Specifikace společného jazyka ukládá přetíženým členům následující požadavky:

* Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru. Volání konvence, návratový typ, vlastní modifikátory použité na metodu nebo její parametr a zda parametry jsou předány hodnotou nebo odkazem nejsou považovány při rozlišování mezi přetížení. Příklad naleznete v kódu požadavku, že názvy musí být jedinečné v rámci oboru v části [Konvence pojmenování.](#naming-conventions)

* Pouze vlastnosti a metody mohou být přetíženy. Pole a události nemohou být přetíženy.

* Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.

> [!NOTE]
> A `op_Explicit` `op_Implicit` operátory jsou výjimky z pravidla, že vrácená hodnota není považována za součást podpisu metody pro řešení přetížení. Tyto dva operátory mohou být přetíženy na základě jejich parametry a jejich vrácená hodnota.

### <a name="exceptions"></a>Výjimky

Objekty výjimek musí být odvozeny z `System.Exception` [system.exception](xref:System.Exception) nebo z jiného typu odvozeného z . Následující příklad ilustruje chybu kompilátoru, která `ErrorClass` se vynaložit při vlastní třídy s názvem se používá pro zpracování výjimek.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

Chcete-li opravit `ErrorClass` tuto chybu, `System.Exception`třída musí dědit z . Kromě toho Message vlastnost musí být přepsána. Následující příklad opravuje tyto chyby definovat třídu, `ErrorClass` která je kompatibilní se standardem CLS.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a>Atributy

In.NET framework sestavení, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody. Vlastní atributy musí být odvozeny z [System.Attribute](xref:System.Attribute) nebo z typu odvozeného z . `System.Attribute`

Následující příklad porušuje toto pravidlo. Definuje třídu, `NumericAttribute` která není `System.Attribute`odvozena z . Všimněte si, že chyba kompilátoru výsledky pouze v případě, že je použit atribut nekompatibilní se standardem CLS, nikoli při definování třídy.

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

Konstruktor nebo vlastnosti atributu kompatibilního se standardem CLS mohou vystavit pouze následující typy:

* [Logická hodnota](xref:System.Boolean)

* [Byte](xref:System.Byte)

* [Char](xref:System.Char)

* [Dvojité](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Single](xref:System.Single)

* [Řetězec](xref:System.String)

* [Typ](xref:System.Type)

* Libovolný typ výčtu, `Byte`jehož `Int32`základní `Int64`typ je , `Int16`, , nebo .

Následující příklad definuje `DescriptionAttribute` třídu, která je odvozena z [Atribut](xref:System.Attribute). Konstruktor třídy má parametr `Descriptor`typu , takže třída není kompatibilní se seznamem CLS. Všimněte si, že kompilátor Jazyka C# vydává upozornění, ale úspěšně se zkompiluje.

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a>Atribut CLSCompliantAttribute

Atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) se používá k označení, zda prvek programu splňuje specifikaci společného jazyka. Konstruktor `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` obsahuje jeden povinný parametr *isCompliant*, který označuje, zda je prvek programu kompatibilní se standardem CLS.

V době kompilace kompilátor zjistí nekompatibilní prvky, které jsou považovány za kompatibilní se standardem CLS a vydává upozornění. Kompilátor nevydává upozornění pro typy nebo členy, které jsou explicitně deklarovány jako nekompatibilní.

Vývojáři komponent `CLSCompliantAttribute` mohou atribut použít dvěma způsoby:

* Chcete-li definovat části veřejného rozhraní vystavené komponenty, které jsou kompatibilní se seznamem CLS a součásti, které nejsou kompatibilní se standardem CLS. Pokud se atribut používá k označení určitých prvků programu jako kompatibilní se standardem CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na rozhraní .NET Framework.

* Chcete-li zajistit, že veřejné rozhraní knihovny komponent zpřístupňuje pouze prvky programu, které jsou kompatibilní se standardem CLS. Pokud prvky nejsou kompatibilní se seznamem CLS, kompilátory obecně vydá upozornění.

> [!WARNING]
> V některých případech kompilátory jazyka vynucovat cls kompatibilní pravidla bez ohledu na to, zda se používá `CLSCompliantAttribute` atribut. Například definování `*static` člena v rozhraní porušuje pravidlo CLS. Pokud však definujete `*static` člena v rozhraní, kompilátor Jazyka C# zobrazí chybovou zprávu a nepodaří se zkompilovat aplikaci.

Atribut `CLSCompliantAttribute` je označen atributem [AttributeUsageAttribute,](xref:System.AttributeUsageAttribute) který `AttributeTargets.All`má hodnotu . Tato hodnota umožňuje použít `CLSCompliantAttribute` atribut pro libovolný prvek programu, včetně sestavení, modulů, typů (třídy, struktury, výčty, rozhraní a delegáty), členů typu (konstruktory, metody, vlastnosti, pole a události), parametry, obecné parametry a vrácené hodnoty. V praxi byste však měli atribut použít pouze pro sestavení, typy a členy typu. V opačném případě kompilátory ignorovat atribut a nadále generovat upozornění kompilátoru vždy, když narazí na nekompatibilní parametr, obecný parametr nebo vrácenou hodnotu ve veřejné rozhraní knihovny.

Hodnota atributu `CLSCompliantAttribute` je zděděna obsaženými prvky programu. Například pokud je sestavení označeno jako kompatibilní se standardem CLS, jeho typy jsou také kompatibilní se standardem CLS. Pokud je typ označen jako kompatibilní se seznamem CLS, jeho vnořené typy a členy jsou také kompatibilní se standardem CLS.

Zděděnou dodržování předpisů můžete explicitně přepsat použitím atributu `CLSCompliantAttribute` na prvek obsaženého programu. Můžete například použít `CLSCompliantAttribute` atribut s hodnotou `false` *isCompliant* k definování nekompatibilního typu v kompatibilním sestavení a můžete `true` použít atribut s hodnotou *isCompliant* k definování kompatibilního typu v nekompatibilním sestavení. Můžete také definovat nekompatibilní členy v kompatibilním typu. Nekompatibilní typ však nemůže mít kompatibilní členy, takže nelze použít atribut `true` s hodnotou *isCompliant* k přepsání dědičnosti z nekompatibilního typu.

Při vývoji součástí byste měli vždy `CLSCompliantAttribute` použít atribut k označení, zda vaše sestavení, jeho typy a jeho členy jsou kompatibilní se seznamem CLS.

Vytvoření součástí kompatibilních se standardem CLS:

1. Použijte `CLSCompliantAttribute` k označení sestavení jako kompatibilní se standardem CLS.

2. Označte všechny veřejně exponované typy v sestavení, které nejsou kompatibilní se standardem CLS jako nekompatibilní.

3. Označte všechny veřejně exponované členy v typech kompatibilních se standardem CLS jako nekompatibilní.

4. Poskytněte alternativu kompatibilní se standardem CLS pro členy, kteří nejsou kompatibilní se standardem CLS.

Pokud jste úspěšně označili všechny nekompatibilní typy a členy, kompilátor by neměl vyzařovat žádná upozornění na nedodržování předpisů. Měli byste však určit, které členy nejsou kompatibilní se standardem CLS, a v dokumentaci k produktu uvést jejich alternativy kompatibilní se standardem CLS.

Následující příklad používá `CLSCompliantAttribute` atribut k definování sestavení kompatibilního se `CharacterUtilities`seznamem CLS a typu , který má dva členy, které nesplňují požadavky cls. Vzhledem k tomu, `CLSCompliant(false)` že oba členy jsou označeny atributem, kompilátor nevytváří žádná upozornění. Třída také poskytuje alternativu kompatibilní se standardem CLS pro obě metody. Obvykle bychom jen přidat dvě přetížení `ToUTF16` metody poskytnout alternativy kompatibilní se standardem CLS. Protože však metody nemohou být přetíženy na základě vrácené hodnoty, názvy metod kompatibilních se standardem CLS se liší od názvů nekompatibilních metod.

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

Pokud vyvíjíte aplikaci, nikoli knihovnu (to znamená, že nevystavujete typy nebo členy, které mohou využívat jiní vývojáři aplikací), dodržování předpisů CLS pro prvky programu, které vaše aplikace využívá, je zajímavé pouze v případě, že je váš jazyk nepodporuje . V takovém případě kompilátor jazyka vygeneruje chybu při pokusu o použití prvku, který není kompatibilní se standardem CLS.

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden význam zahrnuje bezproblémovou konzumaci typů napsaných v jednom jazyce z aplikace napsané v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód `StringUtil.vb`pro , který `ToTitleCase`zahrnuje jeden `StringLib` člen, , ve své třídě.

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů. Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:

```console
vbc /t:module StringUtil.vb
```

Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:

```console
csc /t:module NumberUtil.cs
```

Potom pomocí nástroje Link (Link.exe) zkompilujte dva moduly do sestavení:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`. Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:

```console
vbc example.vb /r:UtilityLib.dll
```

Chcete-li zkompilovat pomocí jazyka C#, změňte název kompilátoru z vbc na csc a změňte příponu souboru z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```
