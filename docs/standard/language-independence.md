---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: Zjistěte, jak můžete vyvíjet v jednom z mnoha podporované jazyky v rozhraní .NET, jako například C#, C++vyhodnocovací, F#, IronPython, VB, Visual COBOL a prostředí PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: af266a551a194f55bc4951a8bdb0e9af6f823663
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663008"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

.NET je nezávislá na jazyce. To znamená, že jako vývojář můžete vyvíjet v některém z mnoha jazyků, které se zaměřují implementace .NET, jako například C#, F#a Visual Basic. Typy a členům knihoven třídy vyvinutým pro implementace .NET, aniž byste museli znát jazyk, ve kterém byly původně vytvořeny a to bez nutnosti dodržovat všechny původní jazykové konvence mají přístup. Pokud jste vývojářem komponenty, přístupné příslušné součásti žádné aplikace .NET, bez ohledu na jazyk.

> [!NOTE]
> První část Tento článek se zabývá tvorbou jazykově nezávislé komponenty – tedy součástí, které mohou být spotřebovány aplikacemi, které jsou napsané v libovolném jazyce. Můžete také vytvořit jednu součást nebo aplikaci ze zdrojového kódu napsaného v několika jazycích; Zobrazit [vzájemná](#cross-language-interoperability) v druhé části tohoto článku.

Chcete-li plně spolupracovat s ostatními objekty napsanými v libovolném jazyce, musí objektů zveřejnit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato běžná sada funkcí je definována tak specifikace CLS (Common Language), což je sada pravidel, která platí pro vygenerovaná sestavení. Common Language Specification je definována v oddílu I klauzule 7 až 11 [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Pokud vaše komponenta odpovídá specifikaci Common Language, je zaručeně kompatibilní se Specifikací CLS a je přístupný z kódu v sestavení, které jsou napsané v libovolném programovacím jazyce, který podporuje specifikaci CLS. Můžete určit, zda vaše komponenta odpovídá Common Language Specification v době kompilace použitím [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut ke zdrojovému kódu. Další informace najdete v tématu [atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).

V tomto článku:

* [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules)

  * [Typy a signatury členů typu](#types-and-type-member-signatures)

  * [Zásady vytváření názvů](#naming-conventions)

  * [Převod typů](#type-conversion)

  * [Pole](#arrays)

  * [Rozhraní](#interfaces)

  * [Výčty](#enumerations)

  * [Typy členů obecně](#type-members-in-general)

  * [Usnadnění přístupu člena](#member-accessibility)

  * [Obecné typy a členy](#generic-types-and-members)

  * [Konstruktory](#constructors)

  * [Vlastnosti](#properties)

  * [Události](#events)

  * [Overloads](#overloads)

  * [Výjimky](#exceptions)

  * [Atributy](#attributes)

* [Atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute)

* [Vzájemná funkční spolupráce mezi jazyky](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů se specifikací CLS

Tato část popisuje pravidla pro vytváření komponent odpovídajících specifikaci CLS. Úplný seznam pravidel, naleznete v oddílu I klauzule 11 [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Common Language Specification popisuje každé pravidlo pro dodržování specifikace CLS, protože se vztahuje na spotřebitele (vývojáři, kteří programově přistupují komponenty, která je kompatibilní se Specifikací CLS), rozhraní (vývojáři, kteří používají k vytvoření kompileru jazyka CLS-compliant knihovny) a zařízení Extender (vývojáři, kteří vytvářejí nástroj, jako je například kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty odpovídající specifikaci CLS). Tento článek se zaměřuje na pravidla, která je použita pro platformy. Pamatujte však, že některé z pravidel, které se vztahují k rozšiřujícím objektům mohou rovněž platit pro sestavení, která jsou vytvořena pomocí [Reflection.Emit](xref:System.Reflection.Emit).

Chcete-li navrhnout komponentu, která je nezávislá na jazyce, stačí dodržovat pravidla pro dodržování specifikace CLS pro veřejné rozhraní komponenty. Soukromá implementace nemusí odpovídat specifikaci.

> [!IMPORTANT]
> Pravidla pro dodržování specifikace CLS platí pouze pro veřejné rozhraní komponenty, nikoli pro jeho soukromou implementaci.

Například jiné než typu unsigned integer [bajtů](xref:System.Byte) nejsou kompatibilní se Specifikací CLS. Protože `Person` třídy v následujícím příkladu vystavuje `Age` vlastnost typu [UInt16](xref:System.UInt16), následující kód zobrazí upozornění kompilátoru.

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

Provedete osoba třídy odpovídající specifikaci CLS změnou typu `Age` vlastnost z `UInt16` k [Int16](xref:System.Int16), který je kompatibilní se Specifikací CLS, 16bitové celé číslo se znaménkem. Není nutné měnit typ soukromého `personAge` pole.

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

Veřejné rozhraní knihovny se skládá z následujících akcí:

* Definice veřejných tříd.

* Definice veřejných členů náležících veřejným třídám a definice členů schopných přistupovat k odvozeným třídám (tzn. chráněných členů).

* Parametry a návratové typy veřejných metod náležících veřejným třídám a parametry a návratové typy metod přistupovat k odvozeným třídám.

Pravidla pro dodržování specifikace CLS jsou uvedeny v následující tabulce. Text pravidel je doslova převzat z [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 společnosti Ecma International. Podrobnější informace o těchto pravidlech naleznete v následující části.

Kategorie | Další informace naleznete v tématu | Pravidlo | Číslo pravidla
-------- | --- | ---- | -----------
Usnadnění | [Usnadnění přístupu člena](#member-accessibility) | Přístupnost nesmí být změněna při přepisu zděděného metody kromě těch, kdy překrytí metody zděděné z jiného sestavení s přístupností `family-or-assembly`. V takovém případě musí mít přístupnost přetížení `family`. | 10
Usnadnění | [Usnadnění přístupu člena](#member-accessibility) | Viditelnost a přístupnost typů a členů musí být takový, že typy v podpisu kteréhokoli člena musí být viditelné a přístupné, kdykoli je samotný člen viditelný a přístupný. Například veřejnou metodu, která je viditelná mimo sestavení, nebude mít argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typy psaní obecného typu použít v podpisu kteréhokoli člena musí být viditelné a přístupné kdykoli je samotný člen viditelný a přístupný. Například instance obecného typu uvedená v podpisu člena, který je viditelný mimo sestavení, nebude mít obecný argument, jehož typ je viditelný pouze v rámci sestavení. | 12
Pole | [Pole](#arrays) | Pole musí mít prvky s typem kompatibilní se Specifikací CLS, a všechny dimenze pole musí mít nižší mez nula. Pouze skutečnost, že položka je pole a typ prvku pole musí rozlišovat mezi přetíženími. Když je přetížení založeno na dvou nebo více typech pole typy prvků by jsou pojmenované typy. | 16
Atributy | [Atributy](#attributes) | Atributy musí být typu [System.Attribute](xref:System.Attribute), nebo typu, který z něj dědí. | 41
Atributy | [Atributy](#attributes) | Specifikace CLS umožňuje pouze podsadu kódování vlastních atributů. Pouze typy, které se zobrazí v těchto kódováních jsou (viz oddíl IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [ System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), a libovolný typ výčtu, založený na typu základního celého čísla kompatibilním se Specifikací CLS. | 34
Atributy | [Atributy](#attributes) | Specifikace CLS neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz oddíl II), ale umožňuje volitelné modifikátory (`modopt`, viz oddíl II) nerozumí. | 35
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu zavolá nějakou instanci konstruktoru své základní třídy, předtím, než dojde k jakémukoli přístupu ke zděděným datům instance. (To neplatí pro typy hodnot, které nemusí mít konstruktory.)  | 21
Konstruktory | [Konstruktory](#constructors) | Konstruktor objektu nebude volán, jedině jako část vytvoření objektu a objekt nelze inicializovat dvakrát. | 22
Výčty | [Výčty](#enumerations) | Základní typ výčtu musí být vestavěný celočíselný typ, název pole musí být "value__" a toto pole musí být označen `RTSpecialName`. |  7
Výčty | [Výčty](#enumerations) | Existují dva odlišné typy výčtů, podle přítomnosti nebo nepřítomnosti [System.FlagsAttribute](xref:System.FlagsAttribute) vlastní atribut (viz oddíl IV knihovna). Jedna představuje pojmenované celočíselné hodnoty. bude představovat pojmenované bitové příznaky, které mohou být kombinovány pro generování nepojmenovaných hodnot. Hodnota `enum` není omezena pouze na zadané hodnoty. |  8
Výčty | [Výčty](#enumerations) | Pole statických literálů výčtu musejí mít typ samotného výčtu. |  9
Události | [Události](#events) | Metody, které implementují událost musí být označeno `SpecialName` v metadatech. |29
Události | [Události](#events) | Usnadnění události a jejich přístupových objektů musí být stejné. |30
Události | [Události](#events) | `add` a `remove` metody pro buď událost obě musí být k dispozici nebo zcela chybět. |31
Události | [Události](#events) | `add` a `remove` metody pro událost musí každá vzít jeden parametr typu definuje typ události a musí být odvozen z [System.Delegate](xref:System.Delegate). |32
Události | [Události](#events) | Události musí dodržovat zvláštní vzor pro pojmenování. Atribut SpecialName podle pravidla specifikace CLS 29 bude ignorován v porovnání s odpovídajícím názvem a musí dodržovat pravidla identifikátoru.  |33
Výjimky | [Výjimky](#exceptions) | Objekty, které jsou vyvolány musí být typu [System.Exception](xref:System.Exception) nebo typu, který z něj dědí. Nicméně metod odpovídajících specifikaci CLS nemusí blokovat šíření jiných typů výjimek. | 40
Obecné | [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules) | Pravidla specifikace CLS se vztahují pouze na ty části typu, které jsou přístupné nebo viditelné mimo definiční sestavení. | 1
Obecné | [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules) | Členy kompatibilní s typy neodpovídající specifikaci CLS nebudou označeny jako kompatibilní se Specifikací CLS. | 2
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Vnořené typy musí mít alespoň tolik obecných parametrů jako nadřazený typ. Obecné parametry ve vnořených typech odpovídají podle pozice obecným parametrům v jejich nadřazeném typu.  | 42
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Název obecného typu musí kódovat počet parametrů typu deklarované na nevnořeném typu nebo nově zavedeném do typu, pokud je vnořený, podle výše uvedených pravidel. | 43
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Obecný typ se předeklarovat dostatečná omezení k zajištění, že jakákoliv omezení u základního typu nebo rozhraní budou splněna díky jeho omezením. | 44
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Typy použité jako omezení u obecných parametrů musí samy odpovídat specifikaci kompatibilní se Specifikací CLS. | 45
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Viditelnost a přístupnost členů (včetně vnořených typů) v instanci obecného typu se považovat za vymezenou pro konkrétní instanci spíše než deklarace obecného typu jako celku. Za předpokladu, že to, pravidla viditelnosti a přístupnosti specifikace CLS, pravidla 12 stále platí. | 46
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Pro každou abstraktní nebo virtuální obecnou metodu musí existovat výchozí konkrétní (neabstraktní) implementace | 47
Rozhraní | [Rozhraní](#interfaces) | Rozhraní kompatibilní se Specifikací CLS nebudou vyžadovat definici metod odpovídajících neodpovídající specifikaci CLS, aby jejich implementaci. | 18
Rozhraní | [Rozhraní](#interfaces) | Rozhraní odpovídající specifikaci CLS nesmí definovat statické metody ani musí definovat pole. | 19
Členové | [Typy členů obecně](#type-members-in-general) | Globální statické položky a metody nejsou kompatibilní se Specifikací CLS. | 36
Členové | -- | Hodnota statického literálu je určena pomocí metadat inicializace pole. Literál odpovídající specifikaci CLS musí mít hodnotu zadanou v poli Inicializace metadat, která je stejného typu jako literál (nebo základního typu, pokud je literál `enum`). | 13
Členové | [Typy členů obecně](#type-members-in-general) | Omezení vararg není částí specifikace CLS a jedinou konvencí volání podporuje specifikace CLS je že standardní spravované konvence volání. | 15
Zásady vytváření názvů | [Zásady vytváření názvů](#naming-conventions) | Sestavení musí dodržovat přílohu 7 technické zprávy 15 sady Unicode Standard3.0 řídící sadu znaků povolených pro spuštění a být součástí identifikátory, které jsou k dispozici online na [tvarů normalizace Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identifikátory musí být v kanonickém formátu definovaném v normalizačním formuláři Unicode C. Pro účely specifikace CLS jsou dva identifikátory stejné v případě mapování jejich malých písmen (podle specifikací Unicode národním prostředí, 1: 1 malé písmeno mapování) jsou totožné. To znamená, že dva identifikátory, aby bylo považováno za jiné v rámci specifikace CLS se liší se ve více než jednoduchém případě. Za účelem přepsání zděděné definice však rozhraní příkazového řádku vyžaduje, přesného kódování v původní deklaraci použít. | 4
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Všechny názvy zavedené v oboru kompatibilní se Specifikací CLS musí být odlišné bez ohledu na typ, s výjimkou případů, kdy jsou názvy shodné a jsou vyřešeny prostřednictvím přetížení. To znamená, že zatímco CTS umožňuje jeden typ používal stejný název pro metodu a pole, CLS to neumožňuje. | 5
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Pole a vnořené typy musí být různé podle porovnání identifikátoru, i když CTS umožňuje odlišit různé podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátoru) se musí lišit více než jen návratovým typem, mimo specifikaci v pravidla 39 CLS | 6
Přetížení | [Overloads](#overloads) | Mohou být přetíženy pouze vlastnosti a metody. | 37
Přetížení | [Overloads](#overloads) |Vlastnosti a metody mohou být přetíženy pouze na základě čísla a typů jejich parametrů, s výjimkou operátorů převodu s názvem `op_Implicit` a `op_Explicit`, které mohou také být přetíženy podle jejich návratového typu. | 38
Přetížení | -- | Pokud mají dvě nebo více kompatibilní se Specifikací CLS metod deklarovaných v typu stejný název a pro konkrétní sadu vytváření instancí typů mají stejný parametr a návratové typy, musí být sémanticky rovnocenné v těchto instancí typů všechny tyto metody. | 48
Vlastnosti | [Vlastnosti](#properties) | Metody, které implementují metody getter a setter vlastnosti musí být označeny `SpecialName` v metadatech. | 24
Vlastnosti | [Vlastnosti](#properties) | Přistupující objekty vlastnosti musí být statická, virtuální nebo instanční. | 26
Vlastnosti | [Vlastnosti](#properties) | Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro getter a typy všech kromě posledního parametru metodu setter. Všechny tyto typy musí být kompatibilní se Specifikací CLS a nesmí být spravovanými ukazateli (tj. nesmí být předávány odkazem). | 27
Vlastnosti | [Vlastnosti](#properties) | Vlastnosti musí dodržovat zvláštní vzor pro pojmenování. `SpecialName` Podle pravidla specifikace CLS 24 atribut bude ignorován v porovnání s odpovídajícím názvem a musí dodržovat pravidla identifikátoru. Vlastnost musí mít metodu getter a setter metoda. | 28
Převod typů | [Převod typů](#type-conversion) | Pokud je k dispozici op_Implicit nebo op_Explicit, musí být k dispozici alternativní způsob vynucení. | 39
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Pevně určené typy hodnot nejsou kompatibilní se Specifikací CLS. | 3
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Všechny typy uvedené v označení musí být kompatibilní se Specifikací CLS. Všechny typy psaní obecného typu musí být kompatibilní se Specifikací CLS. | 11
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Typové odkazy nejsou kompatibilní se Specifikací CLS. | 14
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Nespravované typy ukazatelů nejsou kompatibilní se Specifikací CLS. | 17
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | Třídy odpovídající specifikaci CLS, typy hodnot a rozhraní nevyžadují implementaci členů mimo-kompatibilní se Specifikací CLS | 20
Typy | [Typy a signatury členů typu](#types-and-type-member-signatures) | [System.Object](xref:System.Object) je kompatibilní se Specifikací CLS. Jiná třída odpovídající specifikaci CLS musí dědit z třídy odpovídající specifikaci CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy a signatury členů typu

[System.Object](xref:System.Object) typ je kompatibilní se Specifikací CLS a je základní typ pro všechny typy objektů v systému typů rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je buď implicitní (například [řetězec](xref:System.String) třídy implicitně dědí z `Object` třídy) nebo explicitní (například [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) třída dědí explicitně z [ArgumentException](xref:System.ArgumentException) třída, která dědí explicitně z [výjimka](xref:System.Exception) třídy. Odvozený typ vyhovoval specifikaci CLS jeho základní typ musí být kompatibilní se Specifikací CLS.

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se Specifikací CLS. Definuje základní `Counter` třídu, která používá nepodepsané 32bitové celé číslo jako čítač. Protože třída poskytuje funkce čítače obalením celého čísla bez znaménka, třída je označena jako bez-kompatibilní se Specifikací CLS. V důsledku toho odvozená třída `NonZeroCounter`, není kompatibilní se Specifikací CLS.

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
      return String.Format("{0}). ", ctr);
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
      Return String.Format("{0}). ", ctr)
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

Všechny typy, které se zobrazují v signaturách členu, včetně návratový typ metody nebo vlastnosti typu, musí být kompatibilní se Specifikací CLS. Kromě toho pro obecné typy platí:

* Všechny typy, které píší obecný typ musí být kompatibilní se Specifikací CLS.

* Všechny typy použité jako omezení u obecných parametrů musí být kompatibilní se Specifikací CLS.

.NET [obecný systém typů](common-type-system.md) obsahuje několik předdefinovaných typů, které přímo podporují modul common language runtime a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů typů uvedených v následující tabulce jsou kompatibilní se Specifikací CLS.

Typ kompatibilní se Specifikací CLS | Popis
------------------ | -----------
[Bajtů](xref:System.Byte) | 8bitové celé číslo bez znaménka
[Int16](xref:System.Int16) | 16bitové celé číslo se znaménkem
[Int32](xref:System.Int32) | 32bitové celé číslo se znaménkem
[Int64](xref:System.Int64) | 64bitové celé číslo se znaménkem
[Jeden](xref:System.Single) | S plovoucí desetinnou čárkou s jednoduchou přesností
[Double](xref:System.Double) | Dvojité přesnosti s plovoucí desetinnou čárkou
[Datový typ Boolean](xref:System.Boolean) | Typ hodnoty true nebo false
[Char](xref:System.Char) | Kódová jednotka v kódování UTF-16
[Decimal](xref:System.Decimal) | Desetinné číslo bez plovoucí desetinné čárky
[IntPtr](xref:System.IntPtr) | Ukazatel nebo popisovač platformou definované velikosti
[Řetězec](xref:System.String) | Kolekce žádným, jedním nebo více objektů Char

Vnitřní typy, které jsou uvedeny v následující tabulce nejsou kompatibilní se Specifikací CLS.

Nevyhovující typ | Popis | Alternativy CLS
------------------ | ----------- | -------------------------
[SByte –](xref:System.SByte) | 8bitové celé číslo se znaménkem datový typ | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16bitové celé číslo bez znaménka | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32bitové celé číslo bez znaménka | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64bitové celé číslo bez znaménka | [Int64](xref:System.Int64) (může přetéci), [BigInteger](xref:System.Numerics.BigInteger), nebo [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Nepodepsaný ukazatel nebo popisovač | [IntPtr](xref:System.IntPtr)

Knihovny tříd rozhraní .NET Framework nebo jiná knihovna tříd může obsahovat další typy, které nejsou kompatibilní se Specifikací CLS; Příklad:

* Pevně určené typy hodnot. Následující C# příklad vytvoří třídu, která má veřejnou vlastnost typu `int`* s názvem `Value`. Protože `int`* je zabalený typ hodnoty, kompilátor jej označí příznakem jako bez-kompatibilní se Specifikací CLS.

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

* Typové odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ.

Pokud typ není kompatibilní se Specifikací CLS, měli byste použít [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atributem *isCompliant* parametr s hodnotou `false` k němu. Další informace najdete v tématu [atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute) oddílu.

Následující příklad ilustruje daný problém dodržování specifikace CLS v podpisu metody a obecný typ instance. Definuje `InvoiceItem` třídu s vlastností typu [UInt32](xref:System.UInt32), vlastnost typu [s možnou hodnotou Null (z UInt32)](xref:System.Nullable%601)a konstruktor s parametry typu `UInt32` a `Nullable(Of UInt32)`. Při pokusu o kompilaci tohoto příkladu, se čtyři upozornění kompilátoru.

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

Chcete-li vyloučit upozornění kompilátoru, nahraďte kompatibilní se Specifikací neodpovídajících typů v `InvoiceItem` veřejného rozhraní kompatibilními typy:

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

Kromě konkrétních uvedených typů některé kategorie typů nejsou kompatibilní se Specifikací CLS. Patří mezi ně typy nespravovaného ukazatele a typy ukazatelů na funkci. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo, chcete-li vytvořit pole celých čísel.

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

Pro kompatibilní se Specifikací CLS abstraktní třídy (tedy třídy označené jako `abstract` v C#), všichni členové třídy také musí být kompatibilní se Specifikací CLS.

### <a name="naming-conventions"></a>Zásady vytváření názvů

Protože některé programovací jazyky rozlišují velká a malá písmena, musí identifikátory (například názvy oborů názvů, typů a členů) lišit více než velikostí písmen. Dva identifikátory jsou považovány za rovnocenné, pokud mapování jejich malých písmen jsou stejné. Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person`. Protože se liší pouze velikostí písma, kompilátor jazyka C# je označí příznakem jako není kompatibilní se Specifikací CLS.

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

Identifikátory programovacího jazyka, jako je například názvy oborů názvů, typů a členů, musí odpovídat [Unicode Standard 3.0, technická zpráva 15, příloha 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

* První znak identifikátoru může být jakékoli Unicode velkým písmenem, malým písmenem, písmenem nadpisu, modifikátor, jiným písmenem nebo číslem. Informace o kategoriích znaků Unicode naleznete v tématu [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) výčtu.

* Následující znaky mohou být z kategorií jako první znak a může obsahovat také značky bez mezer mezer, kombinované značky, desetinná čísla, interpunkční znaménka konektoru a formátování kódů.

Než porovnáte identifikátory, měli byste odfiltrovat formátovací kódy a převést identifikátory na normalizační formu Unicode C, protože jeden znak může být reprezentován více jednotkami kódu kódování UTF-16. Sekvence znaků, které vyvolávají stejné jednotky kódu v normalizačním formuláři Unicode C nejsou kompatibilní se Specifikací CLS. Následující příklad definuje vlastnost s názvem `Å`, který se skládá ze znaku ANGSTROM SIGN (U + 212B) a druhé vlastnosti s názvem `Å` který se skládá ze znaků LATINKY velké písmeno s KROUŽKEM (U + 00 C 5). C# Kompilátor označí zdrojový kód jako bez-kompatibilní se Specifikací CLS.

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

Názvy členů v rámci určitého oboru (jako je například obory názvů v rámci sestavení, typy v oboru názvů nebo členy v rámci typu) musí být jedinečné, kromě názvů vyřešených prostřednictvím přetížení. Tento požadavek je přísnější než u systému obecného typu, což umožňuje více členům v rámci oboru mít stejný název, za předpokladu, že jsou různé druhy členů (například jeden je metoda a jeden je pole). Zejména pro členy typu:

* Pole a vnořené typy se rozlišují podle názvu.

* Metody, vlastnosti a události, které mají stejný název se musí lišit více než jen návratovým typem.

Následující příklad ukazuje požadavek, aby názvy členů musely být jedinečné v rámci jejich oboru. Definuje třídu s názvem `Converter` , který obsahuje čtyři členy s názvem `Conversion`. Tři jsou metody a jeden je vlastnost. Metoda, která zahrnuje `Int64` parametr je jedinečně pojmenovaná, ale dvě metody s `Int32` parametr nejsou, protože vrácená hodnota není považováno za součást podpisu člena. `Conversion` Vlastnost také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.

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

Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které se zaměřují modul CLR musí rovněž poskytnout určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v jazyce C# a Visual Basic. Následující příklad jazyka Visual Basic je však dokáže odlišit třídu s názvem `case` z `case` – klíčové slovo s využitím levé a pravé složené závorky. V opačném případě by v příkladu vytvoří chybová zpráva "Klíčové slovo není platné jako identifikátor" a kompilace selže.

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

Následující C# příklad je možné vytvořit instanci `case` pomocí symbolem @ do rozpoznání identifikátoru z klíčového slova jazyka. Bez něho zobrazí kompilátor jazyka C# dvě chybové zprávy: "Očekáván typ" a "Neplatný výraz pojem"case."

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

Common Language Specification definuje dva operátory převodu:

* `op_Implicit`, který se používá pro rozšiřující převody, při kterých nedojde ke ztrátě dat nebo přesnosti. Například [desítkové](xref:System.Decimal) struktura obsahuje přetíženou `op_Implicit` operátor pro převod integrálních hodnot a [Char](xref:System.Char) hodnoty `Decimal` hodnoty.

* `op_Explicit`, který se používá pro zužující převody, které můžou vést ke ztrátě velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. Například `Decimal` struktura obsahuje přetíženou `op_Explicit` operátor převodu [Double](xref:System.Double) a [jeden](xref:System.Single) hodnoty `Decimal` a k převodu `Decimal` hodnoty integrální hodnoty `Double`, `Single`, a `Char`.

Ale ne všechny jazyky podporují přetěžování nebo definici vlastních operátorů. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob provedení převodu. Doporučujeme vám, že zadáte `From`Xxx a `To`Xxx metody.

Následující příklad definuje odpovídající specifikaci CLS implicitní a explicitní převody. Vytvoří `UDouble` třídu, která představuje podepsané číslo s dvojitou přesností a plovoucí desetinnou čárkou. Poskytuje implicitní převody z `UDouble` k `Double` a explicitní převody z `UDouble` k `Single`, `Double` k `UDouble`, a `Single` k `UDouble`. Definuje také `ToDouble` metody jako alternativa k operátoru implicitního převodu a `ToSingle`, `FromDouble`, a `FromSingle` metody jako alternativy k operátorům explicitního převodu.

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

Pole kompatibilní se Specifikací CLS v souladu s těmito pravidly:

* Všechny dimenze pole musí mít nižší mez nula. Následující příklad vytvoří pole bez-kompatibilní se Specifikací CLS s dolní hranicí jednoho. Všimněte si, že bez ohledu na přítomnost [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut, kompilátor nezjistí, že pole vrácené metodou `Numbers.GetTenPrimes` metoda není kompatibilní se Specifikací CLS.

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

* Všechny prvky pole musí obsahovat typy odpovídající specifikaci CLS. Následující příklad definuje dvě metody, které vrací pole bez-kompatibilní se Specifikací CLS. První vrátí matici [UInt32](xref:System.UInt32) hodnoty. Druhý vrátí [objekt](xref:System.Object) pole, které zahrnuje [Int32](xref:System.Int32) a `UInt32` hodnoty. Ačkoli kompilátor identifikuje první pole jako nevyhovující z důvodu jeho `UInt32` typ, není schopna rozpoznat, že druhé pole obsahuje elementy bez-kompatibilní se Specifikací CLS.

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

* Rozlišení přetížení pro metody, které mají parametry pole je založeno na skutečnosti, že se jedná o pole a na jejich typu prvku. Z tohoto důvodu se následující definice přetížené `GetSquares` metoda je kompatibilní se Specifikací CLS.

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

Rozhraní odpovídající specifikaci CLS může definovat vlastnosti, události a virtuální metody (metody bez implementace). Kompatibilní se Specifikací CLS rozhraní nemůže mít některý z následujících akcí:

* Statické metody nebo statická pole. C# Kompilátor vygeneruje chyby kompilátoru při definování statického člena v rozhraní.

* Pole. C# Kompilátor vygeneruje chyby kompilátoru při definování pole v rozhraní.

* Metody, které nejsou kompatibilní se Specifikací CLS. Například následující definice rozhraní obsahuje metodu, `INumber.GetUnsigned`, která je označena jako bez-kompatibilní se Specifikací CLS. Tento příklad generuje upozornění kompilátoru.

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

  Kvůli tomuto pravidlu není nutné implementovat členy kompatibilní se Specifikací neodpovídajících typy kompatibilní se Specifikací CLS. Pokud rozhraní kompatibilní se Specifikací CLS zpřístupní třídu, která implementuje rozhraní kompatibilním neodpovídající specifikaci CLS, mělo by také poskytovat konkrétní implementace všech členů mimo-kompatibilní se Specifikací CLS.

Kompilátory jazyka odpovídající specifikaci CLS musí také umožnit třídě poskytnout samostatné implementace členů, kteří mají stejný název a podpis ve více rozhraní. C#podporuje explicitní implementace rozhraní k poskytují tak různé implementace identicky pojmenovaných metod. Následující příklad ukazuje tento scénář definováním `Temperature` třídu, která implementuje `ICelsius` a `IFahrenheit` rozhraní jako explicitní implementace rozhraní.

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

Výčty odpovídající specifikaci CLS musí postupovat podle těchto pravidel:

* Základní typ výčtu musí být celé číslo kompatibilní se Specifikací CLS vnitřní ([bajtů](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), nebo [Int64](xref:System.Int64)). Například následující kód se pokusí definovat výčet, jehož základní typ je [UInt32](xref:System.UInt32) a generuje upozornění kompilátoru.

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

* Typ výčtu musí mít jediné pole instance s názvem `Value__` , která je označena `FieldAttributes.RTSpecialName` atribut. To umožňuje implicitně odkazovat na hodnotu pole.

* Výčet zahrnuje statické literální pole, jejichž typy odpovídající typu stejný jako daný výčet. Například pokud definujete `State` výčet s hodnotami `State.On` a `State.Off`, `State.On` a `State.Off` jsou obě literální statická pole, jehož typ je `State`.

* Existují dva typy výčtů:

  * Výčet, který představuje sadu vzájemně se vylučujících pojmenovaných celočíselných hodnot. Tento typ výčtu se vyznačuje nepřítomností z [System.FlagsAttribute](xref:System.FlagsAttribute) vlastního atributu.

  * Výčet, který představuje sadu bitových příznaků, které lze kombinovat a generovat tak nepojmenovanou hodnotu. Tento typ výčtu se vyznačuje přítomnost [System.FlagsAttribute](xref:System.FlagsAttribute) vlastního atributu.

Další informace najdete v tématu v dokumentaci [výčtu](xref:System.Enum) struktury.

* Hodnota výčtu není omezena na rozsah zadaných hodnot. Jinými slovy rozsah hodnot ve výčtu je oblast jeho základní hodnoty. Můžete použít `Enum.IsDefined` metodou ke zjištění, zda zadaná hodnota je člen výčtu.

### <a name="type-members-in-general"></a>Typy členů obecně

Common Language Specification vyžaduje všem polím a metodám jako členům určité třídy přístup. Globální statické položky a metody (tedy statické pole nebo metody, které jsou definovány mimo typ) proto nejsou kompatibilní se Specifikací CLS. Pokud se pokusíte zahrnout globální pole nebo metoda ve zdrojovém kódu C# kompilátor vygeneruje chybu kompilátoru.

Common Language Specification podporuje pouze standardní spravované konvence volání. Nepodporuje podporovány konvence nespravovaného volání a metody se seznamy argumentů proměnných označené `varargs` – klíčové slovo. Seznamy argumentů proměnných, které jsou kompatibilní se standardní spravovanou konvencí volání, použijte [ParamArrayAttribute](xref:System.ParamArrayAttribute) atribut nebo implementaci jednotlivých jazyků, jako `params` – klíčové slovo v C# a `ParamArray` – klíčové slovo v jazyce Visual Basic.

### <a name="member-accessibility"></a>Usnadnění přístupu člena

Přepsání zděděných členů nemůže změnit přístupnost daného člena. Například veřejnou metodu v základní třídě nelze přepsat pomocí soukromé metody v odvozené třídě. Existuje jedna výjimka: `protected internal` (v jazyce C#) nebo `Protected Friend` (v jazyce Visual Basic) člen v jednom sestavení, který je přepsán typem v jiném sestavení.  V takovém případě je přístup k přepsání `Protected`.

Následující příklad ukazuje chybu, která je generován, když [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut je nastaven na `true`, a `Person`, což je třída odvozena z `Animal`, pokouší o změnu přístupnost `Species` vlastnost z veřejné na privátní. Příklad se zkompiluje úspěšně, pokud jeho přístupnost je změněna na veřejné.

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

Typy v signatuře člena musí být přístupné, pokaždé, když se tento člen přístupný. To například znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je privátní, chráněné nebo interní. Následující příklad ukazuje chybu kompilátoru, která způsobí, že když `StringWrapper` konstruktoru třídy poskytuje vnitřní `StringOperationType` hodnota výčtu, která určuje, jak by měl být uzavřen řetězcovou hodnotu.

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

Vnořené typy musí mít vždy alespoň tolik obecných parametrů jako jejich nadřazených typů. Tyto odpovídají podle pozice obecným parametrům nadřazeného typu. Obecný typ může zahrnovat také nové obecné parametry.

Vztah mezi parametry obecného typu nadřazeného typu a jeho vnořenými typy mohou být skryty pomocí syntaxe jednotlivých jazyků. V následujícím příkladu obecný typ `Outer<T>` obsahuje dvě vnořené třídy, `Inner1A` a `Inner1B<U>`. Volání `ToString` metoda, kterou každá třída dědí z `Object.ToString`, ukazují, že jednotlivé vnořené třídy zahrnují parametry typu jeho obsahující třídy.

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

Generické názvy jsou kódovány ve formě *název*"*n*, kde *název* je název typu *`* je znak literálu, a *n* je počet parametrů deklarovaných v typu, nebo případě vnořených obecných typů počet nově zavedených parametrů typu. Toto kódování názvů obecného typu je primárně určeno vývojářům, kteří používají reflexi k přístupu jsou kompatibilní se Specifikací obecné typy v knihovně.

Pokud platí omezení pro obecný typ, všechny typy použité jako omezení musí být také kompatibilní se Specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass` tedy není kompatibilní se Specifikací CLS a obecnou třídu s názvem `BaseCollection` jejíž typ parametru musí být odvozen od `BaseClass`. Ale protože `BaseClass` není kompatibilní se Specifikací CLS, kompilátor vytvoří upozornění.

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

Pokud obecný typ je odvozen z obecného základního typu, je nutné opětovně deklarovat všechna omezení tak, aby mohli zaručit, že jsou splněny také omezení u základního typu. Následující příklad definuje `Number<T>` , které představují libovolného číselného typu. Definuje také `FloatingPoint<T>` třídu, která představuje hodnotu s plovoucí desetinnou čárkou. Ale zdrojového kódu nejde zkompilovat, protože se nevztahuje omezení na `Number<T>` (T musí být typem hodnoty) na `FloatingPoint<T>`.

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

Příklad se zkompiluje úspěšně, pokud omezení se přidá do `FloatingPoint<T>` třídy.

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

Common Language Specification ukládá konzervativní instance modelu pro vnořené typy a chráněné členy. Otevření obecných typů nemůže vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného, chráněného obecného typu. Neobecné typy, které rozšiřují konkrétní vytváření instancí obecné základní třídy nebo rozhraní nemůže vystavovat pole nebo členy s podpisy, které obsahují různé vytváření instancí vnořených chráněných obecných typů.

Následující příklad definuje obecný typ, `C1<T>`a chráněnou třídu `C1<T>.N`. `C1<T>` poskytuje dva způsoby, `M1` a `M2`. Ale `M1` není kompatibilní se Specifikací CLS, protože se pokusí vrátit `C1<int>.N` objektu z `C1<T>`. Druhá třída `C2`, je odvozen z `C1<long>`. Nabízí dvě metody `M3` a `M4`. `M3` není kompatibilní se Specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z podtřídy `C1<long>`. Všimněte si, že kompilátory jazyka mohou být ještě více omezující. V tomto příkladu zobrazí Visual Basic chybu při pokusu o kompilaci `M4`.

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

Konstruktory ve kompatibilní se Specifikací CLS třídách a strukturách musí dodržovat tato pravidla:

* Konstruktor odvozené třídy musí volat instanci konstruktoru své základní třídy před přístupem ke zděděným datům instance. Tento požadavek je skutečnost, že konstruktory základních tříd nejsou zděděny svými odvozenými třídami. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.

  Obvykle kompilátory vynucují toto pravidlo nezávisle na dodržení specifikace CLS, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je odvozena od `Person` třídy, ale `Doctor` třídy selže při volání `Person` konstruktoru třídy inicializace zděděných polí instancí.

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

* S výjimkou vytvoření objektu nelze volat konstruktor objektu. Objekt navíc nelze inicializovat dvakrát. Například to znamená, že `Object.MemberwiseClone` nesmí volat konstruktory.

### <a name="properties"></a>Vlastnosti

Vlastnosti v typech odpovídajících specifikaci CLS musí postupovat podle těchto pravidel:

* Vlastnost musí mít setter, getter nebo oba. V sestavení, jsou implementovány jako speciální metody, což znamená, že se zobrazí jako samostatné metody (metoda getter má název `get` \_ *propertyname* a Metoda setter je `set` \_ *propertyname*) označené jako `SpecialName` v metadatech sestavení. C# Kompilátor vynucuje toto pravidlo automaticky bez nutnosti použít <xref:System.CLSCompliantAttribute> atribut.

* Typ vlastnosti je návratový typ vlastnosti getter a poslední argument metody setter. Tyto typy musí být kompatibilní se Specifikací CLS a argumenty nelze přiřazovat na vlastnost odkazem (to znamená, že nemůže být spravovanými ukazateli).

* Pokud je vlastnost getter a setter, musí být oba virtuální, statické, nebo obě instance. C# Kompilátor automaticky vynutí toto pravidlo prostřednictvím vlastností syntaxe definice.

### <a name="events"></a>Události

Událost je definována podle názvu a jeho typu. Typ události je delegát, který se používá k označení události. Například `DbConnection.StateChange` událostí je typu `StateChangeEventHandler`. Kromě samotné události zadat implementaci události tři metody s názvy založenými na názvu události a jsou označeny jako `SpecialName` v metadatech sestavení:

* Metoda pro přidání obslužné rutiny události s názvem `add`_*EventName*. Například metoda odběru události pro `DbConnection.StateChange` událost získá název `add_StateChange`.

* Metoda pro odebrání obslužné rutiny události s názvem `remove`_*EventName*. Například metoda odebrání pro `DbConnection.StateChange` událost získá název `remove_StateChange`.

* Metoda označující, že došlo k události, s názvem `raise` \_ *EventName*.

> [!NOTE]
> Většina Common Language Specification pravidla týkající se událostí je implementována pomocí kompilátorů jazyka a je transparentní pro vývojáře komponent.

Metody pro přidávání, odebírání a vyvolávání události musí mít stejné usnadnění. Musí také všechny být statické, instance, nebo virtuální. Metody pro přidávání a odebírání události mají jeden parametr, jehož typ je typ delegáta události. Metody add a remove musí být přítomen nebo nepřítomny.

Následující příklad definuje třídu odpovídající specifikaci CLS s názvem `Temperature` , která vyvolává `TemperatureChanged` událost, pokud změna teploty mezi dvěma měřeními rovná nebo překračuje prahovou hodnotu. `Temperature` Třída explicitně definuje `raise_TemperatureChanged` metodu tak, že je možné selektivně provést obslužné rutiny událostí.

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

Common Language Specification vyžaduje následující požadavky na přetížených členů:

* Členy můžete přetížit na základě počtu parametrů a typu parametrů. Konvence volání, návratový typ, vlastní modifikátory použité metody nebo jejího parametru a případné předání parametrů podle hodnoty nebo odkazu nejsou považovány za při rozlišování přetížení. Příklad naleznete v tématu kód pro požadavek, aby názvy musí být jedinečné v rámci oboru v [zásady vytváření názvů](#naming-conventions) oddílu.

* Mohou být přetíženy pouze vlastnosti a metody. Pole a události nemohou být přetíženy.

* Obecné metody lze přetížit na základě počtu jejich obecných parametrů.

> [!NOTE]
> `op_Explicit` a `op_Implicit` operátory jsou výjimky z pravidla, které vracejí hodnoty není považováno za součást podpisu pro řešení přetížení. Tyto dva operátory můžete přetížit na základě jejich parametrů a jejich návratové hodnoty.

### <a name="exceptions"></a>Výjimky

Objekty výjimky musí být odvozen od [System.Exception](xref:System.Exception) nebo z typu odvozeného z `System.Exception`. Následující příklad ukazuje chybu kompilátoru, která vznikne, když vlastní třída s názvem `ErrorClass` se používá pro zpracování výjimek.

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

Chcete-li opravit tuto chybu, `ErrorClass` třída musí dědit z `System.Exception`. Kromě toho se musí přepsat vlastnost zprávy. Následující příklad upravuje tyto chyby pro definování `ErrorClass` třídu, která je kompatibilní se Specifikací CLS.

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

V sestaveních.NET Framework vlastní atributy poskytují rozšiřitelné mechanismy pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako je například sestavení, typy, členy a parametry metody. Vlastní atributy musí být odvozen od [System.Attribute](xref:System.Attribute) nebo z typu odvozeného z `System.Attribute`.

Následující příklad poruší toto pravidlo. Definuje `NumericAttribute` třídu, která není odvozena od `System.Attribute`. Všimněte si, že k chybě kompilátoru dojde pouze při bez-kompatibilní se Specifikací CLS atributu se použije, ne v případě, že třída je definována.

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

Konstruktor nebo vlastnosti odpovídající specifikaci CLS atributu mohou vystavit pouze následující typy:

* [Datový typ Boolean](xref:System.Boolean)

* [Bajtů](xref:System.Byte)

* [Char](xref:System.Char)

* [Double](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Jeden](xref:System.Single)

* [Řetězec](xref:System.String)

* [Typ](xref:System.Type)

* Libovolný typ výčtu, jehož základní typ je `Byte`, `Int16`, `Int32`, nebo `Int64`.

Následující příklad definuje `DescriptionAttribute` třídu odvozenou od [atribut](xref:System.Attribute). Konstruktor třídy má parametr typu `Descriptor`, takže třída není kompatibilní se Specifikací CLS. Všimněte si, C# kompilátor vydá upozornění, ale provede kompilaci úspěšně.

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

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut se používá k označení, zda prvek programu v souladu s Common Language Specification. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Konstruktor obsahuje jeden povinný parametr, *isCompliant*, který určuje, zda ovládací prvek programu je kompatibilní se Specifikací CLS.

V době kompilace kompilátor zjistí nekompatibilní prvky, které jsou považovány za kompatibilní se Specifikací CLS a vysílá varování. Kompilátor negeneruje upozornění pro typy nebo členy, které jsou výslovně prohlášeny za nedodržující předpisy.

Vývojáři komponent mohou používat `CLSCompliantAttribute` atribut dvěma způsoby:

* Chcete-li definovat částí veřejného rozhraní vystavené komponentou, které jsou kompatibilní se Specifikací CLS a části, které nejsou kompatibilní se Specifikací CLS. Pokud atribut slouží k označení určitých prvků programu jako odpovídajících specifikaci CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které se zaměřují na rozhraní .NET Framework.

* Chcete-li zajistit, aby veřejné rozhraní knihovny součástí zpřístupňuje pouze prvky programu, které jsou kompatibilní se Specifikací CLS. Pokud nejsou prvky odpovídající specifikaci CLS, kompilátory standardně upozornění.

> [!WARNING]
> V některých případech vynucují kompilátory jazyka odpovídající specifikaci CLS pravidla bez ohledu na to, zda `CLSCompliantAttribute` atribut se používá. Například definování `*static` člena v rozhraní porušuje pravidla specifikace CLS. Ale pokud definujete `*static` člena v rozhraní, C# kompilátor zobrazí chybovou zprávu a kompilace aplikace selže.

`CLSCompliantAttribute` Je označena atributem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) atribut, který má hodnotu `AttributeTargets.All`. Tato hodnota vám umožní použít `CLSCompliantAttribute` atribut na libovolný prvek programu, včetně sestavení, modulů, typů (tříd, struktur, výčtů, rozhraní a delegátů), zadejte členů (konstruktorů, metody, vlastnosti, pole a události), parametrů, obecných parametrů a návratové hodnoty. V praxi však měli použít atribut pouze na sestavení, typy a členy typu. Jinak kompilátory ignorují atribut a pokračují v generování upozornění překladače pokaždé, když dojde k nevyhovující parametr, obecný parametr nebo vrátí hodnotu do veřejného rozhraní knihovny.

Hodnota `CLSCompliantAttribute` atribut je děděna prvky obsaženého programu. Například pokud je sestavení označeno jako kompatibilní se Specifikací CLS, jeho typy jsou také kompatibilní se Specifikací CLS. Pokud je typ označen jako kompatibilní se Specifikací CLS, jeho vnořené typy a členy jsou také kompatibilní se Specifikací CLS.

Můžete explicitně přepsat zděděný soulad použitím `CLSCompliantAttribute` atribut u obsaženého elementu programu. Například můžete použít `CLSCompliantAttribute` atributem *isCompliant* hodnotu `false` definovat nekompatibilní typ ve vyhovujícím sestavení a vy můžete použít atribut s *isCompliant*hodnotu `true` definovat kompatibilní typ v sestavení nevyhovující. Můžete také definovat nekompatibilní členy v kompatibilním typu. Nevyhovující typ však nemůže mít kompatibilní členy, proto nelze použít atribut s *isCompliant* hodnotu `true` k potlačení dědičnosti z nevyhovujícího typu.

Při vývoji komponentu byste měli vždy používat `CLSCompliantAttribute` atribut označuje, zda vaše sestavení, jeho typy a její členy jsou kompatibilní se Specifikací CLS.

Vytváření komponent odpovídajících specifikaci CLS:

1. Použití `CLSCompliantAttribute` označit sestavení jako kompatibilní se Specifikací CLS.

2. Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se Specifikací CLS jako nevyhovující.

3. Označte všechny veřejně vystavené členy v typech odpovídajících specifikaci CLS jako nevyhovující.

4. Poskytnout alternativu odpovídající specifikaci CLS pro členy mimo-kompatibilní se Specifikací CLS.

Pokud jste úspěšně označili nekompatibilní typy a členy, kompilátor by neměl generovat upozornění na nekompatibilitu. Však vhodné určit členy, které nejsou kompatibilní se Specifikací CLS a seznam jejich alternativ kompatibilní se Specifikací CLS v dokumentaci k produktu.

V následujícím příkladu `CLSCompliantAttribute` atribut pro definování kompatibilní se Specifikací CLS sestavení a typu, `CharacterUtilities`, který má dva členy mimo-kompatibilní se Specifikací CLS. Vzhledem k tomu, že oba členy jsou označeny `CLSCompliant(false)` atribut, kompilátor nevytvoří žádná varování. Třída rovněž poskytuje alternativy CLS pro obě metody. Obvykle bychom jen přidali dvě přetížení k `ToUTF16` metodu k dispozici alternativ odpovídajících specifikaci CLS. Ale vzhledem k tomu, že metody nemohou být přetíženy podle návratové hodnoty, názvy metod odpovídajících specifikaci CLS se liší od názvů nekompatibilních metod.

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

Pokud vyvíjíte aplikaci, nikoli knihovnu (tedy pokud nevystavujete typy nebo členy, které mohou být spotřebovány další vývojáři aplikací), dodržování specifikace CLS u prvků programu, které vaše aplikace využívá službu jsou zajímavé pouze v případě, že je váš jazyk nepodporuje . V takovém případě kompilátor jazyka vygeneruje chybu při pokusu o použití prvku bez-kompatibilní se Specifikací CLS.

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden význam, zahrnuje bezproblémové využití typů napsaných v jednom jazyce aplikací v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro `StringUtil.vb`, který obsahuje jeden člen, `ToTitleCase`v jeho `StringLib` třídy.

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

Pak použijete nástroj Link (Link.exe) ke kompilaci dvou modulů do sestavení:

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

Pro kompilaci pomocí C#, změňte název kompilátoru z Vbc – na csc a příponu souboru změňte z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```
