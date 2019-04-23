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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b64b0dd843f408f9a6d064aff935f8d18b3dbddd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313369"
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty
Rozhraní .NET Framework je nezávislá na jazyce. To znamená, že jako vývojář můžete vyvíjet v některém z mnoha jazyků, které se zaměřují rozhraní .NET Framework, například C#, C++vyhodnocovací, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL a Windows Powershellu. Typy a členům knihoven třídy vyvinutým pro rozhraní .NET Framework, aniž byste museli znát jazyk, ve kterém byly původně vytvořeny a to bez nutnosti dodržovat všechny původní jazykové konvence mají přístup. Pokud jste vývojářem komponenty, přístupné příslušné součásti žádné aplikace rozhraní .NET Framework bez ohledu na jazyk.  
  
> [!NOTE]
>  První část Tento článek se zabývá tvorbou jazykově nezávislé komponenty – tedy součástí, které mohou být spotřebovány aplikacemi, které jsou napsané v libovolném jazyce. Můžete také vytvořit jednu součást nebo aplikaci ze zdrojového kódu napsaného v několika jazycích; Zobrazit [vzájemná](#CrossLang) v druhé části tohoto článku.  
  
 Chcete-li plně spolupracovat s ostatními objekty napsanými v libovolném jazyce, musí objektů zveřejnit volajícím pouze ty funkce, které jsou společné pro všechny jazyky. Tato běžná sada funkcí je definována tak specifikace CLS (Common Language), což je sada pravidel, která platí pro vygenerovaná sestavení. Common Language Specification je definována v oddílu I klauzule 7 až 11 [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Pokud vaše komponenta odpovídá specifikaci Common Language, je zaručeně kompatibilní se Specifikací CLS a je přístupný z kódu v sestavení, které jsou napsané v libovolném programovacím jazyce, který podporuje specifikaci CLS. Můžete určit, zda vaše komponenta odpovídá Common Language Specification v době kompilace použitím <xref:System.CLSCompliantAttribute> atribut ke zdrojovému kódu. Další informace najdete v tématu [atribut CLSCompliantAttribute](#CLSAttribute).  
  
 V tomto článku:  
  
-   [Pravidla dodržování předpisů se specifikací CLS](#Rules)  
  
    -   [Typy a signatury členů typu](#Types)  
  
    -   [Zásady vytváření názvů](#naming)  
  
    -   [Převod typů](#conversion)  
  
    -   [Pole](#arrays)  
  
    -   [Rozhraní](#Interfaces)  
  
    -   [Výčty](#enums)  
  
    -   [Typy členů obecně](#members)  
  
    -   [Usnadnění přístupu člena](#MemberAccess)  
  
    -   [Obecné typy a členy](#Generics)  
  
    -   [Konstruktory](#ctors)  
  
    -   [Vlastnosti](#properties)  
  
    -   [Události](#events)  
  
    -   [Overloads](#overloads)  
  
    -   [Výjimky](#exceptions)  
  
    -   [Atributy](#attributes)  
  
-   [Atribut CLSCompliantAttribute](#CLSAttribute)  
  
-   [Vzájemná funkční spolupráce mezi jazyky](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů se specifikací CLS  
 Tato část popisuje pravidla pro vytváření komponent odpovídajících specifikaci CLS. Úplný seznam pravidel, naleznete v oddílu I klauzule 11 [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
> [!NOTE]
>  Common Language Specification popisuje každé pravidlo pro dodržování specifikace CLS, protože se vztahuje na spotřebitele (vývojáři, kteří programově přistupují komponenty, která je kompatibilní se Specifikací CLS), rozhraní (vývojáři, kteří používají k vytvoření kompileru jazyka CLS-compliant knihovny) a zařízení Extender (vývojáři, kteří vytvářejí nástroj, jako je například kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty odpovídající specifikaci CLS). Tento článek se zaměřuje na pravidla, která je použita pro platformy. Pamatujte však, že některá pravidla, které se vztahují k rozšiřujícím objektům mohou rovněž platit pro sestavení, která jsou vytvořena pomocí třídy Reflection.Emit.  
  
 Chcete-li navrhnout komponentu, která je nezávislá na jazyce, stačí dodržovat pravidla pro dodržování specifikace CLS pro veřejné rozhraní komponenty. Soukromá implementace nemusí odpovídat specifikaci.  
  
> [!IMPORTANT]
>  Pravidla pro dodržování specifikace CLS platí pouze pro veřejné rozhraní komponenty, nikoli pro jeho soukromou implementaci.  
  
 Například jiné než typu unsigned integer <xref:System.Byte> nejsou kompatibilní se Specifikací CLS. Protože `Person` třídy v následujícím příkladu vystavuje `Age` vlastnost typu <xref:System.UInt16>, následující kód zobrazí upozornění kompilátoru.  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 Můžete provést `Person` třídou CLS změnou typu `Age` vlastnost z <xref:System.UInt16> k <xref:System.Int16>, který je kompatibilní se Specifikací CLS, 16bitové celé číslo se znaménkem. Není nutné měnit typ soukromého `personAge` pole.  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 Veřejné rozhraní knihovny se skládá z následujících akcí:  
  
-   Definice veřejných tříd.  
  
-   Definice veřejných členů náležících veřejným třídám a definice členů schopných přistupovat k odvozeným třídám (tzn. chráněných členů).  
  
-   Parametry a návratové typy veřejných metod náležících veřejným třídám a parametry a návratové typy metod přistupovat k odvozeným třídám.  
  
 Pravidla pro dodržování specifikace CLS jsou uvedeny v následující tabulce. Text pravidel je doslova převzat z [Standard ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 společnosti Ecma International. Podrobnější informace o těchto pravidlech naleznete v následující části.  
  
|Kategorie|Další informace naleznete v tématu|Pravidlo|Číslo pravidla|  
|--------------|---------|----------|-----------------|  
|Usnadnění|[Usnadnění přístupu člena](#MemberAccess)|Přístupnost nesmí být změněna při přepisu zděděného metody kromě těch, kdy překrytí metody zděděné z jiného sestavení s přístupností `family-or-assembly`. V takovém případě musí mít přístupnost přetížení `family`.|10|  
|Usnadnění|[Usnadnění přístupu člena](#MemberAccess)|Viditelnost a přístupnost typů a členů musí být takový, že typy v podpisu kteréhokoli člena musí být viditelné a přístupné, kdykoli je samotný člen viditelný a přístupný. Například veřejnou metodu, která je viditelná mimo sestavení, nebude mít argument, jehož typ je viditelný pouze v rámci sestavení. Viditelnost a přístupnost typy psaní obecného typu použít v podpisu kteréhokoli člena musí být viditelné a přístupné kdykoli je samotný člen viditelný a přístupný. Například instance obecného typu uvedená v podpisu člena, který je viditelný mimo sestavení, nebude mít obecný argument, jehož typ je viditelný pouze v rámci sestavení.|12|  
|Pole|[Pole](#arrays)|Pole musí mít prvky s typem kompatibilní se Specifikací CLS, a všechny dimenze pole musí mít nižší mez nula. Pouze skutečnost, že položka je pole a typ prvku pole musí rozlišovat mezi přetíženími. Když je přetížení založeno na dvou nebo více typech pole typy prvků by jsou pojmenované typy.|16|  
|Atributy|[Atributy](#attributes)|Atributy musí být typu <xref:System.Attribute?displayProperty=nameWithType>, nebo typu, který z něj dědí.|41|  
|Atributy|[Atributy](#attributes)|Specifikace CLS umožňuje pouze podsadu kódování vlastních atributů. Jediné typy, které se zobrazí v těchto kódováních jsou (viz oddíl IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , a jakýkoli typ výčtu založený na typu základního celého čísla kompatibilním se Specifikací CLS.|34|  
|Atributy|[Atributy](#attributes)|Specifikace CLS neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz oddíl II), ale umožňuje volitelné modifikátory (`modopt`, viz oddíl II) nerozumí.|35|  
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu zavolá nějakou instanci konstruktoru své základní třídy, předtím, než dojde k jakémukoli přístupu ke zděděným datům instance. (To neplatí pro typy hodnot, které nemusí mít konstruktory.)|21|  
|Konstruktory|[Konstruktory](#ctors)|Konstruktor objektu nebude volán, jedině jako část vytvoření objektu a objekt nelze inicializovat dvakrát.|22|  
|Výčty|[Výčty](#enums)|Základní typ výčtu musí být vestavěný celočíselný typ, název pole musí být "value__" a toto pole musí být označen `RTSpecialName`.|7|  
|Výčty|[Výčty](#enums)|Existují dva odlišné typy výčtů, podle přítomnosti nebo nepřítomnosti <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastní atribut (viz oddíl IV knihovna). Jedna představuje pojmenované celočíselné hodnoty. bude představovat pojmenované bitové příznaky, které mohou být kombinovány pro generování nepojmenovaných hodnot. Hodnota `enum` není omezena pouze na zadané hodnoty.|8|  
|Výčty|[Výčty](#enums)|Pole statických literálů výčtu musejí mít typ samotného výčtu.|9|  
|Události|[Události](#events)|Metody, které implementují událost musí být označeno `SpecialName` v metadatech.|29|  
|Události|[Události](#events)|Usnadnění události a jejich přístupových objektů musí být stejné.|30|  
|Události|[Události](#events)|`add` a `remove` metody pro buď událost obě musí být k dispozici nebo zcela chybět.|31|  
|Události|[Události](#events)|`add` a `remove` metody pro událost musí každá vzít jeden parametr typu definuje typ události a musí být odvozen z <xref:System.Delegate?displayProperty=nameWithType>.|32|  
|Události|[Události](#events)|Události musí dodržovat zvláštní vzor pro pojmenování. `SpecialName` Atribut podle pravidla specifikace CLS 29 bude ignorován v porovnání s odpovídajícím názvem a musí dodržovat pravidla identifikátoru.|33|  
|Výjimky|[Výjimky](#exceptions)|Objekty, které jsou vyvolány musí být typu <xref:System.Exception?displayProperty=nameWithType> nebo typu, který z něj dědí. Nicméně metod odpovídajících specifikaci CLS nemusí blokovat šíření jiných typů výjimek.|40|  
|Obecné|[Dodržování specifikace CLS: pravidla](#Rules)|Pravidla specifikace CLS se vztahují pouze na ty části typu, které jsou přístupné nebo viditelné mimo definiční sestavení.|1|  
|Obecné|[Dodržování specifikace CLS: pravidla](#Rules)|Členy kompatibilní s typy neodpovídající specifikaci CLS nebudou označeny jako kompatibilní se Specifikací CLS.|2|  
|Obecné typy|[Obecné typy a členy](#Generics)|Vnořené typy musí mít alespoň tolik obecných parametrů jako nadřazený typ. Obecné parametry ve vnořených typech odpovídají podle pozice obecným parametrům v jejich nadřazeném typu.|42|  
|Obecné typy|[Obecné typy a členy](#Generics)|Název obecného typu musí kódovat počet parametrů typu deklarované na nevnořeném typu nebo nově zavedeném do typu, pokud je vnořený, podle výše uvedených pravidel.|43|  
|Obecné typy|[Obecné typy a členy](#Generics)|Obecný typ se předeklarovat dostatečná omezení k zajištění, že jakákoliv omezení u základního typu nebo rozhraní budou splněna díky jeho omezením.|4444|  
|Obecné typy|[Obecné typy a členy](#Generics)|Typy použité jako omezení u obecných parametrů musí samy odpovídat specifikaci kompatibilní se Specifikací CLS.|45|  
|Obecné typy|[Obecné typy a členy](#Generics)|Viditelnost a přístupnost členů (včetně vnořených typů) v instanci obecného typu se považovat za vymezenou pro konkrétní instanci spíše než deklarace obecného typu jako celku. Za předpokladu, že to, pravidla viditelnosti a přístupnosti specifikace CLS, pravidla 12 stále platí.|46|  
|Obecné typy|[Obecné typy a členy](#Generics)|Pro každou abstraktní nebo virtuální obecnou metodu musí existovat výchozí konkrétní (neabstraktní) implementace.|47|  
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní kompatibilní se Specifikací CLS nebudou vyžadovat definici metod odpovídajících neodpovídající specifikaci CLS, aby jejich implementaci.|18|  
|Rozhraní|[Rozhraní](#Interfaces)|Rozhraní odpovídající specifikaci CLS nesmí definovat statické metody ani musí definovat pole.|19|  
|Členové|[Typy členů obecně](#members)|Globální statické položky a metody nejsou kompatibilní se Specifikací CLS.|36|  
|Členové|--|Hodnota statického literálu je určena pomocí metadat inicializace pole. Literál odpovídající specifikaci CLS musí mít hodnotu zadanou v poli Inicializace metadat, která je stejného typu jako literál (nebo základního typu, pokud je literál `enum`).|13|  
|Členové|[Typy členů obecně](#members)|Omezení vararg není částí specifikace CLS a jedinou konvencí volání podporuje specifikace CLS je že standardní spravované konvence volání.|15|  
|Zásady vytváření názvů|[Zásady vytváření názvů](#naming)|Sestavení musí dodržovat přílohu 7 technické zprávy 15 sady Unicode Standard3.0 řídící sadu znaků povolených pro spuštění a být součástí identifikátory, které jsou k dispozici online na <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Identifikátory musí být v kanonickém formátu definovaném v normalizačním formuláři Unicode C. Pro účely specifikace CLS jsou dva identifikátory stejné v případě mapování jejich malých písmen (podle specifikací Unicode národním prostředí, 1: 1 malé písmeno mapování) jsou totožné. To znamená, že dva identifikátory, aby bylo považováno za jiné v rámci specifikace CLS se liší se ve více než jednoduchém případě. Za účelem přepsání zděděné definice však rozhraní příkazového řádku vyžaduje, přesného kódování v původní deklaraci použít.|4|  
|Přetížení|[Zásady vytváření názvů](#naming)|Všechny názvy zavedené v oboru kompatibilní se Specifikací CLS musí být odlišné bez ohledu na typ, s výjimkou případů, kdy jsou názvy shodné a jsou vyřešeny prostřednictvím přetížení. To znamená, že při CTS umožňuje, aby jeden typ používal stejný název pro metodu a pole, CLS to neumožňuje.|5|  
|Přetížení|[Zásady vytváření názvů](#naming)|Pole a vnořené typy musí být různé podle porovnání identifikátoru, i když CTS umožňuje odlišit různé podpisy. Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátoru) se musí lišit více než jen návratovým typem, mimo specifikaci v pravidla 39 CLS.|6|  
|Přetížení|[Overloads](#overloads)|Mohou být přetíženy pouze vlastnosti a metody.|37|  
|Přetížení|[Overloads](#overloads)|Vlastnosti a metody mohou být přetíženy pouze na základě čísla a typů jejich parametrů, s výjimkou operátorů převodu s názvem `op_Implicit` a `op_Explicit`, které mohou také být přetíženy podle jejich návratového typu.|38|  
|Přetížení|--|Pokud mají dvě nebo více kompatibilní se Specifikací CLS metod deklarovaných v typu stejný název a pro konkrétní sadu vytváření instancí typů mají stejný parametr a návratové typy, musí být sémanticky rovnocenné v těchto instancí typů všechny tyto metody.|48|  
|Typy|[Typ a signatury členů typu](#Types)|<xref:System.Object?displayProperty=nameWithType> je kompatibilní se Specifikací CLS. Jiná třída odpovídající specifikaci CLS musí dědit z třídy odpovídající specifikaci CLS.|23|  
|Vlastnosti|[Vlastnosti](#properties)|Metody, které implementují metody getter a setter vlastnosti musí být označeny `SpecialName` v metadatech.|24|  
|Vlastnosti|[Vlastnosti](#properties)|Přistupující objekty vlastnosti musí být statická, virtuální nebo instanční.|26|  
|Vlastnosti|[Vlastnosti](#properties)|Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter. Typy parametrů vlastnosti musí být typy parametrů pro getter a typy všech kromě posledního parametru metodu setter. Všechny tyto typy musí být kompatibilní se Specifikací CLS a nesmí být spravovanými ukazateli (tzn. nesmí být předávány odkazem).|27|  
|Vlastnosti|[Vlastnosti](#properties)|Vlastnosti musí dodržovat zvláštní vzor pro pojmenování. `SpecialName` Podle pravidla specifikace CLS 24 atribut bude ignorován v porovnání s odpovídajícím názvem a musí dodržovat pravidla identifikátoru. Vlastnost musí mít metodu getter a setter metoda.|28|  
|Převod typů|[Převod typů](#conversion)|Pokud `op_Implicit` nebo `op_Explicit` je k dispozici, musí být k dispozici alternativní způsob vynucení.|39|  
|Typy|[Typ a signatury členů typu](#Types)|Pevně určené typy hodnot nejsou kompatibilní se Specifikací CLS.|3|  
|Typy|[Typ a signatury členů typu](#Types)|Všechny typy uvedené v označení musí být kompatibilní se Specifikací CLS. Všechny typy psaní obecného typu musí být kompatibilní se Specifikací CLS.|11|  
|Typy|[Typ a signatury členů typu](#Types)|Typové odkazy nejsou kompatibilní se Specifikací CLS.|14|  
|Typy|[Typ a signatury členů typu](#Types)|Nespravované typy ukazatelů nejsou kompatibilní se Specifikací CLS.|17|  
|Typy|[Typ a signatury členů typu](#Types)|Třídy odpovídající specifikaci CLS, typy hodnot a rozhraní nevyžadují implementaci členů mimo-kompatibilní se Specifikací CLS.|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>Typy a signatury členů typu  
 <xref:System.Object?displayProperty=nameWithType> Typ je kompatibilní se Specifikací CLS a je základní typ pro všechny typy objektů v systému typů rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je buď implicitní (například <xref:System.String> třídy implicitně dědí z <xref:System.Object> třídy) nebo explicitní (například <xref:System.Globalization.CultureNotFoundException> třída dědí explicitně z <xref:System.ArgumentException> třídy, které dědí explicitně z <xref:System.SystemException> třída, která dědí explicitně z <xref:System.Exception> třídy). Odvozený typ vyhovoval specifikaci CLS jeho základní typ musí být kompatibilní se Specifikací CLS.  
  
 Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se Specifikací CLS. Definuje základní `Counter` třídu, která používá nepodepsané 32bitové celé číslo jako čítač. Protože třída poskytuje funkce čítače obalením celého čísla bez znaménka, třída je označena jako bez-kompatibilní se Specifikací CLS. V důsledku toho odvozená třída `NonZeroCounter`, není kompatibilní se Specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 Všechny typy, které se zobrazují v signaturách členu, včetně návratový typ metody nebo vlastnosti typu, musí být kompatibilní se Specifikací CLS. Kromě toho pro obecné typy platí:  
  
-   Všechny typy, které píší obecný typ musí být kompatibilní se Specifikací CLS.  
  
-   Všechny typy použité jako omezení u obecných parametrů musí být kompatibilní se Specifikací CLS.  
  
 Rozhraní .NET Framework [obecný systém typů](../../docs/standard/base-types/common-type-system.md) obsahuje několik předdefinovaných typů, které přímo podporují modul common language runtime a jsou speciálně kódovány v metadatech sestavení. Z těchto vnitřních typů typů uvedených v následující tabulce jsou kompatibilní se Specifikací CLS.  
  
|Typ kompatibilní se Specifikací CLS|Popis|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8bitové celé číslo bez znaménka|  
|<xref:System.Int16>|16bitové celé číslo se znaménkem|  
|<xref:System.Int32>|32bitové celé číslo se znaménkem|  
|<xref:System.Int64>|64bitové celé číslo se znaménkem|  
|<xref:System.Single>|S plovoucí desetinnou čárkou s jednoduchou přesností|  
|<xref:System.Double>|Dvojité přesnosti s plovoucí desetinnou čárkou|  
|<xref:System.Boolean>|`true` nebo `false` typ hodnoty|  
|<xref:System.Char>|Kódová jednotka v kódování UTF-16|  
|<xref:System.Decimal>|Desetinné číslo bez plovoucí desetinné čárky|  
|<xref:System.IntPtr>|Ukazatel nebo popisovač platformou definované velikosti|  
|<xref:System.String>|Kolekce žádným, jedním nebo více <xref:System.Char> objekty|  
  
 Vnitřní typy, které jsou uvedeny v následující tabulce nejsou kompatibilní se Specifikací CLS.  
  
|Nevyhovující typ|Popis|Alternativy CLS|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|8bitové celé číslo se znaménkem datový typ|<xref:System.Int16>|  
|<xref:System.TypedReference>|Ukazatel na objekt a jeho typ runtime|Žádný|  
|<xref:System.UInt16>|16bitové celé číslo bez znaménka|<xref:System.Int32>|  
|<xref:System.UInt32>|32bitové celé číslo bez znaménka|<xref:System.Int64>|  
|<xref:System.UInt64>|64bitové celé číslo bez znaménka|<xref:System.Int64> (může přetéci), <xref:System.Numerics.BigInteger>, nebo <xref:System.Double>|  
|<xref:System.UIntPtr>|Nepodepsaný ukazatel nebo popisovač|<xref:System.IntPtr>|  
  
 Knihovny tříd rozhraní .NET Framework nebo jiná knihovna tříd může obsahovat další typy, které nejsou kompatibilní se Specifikací CLS; Příklad:  
  
-   Pevně určené typy hodnot. Následující příklad jazyka C# vytvoří třídu, která má veřejnou vlastnost typu `int*` s názvem `Value`. Protože `int*` je zabalený typ hodnoty, kompilátor jej označí příznakem jako bez-kompatibilní se Specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
-   Typové odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ. Typové odkazy jsou reprezentovány v rozhraní .NET Framework, tak <xref:System.TypedReference> třídy.  
  
 Pokud typ není kompatibilní se Specifikací CLS, měli byste použít <xref:System.CLSCompliantAttribute> atributem `isCompliant` hodnotu `false` k němu. Další informace najdete v tématu [atribut CLSCompliantAttribute](#CLSAttribute) oddílu.  
  
 Následující příklad ilustruje daný problém dodržování specifikace CLS v podpisu metody a obecný typ instance. Definuje `InvoiceItem` třídu s vlastností typu <xref:System.UInt32>, vlastnost typu `Nullable(Of UInt32)`a konstruktor s parametry typu <xref:System.UInt32> a `Nullable(Of UInt32)`. Při pokusu o kompilaci tohoto příkladu, se čtyři upozornění kompilátoru.  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 Chcete-li vyloučit upozornění kompilátoru, nahraďte kompatibilní se Specifikací neodpovídajících typů v `InvoiceItem` veřejného rozhraní kompatibilními typy:  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 Kromě konkrétních uvedených typů některé kategorie typů nejsou kompatibilní se Specifikací CLS. Patří mezi ně typy nespravovaného ukazatele a typy ukazatelů na funkci. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo, chcete-li vytvořit pole celých čísel.  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 Pro kompatibilní se Specifikací CLS abstraktní třídy (tedy třídy označené jako `abstract` v jazyce C# nebo jako `MustInherit` v jazyce Visual Basic), všichni členové třídy také musí být kompatibilní se Specifikací CLS.  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>Zásady vytváření názvů  
 Protože některé programovací jazyky rozlišují velká a malá písmena, musí identifikátory (například názvy oborů názvů, typů a členů) lišit více než velikostí písmen. Dva identifikátory jsou považovány za rovnocenné, pokud mapování jejich malých písmen jsou stejné. Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person`. Protože se liší pouze velikostí písma, kompilátor jazyka C# je označí příznakem jako není kompatibilní se Specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 Identifikátory programovacího jazyka, jako je například názvy oborů názvů, typů a členů, musí odpovídat [Unicode Standard 3.0, technická zpráva 15, příloha 7](https://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:  
  
-   První znak identifikátoru může být jakékoli Unicode velkým písmenem, malým písmenem, písmenem nadpisu, modifikátor, jiným písmenem nebo číslem. Informace o kategoriích znaků Unicode naleznete v tématu <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> výčtu.  
  
-   Následující znaky mohou být z kategorií jako první znak a může obsahovat také značky bez mezer mezer, kombinované značky, desetinná čísla, interpunkční znaménka konektoru a formátování kódů.  
  
 Než porovnáte identifikátory, měli byste odfiltrovat formátovací kódy a převést identifikátory na normalizační formu Unicode C, protože jeden znak může být reprezentován více jednotkami kódu kódování UTF-16. Sekvence znaků, které vyvolávají stejné jednotky kódu v normalizačním formuláři Unicode C nejsou kompatibilní se Specifikací CLS. Následující příklad definuje vlastnost s názvem `Å`, který se skládá ze znaku ANGSTROM SIGN (U + 212B) a druhé vlastnosti s názvem `Å`, který se skládá ze znaků LATINKY velké písmeno s KROUŽKEM (U + 00 C 5). C# i kompilátory jazyka Visual Basic označí zdrojový kód jako bez-kompatibilní se Specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 Názvy členů v rámci určitého oboru (jako je například obory názvů v rámci sestavení, typy v oboru názvů nebo členy v rámci typu) musí být jedinečné, kromě názvů vyřešených prostřednictvím přetížení. Tento požadavek je přísnější než u systému obecného typu, což umožňuje více členům v rámci oboru mít stejný název, za předpokladu, že jsou různé druhy členů (například jeden je metoda a jeden je pole). Zejména pro členy typu:  
  
-   Pole a vnořené typy se rozlišují podle názvu.  
  
-   Metody, vlastnosti a události, které mají stejný název se musí lišit více než jen návratovým typem.  
  
 Následující příklad ukazuje požadavek, aby názvy členů musely být jedinečné v rámci jejich oboru. Definuje třídu s názvem `Converter` , který obsahuje čtyři členy s názvem `Conversion`. Tři jsou metody a jeden je vlastnost. Metoda, která zahrnuje <xref:System.Int64> parametr je jedinečně pojmenovaná, ale dvě metody s <xref:System.Int32> parametr nejsou, protože vrácená hodnota není považováno za součást podpisu člena. `Conversion` Vlastnost také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které se zaměřují modul CLR musí rovněž poskytnout určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy. Například `case` je klíčové slovo v jazyce C# a Visual Basic. Následující příklad jazyka Visual Basic je však dokáže odlišit třídu s názvem `case` z `case` – klíčové slovo s využitím levé a pravé složené závorky. V opačném případě by v příkladu vytvoří chybová zpráva "Klíčové slovo není platné jako identifikátor" a kompilace selže.  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 Následující příklad jazyka C# je možné vytvořit instanci `case` pomocí `@` symbolů pro rozpoznání identifikátoru z klíčového slova jazyka. Bez něho zobrazí kompilátor jazyka C# dvě chybové zprávy: "Očekáván typ" a "Neplatný výraz pojem"case."  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>Převod typů  
 Common Language Specification definuje dva operátory převodu:  
  
-   `op_Implicit`, který se používá pro rozšiřující převody, při kterých nedojde ke ztrátě dat nebo přesnosti. Například <xref:System.Decimal> struktura obsahuje přetíženou `op_Implicit` operátor pro převod integrálních hodnot a <xref:System.Char> hodnoty <xref:System.Decimal> hodnoty.  
  
-   `op_Explicit`, který se používá pro zužující převody, které můžou vést ke ztrátě velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost. Například <xref:System.Decimal> struktura obsahuje přetíženou `op_Explicit` operátor převodu <xref:System.Double> a <xref:System.Single> hodnoty <xref:System.Decimal> a k převodu <xref:System.Decimal> hodnoty na integrální hodnoty <xref:System.Double>, <xref:System.Single>, a <xref:System.Char>.  
  
 Ale ne všechny jazyky podporují přetěžování nebo definici vlastních operátorů. Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob provedení převodu. Doporučujeme vám, že zadáte `From` *Xxx* a `To` *Xxx* metody.  
  
 Následující příklad definuje odpovídající specifikaci CLS implicitní a explicitní převody. Vytvoří `UDouble` třídu, která představuje podepsané číslo s dvojitou přesností a plovoucí desetinnou čárkou. Poskytuje implicitní převody z `UDouble` k <xref:System.Double> a explicitní převody z `UDouble` k <xref:System.Single>, <xref:System.Double> k `UDouble`, a <xref:System.Single> k `UDouble`. Definuje také `ToDouble` metody jako alternativa k operátoru implicitního převodu a `ToSingle`, `FromDouble`, a `FromSingle` metody jako alternativy k operátorům explicitního převodu.  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>Pole  
 Pole kompatibilní se Specifikací CLS v souladu s těmito pravidly:  
  
-   Všechny dimenze pole musí mít nižší mez nula. Následující příklad vytvoří pole bez-kompatibilní se Specifikací CLS s dolní hranicí jednoho. Všimněte si, že bez ohledu na přítomnost <xref:System.CLSCompliantAttribute> atribut, kompilátor nezjistí, že pole vrácené metodou `Numbers.GetTenPrimes` metoda není kompatibilní se Specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
-   Všechny prvky pole musí obsahovat typy odpovídající specifikaci CLS. Následující příklad definuje dvě metody, které vrací pole bez-kompatibilní se Specifikací CLS. První vrátí matici <xref:System.UInt32> hodnoty. Druhý vrátí <xref:System.Object> pole, které zahrnuje <xref:System.Int32> a <xref:System.UInt32> hodnoty. Ačkoli kompilátor identifikuje první pole jako nevyhovující z důvodu jeho <xref:System.UInt32> typ, není schopna rozpoznat, že druhé pole obsahuje elementy bez-kompatibilní se Specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
-   Rozlišení přetížení pro metody, které mají parametry pole je založeno na skutečnosti, že se jedná o pole a na jejich typu prvku. Z tohoto důvodu se následující definice přetížené `GetSquares` metoda je kompatibilní se Specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Rozhraní  
 Rozhraní odpovídající specifikaci CLS může definovat vlastnosti, události a virtuální metody (metody bez implementace). Kompatibilní se Specifikací CLS rozhraní nemůže mít některý z následujících akcí:  
  
-   Statické metody nebo statická pole. C# i kompilátory jazyka Visual Basic generují chyby kompilátoru při definování statického člena v rozhraní.  
  
-   Pole. C# i kompilátory jazyka Visual Basic generují chyby kompilátoru při definování pole v rozhraní.  
  
-   Metody, které nejsou kompatibilní se Specifikací CLS. Například následující definice rozhraní obsahuje metodu, `INumber.GetUnsigned`, která je označena jako bez-kompatibilní se Specifikací CLS. Tento příklad generuje upozornění kompilátoru.  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     Kvůli tomuto pravidlu není nutné implementovat členy kompatibilní se Specifikací neodpovídajících typy kompatibilní se Specifikací CLS. Pokud rozhraní kompatibilní se Specifikací CLS zpřístupní třídu, která implementuje rozhraní kompatibilním neodpovídající specifikaci CLS, mělo by také poskytovat konkrétní implementace všech členů mimo-kompatibilní se Specifikací CLS.  
  
 Kompilátory jazyka odpovídající specifikaci CLS musí také umožnit třídě poskytnout samostatné implementace členů, kteří mají stejný název a podpis ve více rozhraní.  Podpora jazyka C# i Visual Basic [explicitní implementace rozhraní](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) poskytnout různé implementace identicky pojmenovaných metod. Visual Basic podporuje také `Implements` – klíčové slovo, které umožňuje explicitně určit, které rozhraní a člen určitý člen implementuje. Následující příklad ukazuje tento scénář definováním `Temperature` třídu, která implementuje `ICelsius` a `IFahrenheit` rozhraní jako explicitní implementace rozhraní.  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>Výčty  
 Výčty odpovídající specifikaci CLS musí postupovat podle těchto pravidel:  
  
-   Základní typ výčtu musí být celé číslo kompatibilní se Specifikací CLS vnitřní (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, nebo <xref:System.Int64>). Například následující kód se pokusí definovat výčet, jehož základní typ je <xref:System.UInt32> a generuje upozornění kompilátoru.  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
-   Typ výčtu musí mít jediné pole instance s názvem `Value__` , která je označena <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> atribut. To umožňuje implicitně odkazovat na hodnotu pole.  
  
-   Výčet zahrnuje statické literální pole, jejichž typy odpovídající typu stejný jako daný výčet. Například pokud definujete `State` výčet s hodnotami `State.On` a `State.Off`, `State.On` a `State.Off` jsou obě literální statická pole, jehož typ je `State`.  
  
-   Existují dva typy výčtů:  
  
    -   Výčet, který představuje sadu vzájemně se vylučujících pojmenovaných celočíselných hodnot. Tento typ výčtu se vyznačuje nepřítomností z <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastního atributu.  
  
    -   Výčet, který představuje sadu bitových příznaků, které lze kombinovat a generovat tak nepojmenovanou hodnotu. Tento typ výčtu se vyznačuje přítomnost <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastního atributu.  
  
     Další informace najdete v tématu v dokumentaci <xref:System.Enum> struktury.  
  
-   Hodnota výčtu není omezena na rozsah zadaných hodnot. Jinými slovy rozsah hodnot ve výčtu je oblast jeho základní hodnoty. Můžete použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metodou ke zjištění, zda zadaná hodnota je člen výčtu.  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>Typy členů obecně  
 Common Language Specification vyžaduje všem polím a metodám jako členům určité třídy přístup. Globální statické položky a metody (tedy statické pole nebo metody, které jsou definovány mimo typ) proto nejsou kompatibilní se Specifikací CLS. Pokud se pokusíte zahrnout globální pole nebo metoda ve zdrojovém kódu, C# i Visual Basic vygeneruje chybu kompilátoru.  
  
 Common Language Specification podporuje pouze standardní spravované konvence volání. Nepodporuje podporovány konvence nespravovaného volání a metody se seznamy argumentů proměnných označené `varargs` – klíčové slovo. Seznamy argumentů proměnných, které jsou kompatibilní se standardní spravovanou konvencí volání, použijte <xref:System.ParamArrayAttribute> atribut nebo implementaci jednotlivých jazyků, jako `params` – klíčové slovo v jazyce C# a `ParamArray` – klíčové slovo v jazyce Visual Basic.  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>Usnadnění přístupu člena  
 Přepsání zděděných členů nemůže změnit přístupnost daného člena. Například veřejnou metodu v základní třídě nelze přepsat pomocí soukromé metody v odvozené třídě. Existuje jedna výjimka: `protected internal` (v jazyce C#) nebo `Protected Friend` (v jazyce Visual Basic) člen v jednom sestavení, který je přepsán typem v jiném sestavení. V takovém případě je přístup k přepsání `Protected`.  
  
 Následující příklad ukazuje chybu, která je generován, když <xref:System.CLSCompliantAttribute> atribut je nastaven na `true`, a `Human`, což je třída odvozena z `Animal`, se pokusí změnit dostupnost `Species` vlastnost z veřejné na privátní. Příklad se zkompiluje úspěšně, pokud jeho přístupnost je změněna na veřejné.  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 Typy v signatuře člena musí být přístupné, pokaždé, když se tento člen přístupný. To například znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je privátní, chráněné nebo interní. Následující příklad ukazuje chybu kompilátoru, která způsobí, že když `StringWrapper` konstruktoru třídy poskytuje vnitřní `StringOperationType` hodnota výčtu, která určuje, jak by měl být uzavřen řetězcovou hodnotu.  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>Obecné typy a členy  
 Vnořené typy musí mít vždy alespoň tolik obecných parametrů jako jejich nadřazených typů. Tyto odpovídají podle pozice obecným parametrům nadřazeného typu. Obecný typ může zahrnovat také nové obecné parametry.  
  
 Vztah mezi parametry obecného typu nadřazeného typu a jeho vnořenými typy mohou být skryty pomocí syntaxe jednotlivých jazyků. V následujícím příkladu obecný typ `Outer<T>` obsahuje dvě vnořené třídy, `Inner1A` a `Inner1B<U>`. Volání `ToString` metoda, kterou každá třída dědí z <xref:System.Object.ToString%2A?displayProperty=nameWithType>, ukazují, že jednotlivé vnořené třídy zahrnují parametry typu jeho obsahující třídy.  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 Generické názvy jsou kódovány ve formě *název\`n*, kde *název* je název typu \` znak je literál, a *n* je počet parametry deklarovanými jako typ, nebo v případě vnořených obecných typů počet nově zavedené parametry typu. Toto kódování názvů obecného typu je primárně určeno vývojářům, kteří používají reflexi k přístupu jsou kompatibilní se Specifikací obecné typy v knihovně.  
  
 Pokud platí omezení pro obecný typ, všechny typy použité jako omezení musí být také kompatibilní se Specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass` tedy není kompatibilní se Specifikací CLS a obecnou třídu s názvem `BaseCollection` jejíž typ parametru musí být odvozen od `BaseClass`. Ale protože `BaseClass` není kompatibilní se Specifikací CLS, kompilátor vytvoří upozornění.  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 Pokud obecný typ je odvozen z obecného základního typu, je nutné opětovně deklarovat všechna omezení tak, aby mohli zaručit, že jsou splněny také omezení u základního typu. Následující příklad definuje `Number<T>` , které představují libovolného číselného typu. Definuje také `FloatingPoint<T>` třídu, která představuje hodnotu s plovoucí desetinnou čárkou. Ale zdrojového kódu nejde zkompilovat, protože se nevztahuje omezení na `Number<T>` (T musí být typem hodnoty) na `FloatingPoint<T>`.  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 Příklad se zkompiluje úspěšně, pokud omezení se přidá do `FloatingPoint<T>` třídy.  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Common Language Specification ukládá konzervativní instance modelu pro vnořené typy a chráněné členy. Otevření obecných typů nemůže vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného, chráněného obecného typu. Neobecné typy, které rozšiřují konkrétní vytváření instancí obecné základní třídy nebo rozhraní nemůže vystavovat pole nebo členy s podpisy, které obsahují různé vytváření instancí vnořených chráněných obecných typů.  
  
 Následující příklad definuje obecný typ, `C1<T>` (nebo `C1(Of T)` v jazyce Visual Basic) a chráněnou třídu `C1<T>.N` (nebo `C1(Of T).N` v jazyce Visual Basic). `C1<T>` poskytuje dva způsoby, `M1` a `M2`. Ale `M1` není kompatibilní se Specifikací CLS, protože se pokusí vrátit `C1<int>.N` (nebo `C1(Of Integer).N`) z C1\<T > (nebo `C1(Of T)`). Druhá třída `C2`, je odvozen z `C1<long>` (nebo `C1(Of Long)`). Nabízí dvě metody `M3` a `M4`. `M3` není kompatibilní se Specifikací CLS, protože se pokusí vrátit `C1<int>.N` (nebo `C1(Of Integer).N`) z podtřídy z `C1<long>`. Všimněte si, že kompilátory jazyka mohou být ještě více omezující. V tomto příkladu zobrazí Visual Basic chybu při pokusu o kompilaci `M4`.  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>Konstruktory  
 Konstruktory ve kompatibilní se Specifikací CLS třídách a strukturách musí dodržovat tato pravidla:  
  
-   Konstruktor odvozené třídy musí volat instanci konstruktoru své základní třídy před přístupem ke zděděným datům instance. Tento požadavek je skutečnost, že konstruktory základních tříd nejsou zděděny svými odvozenými třídami. Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.  
  
     Obvykle kompilátory vynucují toto pravidlo nezávisle na dodržení specifikace CLS, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je odvozena od `Person` třídy, ale `Doctor` třídy selže při volání `Person` konstruktoru třídy inicializace zděděných polí instancí.  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
-   S výjimkou vytvoření objektu nelze volat konstruktor objektu. Objekt navíc nelze inicializovat dvakrát. Například to znamená, že <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> a metody deserializace, jako například <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> nesmí volat konstruktory.  
  
<a name="properties"></a>   
### <a name="properties"></a>Vlastnosti  
 Vlastnosti v typech odpovídajících specifikaci CLS musí postupovat podle těchto pravidel:  
  
-   Vlastnost musí mít setter, getter nebo oba. V sestavení, jsou implementovány jako speciální metody, což znamená, že se zobrazí jako samostatné metody (metoda getter má název `get_` *propertyname* a Metoda setter je `set_` *propertyname*) označen jako `SpecialName` v metadatech sestavení. Kompilátory C# a Visual Basic vynutí toto pravidlo automaticky bez nutnosti použít <xref:System.CLSCompliantAttribute> atribut.  
  
-   Typ vlastnosti je návratový typ vlastnosti getter a poslední argument metody setter. Tyto typy musí být kompatibilní se Specifikací CLS a argumenty nelze přiřazovat na vlastnost odkazem (to znamená, že nemůže být spravovanými ukazateli).  
  
-   Pokud je vlastnost getter a setter, musí být oba virtuální, statické, nebo obě instance. C# a kompilátory jazyka Visual Basic automaticky vynutí toto pravidlo prostřednictvím jejich vlastností syntaxe definice.  
  
<a name="events"></a>   
### <a name="events"></a>Události  
 Událost je definována podle názvu a jeho typu. Typ události je delegát, který se používá k označení události. Například <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí je typu <xref:System.ResolveEventHandler>. Kromě samotné události zadat implementaci události tři metody s názvy založenými na názvu události a jsou označeny jako `SpecialName` v metadatech sestavení:  
  
-   Metoda pro přidání obslužné rutiny události s názvem `add_` *EventName*. Například metoda odběru události pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost získá název `add_AssemblyResolve`.  
  
-   Metoda pro odebrání obslužné rutiny události s názvem `remove_` *EventName*. Například metoda odebrání pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost získá název `remove_AssemblyResolve`.  
  
-   Metoda označující, že došlo k události, s názvem `raise_` *EventName*.  
  
> [!NOTE]
>  Většina Common Language Specification pravidla týkající se událostí je implementována pomocí kompilátorů jazyka a je transparentní pro vývojáře komponent.  
  
 Metody pro přidávání, odebírání a vyvolávání události musí mít stejné usnadnění. Musí také všechny být statické, instance, nebo virtuální. Metody pro přidávání a odebírání události mají jeden parametr, jehož typ je typ delegáta události. Metody add a remove musí být přítomen nebo nepřítomny.  
  
 Následující příklad definuje třídu odpovídající specifikaci CLS s názvem `Temperature` , která vyvolává `TemperatureChanged` událost, pokud změna teploty mezi dvěma měřeními rovná nebo překračuje prahovou hodnotu. `Temperature` Třída explicitně definuje `raise_TemperatureChanged` metodu tak, že je možné selektivně provést obslužné rutiny událostí.  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Přetížení  
 Common Language Specification vyžaduje následující požadavky na přetížených členů:  
  
-   Členy můžete přetížit na základě počtu parametrů a typu parametrů. Konvence volání, návratový typ, vlastní modifikátory použité metody nebo jejího parametru a případné předání parametrů podle hodnoty nebo odkazu nejsou považovány za při rozlišování přetížení. Příklad naleznete v tématu kód pro požadavek, aby názvy musí být jedinečné v rámci oboru v [zásady vytváření názvů](#naming) oddílu.  
  
-   Mohou být přetíženy pouze vlastnosti a metody. Pole a události nemohou být přetíženy.  
  
-   Obecné metody lze přetížit na základě počtu jejich obecných parametrů.  
  
> [!NOTE]
>  `op_Explicit` a `op_Implicit` operátory jsou výjimky z pravidla, které vracejí hodnoty není považováno za součást podpisu pro řešení přetížení. Tyto dva operátory můžete přetížit na základě jejich parametrů a jejich návratové hodnoty.  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>Výjimky  
 Objekty výjimky musí být odvozen od <xref:System.Exception?displayProperty=nameWithType> nebo z typu odvozeného z <xref:System.Exception?displayProperty=nameWithType>. Následující příklad ukazuje chybu kompilátoru, která vznikne, když vlastní třída s názvem `ErrorClass` se používá pro zpracování výjimek.  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 Chcete-li opravit tuto chybu, `ErrorClass` třída musí dědit z <xref:System.Exception?displayProperty=nameWithType>. Kromě toho `Message` musí přepsat vlastnost. Následující příklad upravuje tyto chyby pro definování `ErrorClass` třídu, která je kompatibilní se Specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>Atributy  
 V sestaveních.NET Framework vlastní atributy poskytují rozšiřitelné mechanismy pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako je například sestavení, typy, členy a parametry metody. Vlastní atributy musí být odvozen od <xref:System.Attribute?displayProperty=nameWithType> nebo z typu odvozeného z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Následující příklad poruší toto pravidlo. Definuje `NumericAttribute` třídu, která není odvozena od <xref:System.Attribute?displayProperty=nameWithType>. Všimněte si, že k chybě kompilátoru dojde pouze při bez-kompatibilní se Specifikací CLS atributu se použije, ne v případě, že třída je definována.  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 Konstruktor nebo vlastnosti odpovídající specifikaci CLS atributu mohou vystavit pouze následující typy:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Byte>  
  
-   <xref:System.Char>  
  
-   <xref:System.Double>  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int64>  
  
-   <xref:System.Single>  
  
-   <xref:System.String>  
  
-   <xref:System.Type>  
  
-   Libovolný typ výčtu, jehož základní typ je <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, nebo <xref:System.Int64>.  
  
 Následující příklad definuje `DescriptionAttribute` třídu odvozenou od <xref:System.Attribute>. Konstruktor třídy má parametr typu `Descriptor`, takže třída není kompatibilní se Specifikací CLS. Vezměte na vědomí, že kompilátor jazyka C# vysílá varování, ale provede kompilaci úspěšně, zatímco kompilátor jazyka Visual Basic generuje upozornění ani chybu.  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>Atribut CLSCompliantAttribute  
 <xref:System.CLSCompliantAttribute> Atribut se používá k označení, zda prvek programu v souladu s Common Language Specification. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Konstruktor obsahuje jeden povinný parametr, `isCompliant`, který určuje, zda ovládací prvek programu je kompatibilní se Specifikací CLS.  
  
 V době kompilace kompilátor zjistí nekompatibilní prvky, které jsou považovány za kompatibilní se Specifikací CLS a vysílá varování. Kompilátor negeneruje upozornění pro typy nebo členy, které jsou výslovně prohlášeny za nedodržující předpisy.  
  
 Vývojáři komponent mohou používat <xref:System.CLSCompliantAttribute> atribut dvěma způsoby:  
  
-   Chcete-li definovat částí veřejného rozhraní vystavené komponentou, které jsou kompatibilní se Specifikací CLS a části, které nejsou kompatibilní se Specifikací CLS. Pokud atribut slouží k označení určitých prvků programu jako odpovídajících specifikaci CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které se zaměřují na rozhraní .NET Framework.  
  
-   Chcete-li zajistit, aby veřejné rozhraní knihovny součástí zpřístupňuje pouze prvky programu, které jsou kompatibilní se Specifikací CLS. Pokud nejsou prvky odpovídající specifikaci CLS, kompilátory standardně upozornění.  
  
> [!WARNING]
>  V některých případech vynucují kompilátory jazyka odpovídající specifikaci CLS pravidla bez ohledu na to, zda <xref:System.CLSCompliantAttribute> atribut se používá. Například definice statického člena v rozhraní porušuje pravidla specifikace CLS. V tomto ohledu, pokud definujete `static` (v jazyce C#) nebo `Shared` (v jazyce Visual Basic) člen rozhraní, jak kompilátory jazyků C# a Visual Basic zobrazí chybovou zprávu a kompilace aplikace selže.  
  
 <xref:System.CLSCompliantAttribute> Je označena atributem <xref:System.AttributeUsageAttribute> atribut, který má hodnotu <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Tato hodnota vám umožní použít <xref:System.CLSCompliantAttribute> atribut na libovolný prvek programu, včetně sestavení, modulů, typů (tříd, struktur, výčtů, rozhraní a delegátů), zadejte členů (konstruktorů, metody, vlastnosti, pole a události), parametrů, obecných parametrů a návratové hodnoty. V praxi však měli použít atribut pouze na sestavení, typy a členy typu. Jinak kompilátory ignorují atribut a pokračují v generování upozornění překladače pokaždé, když dojde k nevyhovující parametr, obecný parametr nebo vrátí hodnotu do veřejného rozhraní knihovny.  
  
 Hodnota <xref:System.CLSCompliantAttribute> atribut je děděna prvky obsaženého programu. Například pokud je sestavení označeno jako kompatibilní se Specifikací CLS, jeho typy jsou také kompatibilní se Specifikací CLS. Pokud je typ označen jako kompatibilní se Specifikací CLS, jeho vnořené typy a členy jsou také kompatibilní se Specifikací CLS.  
  
 Můžete explicitně přepsat zděděný soulad použitím <xref:System.CLSCompliantAttribute> atribut u obsaženého elementu programu. Například můžete použít <xref:System.CLSCompliantAttribute> atributem `isCompliant` hodnotu `false` definovat nekompatibilní typ ve vyhovujícím sestavení a vy můžete použít atribut s `isCompliant` hodnotu `true` definovat kompatibilní typ v sestavení nevyhovující. Můžete také definovat nekompatibilní členy v kompatibilním typu. Nevyhovující typ však nemůže mít kompatibilní členy, proto nelze použít atribut s `isCompliant` hodnotu `true` k potlačení dědičnosti z nevyhovujícího typu.  
  
 Při vývoji komponentu byste měli vždy používat <xref:System.CLSCompliantAttribute> atribut označuje, zda vaše sestavení, jeho typy a její členy jsou kompatibilní se Specifikací CLS.  
  
 Vytváření komponent odpovídajících specifikaci CLS:  
  
1. Použití <xref:System.CLSCompliantAttribute> označit sestavení jako kompatibilní se Specifikací CLS.  
  
2. Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se Specifikací CLS jako nevyhovující.  
  
3. Označte všechny veřejně vystavené členy v typech odpovídajících specifikaci CLS jako nevyhovující.  
  
4. Poskytnout alternativu odpovídající specifikaci CLS pro členy mimo-kompatibilní se Specifikací CLS.  
  
 Pokud jste úspěšně označili nekompatibilní typy a členy, kompilátor by neměl generovat upozornění na nekompatibilitu. Však vhodné určit členy, které nejsou kompatibilní se Specifikací CLS a seznam jejich alternativ kompatibilní se Specifikací CLS v dokumentaci k produktu.  
  
 V následujícím příkladu <xref:System.CLSCompliantAttribute> atribut pro definování kompatibilní se Specifikací CLS sestavení a typu, `CharacterUtilities`, který má dva členy mimo-kompatibilní se Specifikací CLS. Vzhledem k tomu, že oba členy jsou označeny `CLSCompliant(false)` atribut, kompilátor nevytvoří žádná varování. Třída rovněž poskytuje alternativy CLS pro obě metody. Obvykle bychom jen přidali dvě přetížení k `ToUTF16` metodu k dispozici alternativ odpovídajících specifikaci CLS. Ale vzhledem k tomu, že metody nemohou být přetíženy podle návratové hodnoty, názvy metod odpovídajících specifikaci CLS se liší od názvů nekompatibilních metod.  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 Pokud vyvíjíte aplikaci, nikoli knihovnu (tedy pokud nevystavujete typy nebo členy, které mohou být spotřebovány další vývojáři aplikací), dodržování specifikace CLS u prvků programu, které vaše aplikace využívá službu jsou zajímavé pouze v případě, že je váš jazyk nepodporuje . V takovém případě kompilátor jazyka vygeneruje chybu při pokusu o použití prvku bez-kompatibilní se Specifikací CLS.  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky  
 Jazyková nezávislost má několik možných významů. Jeden význam, který je popsán v článku [jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md), zahrnuje bezproblémové využití typů napsaných v jednom jazyce aplikací v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.  
  
 Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro StringUtil.vb, který obsahuje jeden člen, `ToTitleCase`, ve své třídě `StringLib`.  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů. Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:  
  
```console  
vbc /t:module StringUtil.vb   
```  
  
 Další informace o syntaxi příkazového řádku kompilátoru jazyka Visual Basic najdete v tématu [sestavení z příkazového řádku](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
 Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:  
  
```console  
csc /t:module NumberUtil.cs  
```  
  
 Další informace o syntaxi příkazového řádku kompilátoru jazyka C# najdete v tématu [sestavení příkazového řádku s csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
 Pak použijete [možnosti Linkeru](/cpp/build/reference/linker-options) ke kompilaci dvou modulů do sestavení:  
  
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
  
 Pro kompilaci pomocí jazyka C#, změňte název kompilátoru z **Vbc –** k **csc**a příponu souboru změňte z .vb na .cs:  
  
```console  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.CLSCompliantAttribute>
