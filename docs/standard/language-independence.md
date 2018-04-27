---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: 'Zjistěte, jak můžete vyvíjet v jednom z mnoha jazyků podporovaných v rozhraní .NET, například C#, C + +/ CLI, F #, IronPython, jazyka Visual Basic, Visual COBOL a prostředí PowerShell.'
keywords: Rozhraní .NET, .NET core
author: dotnet-bot
ms.author: dotnetcontent
ms.date: 07/22/2016
ms.topic: article
dev_langs:
- csharp
- vb
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2745bc67c926f50c28f5fdfb122ee94a85f020ec
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty

Rozhraní .NET je závislý na jazyce. To znamená, že jako vývojář, můžete vyvíjet v jednom z mnoha jazycích, které cílí implementace rozhraní .NET, například C#, F # a Visual Basic. Můžete přejít na typy a členy vytvořených pro implementace rozhraní .NET, aniž by museli znát jazyk, ve kterém byly původně zapsán a bez nutnosti postupovat podle některého z původní jazyk konvence knihovny tříd. Pokud jste vývojář součásti, příslušné součásti byla přístupná pomocí jakékoli aplikace .NET, bez ohledu na jeho jazyk.

> [!NOTE]
> Tato první část tohoto článku popisuje vytvoření nezávislé na jazyku komponenty, který je součástí, které mohou být spotřebovávána aplikace, které jsou napsané v libovolném jazyce. Můžete také vytvořit jedna součást nebo aplikace z zdrojový kód napsaný v několika jazycích; v tématu [vzájemná funkční spolupráce mezi jazyky](#cross-language-interoperability) v druhé části tohoto článku. 

Plně pracovat s jinými objekty napsané v libovolném jazyce, musí objekty zpřístupnit volajícím jenom ty funkce, které jsou společné pro všechny jazyky. Tato společnou sadu funkcí je definována pomocí specifikace CLS (Common Language), což je sada pravidel, která se týkají vygenerované sestavení. Common Language Specification je definovaný v oddílu I klauzule 7 až 11 [standardy ECMA-335 standardní: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm). 

Pokud vaše součást splňuje Common Language Specification, se musí být kompatibilní se specifikací CLS a je přístupný z kódu v sestavení, které jsou napsané v žádný programovací jazyk, který podporuje specifikaci CLS. Můžete určit, zda příslušné součásti vyhovuje Common Language Specification při kompilaci s použitím [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut ke zdrojovému kódu. Další informace najdete v tématu [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute).

V tomto článku:

* [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules)

    * [Typy a typ člena podpisy](#types-and-type-member-signatures)

    * [Zásady vytváření názvů](#naming-conventions)
    
    * [Převod typů](#type-conversion)
    
    * [Pole](#arrays)
    
    * [Rozhraní](#interfaces)
    
    * [Výčty](#enumerations)
    
    * [Zadejte obecné členy](#type-members-in-general)
    
    * [Člen usnadnění](#member-accessibility)
    
    * [Obecné typy a členy](#generic-types-and-members)
    
    * [Konstruktory](#constructors)
    
    * [Vlastnosti](#properties)
    
    * [Události](#events)
    
    * [Overloads](#overloads)
    
    * [Výjimky](#exceptions)
    
    * [Atributy](#attributes)
    
* [Atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute)

* [Vzájemná funkční spolupráce mezi jazyky](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů se specifikací CLS

Tato část popisuje pravidla pro vytváření komponentu kompatibilní se specifikací CLS. Úplný seznam pravidel, viz oddíl I 11 klauzule [standardy ECMA-335 standardní: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Common Language Specification popisuje každé pravidlo pro souladu se specifikací CLS, protože se vztahuje k příjemce (vývojáři, kteří mají přístup prostřednictvím kódu programu komponenty, která je kompatibilní se specifikací CLS), rozhraní (vývojáře, kteří používají k vytvoření kompilátoru jazyka CLS-compliant knihovny) a Extender (vývojáře, kteří jsou vytvoření nástroje, jako je kompilátor jazyka nebo analyzátor kódu, který vytváří kompatibilní se specifikací CLS součásti). Tento článek se zaměřuje na pravidla, protože se vztahují na rozhraní. Upozorňujeme ale, že některé z pravidel, která se týkají Extender může také použít sestavení, které jsou vytvořené pomocí [Reflection.Emit](xref:System.Reflection.Emit). 

K návrhu komponenty, která je nezávislá na jazyk, stačí použít pravidla pro souladu se specifikací CLS pro veřejné rozhraní příslušné součásti. Implementaci privátní tak, aby odpovídala specifikace nemá. 

> [!IMPORTANT]
> Pravidla pro souladu se specifikací CLS platí pouze pro komponenty veřejné rozhraní, tak, aby jeho privátní implementace. 

Například jiné než nepodepsané celá čísla [bajtů](xref:System.Byte) nejsou kompatibilní se specifikací CLS. Protože `Person` třída v následujícím příkladu zpřístupňuje `Age` vlastnost typu [UInt16](xref:System.UInt16), následující kód zobrazí upozornění kompilátoru.

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

Můžete použít třídu osoba, která je kompatibilní se specifikací CLS změnou typu `Age` vlastnost z `UInt16` k [Int16](xref:System.Int16), který je kompatibilní se specifikací CLS, 16bitové znaménkem. Není nutné změnit typ privátní `personAge` pole. 

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

Knihovny veřejné rozhraní se skládá z následujících akcí:

* Definice třídy veřejné.

* Definice veřejné členy veřejné třídy a definice členů, které jsou přístupné do odvozených tříd (tedy chráněné členy). 

* Parametry a návratové typy veřejných metod veřejné třídy a parametry a návratové typy metod, které jsou přístupné pro odvozené třídy. 

V následující tabulce jsou uvedena pravidla pro souladu se specifikací CLS. Text tohoto pravidla se provede typu verbatim z [standardy ECMA-335 standardní: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 Ecma mezinárodní. Podrobnější informace o těchto pravidel je najít v následujících částech. 

Kategorie | Další informace naleznete v tématu | Pravidlo | Číslo pravidla
-------- | --- | ---- | -----------
Usnadnění | [Člen usnadnění](#member-accessibility) | Usnadnění přístupu se nezmění, pokud přepis zděděných metod, s výjimkou při přepsání metody zděděna z jiného sestavení pomocí usnadnění `family-or-assembly`. V takovém případě přepsání musí mít usnadnění `family`. | 10
Usnadnění | [Člen usnadnění](#member-accessibility) | Viditelnost a usnadnění typů a členů musí být tak, že typy v podpis kteréhokoli člena musí být viditelné a dostupné vždy, když je člena samotného viditelné a přístupné. Například veřejnou metodu, která je viditelná mimo jeho sestavení nebude mít argument s typem je viditelná pouze v rámci sestavení. Viditelnost a usnadnění typů skládání instanci obecného typu používá v podpis kteréhokoli člena musí být viditelné a dostupné vždy, když je člena samotného viditelné a přístupné. Například instanci obecného typu součástí podpis člena, který je viditelný mimo jeho sestavení nebude mít obecný argument s typem je viditelná pouze v rámci sestavení. | 12
Pole | [Pole](#arrays) | Pole musí obsahovat elementy s typem kompatibilní se specifikací CLS a všechny dimenze pole musí mít dolní meze nula. Pouze skutečnost, že je položka pole a typ elementu pole musí k rozlišení přetížení. Při přetížení je založena na dva nebo více pole typy typy elementů jmenuje typy. | 16
Atributy | [Atributy](#attributes) | Atributy musí být typu [System.Attribute](xref:System.Attribute), nebo typu, která dědí z něj. | 41
Atributy | [Atributy](#attributes) | Specifikace CLS umožňuje pouze podmnožinu kódování vlastních atributů. Jsou pouze typy, které se zobrazí v těchto kódování (viz oddíl IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [ System.Single](xref:System.Single), [System.Double](xref:System.Double), a jakýkoli typ výčtu založený na typu kompatibilní se specifikací CLS základní celé číslo. | 34
Atributy | [Atributy](#attributes) | Specifikace CLS neumožňuje veřejně viditelný požadované modifikátory (`modreq`, najdete v oddílu II), ale umožňuje volitelné modifikátory (`modopt`, najdete v oddílu II) nerozumí. | 35
Konstruktory | [Konstruktory](#constructors) | Před všechny přístupy dojde k data zděděné instance, musí volat konstruktor k objektu některé instance konstruktoru její základní třída. (To neplatí pro typy hodnot, které nemusí být konstruktory.)  | 21
Konstruktory | [Konstruktory](#constructors) | K objektu konstruktor nebude volána s výjimkou v rámci vytváření objektu a objekt nebude inicializovat dvakrát. | 22
Výčty | [Výčty](#enumerations) | Podkladový typ výčtového musí být vestavěný typ celé číslo, název pole musí být "value__" a toto pole musí být označen `RTSpecialName`. |  7
Výčty | [Výčty](#enumerations) | Existují dva odlišné typy výčtů, indikován přítomnosti nebo absenci [System.FlagsAttribute](xref:System.FlagsAttribute) vlastních atributů (viz oddíl IV knihovny). Jeden představuje pojmenovanou celočíselné hodnoty; Další představuje s názvem bitové příznaky, které mohou být kombinovány ke generování nepojmenované hodnotu. Hodnota `enum` není omezeno na zadané hodnoty. |  8
Výčty | [Výčty](#enumerations) | Výčet literálu statické pole musí mít typ výčtu, sám sebe. |  9
Události | [Události](#events) | Metody, které implementují událost musí být označen `SpecialName` v metadatech. |29
Události | [Události](#events) | Usnadnění událost a její přístupové objekty musí být stejné. |30
Události | [Události](#events) | `add` a `remove` metody pro buď událost obě musí být přítomen nebo chybí. |31
Události | [Události](#events) | `add` a `remove` metody pro událost každý přijme jeden parametr s typem definuje typ události a musí být odvozen od [System.Delegate](xref:System.Delegate). |32
Události | [Události](#events) | Události musí splňovat specifické vzoru pro pojmenovávání. Atribut SpecialName uvedené v pravidle specifikací CLS 29 se ignorují v porovnávání odpovídající název a musí splňovat pravidla identifikátor.  |33
Výjimky | [Výjimky](#exceptions) | Objekty, které jsou vyvolány musí být typu [System.Exception](xref:System.Exception) , nebo typu, která dědí z něj. Nicméně kompatibilní se specifikací CLS metody nemusejí blokovat šíření jiných typů výjimek. | 40
Obecné | [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules) | Specifikací CLS pravidla použít pouze na ty části typu, které jsou přístupné nebo viditelné outsideof definující sestavení. | 1
Obecné | [Pravidla dodržování předpisů se specifikací CLS](#cls-compliance-rules) | Členové kompatibilní s typy specifikací CLS nebudou označeny za kompatibilní se specifikací CLS. | 2
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Vnořené typy musí mít alespoň tolik obecné parametry jako nadřazených typů. Obecné parametry ve vnořené typy odpovídají umístěním obecné parametry v jeho nadřazených typů.  | 42
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Název obecného typu se kódovat počet parametrů typu deklarovaná u typu-nested nebo nově zavedených typ, pokud je vnořený podle z pravidel definovaných výše. | 43
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Obecný typ se redeclare dostatečná omezení, aby zaručil, že žádná omezení na základní typ, nebo rozhraní by vyhovět omezení obecného typu. | 44
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Typy používané jako sami omezení obecné parametry musí být kompatibilní se specifikací CLS. | 45
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Viditelnost a usnadnění přístupu členů (včetně vnořené typy) v instanci obecného typu se považuje být omezená na konkrétní instanci spíše než deklarace obecného typu jako celek. Za předpokladu, že to, viditelnost a usnadnění pravidla se specifikací CLS pravidla 12 stále platit. | 46
Obecné typy | [Obecné typy a členy](#generic-types-and-members) | Pro každou abstraktní nebo virtuální obecné metodu musí být výchozí implementace konkrétní (neabstraktní) | 47
Rozhraní | [Rozhraní](#interfaces) | Kompatibilní se specifikací CLS rozhraní nebude vyžadovat definici-specifikací CLS compliantmethods kvůli jejich implementaci. | 18
Rozhraní | [Rozhraní](#interfaces) | Kompatibilní se specifikací CLS rozhraní nebude definovat statických metod, ani se definování polí. | 19
Členové | [Zadejte obecné členy](#type-members-in-general) | Globální statická pole a metody nejsou kompatibilní se specifikací CLS. | 36
Členové | -- | Pomocí pole inicializace metadat je zadaná hodnota literálu statického. Kompatibilní se specifikací CLS literál musí mít zadaný v metadatech inicializace pole, které je stejného typu jako literál hodnotu (nebo základní typ, pokud je tento literál `enum`). | 13
Členové | [Zadejte obecné členy](#type-members-in-general) | Vararg omezení není součástí specifikaci CLS a pouze konvence volání podporuje specifikaci CLS je že standardní spravované konvence volání. | 15
Zásady vytváření názvů | [Zásady vytváření názvů](#naming-conventions) | Sestavení se řídí přílohy 7 z Technical Report 15 z Standard3.0 znakové sady Unicode, kterými se řídí sadu znaků povolených pro spuštění a být součástí identifikátory, které jsou k dispozici online v [Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html). Identifikátory musí být v kanonickém formátu definované Unicode normalizaci formuláře C. Pro účely specifikací CLS, dvě identifiersare stejné, pokud jejich malá mapování (podle Unicode malých a velkých písmen národního prostředí, 1: 1 malé písmeno mapování) jsou stejné. To znamená dva identifikátory, aby byla považována za jiný pod specifikaci CLS se liší se pouze jejich případě. Ale aby bylo možné přepsat zděděné definice rozhraní příkazového řádku vyžaduje přesné kódování původní deklaraci použít. | 4
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Všechny názvy, které se zavedly v kompatibilní se specifikací CLS oboru musí být odlišné bez ohledu na typ, s výjimkou případů, kdy jsou názvy identické a vyřešené prostřednictvím přetížení. To znamená Přestože CTS umožňuje jeden typ používat stejný název pro metodu a pole, specifikaci CLS neexistuje. | 5
Přetížení | [Zásady vytváření názvů](#naming-conventions) | Vnořené typy a pole musí být odlišné podle porovnání identifikátoru samostatně, eventhough CTS umožňuje odlišné podpisy odlišit. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátoru) se liší o více než jen návratový typ, s výjimkou zadané v 39 pravidlo specifikací CLS | 6
Přetížení | [Overloads](#overloads) | Mohou být přetíženy pouze vlastnosti a metody. | 37
Přetížení | [Overloads](#overloads) |Vlastnosti a metody mohou být přetíženy na základě pouze na počtu a typů jejich parametrů, s výjimkou operátory převodu s názvem `op_Implicit` a `op_Explicit`, které mohou také být přetíženy podle jejich návratový typ. | 38
Přetížení | -- | Pokud dva nebo více metod kompatibilní se specifikací CLS deklarovaného v typu mít stejné nameand, pro konkrétní sadu konkretizací typu, budou mít stejný parametr a návratové typy a pak musí být všechny tyto metody sémanticky ekvivalentní v těchto konkretizací typu. | 48
Vlastnosti | [Vlastnosti](#properties) | Metody, které implementují metody getter a setter vlastnosti, musí být označen `SpecialName` v metadatech. | 24
Vlastnosti | [Vlastnosti](#properties) | Přístupové objekty vlastnosti musí být statické, virtuální nebo být všechny instance. | 26
Vlastnosti | [Vlastnosti](#properties) | Typ vlastnosti musí být návratový typ metoda getter a typ poslední argument nastavovací metoda. Typy parametrů vlastnosti musí být typy parametrů metoda getter a všechny typy, ale konečný parametr nastavovací metoda. Všechny tyto typy musí být kompatibilní se specifikací CLS a nebude spravovaný ukazatele (to znamená, nebude předání odkazem). | 27
Vlastnosti | [Vlastnosti](#properties) | Vlastnosti musí splňovat specifické vzoru pro pojmenovávání. `SpecialName` Atribut podle specifikací CLS pravidlo 24 se ignorují v porovnávání odpovídající název a musí splňovat pravidla identifikátor. Vlastnost má metoda getter a setter metoda. | 28
Převod typů | [Převod typů](#type-conversion) | Pokud je zadaný op_Implicit nebo op_Explicit, předloží se alternativní způsob poskytování převod. | 39
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | Pevně určené typy hodnot nejsou kompatibilní se specifikací CLS. | 3
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | Všechny typy zobrazovaných v podpis musí být kompatibilní se specifikací CLS. Všechny typy skládání instanci obecného typu musí být kompatibilní se specifikací CLS. | 11
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | Typové odkazy nejsou kompatibilní se specifikací CLS. | 14
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | Nespravovaný ukazatel typy nejsou kompatibilní se specifikací CLS. | 17
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | Kompatibilní se specifikací CLS třídy, hodnotové typy a rozhraní nebude vyžadovat provádění jiných kompatibilní se specifikací CLS členy | 20
Typy | [Typy a typ člena podpisy](#types-and-type-member-signatures) | [System.Object](xref:System.Object) je kompatibilní se specifikací CLS. Jiná kompatibilní se specifikací CLS třída musí dědit z třídu kompatibilní se specifikací CLS. | 23

### <a name="types-and-type-member-signatures"></a>Typy a typ člena podpisy

[System.Object](xref:System.Object) typ je kompatibilní se specifikací CLS a je základní typ všechny typy objektů v systému typ rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je buď implicitní (například [řetězec](xref:System.String) třída implicitně dědí z `Object` třída) nebo explicitní (například [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) Třída explicitně dědí z [ArgumentException –](xref:System.ArgumentException) třídy, která explicitně dědí z [výjimka](xref:System.Exception) třídy. Odvozený typ jako kompatibilní se specifikací CLS jeho základní typ musí být kompatibilní se specifikací CLS. 

Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se specifikací CLS. Definuje základní `Counter` třídu, která používá jako čítač 32bitové celé číslo bez znaménka. Protože třída poskytuje funkce čítač nástrojem pro zabalení celé číslo bez znaménka, třída je označena jako jiný kompatibilní se specifikací CLS. V důsledku toho odvozené třídy `NonZeroCounter`, je také není kompatibilní se specifikací CLS. 

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

Všechny typy, které se zobrazují v signaturách členu, včetně metoda návratový typ nebo typ vlastnosti musí být kompatibilní se specifikací CLS. Kromě toho pro obecné typy: 

* Všechny typy, které tvoří instanci obecného typu musí být kompatibilní se specifikací CLS.

* Všechny typy používané jako omezení obecné parametry musí být kompatibilní se specifikací CLS. 

.NET [obecný systém typů](common-type-system.md) zahrnuje několik předdefinovaných typů, které jsou podporované přímo z modulu CLR a speciálně zakódovaným v metadatech sestavení. Z těchto typů vnitřní typy uvedené v následující tabulce jsou kompatibilní se specifikací CLS. 


Kompatibilní se specifikací CLS typu | Popis
------------------ | -----------
[Bajtů](xref:System.Byte) | 8bitové celé číslo bez znaménka 
[Int16](xref:System.Int16) | 16bitové celé číslo se znaménkem 
[Int32](xref:System.Int32) | 32bitové celé číslo se znaménkem 
[Int64](xref:System.Int64) | 64bitové celé číslo se znaménkem
[Jeden](xref:System.Single) | Desetinnou čárkou s jednoduchou přesností
[Double](xref:System.Double) | Dvojitá přesnost s plovoucí desetinnou čárkou
[Logická hodnota](xref:System.Boolean) | Typ hodnoty true nebo false 
[Char](xref:System.Char) | Kódování UTF-16 jednotka kódu
[Decimal](xref:System.Decimal) | Bez plovoucí čárkou desetinné číslo
[IntPtr](xref:System.IntPtr) | Ukazatel nebo popisovač velikosti definované platformy
[Řetězec](xref:System.String) | Kolekce nula, jednu nebo více objektů Char 
 
Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se specifikací CLS.


Nekompatibilní typ | Popis | Kompatibilní se specifikací CLS alternativní
------------------ | ----------- | -------------------------
[SByte –](xref:System.SByte) | datový typ 8bitové celé číslo se znaménkem | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16bitové celé číslo bez znaménka | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32bitové celé číslo bez znaménka | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64bitové celé číslo bez znaménka | [Int64](xref:System.Int64) (může přetečení), [BigInteger](xref:System.Numerics.BigInteger), nebo [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | Nepodepsané ukazatel nebo popisovač | [IntPtr](xref:System.IntPtr)
 
 Knihovna tříd rozhraní .NET Framework nebo jiné knihovny tříd mohou zahrnovat jiné typy, které nejsou kompatibilní se specifikací CLS; například: 
 
 * Pevně určené typy hodnot. Následující příklad jazyka C# vytvoří třídy, která má veřejná vlastnost typu `int`* s názvem `Value`. Protože `int`* je typu zabalené hodnoty kompilátor flags se jako jiný kompatibilní se specifikací CLS.

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

Pokud typ není kompatibilní se specifikací CLS, byste měli použít [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut s *isCompliant* parametr s hodnotou `false` k němu. Další informace najdete v tématu [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute) části.  

Následující příklad ilustruje problém v podpis metody a vytváření instancí obecného typu se specifikací CLS. Definuje, `InvoiceItem` s vlastností typu [UInt32](xref:System.UInt32), vlastnost typu [Nullable (z UInt32)](xref:System.Nullable%601)a konstruktor s parametry typu `UInt32` a `Nullable(Of UInt32)`. Při pokusu o zkompilování tohoto příkladu získáte čtyři upozornění kompilátoru.

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

Chcete-li eliminovat upozornění kompilátoru, nahraďte jiný kompatibilní se specifikací CLS typy v `InvoiceItem` veřejné rozhraní s kompatibilní s typy:

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

Kromě konkrétní typy uvedený některé jsou typy není kompatibilní se specifikací CLS. Mezi ně patří nespravovaný ukazatel typy a typy ukazatel funkce. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo pro vytvoření pole celých čísel. 

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

```vb
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

Pro kompatibilní se specifikací CLS abstraktní třídy (tedy třídy označeny jako `abstract` v jazyce C#), všichni členové třídy také musí být kompatibilní se specifikací CLS. 

### <a name="naming-conventions"></a>Zásady vytváření názvů

Vzhledem k tomu, že některé programovací jazyky jsou velká a malá písmena, identifikátory (například názvy oborů názvů, typy a členy) se musí lišit o více než případ. Dva identifikátory jsou považovány za ekvivalentní, pokud jejich malá mapování jsou stejné. Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person`. Protože se liší pouze v případě, kompilátor jazyka C# je označí jako není kompatibilní se specifikací CLS. 

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

Programovací jazyk identifikátory, třeba názvů obory názvů, typy a členy, musí odpovídat [Unicode Standard 3.0, technické sestavy 15, přílohy 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:

* První znak identifikátoru můžete být žádné Unicode velké písmeno, malé písmeno, malá písmena title, modifikátor, jiné písmeno nebo číslo písmeno. Informace o kategoriích znakové sady Unicode, najdete v článku [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) výčtu. 

* Následující znaky mohou být ze všech kategorií jako první znak a může také obsahovat bez mezer značky, mezer kombinování značky, desetinná čísla, spojovací interpunkci a formátování kódy. 

Předtím, než můžete porovnat identifikátory, musí odfiltrovat formátování kódy a převést identifikátory Unicode normalizaci formuláře C, protože jeden znak může být reprezentovaný víc jednotek kódu kódování UTF-16. Sekvence znaků, které produkují stejné jednotky kódu v jazyce C formuláře normalizaci Unicode nejsou kompatibilní se specifikací CLS. V následujícím příkladu definuje vlastnost s názvem `Å`, která zahrnuje znaku značka ANGSTROM (U + 212B) a druhý vlastnost s názvem `Å` který se skládá z znak LATIN velké písmeno A s PRSTENEC nad (U + 00 C 5). Kompilátor jazyka C# příznaky zdrojový kód jako jiný kompatibilní se specifikací CLS.

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

Názvy členů v konkrétním oboru (například obory názvů v rámci sestavení, typů v rámci oboru názvů nebo členy v rámci typu) musí být jedinečný, s výjimkou názvy, které se vyřeší prostřednictvím přetížení. Tento požadavek je přísnější než obecný systém typů, která umožňuje více členů v rámci oboru mít identické názvy, dokud jsou různé druhy členy (například jeden je metoda a jedna je pole). Konkrétně pro členy typu: 

* Vnořené typy a pole jsou rozlišené název samostatně. 

* Metody, vlastnosti a události, které mají stejný název se musí lišit o více než jen návratový typ. 

Následující příklad ilustruje požadavek, že názvy členů musí být jedinečný v rámci svého oboru. Definuje třídu s názvem `Converter` , který obsahuje čtyři členy s názvem `Conversion`. Tři způsoby, a jedna je vlastnost. Metoda, která zahrnuje `Int64` parametr je jednoznačně s názvem, ale tyto dvě metody s `Int32` parametr nejsou, protože návratová hodnota není součástí podpis člena. `Conversion` Vlastnost také porušuje tento požadavek, protože vlastnosti nemůže mít stejný název jako přetížené metody. 

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

Jednotlivé jazyky zahrnují jedinečný klíčová slova, takže jazyky cílených modul common language runtime nutné také zadat některé mechanismus pro odkazování identifikátorů (například názvy typů), který se shoduje s klíčová slova. Například `case` je klíčové slovo v jak C# a Visual Basic. Následující příklad jazyka Visual Basic je však možné kvůli zajištění jednoznačnosti třídy s názvem `case` z `case` – klíčové slovo pomocí otvírání a zavírání složené závorky. V příkladu by jinak chybová zpráva, "– klíčové slovo není platný jako identifikátor," a nepovede zkompilovat. 

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

Následující příklad jazyka C# je možné vytvořit instanci `case` pomocí @ symbol, který má-li odstranit nejednoznačnost identifikátor z klíčové slovo jazyka. Bez toho by kompilátor jazyka C# zobrazí dvě chybové zprávy, "Očekáván typ" a "Neplatný výraz výraz 'case'." 

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

* `op_Implicit`, který se používá pro rozšiřující převody, které není dojít ke ztrátě dat nebo přesnosti. Například [Decimal](xref:System.Decimal) struktura zahrnuje přetížené `op_Implicit` operátor k převedení hodnoty celočíselných typů a [Char](xref:System.Char) hodnoty k `Decimal` hodnoty. 

* `op_Explicit`, který se používá pro zúžení převodů, které může dojít ke ztrátě velikosti (hodnota je převést na hodnotu, která má menší oblast) nebo přesnosti. Například `Decimal` struktura zahrnuje přetížené `op_Explicit` operátor převést [dvojité](xref:System.Double) a [jeden](xref:System.Single) hodnoty k `Decimal` a převést `Decimal` hodnoty k celočíselné hodnoty, `Double`, `Single`, a `Char`. 

Ne všechny jazyky však podporovat přetížení operátoru nebo definici vlastní operátory. Pokud zvolíte možnost implementovat tyto operátory převodu, musí zadat jiný způsob, jak provést převod. Doporučujeme, aby poskytovaly `From`Xxx a `To`Xxx metody. 

V následujícím příkladu definuje implicitní a explicitní převody kompatibilní se specifikací CLS. Vytvoří `UDouble` třídu, která představuje podepsaný číslo s dvojitou přesností a s plovoucí desetinnou čárkou. Poskytuje pro implicitní převody z `UDouble` k `Double` a explicitní převody z `UDouble` k `Single`, `Double` k `UDouble`, a `Single` k `UDouble`. Také definuje `ToDouble` metoda jako alternativu k operátor implicitní převod a `ToSingle`, `FromDouble`, a `FromSingle` metody jako alternativy operátory explicitního převodu. 

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

Kompatibilní se specifikací CLS pole splňovat následující pravidla: 

* Všechny dimenze pole musí mít dolní mez 0. Následující příklad vytvoří jiný kompatibilní se specifikací CLS pole s dolní mez jednoho. Všimněte si, že, bez ohledu na přítomnost [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metoda není kompatibilní se specifikací CLS. 

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

* Všechny elementy pole musí obsahovat typy kompatibilní se specifikací CLS. V následujícím příkladu definuje dvě metody, které vrátí pole jiný kompatibilní se specifikací CLS. Vrátí první pole [UInt32](xref:System.UInt32) hodnoty. Druhý vrátí [objekt](xref:System.Object) pole, která zahrnuje [Int32](xref:System.Int32) a `UInt32` hodnoty. I když kompilátor identifikuje první pole jako nevyhovující z důvodu jeho `UInt32` typu, se nezdaří rozpoznat, že pole druhý obsahuje prvky jiný kompatibilní se specifikací CLS. 

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

* Řešení přetížení metody, které mají parametry pole je na základě toho, že jsou pole a na jejich typ elementu. Z tohoto důvodu následující definice přetížené `GetSquares` metoda je kompatibilní se specifikací CLS. 

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

Kompatibilní se specifikací CLS rozhraní můžete definovat vlastnosti, události a virtuální metody (metody s žádnou implementaci). Rozhraní, které je kompatibilní se specifikací CLS nemůže mít některé z následujících: 

* Statické metody nebo statických polí. C# kompilátoru generatse kompilátoru chyby, pokud je statický člen definujete v rozhraní. 

* Pole. Acompiler C# generuje chyby kompilátoru, pokud definujete pole v rozhraní.

* Metody, které nejsou kompatibilní se specifikací CLS. Například následující definice rozhraní obsahuje metody, `INumber.GetUnsigned`, která je označena jako jiný kompatibilní se specifikací CLS. Tento příklad vytvoří upozornění kompilátoru. 

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

  Podle tohoto pravidla není nutné kompatibilní se specifikací CLS typy implementace jiných kompatibilní se specifikací CLS členů. Pokud kompatibilní se specifikací CLS framework vystavit třídu, která implementuje rozhraní kompatibilní-specifikací CLS, se musí zadat konkrétní implementace všech členů jiný kompatibilní se specifikací CLS. 

Kompilátory jazyka kompatibilní se specifikací CLS musíte také povolit třídu zajistit samostatné implementace členů, které nemají se stejným názvem a podpis ve více rozhraní. C# podporuje explicitní implementace rozhraní k poskytovat různé implementace metod stejně jako s názvem. Následující příklad ilustruje tento scénář tak, že definujete `Temperature` třídu, která implementuje `ICelsius` a `IFahrenheit` rozhraní jako explicitní implementace rozhraní. 

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

Kompatibilní se specifikací CLS výčty nutné postupovat podle těchto pravidel: 

* Základní typ výčtu musí být celé vnitřní kompatibilní se specifikací CLS ([bajtů](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), nebo [Int64](xref:System.Int64)). Například následující kód pokusí definovat výčet jejíž základní typ je [UInt32](xref:System.UInt32) a vygeneruje upozornění kompilátoru. 

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

* Typ výčtu musí mít jednu instanci pole s názvem `Value__` , je označené `FieldAttributes.RTSpecialName` atribut. Můžete tak, aby odkazovaly hodnota pole implicitně. 

* Výčet obsahuje literál statická pole, jejichž typy shodovat s typem výčtu sám sebe. Například pokud definujete `State` výčtu s hodnotami `State.On` a `State.Off`, `State.On` a `State.Off` jsou obě literálu statické pole s typem `State`. 

* Existují dva druhy výčty: 
    
    * Výčet, který představuje sadu navzájem vylučují s názvem celočíselné hodnoty. Tento typ výčtu je indikován absenci [System.FlagsAttribute](xref:System.FlagsAttribute) vlastních atributů.
    
    * Výčet, který představuje sadu bitové příznaky, které můžete kombinovat ke generování nepojmenované hodnotu. Tento typ výčtu je indikován přítomnost [System.FlagsAttribute](xref:System.FlagsAttribute) vlastních atributů.
    
 Další informace najdete v dokumentaci pro [výčtu](xref:System.Enum) struktura. 

* Hodnota výčtu není omezen na rozsah jeho zadané hodnoty. Jinými slovy rozsahu hodnot v výčet je rozsah jeho základní hodnoty. Můžete použít `Enum.IsDefined` metoda k určení, zda je zadaná hodnota člena výčtu. 

### <a name="type-members-in-general"></a>Zadejte obecné členy

Common Language Specification vyžaduje všechna pole a metody pro přístupná jako členy určité třídy. Globální statická pole a metody (tedy statických polí nebo metod, které jsou definovány kromě typu) proto nejsou kompatibilní se specifikací CLS. Pokud se pokusíte zahrnout globální pole nebo metoda ve zdrojovém kódu, kompilátor jazyka C# generuje chybu kompilátoru. 

Common Language Specification podporuje jenom standardní spravovaných konvence volání. Nepodporuje nespravované konvence volání a metody s seznam argumentů s proměnnou délkou označené jako `varargs` – klíčové slovo. Seznamy argumentů proměnných, které jsou kompatibilní s standardní spravované konvence volání, použijte [ParamArrayAttribute](xref:System.ParamArrayAttribute) atribut nebo implementace tohoto jazyka, jako `params` – klíčové slovo v jazyce C# a `ParamArray` – klíčové slovo v jazyce Visual Basic. 

### <a name="member-accessibility"></a>Člen usnadnění

Přepsání zděděného členu nelze změnit pro usnadnění tohoto člena. Veřejná metoda v základní třídě například nelze přepsat privátní metoda v odvozené třídě. Existuje jedna výjimka: `protected internal` (v jazyku C#) nebo `Protected Friend` (v jazyce Visual Basic) člena v jedné sestavení, které je přepsat typu v jiném sestavení.  V takovém případě je usnadnění mají přednost před `Protected`. 

Následující příklad ukazuje chybu, která je generováno v případě [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) je atribut nastaven na `true`, a `Person`, což je třída odvozená z `Animal`, pokouší o změnu usnadnění přístupu `Species` vlastnost z veřejné privátní. V příkladu zkompiluje úspěšně, pokud jeho usnadnění se změní na veřejné. 

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

Typy v podpis člena musí být přístupné, vždy, když je dostupný tohoto člena. Například to znamená, že veřejné člena nelze zahrnout parametr, jehož typ je soukromý, chráněný nebo interní. Následující příklad ilustruje Chyba kompilátoru, která způsobí, že když `StringWrapper` konstruktoru třídy zpřístupní interní `StringOperationType` hodnota výčtu, která určuje, jak by měl být uzavřen hodnotu řetězce. 

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

Vnořené typy mít vždy alespoň tolik obecné parametry jako názvy jejich nadřazených typů. Tyto odpovídají umístěním obecné parametry v nadřazených typů. Obecný typ dále můžete přidat nové obecné parametry. 

Vztah mezi parametry obecného typu obsahující typu a jeho vnořené typy může být skrytý na základě syntaxe jednotlivé jazyky. V následujícím příkladu, obecného typu `Outer<T>` obsahuje dvě vnořené třídy `Inner1A` a `Inner1B<U>`. Volání `ToString` metodu, která každá třída dědí z `Object.ToString`, zobrazit, že každý vnořené třídy obsahuje parametry typu jeho obsahující třídy. 

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

Ve formuláři jsou zakódovány obecného typu názvy *název*'*n*, kde *název* je název typu *`* znak je literál, a *n* je počet parametrů deklarovaná u typu nebo pro vnořené obecné typy, počet parametrů nově přináší typu. Toto kódování obecného typu názvy je primárně určen pro vývojáře, kteří pomocí reflexe kompatibilní se specifikací CLS obecné typy v knihovně. 

Pokud omezení se použijí pro obecný typ, všechny typy používané jako omezení také musí být kompatibilní se specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass` není kompatibilní se specifikací CLS a obecné třídy s názvem `BaseCollection` jehož typ parametru musí být odvozeny od `BaseClass`. Ale protože `BaseClass` není kompatibilní se specifikací CLS, kompilátor vydá upozornění. 

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

Pokud obecný typ je odvozen od obecného typu základní, musí ho redeclare žádná omezení, tak, aby může zaručit, že jsou splněny také omezení u základního typu. V následujícím příkladu definuje `Number<T>` , může představovat libovolný číselného typu. Také definuje `FloatingPoint<T>` třídu, která představuje plovoucí bodu hodnotu. Ale zdrojového kódu se nepovede zkompilovat, protože jej nelze použít omezení na `Number<T>` (aby T musí být hodnota typu) k `FloatingPoint<T>`.

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
// The attempt to comple the example displays the following output:
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
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

V příkladu zkompiluje úspěšně Pokud omezení je přidán do `FloatingPoint<T>` třídy.

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

Common Language Specification ukládá konzervativní za konkretizaci model pro vnořené typy a chráněné členy. Otevřete obecné typy nemůže vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořené, chráněné obecného typu. Non obecné typy, které rozšiřují konkrétní instanci obecné základní třídy nebo rozhraní nemůže vystavovat pole nebo členy s podpisy, které obsahují různé konkretizaci vnořené, chráněné obecného typu.

V následujícím příkladu definuje obecného typu `C1<T>`a chráněná třída `C1<T>.N`. `C1<T>` má dvě metody, `M1` a `M2`. Ale `M1` není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objektu z `C1<T>`. Třídu sekundu `C2`, je odvozený od `C1<long>`. Nabízí dvě metody, `M3` a `M4`. `M3` není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z podtřídou třídy `C1<long>`. Všimněte si, že můžou být i víc omezující kompilátory jazyka. V tomto příkladu jazyka Visual Basic zobrazí chybu při pokusu o zkompilovat `M4`. 

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

Konstruktory v kompatibilní se specifikací CLS třídy a struktury nutné postupovat podle těchto pravidel: 

* Konstruktoru odvozené třídy musí volat konstruktoru instance její základní třída před přistupuje k data zděděné instance. Tento požadavek je skutečnost, že jejich odvozených tříd nejsou zdědí konstruktory základní třídy. Toto pravidlo se nevztahuje na struktury, které nepodporují přímý dědičnosti. 

  Kompilátory obvykle vynutit toto pravidlo nezávisle na souladu se specifikací CLS, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je odvozená od `Person` třídy, ale `Doctor` třída nepodaří volání `Person` konstruktoru třídy k chybě při inicializaci instance zděděné pole. 

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
    
* S výjimkou vytvoření objektu nelze volat konstruktor k objektu. Objekt kromě toho nelze inicializovat dvakrát. Například to znamená, že `Object.MemberwiseClone` konstruktory nesmějí provádět volání.  

### <a name="properties"></a>Vlastnosti

Vlastnosti v kompatibilní se specifikací CLS typy nutné postupovat podle těchto pravidel:

* Vlastnost musí mít setter, příjemce nebo obojí. V sestavení, ty jsou implementované jako speciální metody, což znamená, že se zobrazí jako samostatné metody (metoda getter jmenuje `get` \_ *propertyname* a nastavovací metoda je `set*\_*propertyname*) marked as `SpecialName' v na metadata sestavení. Kompilátor jazyka C# vynucuje toto pravidlo automaticky bez nutnosti použít [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut. 

* Typ vlastnost je návratový typ metoda getter vlastnosti a poslední argument nastavovací metoda. Tyto typy musí být kompatibilní se specifikací CLS a argumenty nelze přiřadit k vlastnosti podle reference (to znamená, že nemůže být spravované ukazatele). 

* Pokud vlastnost má metoda getter a setter, musí být obě virtuální, statické, nebo obě instance. Kompilátor jazyka C# automaticky vynucuje toto pravidlo prostřednictvím vlastnosti definice syntaxe. 

### <a name="events"></a>Události

Událost je definována podle názvu a jeho typu. Typ události je delegáta, který slouží k označení události. Například `DbConnection.StateChange` událostí je typu `StateChangeEventHandler`. Kromě samotné události tři metody s názvy na základě názvu událostí zadejte implementace události a jsou označeny jako `SpecialName` v metadat sestavení: 

* Metoda pro přidání obslužné rutiny události, s názvem `add`_*EventName*. Například metoda předplatného události pro `DbConnection.StateChange` událostí jmenuje `add_StateChange`. 

* Metoda pro odebrání obslužné rutiny události, s názvem `remove`_*EventName*. Například metoda odebrání pro `DbConnection.StateChange` událostí jmenuje `remove_StateChange`.

* Metoda pro označující, že došlo k události, název `raise`_*EventName*. 

> [!NOTE]
> Většina Common Language Specification pravidla týkající se událostí jsou implementované kompilátory jazyka a jsou transparentní pro vývojáře součásti. 

Metody pro přidání, odebrání a vyvolání události musí mít stejné usnadnění. Musí také všechny být statické, instanci, nebo virtuální. Metody pro přidávání a odebírání událost mít jeden parametr, jehož typ je typ delegáta události. Obě metody přidat a odebrat musí být přítomen nebo obě chybět. 

V následujícím příkladu definuje kompatibilní se specifikací CLS třídy s názvem `Temperature` , vyvolá `TemperatureChanged` událost, pokud změnu v hodnotě teploty mezi dvěma odečty rovná nebo překračuje prahovou hodnotu. `Temperature` Třída explicitně definuje `raise_TemperatureChanged` metoda proto to můžete provést selektivní obslužné rutiny událostí.

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

Common Language Specification ukládá tyto požadavky na přetěžované členy: 

* Členové mohou být přetíženy na základě počtu parametrů a typ libovolný parametr. Konvence, návratový typ volání vlastní modifikátory použít pro metodu nebo její parametr, a zda jsou parametry předány hodnotou nebo odkazem nejsou považovány za při rozlišování přetížení. Příklad, naleznete v části kód pro požadavek na názvy musí být jedinečný v rámci oboru v [konvence vytváření názvů](#naming-conventions) části. 

* Mohou být přetíženy pouze vlastnosti a metody. Nemohou být přetíženy pole a události. 

* Obecné metody mohou být přetíženy na základě počtu jejich obecné parametry. 

> [!NOTE]
>`op_Explicit` a `op_Implicit` operátory jsou výjimky pro pravidlo, které vrací hodnotu není považovány za součást podpis metody pro rozlišení přetížení. Tyto dva operátory mohou být přetíženy na základě jejich parametrů a jejich návratovou hodnotu. 

### <a name="exceptions"></a>Výjimky

Objekty výjimek musí být odvozeny od [System.Exception](xref:System.Exception) nebo z jiného typu odvozeného z `System.Exception`. Následující příklad ilustruje Chyba kompilátoru, který nastane, když vlastní třídu s názvem `ErrorClass` se používá pro zpracování výjimek.

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

Tuto chybu `ErrorClass` třída musí dědit z `System.Exception`. Kromě toho musí být přepsána vlastnosti zprávy. Následující příklad vyřeší tyto chyby můžete definovat `ErrorClass` třída, která je kompatibilní se specifikací CLS.  

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

Sestavení In.NET architektury, vlastní atributy poskytují mechanismus extensible pro vlastní atributy ukládání a načítání metadat o programování objekty, například sestavení, typy, členů a parametry metody. Vlastní atributy musí být odvozeny od [System.Attribute](xref:System.Attribute) nebo z typu odvozeného z `System.Attribute`.

Toto pravidlo je v rozporu v následujícím příkladu. Definuje `NumericAttribute` třídu, která není odvozena od `System.Attribute`. Všimněte si, že chyba kompilátoru výsledky, pouze když jiný kompatibilní se specifikací CLS atribut se použije, ne v případě, že je třída definovaná. 

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

V konstruktoru nebo z vlastností kompatibilní se specifikací CLS atributu můžou zpřístupnit pouze následující typy:

* [Logická hodnota](xref:System.Boolean)

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

V následujícím příkladu definuje `DescriptionAttribute` třídu odvozenou od [atribut](xref:System.Attribute). Konstruktoru třídy má parametr typu `Descriptor`, takže třída není kompatibilní se specifikací CLS. Všimněte si, že kompilátor jazyka C# vydá upozornění, ale zkompiluje úspěšně. 

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

## <a name="the-clscompliantattribute-attribute"></a>Atributu CLSCompliantAttribute

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atribut slouží k označení, zda je program element v souladu s Common Language Specification. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Konstruktor obsahuje jeden požadovaný parametr *isCompliant*, která určuje, zda je program element kompatibilní se specifikací CLS. 

Při kompilaci kompilátor zjistí nevyhovující prvky, které se předpokládá, že se kompatibilní se specifikací CLS a vydá upozornění. Kompilátor není emitování upozornění pro typy nebo členy, kteří jsou explicitně deklarované jako nevyhovující. 

Součást vývojáři mohou použít `CLSCompliantAttribute` atribut dvěma způsoby: 

* Chcete-li definovat části veřejné rozhraní vystavené součásti, které jsou kompatibilní se specifikací CLS a částí, které nejsou kompatibilní se specifikací CLS. Pokud atribut slouží k označení určitého programu elementy jako kompatibilní se specifikací CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástroje, které cílí na rozhraní .NET Framework. 

* K zajištění, že součást knihovny veřejné rozhraní zpřístupní pouze program prvky, které jsou kompatibilní se specifikací CLS. Pokud elementů nejsou kompatibilní se specifikací CLS, kompilátory obecně vydá upozornění.

> [!WARNING]
> V některých případech kompilátory jazyka vynutit kompatibilní se specifikací CLS pravidla bez ohledu na to, jestli `CLSCompliantAttribute` je použit atribut. Například definování `*static` člena v rozhraní porušuje pravidlo specifikací CLS. Ale pokud definujete `*static` člena v rozhraní, kompilátor jazyka C# zobrazí chybovou zprávu a selže, kompilace aplikace.

`CLSCompliantAttribute` Atribut je označen jako s [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) atribut, který má hodnotu `AttributeTargets.All`. Tuto hodnotu můžete použít `CLSCompliantAttribute` atribut žádné program elementu, včetně sestavení, moduly, typy (třídy, struktury, výčty, rozhraní a delegáti), zadejte členy (konstruktory, metody, vlastnosti, pole a události) parametry, obecné parametry a návratové hodnoty. Ale v praxi by se měly používat atribut pouze pro sestavení, typy a členy typu. Kompilátory, jinak hodnota ignorovat atribut a dále generovat upozornění kompilátoru, kdykoli se dojde k nevyhovující parametr, obecný parametr nebo vrátí hodnotu v veřejné rozhraní své knihovny.  

Hodnota `CLSCompliantAttribute` atribut zdědí prvky obsažené programu. Například pokud sestavení je označen jako kompatibilní se specifikací CLS, jeho typy jsou také kompatibilní se specifikací CLS. Pokud typ je označena jako kompatibilní se specifikací CLS, jeho vnořené typy a členy, jsou také kompatibilní se specifikací CLS. 

Zděděné dodržování předpisů můžete přepsat explicitně použitím `CLSCompliantAttribute` atribut elementu obsažené programu. Například můžete použít `CLSCompliantAttribute` atribut s *isCompliant* hodnotu `false` k definování typu nevyhovující v kompatibilní sestavení a vy můžete použít atribut s *isComplian*hodnotu `true` k definování typu kompatibilní v nevyhovující sestavení. Můžete také definovat nevyhovující členů v typu kompatibilní. Však nekompatibilní typ nemůže mít členy kompatibilní, proto nemůžete použít atribut s *isCompliant* hodnotu `true` přepsat dědičnost z typu nevyhovující. 

Při vývoji součásti, byste měli vždycky používat `CLSCompliantAttribute` atribut označuje, zda je kompatibilní se specifikací CLS vaše sestavení, jeho typy a její členy. 

Chcete-li vytvořit kompatibilní se specifikací CLS součásti: 

1. Použití `CLSCompliantAttribute` můžete označit sestavení jako kompatibilní se specifikací CLS.

2. Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se specifikací CLS jako nekompatibilní. 

3. Označte všechny veřejně vystavené členy v kompatibilní se specifikací CLS typy jako nekompatibilní. 

4. Zadejte kompatibilní se specifikací CLS alternativní pro členy jiné kompatibilní se specifikací CLS. 

Byl úspěšně označen nekompatibilní typy a členy, by neměl vaší kompilátoru emitování všechna upozornění, porušení. Ale by měl být uveden členy, které nejsou kompatibilní se specifikací CLS seznam a jejich kompatibilní se specifikací CLS alternativy v dokumentaci k produktu. 

Následující příklad používá `CLSCompliantAttribute` atribut pro definování kompatibilní se specifikací CLS sestavení a typu, `CharacterUtilities`, který má dva členy jiné kompatibilní se specifikací CLS. Vzhledem k tomu, že jsou oba členy označené `CLSCompliant(false)` atribut, kompilátor vytváří žádná upozornění. Třída poskytuje kompatibilní se specifikací CLS alternativní pro obě metody. Normálně, doporučujeme stačí přidat dvě přetížení k `ToUTF16` metody můžete zajistit kompatibilní se specifikací CLS alternativy. Ale protože metody nemohou být přetíženy na základě návratové hodnoty, názvy kompatibilní se specifikací CLS metody se liší od názvy nevyhovující metod.  

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

Pokud vyvíjíte aplikaci, nikoli knihovny (pokud nejsou vystavení typy nebo členy, kteří mohou být spotřebovávána jinými vývojáři aplikace), jsou souladu se specifikací CLS program prvků, které vaše aplikace využívá týkající se pouze v případě, že je váš jazyk nepodporuje . V takovém případě vaší kompilátoru jazyka dojde k chybě při pokusu použít element jiný kompatibilní se specifikací CLS. 

## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky

Jazyková nezávislost má několik možných významů. Jeden význam zahrnuje bezproblémově využívání typy, které jsou napsané v jednom jazyce z aplikace v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework. 

Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Tady je zdrojový kód pro `StringUtil.vb`, což zahrnuje jednoho člena, `ToTitleCase`v jeho `StringLib` třídy.

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

```
vbc /t:module StringUtil.vb 
```

Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:

```
csc /t:module NumberUtil.cs
```

Pak použijte nástroj Link (Link.exe) pro kompilaci dva moduly na sestavení: 

```
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

```
vbc example.vb /r:UtilityLib.dll
```

Kompilace pomocí C#, změňte název kompilátoru z Vbc – k csc a změnit příponu souboru z vb na .cs:

```
csc example.cs /r:UtilityLib.dll
```

