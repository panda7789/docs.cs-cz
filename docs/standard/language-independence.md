---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: 'Přečtěte si, jak můžete vyvíjet v jednom z mnoha podporovaných jazyků v .NET, jako je C#, C++/CLI, F #, Ironpythonu, VB, Visual COBOL a PowerShell.'
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: f04ff902743c91147a6f056bca3292ee47952bbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420549"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

Rozhraní .NET je nezávislé na jazyce. To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na implementace technologie .NET, jako je C#, F # a Visual Basic. Můžete přistupovat k typům a členům knihoven tříd vyvinutým pro implementace v rozhraní .NET bez nutnosti znát jazyk, ve kterém byly původně zapsány, a aniž byste museli sledovat některé z původních konvencí jazyka. Pokud jste vývojář komponent, k vaší komponentě se dá dostat z aplikace .NET bez ohledu na její jazyk.

> [!NOTE]
> Tato první část tohoto článku popisuje vytváření komponent nezávislých na jazyce – to znamená komponenty, které mohou být spotřebovány aplikacemi, které jsou napsané v libovolném jazyce. Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného v několika jazycích. viz [interoperabilita mezi jazyky](#cross-language-interoperability) v druhé části tohoto článku.

Aby bylo možné plně spolupracovat s jinými objekty napsanými v libovolném jazyce, musí tyto objekty zveřejnit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která se vztahují na generovaná sestavení. Specifikace CLS (Common Language Specification) je definována v oddílu I klauzule 7 až 11 ze [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Pokud vaše komponenta odpovídá specifikaci CLS (Common Language Specification), je zaručena, že je kompatibilní se specifikací CLS a je možné k nim přicházet z kódu v sestaveních napsaných v jakémkoli programovacím jazyce, který podporuje specifikaci CLS. Můžete určit, zda vaše komponenta odpovídá specifikaci CLS (Common Language Specification) v době kompilace, a to použitím atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) pro váš zdrojový kód. Další informace najdete v [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute).

V tomto článku:

* [Pravidla dodržování předpisů CLS](#cls-compliance-rules)

  * [Typy a signatury členů typu](#types-and-type-member-signatures)

  * [Zásady vytváření názvů](#naming-conventions)

  * [Převod typů](#type-conversion)

  * [Pole](#arrays)

  * [Rozhraní](#interfaces)

  * [Výčty](#enumerations)

  * [Obecné typy členů](#type-members-in-general)

  * [Přístupnost člena](#member-accessibility)

  * [Obecné typy a členy](#generic-types-and-members)

  * [Konstruktory](#constructors)

  * [Vlastnosti](#properties)

  * [Události](#events)

  * [Přetížení](#overloads)

  * [Výjimky](#exceptions)

  * [Atributy](#attributes)

* [CLSCompliantAttribute – atribut](#the-clscompliantattribute-attribute)

* [Vzájemná funkční spolupráce mezi jazyky](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů CLS

Tato část popisuje pravidla pro vytvoření komponenty kompatibilní se specifikací CLS. Úplný seznam pravidel naleznete v oddílu I klauzule 11 ve [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specifikace CLS (Common Language Specification) se zabývá všemi pravidly dodržování specifikace CLS, protože se vztahuje na příjemce (vývojáři, kteří mají programově přístup k komponentě kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytváření knihoven kompatibilních se specifikací CLS) a zařízení (vývojáři, kteří vytvářejí nástroj, jako je kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty kompatibilní se specifikací CLS). Tento článek se zaměřuje na pravidla, která se vztahují na rozhraní. Všimněte si ale, že některá pravidla, která platí pro rozšířené, mohou platit také pro sestavení, která jsou vytvořena pomocí [reflexe. Emit](xref:System.Reflection.Emit).

Chcete-li navrhnout komponentu, která je nezávislá na jazyce, stačí použít pravidla pro dodržování specifikace CLS pro veřejné rozhraní vaší komponenty. Vaše soukromá implementace nemusí odpovídat specifikaci.

> [!IMPORTANT]
> Pravidla pro dodržování předpisů CLS platí pouze pro veřejné rozhraní komponenty, nikoli na jeho soukromou implementaci.

Například celá čísla bez znaménka jiná než [bajt](xref:System.Byte) nejsou kompatibilní se specifikací CLS. Vzhledem k tomu `Person` , že třída v následujícím příkladu zpřístupňuje `Age` vlastnost typu [UInt16](xref:System.UInt16), následující kód zobrazí upozornění kompilátoru.

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

Třídu person kompatibilní se specifikací CLS můžete nastavit tak, že změníte typ `Age` vlastnosti z `UInt16` na [Int16](xref:System.Int16), což je 16bitové podepsané celé číslo kompatibilní se specifikací CLS. Nemusíte měnit typ soukromého `personAge` pole.

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

* Definice veřejných členů veřejných tříd a definice členů přístupných k odvozeným třídám (tj. chráněným členům).

* Parametry a návratové typy veřejných tříd a parametry a návratové typy metod, které jsou přístupné pro odvozené třídy.

Pravidla pro dodržování specifikace CLS jsou uvedená v následující tabulce. Text pravidel se bere v platnost od [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 podle Ecma International. Podrobnější informace o těchto pravidlech najdete v následujících oddílech.

Kategorie | Seznamte se s  | Pravidlo | Číslo pravidla
-------- | --- | ---- | -----------
Přístupnost | [Přístupnost člena](#member-accessibility) | Při přepisu zděděných metod se přístupnost nemění, s výjimkou přepsání metody zděděné z jiného sestavení s přístupností `family-or-assembly` . V takovém případě má přepsání přístup `family` . | 10
Přístupnost | [Přístupnost člena](#member-accessibility) | Viditelnost a přístupnost typů a členů musí být takové, aby typy v signatuře kteréhokoli člena byly viditelné a přístupné, kdykoli je samotný člen viditelný a přístupný. Například veřejná metoda, která je viditelná vně sestavení, nesmí obsahovat argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typů tvořících instanci obecného typu používaného v podpisu každého člena musí být viditelná a přístupná, kdykoli je samotný člen viditelný a přístupný. Například instance obecného typu přítomná v signatuře člena, který je viditelný mimo jeho sestavení, nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení. | 12
Pole | [Pole](#arrays) | Pole musí mít prvky s typem odpovídajícím specifikaci CLS a všechny dimenze pole musí mít nižší meze nula. Pouze skutečnost, že položka je pole a typ elementu pole musí být požadován pro rozlišení mezi přetíženími. Pokud je přetížení založeno na dvou nebo více typech pole, musí být typy prvků pojmenované typy. | 16
Atributy | [Atributy](#attributes) | Atributy musí být typu [System. Attribute](xref:System.Attribute)nebo typu, který z něj dědí. | 41
Atributy | [Atributy](#attributes) | Specifikace CLS umožňuje pouze podmnožinu kódování pro vlastní atributy. Jediné typy, které se zobrazí v těchto kódováních, jsou (viz oddíl IV) [: System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), System. [Byte](xref:System.Byte), System. [Int16](xref:System.Int16), System [. Int32](xref:System.Int32), System [. Int64](xref:System.Int64), System. [Single](xref:System.Single), [System. Double](xref:System.Double)a jakýkoli typ výčtu založený na typu základního typu Integer kompatibilní se specifikací CLS. | 34
Atributy | [Atributy](#attributes) | Specifikace CLS neumožňuje veřejně viditelné požadované modifikátory ( `modreq` , viz oddíl II), ale umožňuje volitelné modifikátory ( `modopt` , viz oddíl II), které nerozumí. | 35
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu musí volat konstruktor instance své základní třídy před jakýmkoli přístupem k zděděným datům instance. (To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)  | 21
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu se nesmí volat kromě v rámci vytváření objektu a objekt se nemůže inicializovat dvakrát. | 22
Výčty | [Výčty](#enumerations) | Nadřazený typ výčtu musí být vestavěný celočíselný typ CLS, název pole musí být "value__" a toto pole musí být označeno `RTSpecialName` . |  7
Výčty | [Výčty](#enumerations) | Existují dva různé druhy výčtů, které jsou označeny přítomností nebo nepřítomností [System. FlagsAttribute](xref:System.FlagsAttribute) (viz oddíl IV Library) vlastní atribut. Jedna představuje pojmenované celočíselné hodnoty; druhý představuje pojmenované bitové příznaky, které lze kombinovat pro vygenerování nepojmenované hodnoty. Hodnota `enum` není omezena na zadané hodnoty. |  8
Výčty | [Výčty](#enumerations) | Literální statická pole výčtového typu musí mít typ samotného výčtu. |  9
Události | [Události](#events) | Metody, které implementují událost, musí být označené `SpecialName` v metadatech. |29
Události | [Události](#events) | Přístupnost události a jejích přistupujících objektů se musí shodovat. |30
Události | [Události](#events) | `add`Metody a `remove` pro událost musí být buď přítomny, nebo chybět. |31
Události | [Události](#events) | `add`Metody a `remove` pro událost musí mít jeden parametr, jehož typ Určuje typ události a který musí být odvozen od typu [System. Delegate](xref:System.Delegate). |32
Události | [Události](#events) | Události musí dodržovat konkrétní vzor pojmenování. Atribut Special, na který se odkazuje v pravidle CLS 29, se ignoruje v odpovídajících porovnáních názvů a musí dodržovat pravidla identifikátoru.  |33
Výjimky | [Výjimky](#exceptions) | Objekty, které jsou vyvolány, musí být typu [System. Exception](xref:System.Exception) nebo typu, který z něj dědí. Nicméně metody kompatibilní se specifikací CLS nejsou požadovány pro blokování šíření jiných typů výjimek. | 40
Obecné | [Pravidla dodržování předpisů CLS](#cls-compliance-rules) | Pravidla CLS se vztahují pouze na ty části typu, které jsou přístupné nebo viditelné mimo definiční sestavení. | 1
Obecné | [Pravidla dodržování předpisů CLS](#cls-compliance-rules) | Členy typů, které nejsou kompatibilní se specifikací CLS, nesmí být označeny jako kompatibilní se specifikací CLS. | 2
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Vnořené typy musí mít alespoň tolik obecných parametrů jako nadřazený typ. Obecné parametry ve vnořeném typu odpovídají umístění obecným parametrům v nadřazeném typu.  | 42
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Název obecného typu musí kódovat počet parametrů typu deklarovaných pro nevnořený typ, nebo nově zavedený na typ, pokud je vnořený, podle pravidel definovaných výše. | 43
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že jakákoli omezení základního typu nebo rozhraní budou splněna omezeními obecného typu. | 44
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Typy, které se používají jako omezení u obecných parametrů, samy o nich vyhovují specifikaci CLS. | 45
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Viditelnost a přístupnost členů (včetně vnořených typů) v instanci generického typu se považují za obor pro konkrétní instanci, nikoli jako deklaraci obecného typu jako celku. Za předpokladu, že pravidla viditelnosti a přístupnosti pravidla CLS 12 budou nadále platit. | 46
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Pro každou abstraktní nebo virtuální obecnou metodu musí být použita výchozí konkrétní (neabstraktní) implementace. | 47
Rozhraní | [Rozhraní](#interfaces) | Rozhraní kompatibilní se specifikací CLS nesmí vyžadovat definici metod nekompatibilních se specifikací CLS, aby je bylo možné implementovat. | 18
Rozhraní | [Rozhraní](#interfaces) | Rozhraní kompatibilní se specifikací CLS nesmějí definovat statické metody ani definovat pole. | 19
Členové | [Obecné typy členů](#type-members-in-general) | Globální statická pole a metody nejsou kompatibilní se specifikací CLS. | 36
Členové | -- | Hodnota statického literálu je určena pomocí inicializačních metadat pole. Literál kompatibilní se specifikací CLS musí mít hodnotu zadanou v metadatech inicializace pole, která jsou přesně stejného typu jako literál (nebo základního typu, pokud je tento literál typu `enum` ). | 13
Členové | [Obecné typy členů](#type-members-in-general) | Omezení vararg není součástí specifikace CLS a jediná konvence volání podporovaná specifikací CLS je standardní spravovaná konvence volání. | 15
Zásady vytváření názvů | [Zásady vytváření názvů](#naming-conventions) | Sestavení se řídí podle přílohy 7 technické sestavy 15 sady Unicode Standard 3.0, která se řídí sadou znaků povolených ke spuštění a jsou součástí identifikátorů, které jsou k dispozici online ve [formulářích normalizace Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identifikátory musí být v kanonickém formátu definovaném formulářem normalizace Unicode C. Pro účely specifikace CLS jsou dva identifikátory stejné, pokud mapování malých písmen (podle specifikace národního prostředí Unicode rozlišuje malá a velká písmena), jsou stejná. To znamená, že u dvou identifikátorů, které se považují za odlišné v rámci specifikace CLS, se liší ve více než pouhém případě. Chcete-li však přepsat zděděnou definici, rozhraní příkazového řádku vyžaduje použití přesného kódování původní deklarace. | 4
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Všechny názvy zavedené v oboru kompatibilním se specifikací CLS musí být nezávislé na druhu, s výjimkou případů, kdy jsou názvy identické a vyřešeny pomocí přetížení. To znamená, že když CTS umožňuje, aby jeden typ používal stejný název pro metodu a pole, specifikace CLS ne. | 5
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Pole a vnořené typy se liší podle porovnání identifikátorů, i když CTS umožňuje odlišit jedinečné podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů), se liší o více než jenom návratovým typem, s výjimkou zadání v pravidle CLS 39. | 6
Přetížení | [Přetížení](#overloads) | Pouze vlastnosti a metody mohou být přetíženy. | 37
Přetížení | [Přetížení](#overloads) |Vlastnosti a metody mohou být přetíženy pouze v závislosti na počtu a typech jejich parametrů, s výjimkou operátorů převodu s názvem `op_Implicit` a `op_Explicit` , které mohou být také přetíženy na základě jejich návratového typu. | 38
Přetížení | -- | Pokud dva nebo více metod odpovídajících specifikaci CLS mají stejný název a pro konkrétní sadu instancí typu, mají stejný parametr a návratové typy, pak všechny tyto metody musí být sémanticky rovnocenné v těchto instancích typu. | 48
Vlastnosti | [Vlastnosti](#properties) | Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech. | 24
Vlastnosti | [Vlastnosti](#properties) | Přistupující objekty vlastnosti musí být všechny statické, všechny virtuální nebo všechny instance. | 26
Vlastnosti | [Vlastnosti](#properties) | Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro metodu getter a typy všech, ale konečný parametr metody setter. Všechny tyto typy musí být kompatibilní se specifikací CLS a nesmí být spravované ukazatele (to znamená, že se nepředávají odkazem). | 27
Vlastnosti | [Vlastnosti](#properties) | Vlastnosti musí splňovat konkrétní vzor pojmenování. `SpecialName`Atribut uvedený v pravidle CLS 24 se bude ignorovat v odpovídajících porovnáních názvů a musí splňovat pravidla identifikátoru. Vlastnost musí mít metodu getter, metodu setter nebo obojí. | 28
Převod typů | [Převod typů](#type-conversion) | Pokud je k dispozici buď op_Implicit, nebo op_Explicit, je k dispozici alternativní způsob poskytnutí tohoto vynucení. | 39
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Typy zabalené hodnoty nejsou kompatibilní se specifikací CLS. | 3
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Všechny typy, které se zobrazují v signatuře, musí být kompatibilní se specifikací CLS. Všechny typy tvořící vytvořená instance obecného typu musí být kompatibilní se specifikací CLS. | 11
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Typové odkazy nejsou kompatibilní se specifikací CLS. | 14
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Nespravované typy ukazatelů nejsou kompatibilní se specifikací CLS. | 17
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Třídy kompatibilní se specifikací CLS, typy hodnot a rozhraní nevyžadují implementaci členů nekompatibilních se specifikací CLS. | 20
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | [System. Object](xref:System.Object) je kompatibilní se specifikací CLS. Všechny ostatní třídy odpovídající specifikaci CLS dědí z třídy kompatibilní se specifikací CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy a signatury členů typu

Typ [System. Object](xref:System.Object) je kompatibilní se specifikací CLS a je základní typ všech typů objektů v systému .NET Frameworkho typu. Dědičnost v .NET Framework je buď implicitní (například třída [String](xref:System.String) implicitně dědí z `Object` třídy) nebo explicitní (například třída [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) explicitně dědí ze třídy [ArgumentException](xref:System.ArgumentException) , která explicitně dědí z třídy [Exception](xref:System.Exception) . Aby byl odvozený typ kompatibilní se specifikací CLS, musí být jeho základní typ také kompatibilní se specifikací CLS.

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se specifikací CLS. Definuje základní `Counter` třídu, která jako čítač používá celé číslo bez znaménka 32-bit. Vzhledem k tomu, že třída poskytuje funkce čítače tím, že zabalí unsigned integer, třída je označena jako nekompatibilní se specifikací CLS. V důsledku toho odvozená třída `NonZeroCounter` také není kompatibilní se specifikací CLS.

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

Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se specifikací CLS. Kromě toho pro obecné typy:

* Všechny typy, které tvoří obecný typ s instancemi, musí být kompatibilní se specifikací CLS.

* Všechny typy použité jako omezení u obecných parametrů musí být kompatibilní se specifikací CLS.

.NET [Common Type System](common-type-system.md) zahrnuje řadu předdefinovaných typů, které jsou podporovány přímo modulem CLR (Common Language Runtime) a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se specifikací CLS.

Typ kompatibilní se specifikací CLS | Popis
------------------ | -----------
[Bytové](xref:System.Byte) | 8 bitů unsigned integer
[Int16](xref:System.Int16) | 16bitové celé číslo se znaménkem
[Int32](xref:System.Int32) | 32 – celé číslo se znaménkem
[Int64](xref:System.Int64) | 64 – celé číslo se znaménkem
[Single](xref:System.Single) | Hodnota s plovoucí desetinnou čárkou s jednoduchou přesností
[Klepat](xref:System.Double) | Hodnota s plovoucí desetinnou čárkou s dvojitou přesností
[Logická hodnota](xref:System.Boolean) | Typ hodnoty true nebo false
[Char](xref:System.Char) | Jednotka kódovaného kódu UTF-16
[Notaci](xref:System.Decimal) | Desítkové číslo jiné než plovoucí desetinné čárky
[IntPtr](xref:System.IntPtr) | Ukazatel nebo popisovač velikosti platformy definované platformou
[Řetězec](xref:System.String) | Kolekce nula, jednoho nebo více objektů char

Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se specifikací CLS.

Neodpovídající typ | Popis | Alternativa odpovídající specifikaci CLS
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8bitový datový typ se znaménkem na 8bitové číslo | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16bitové unsigned integer | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32 – bitová unsigned integer | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64 – bitová unsigned integer | [Int64](xref:System.Int64) (může přetečení), [BigInteger](xref:System.Numerics.BigInteger)nebo [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Nepodepsaný ukazatel nebo popisovač | [IntPtr](xref:System.IntPtr)

Knihovna tříd .NET Framework nebo jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se specifikací CLS; například:

* Zabalené typy hodnot. Následující příklad jazyka C# vytvoří třídu, která má veřejnou vlastnost typu `int*` s názvem `Value` . Vzhledem k tomu `int*` , že je zabalený typ hodnoty, kompilátor ho označí jako nekompatibilní se specifikací CLS.

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

* Typové odkazy, což jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ.

Pokud typ není kompatibilní se specifikací CLS, měli byste použít atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) s parametrem *neodpovídajícím* hodnotě s hodnotou `false` . Další informace najdete v části [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute) .

Následující příklad ilustruje problém dodržování specifikace CLS v signatuře metody a při vytváření instancí obecného typu. Definuje `InvoiceItem` třídu s vlastností typu [UInt32](xref:System.UInt32), vlastností typu [Nullable (of UInt32)](xref:System.Nullable%601)a konstruktorem s parametry typu `UInt32` a `Nullable(Of UInt32)` . Při pokusu o zkompilování tohoto příkladu získáte čtyři upozornění kompilátoru.

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

Chcete-li odstranit upozornění kompilátoru, nahraďte typy neodpovídající specifikaci CLS ve `InvoiceItem` veřejném rozhraní kompatibilními typy:

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

Kromě specifických typů uvedených v některé kategorie typů nejsou kompatibilní se specifikací CLS. Mezi ně patří nespravované typy ukazatelů a typy ukazatelů na funkce. Následující příklad vygeneruje upozornění kompilátoru, protože používá ukazatel na celé číslo pro vytvoření pole celých čísel.

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

Pro abstraktní třídy kompatibilní se specifikací CLS (tj. třídy označené jako `abstract` v jazyce C#) musí být všechny členy třídy také kompatibilní se specifikací CLS.

### <a name="naming-conventions"></a>Zásady vytváření názvů

Vzhledem k tomu, že některé programovací jazyky rozlišují velká a malá písmena, se musí identifikátory (například názvy oborů názvů, typů a členů) lišit o více než případu. Dva identifikátory jsou považovány za ekvivalentní, pokud je jejich mapování malých písmen stejné. Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person` . Protože se liší pouze v případě, kompilátor C# je označí jako nekompatibilní se specifikací CLS.

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

Identifikátory programovacích jazyků, jako jsou názvy oborů názvů, typů a členů, musí být v souladu se [standardem Unicode 3,0, technickým hlášením 15, přílohou 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

* Prvním znakem identifikátoru může být jakékoli velké písmeno Unicode, malé písmeno, název písmene, písmeno, písmeno, jiné písmeno nebo číslo písmen. Informace o kategoriích znaků Unicode naleznete v tématu výčet [System. Globalization. UnicodeCategory](xref:System.Globalization.UnicodeCategory) .

* Další znaky mohou být z libovolné kategorie jako první znak a mohou také obsahovat značky bez mezer mezi mezerami, kombinováním značek mezer, desetinnými čísly, interpunkční znaménky konektoru a formátovacími kódy.

Před porovnáním identifikátorů byste měli odfiltrovat Formátovací kódy a převést identifikátory na normalizační formu Unicode C, protože jeden znak může být reprezentován více jednotkami kódu zakódovanými v kódování UTF-16. Sekvence znaků, které vytvářejí stejné jednotky kódu ve formě normalizace Unicode C, nejsou kompatibilní se specifikací CLS. Následující příklad definuje vlastnost s názvem `Å` , která se skládá z znaku ANGSTROM Sign (U + 212B), a druhá vlastnost s názvem, `Å` která se skládá z znaku velké písmeno latinky a s výše UVEDENým prstenci (U + 00C5). Kompilátor jazyka C# označí zdrojový kód jako nekompatibilní se specifikací CLS.

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

Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v rámci oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou přeloženy prostřednictvím přetížení. Tento požadavek je přísnější než u společného systému typů, což umožňuje více členům v rámci oboru mít stejné názvy, pokud jsou různé druhy členů (například jedna je metoda a jedna je pole). Konkrétně pro členy typu:

* Pole a vnořené typy jsou rozlišeny pouze podle názvu.

* Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouhým návratovým typem.

Následující příklad znázorňuje požadavek, aby názvy členů musely být v rámci svého oboru jedinečné. Definuje třídu s názvem `Converter` , která obsahuje čtyři členy s názvem `Conversion` . Tři jsou metody a jedna je vlastnost. Metoda, která obsahuje `Int64` parametr, je jednoznačně pojmenována, ale tyto dvě metody s `Int32` parametrem nejsou, protože návratová hodnota není považována za součást signatury člena. `Conversion`Tato vlastnost také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.

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

Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na modul CLR (Common Language Runtime), musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v jazyce C# i Visual Basic. Následující příklad Visual Basic však může jednoznačně určit třídu s názvem `case` z `case` klíčového slova pomocí otevírací a pravé složené závorky. V opačném případě by tento příklad vytvořil chybovou zprávu "klíčové slovo není platné jako identifikátor" a kompilace se nezdařila.

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

Následující příklad jazyka C# může vytvořit instanci `case` třídy pomocí symbolu @ pro odstranění identifikátoru z klíčového slova jazyka. Bez něj kompilátor jazyka C# zobrazí dvě chybové zprávy, "očekával se typ" a "neplatný výraz" Case ".

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

Specifikace CLS (Common Language Specification) definuje dva operátory převodu:

* `op_Implicit`, který se používá pro rozšiřující převody, které nemají za následek ztrátu dat nebo přesnost. Například struktura [Decimal](xref:System.Decimal) obsahuje přetížený `op_Implicit` operátor pro převod hodnot integrálních typů a hodnot typu [char](xref:System.Char) na `Decimal` hodnoty.

* `op_Explicit`, který se používá pro zúžení převodů, které mohou mít za následek ztrátu velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. `Decimal`Struktura obsahuje například přetížený `op_Explicit` operátor pro převod [dvojitých](xref:System.Double) a [jednoduchých](xref:System.Single) hodnot na `Decimal` a pro převod `Decimal` hodnot na integrální hodnoty, `Double` , `Single` a `Char` .

Ne všechny jazyky ale podporují přetížení operátoru nebo definici vlastních operátorů. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob, jak provést převod. Doporučujeme zadat `From` metody XXX a `To` xxx.

Následující příklad definuje implicitní a explicitní převody kompatibilní se specifikací CLS. Vytvoří `UDouble` třídu, která představuje podepsané číslo s dvojitou přesností a plovoucí desetinnou čárkou. Poskytuje implicitní převody z `UDouble` na `Double` a pro explicitní převody z `UDouble` na `Single` , do a `Double` `UDouble` `Single` na `UDouble` . Také definuje `ToDouble` metodu jako alternativu implicitního operátoru převodu a `ToSingle` `FromDouble` metody, a `FromSingle` jako alternativy pro explicitní operátory převodu.

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

Pole kompatibilní se specifikací CLS odpovídají následujícím pravidlům:

* Všechny dimenze pole musí mít dolní mez nula. Následující příklad vytvoří pole, které není kompatibilní se specifikací CLS, s dolní mezí jedna. Všimněte si, že navzdory přítomnosti atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metodou není kompatibilní se specifikací CLS.

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

* Všechny prvky pole musí obsahovat typy kompatibilní se specifikací CLS. Následující příklad definuje dvě metody, které vracejí pole neodpovídající specifikaci CLS. První vrátí pole hodnot [UInt32](xref:System.UInt32) . Druhá vrátí pole [objektu](xref:System.Object) , které zahrnuje [Int32](xref:System.Int32) a `UInt32` Values. I když kompilátor identifikuje první pole jako nevyhovující z důvodu jeho `UInt32` typu, nerozpozná, že druhé pole obsahuje prvky neodpovídající specifikaci CLS.

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

* Rozlišení přetěžování pro metody, které mají parametry pole, je založené na tom, že se jedná o pole a na jejich typu prvku. Z tohoto důvodu je následující definice přetížené `GetSquares` metody kompatibilní se specifikací CLS.

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

Rozhraní kompatibilní se specifikací CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace). Rozhraní kompatibilní se specifikací CLS nemůže mít následující:

* Statické metody nebo statická pole. Kompilátor jazyka C# generuje chyby kompilátoru, pokud definujete statického člena v rozhraní.

* Pole. Kompilátor jazyka C# generuje chyby kompilátoru, pokud definujete pole v rozhraní.

* Metody, které nejsou kompatibilní se specifikací CLS. Například následující definice rozhraní obsahuje metodu, `INumber.GetUnsigned` která je označena jako nekompatibilní se specifikací CLS. Tento příklad generuje upozornění kompilátoru.

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

  Vzhledem k tomuto pravidlu nejsou typy kompatibilní se specifikací CLS vyžadovány k implementaci členů, které nedodržují specifikaci CLS. Pokud rozhraní kompatibilní se specifikací CLS zveřejňuje třídu, která implementuje rozhraní nekompatibilní se specifikací CLS, měla by také poskytnout konkrétní implementace všech členů nekompatibilních se specifikací CLS.

Kompilátory jazyka odpovídající specifikaci CLS musí také umožňovat třídě, aby poskytovala samostatné implementace členů, kteří mají stejný název a signaturu ve více rozhraních. Jazyk C# podporuje explicitní implementace rozhraní, které poskytují různé implementace identicky pojmenovaných metod. Následující příklad znázorňuje tento scénář definováním `Temperature` třídy, která implementuje `ICelsius` `IFahrenheit` rozhraní a jako explicitní implementace rozhraní.

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

Výčty kompatibilní se specifikací CLS musí dodržovat tato pravidla:

* Podkladový typ výčtu musí být vnitřní celé číslo kompatibilní se specifikací CLS ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)nebo [Int64](xref:System.Int64)). Například následující kód se pokusí definovat výčet, jehož nadřízený typ je [UInt32](xref:System.UInt32) a vygeneruje upozornění kompilátoru.

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

* Typ výčtu musí mít jedno pole instance s názvem `Value__` , které je označeno `FieldAttributes.RTSpecialName` atributem. To umožňuje implicitně odkazovat na hodnotu pole.

* Výčet zahrnuje statická pole literálů, jejichž typy se shodují s typem výčtu samotného. Například pokud definujete `State` výčet s hodnotami `State.On` a `State.Off` , `State.On` a `State.Off` jsou obě literální statická pole, jejichž typ je `State` .

* Existují dva druhy výčtů:

  * Výčet, který představuje sadu vzájemně se vylučujících pojmenovaných celočíselných hodnot. Tento typ výčtu je označen nepřítomností vlastního atributu [System. FlagsAttribute](xref:System.FlagsAttribute) .

  * Výčet, který představuje sadu bitových příznaků, které lze kombinovat k vygenerování nepojmenované hodnoty. Tento typ výčtu je označen přítomností vlastního atributu [System. FlagsAttribute](xref:System.FlagsAttribute) .

Další informace najdete v dokumentaci ke struktuře [výčtu](xref:System.Enum) .

* Hodnota výčtu není omezena na rozsah zadaných hodnot. Jinými slovy rozsah hodnot ve výčtu je rozsah své základní hodnoty. `Enum.IsDefined`K určení, zda je zadaná hodnota členem výčtu, lze použít metodu.

### <a name="type-members-in-general"></a>Obecné typy členů

Specifikace CLS (Common Language Specification) vyžaduje, aby všechna pole a metody byly dostupné jako členové konkrétní třídy. Proto globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány odděleně od typu) nejsou kompatibilní se specifikací CLS. Pokud se pokusíte do zdrojového kódu zahrnout globální pole nebo metodu, kompilátor jazyka C# vygeneruje chybu kompilátoru.

Specifikace CLS (Common Language Specification) podporuje pouze standardní spravovanou konvenci volání. Nepodporuje konvence nespravovaného volání a metody se seznamy argumentů proměnných označenými `varargs` klíčovým slovem. U seznamů argumentů proměnných, které jsou kompatibilní se standardní spravovanou konvencí volání, použijte atribut [ParamArrayAttribute](xref:System.ParamArrayAttribute) nebo implementaci jednotlivého jazyka, jako je `params` klíčové slovo v jazyce C# a `ParamArray` klíčové slovo v Visual Basic.

### <a name="member-accessibility"></a>Přístupnost člena

Přepsání zděděného člena nemůže změnit přístupnost daného člena. Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě. Existuje jedna výjimka: `protected internal` člen (v jazyce C#) nebo `Protected Friend` (v Visual Basic) v jednom sestavení, který je přepsán typem v jiném sestavení.  V takovém případě je přístupnost přepsání `Protected` .

Následující příklad ukazuje chybu, která je generována, když je atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) nastaven na hodnotu `true` a `Person` , což je třída odvozená z `Animal` , se pokusí změnit přístupnost `Species` vlastnosti z veřejné na soukromou. Příklad se úspěšně zkompiluje, pokud je jeho přístupnost změněno na veřejné.

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

Typy v signatuře člena musí být přístupné, kdykoli je tento člen přístupný. Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je Private, Protected nebo Internal. Následující příklad ukazuje chybu kompilátoru, která je výsledkem, když `StringWrapper` konstruktor třídy zpřístupňuje vnitřní `StringOperationType` hodnotu výčtu, která určuje, jak má být hodnota řetězce zabalena.

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

Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich nadřazený typ. Odpovídají umístění obecným parametrům v nadřazeném typu. Obecný typ může obsahovat také nové obecné parametry.

Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořenými typy mohou být skryty syntaxí jednotlivých jazyků. V následujícím příkladu obecný typ `Outer<T>` obsahuje dvě vnořené třídy `Inner1A` a `Inner1B<U>` . Volání `ToString` metody, ze které jednotlivé třídy dědí `Object.ToString` , ukazují, že každá vnořená třída obsahuje parametry typu své nadřazené třídy.

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

Názvy obecných typů jsou kódovány v *názvu*formuláře*n*, kde *název* je název typu, *`* je znakový literál a *n* je počet parametrů deklarovaných na typ, nebo pro vnořené obecné typy počet nově zavedených parametrů typu. Toto kódování názvů obecného typu je primárně v zájmu vývojářů, kteří používají reflexi pro přístup k obecným typům specifikace CLS v knihovně.

Pokud jsou omezení aplikována na obecný typ, všechny typy použité jako omezení musí být také kompatibilní se specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass` , která není kompatibilní se specifikací CLS, a obecnou třídu s názvem, `BaseCollection` jejíž parametr typu musí být odvozen od `BaseClass` . Ale vzhledem `BaseClass` k tomu, že není kompatibilní se specifikací CLS, kompilátor vygeneruje upozornění.

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

Je-li obecný typ odvozen od obecného základního typu, musí znovu deklarovat jakákoli omezení, aby bylo zaručeno, že jsou také splněna omezení základního typu. Následující příklad definuje `Number<T>` , který může představovat libovolný číselný typ. Definuje také `FloatingPoint<T>` třídu, která představuje hodnotu s plovoucí desetinnou čárkou. Zdrojový kód však nelze zkompilovat, protože neaplikuje omezení na `Number<T>` (Tento T musí být typ hodnoty) na `FloatingPoint<T>` .

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

Příklad se úspěšně zkompiluje, pokud je omezení přidáno do `FloatingPoint<T>` třídy.

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

Specifikace CLS (Common Language Specification) ukládá konzervativní model pro vytváření instancí pro vnořené typy a chráněné členy. Otevřené obecné typy nemohou vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného, chráněného obecného typu. Neobecné typy, které rozšíří specifické instance obecné základní třídy nebo rozhraní, nemůžou vystavovat pole nebo členy s podpisy, které obsahují různé instance vnořeného, chráněného obecného typu.

Následující příklad definuje obecný typ, `C1<T>` a chráněnou třídu `C1<T>.N` . `C1<T>`má dvě metody `M1` a `M2` . Není však `M1` kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z `C1<T>` . Druhá třída `C2` je odvozena z `C1<long>` . Má dvě metody, `M3` a `M4` . `M3`není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z podtřídy `C1<long>` . Všimněte si, že kompilátory jazyka mohou být ještě více omezující. V tomto příkladu Visual Basic při pokusu o zkompilování zobrazit chybu `M4` .

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

Konstruktory v třídách a strukturách odpovídajících specifikaci CLS musí dodržovat tato pravidla:

* Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy před tím, než přistupuje k zděděným datům instance. Tento požadavek je způsoben faktem, že konstruktory základní třídy nejsou děděny jejich odvozenými třídami. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.

  Kompilátory obvykle toto pravidlo vynutil nezávisle na kompatibilitě se specifikací CLS, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je odvozena od `Person` třídy, ale `Doctor` Třída nevolá `Person` konstruktor třídy pro inicializaci zděděných polí instance.

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

* Nelze volat konstruktor objektu s výjimkou vytvoření objektu. Kromě toho objekt nelze inicializovat dvakrát. Například to znamená, že nesmí `Object.MemberwiseClone` volat konstruktory.

### <a name="properties"></a>Vlastnosti

Vlastnosti v typech odpovídajících specifikaci CLS musí dodržovat tato pravidla:

* Vlastnost musí mít metodu Setter, getter nebo obojí. V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí jako samostatné metody (getter má název `get` \_ *PropertyName* a metoda Setter je `set` \_ *PropertyName*) označená jako `SpecialName` v metadatech sestavení. Kompilátor jazyka C# toto pravidlo vynutil automaticky, aniž by bylo nutné použít <xref:System.CLSCompliantAttribute> atribut.

* Typ vlastnosti je návratový typ vlastnosti getter a poslední argument metody setter. Tyto typy musí být kompatibilní se specifikací CLS a argumenty nelze přiřadit vlastnost odkazem (to znamená, že nemohou být spravovány ukazateli).

* Pokud má vlastnost metodu Getter i setter, musí obě být virtuální, obojí i obě instance. Kompilátor jazyka C# automaticky vynutil toto pravidlo prostřednictvím syntaxe definice vlastností.

### <a name="events"></a>Události

Událost je definována podle jejího názvu a typu. Typ události je delegát, který se používá k označení události. Například `DbConnection.StateChange` událost je typu `StateChangeEventHandler` . Kromě samotné události představují implementaci události tři metody s názvy založenými na názvu události a jsou označeny jako `SpecialName` v metadatech sestavení:

* Metoda pro přidání obslužné rutiny události s názvem `add` _*EventName*. Například metoda odběru události pro `DbConnection.StateChange` událost je pojmenována `add_StateChange` .

* Metoda pro odebrání obslužné rutiny události s názvem `remove` _*EventName*. Například metoda odebrání `DbConnection.StateChange` události je pojmenována `remove_StateChange` .

* Metoda pro indikaci, že došlo k události s názvem `raise` \_ *EventName*.

> [!NOTE]
> Většina pravidel specifikace CLS (Common Language Specification) týkajících se událostí je implementována kompilátory jazyka a jsou transparentní pro vývojáře komponent.

Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost. Musí také být všechny statické, instance nebo virtuální. Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události. Metody Add a Remove musí být buď přítomné, nebo obě chybět.

Následující příklad definuje třídu kompatibilní se specifikací CLS s názvem `Temperature` , která vyvolá `TemperatureChanged` událost, pokud změna teploty mezi dvěma čteními se rovná nebo překračuje prahovou hodnotu. `Temperature`Třída explicitně definuje `raise_TemperatureChanged` metodu, aby mohla selektivně provádět obslužné rutiny událostí.

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

Specifikace CLS (Common Language Specification) ukládá následující požadavky na přetížené členy:

* Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru. Konvence volání, návratový typ, vlastní modifikátory použité pro metodu nebo její parametr a zda jsou parametry předány hodnotou nebo odkazem, se nepovažují za rozdíl mezi přetíženími. Příklad naleznete v kódu pro požadavek, aby názvy musí být jedinečné v rámci oboru v části [konvence pojmenování](#naming-conventions) .

* Pouze vlastnosti a metody mohou být přetíženy. Pole a události nemohou být přetíženy.

* Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.

> [!NOTE]
> `op_Explicit`Operátory a `op_Implicit` jsou výjimky z pravidla, které vrací hodnotu, není považována za součást signatury metody pro řešení přetížení. Tyto dva operátory mohou být přetíženy v závislosti na jejich parametrech a jejich návratové hodnotě.

### <a name="exceptions"></a>Výjimky

Objekty výjimky musí být odvozeny od třídy [System. Exception](xref:System.Exception) nebo z jiného typu odvozeného od `System.Exception` . Následující příklad ukazuje chybu kompilátoru, která je výsledkem použití vlastní třídy s názvem `ErrorClass` pro zpracování výjimek.

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

Chcete-li tuto chybu opravit, `ErrorClass` Třída musí dědit z `System.Exception` . Kromě toho musí být vlastnost zprávy přepsána. Následující příklad opravuje tyto chyby k definování `ErrorClass` třídy, která je kompatibilní se specifikací CLS.

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

Sestavení rozhraní In.NET, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody. Vlastní atributy musí být odvozeny od typu [System. Attribute](xref:System.Attribute) nebo z typu odvozeného z `System.Attribute` .

V následujícím příkladu je toto pravidlo porušeno. Definuje `NumericAttribute` třídu, která není odvozena z `System.Attribute` . Všimněte si, že chyba kompilátoru je výsledkem pouze v případě, že je použit atribut, který není kompatibilní se specifikací CLS, nikoli při definování třídy.

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

Konstruktor nebo vlastnosti atributu kompatibilního se specifikací CLS mohou vystavovat pouze následující typy:

* [Logická hodnota](xref:System.Boolean)

* [Bytové](xref:System.Byte)

* [Char](xref:System.Char)

* [Klepat](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Single](xref:System.Single)

* [Řetězec](xref:System.String)

* [Typ](xref:System.Type)

* Jakýkoli typ výčtu, jehož základní typ je `Byte` , `Int16` , `Int32` nebo `Int64` .

Následující příklad definuje `DescriptionAttribute` třídu, která je odvozena z [atributu](xref:System.Attribute). Konstruktor třídy má parametr typu `Descriptor` , takže třída není kompatibilní se specifikací CLS. Všimněte si, že kompilátor jazyka C# generuje upozornění, ale úspěšně zkompiluje.

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

Atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) slouží k označení, zda prvek programu vyhovuje specifikaci CLS (Common Language Specification). `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)`Konstruktor obsahuje jeden povinný parametr, který je v *souladu*s, který označuje, zda je element program kompatibilní se specifikací CLS.

V době kompilace kompilátor detekuje nekompatibilní prvky, které se považují za kompatibilní se specifikací CLS, a vygeneruje upozornění. Kompilátor negeneruje upozornění pro typy nebo členy, které jsou explicitně deklarovány tak, že nejsou kompatibilní.

Vývojáři komponent mohou použít `CLSCompliantAttribute` atribut dvěma způsoby:

* Pro definování částí veřejného rozhraní vystaveného komponentou, která je kompatibilní se specifikací CLS, a částí, které nejsou kompatibilní se specifikací CLS. Když je atribut použit k označení určitých prvků programu jako kompatibilní se specifikací CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na .NET Framework.

* Aby bylo zajištěno, že veřejné rozhraní knihovny součástí zpřístupňuje pouze prvky programu, které jsou kompatibilní se specifikací CLS. Pokud prvky nejsou kompatibilní se specifikací CLS, kompilátory většinou vystaví upozornění.

> [!WARNING]
> V některých případech vynutily jazykové kompilátory pravidla kompatibilní se specifikací CLS bez ohledu na to, zda `CLSCompliantAttribute` je atribut použit. Například definování `*static` člena v rozhraní je v rozporu s pravidlem CLS. Pokud však definujete `*static` člena v rozhraní, kompilátor jazyka C# zobrazí chybovou zprávu a aplikace nebude zkompilována.

`CLSCompliantAttribute`Atribut je označen atributem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) , který má hodnotu `AttributeTargets.All` . Tato hodnota umožňuje použít `CLSCompliantAttribute` atribut na jakýkoli prvek programu, včetně sestavení, modulů, typů (tříd, struktur, výčtů, rozhraní a delegátů), členů typu (konstruktory, metody, vlastnosti, pole a události), parametrů, obecných parametrů a návratových hodnot. Nicméně v praxi byste měli použít atribut pouze pro sestavení, typy a členy typu. V opačném případě kompilátory ignorují atribut a pokračují v generování upozornění kompilátoru pokaždé, když narazí na nekompatibilní parametr, obecný parametr nebo návratovou hodnotu ve veřejném rozhraní knihovny.

Hodnota `CLSCompliantAttribute` atributu je děděna z obsažených prvků programu. Například pokud je sestavení označeno jako kompatibilní se specifikací CLS, jeho typy jsou také kompatibilní se specifikací CLS. Pokud je typ označený jako kompatibilní se specifikací CLS, jeho vnořené typy a členy jsou také kompatibilní se specifikací CLS.

Zděděné dodržování předpisů lze explicitně přepsat použitím `CLSCompliantAttribute` atributu na obsažený prvek programu. Například můžete použít `CLSCompliantAttribute` atribut s hodnotou *nedodržující* předpisy `false` pro definování nekompatibilního typu v vyhovujícím sestavení a můžete použít atribut s hodnotou *nedodržující* předpisy `true` k definování kompatibilního typu v sestavení, které nedodržuje předpisy. Můžete také definovat nekompatibilní členy v typu, který odpovídá. Nevyhovující typ ale nemůže mít odpovídající členy, takže nemůžete použít atribut s hodnotou *neodpovídající* hodnotě `true` pro přepsání dědičnosti z nekompatibilního typu.

Při vývoji komponent byste vždy měli použít `CLSCompliantAttribute` atribut k označení, zda vaše sestavení, jeho typy a jeho členové jsou kompatibilní se specifikací CLS.

Vytvoření součástí odpovídajících specifikaci CLS:

1. Použijte `CLSCompliantAttribute` k označení sestavení jako kompatibilní se specifikací CLS.

2. Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se specifikací CLS, jako nevyhovující.

3. Označte všechny veřejně vystavené členy v typech kompatibilních se specifikací CLS jako nevyhovující.

4. Poskytněte alternativu kompatibilní se specifikací CLS pro členy, které nedodržují specifikaci CLS.

Pokud jste úspěšně označili všechny typy a členy, které nedodržují předpisy, kompilátor by neměl generovat žádná upozornění, která nedodržují předpisy. Měli byste však určit, kteří členové nejsou kompatibilní se specifikací CLS, a seznamte se s alternativami kompatibilními se specifikací CLS v dokumentaci k produktu.

Následující příklad používá `CLSCompliantAttribute` atribut k definování sestavení kompatibilního se specifikací CLS a typu, `CharacterUtilities` , který má dva členy nekompatibilní se specifikací CLS. Vzhledem k tomu, že oba členy jsou označeny `CLSCompliant(false)` atributem, kompilátor nevydá žádná upozornění. Třída také poskytuje alternativu odpovídající specifikaci CLS pro obě metody. Obvykle bychom přidali dvě přetížení do `ToUTF16` metody pro zajištění alternativ odpovídajících specifikaci CLS. Nicméně vzhledem k tomu, že metody nemohou být přetíženy na základě návratové hodnoty, názvy metod odpovídajících specifikaci CLS se liší od názvů nevyhovujících metod.

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

Pokud vyvíjíte aplikaci místo knihovny (tj. Pokud nezveřejňujete typy nebo členy, které mohou být spotřebovány jinými vývojáři aplikací), bude kompatibilita CLS prvků programu, které vaše aplikace spotřebovává, odpovídat pouze v případě, že je váš jazyk nepodporuje. V takovém případě kompilátor jazyka vygeneruje chybu, pokud se pokusíte použít element, který není kompatibilní se specifikací CLS.

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden z nich zahrnuje plynulé využívání typů napsaných v jednom jazyce z aplikace napsané v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro `StringUtil.vb` , který obsahuje jednoho člena, `ToTitleCase` ve své `StringLib` třídě.

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

Pak použijete nástroj Link (Link. exe) ke kompilaci dvou modulů do sestavení:

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

Chcete-li kompilovat v jazyce C#, změňte název kompilátoru z Vbc na CSC a změňte příponu souboru z. vb na. cs:

```console
csc example.cs /r:UtilityLib.dll
```
