---
title: "Jazyková nezávislost a jazykově nezávislé komponenty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc43226a508dfd0286c7667c02bdc2543346be9c
ms.sourcegitcommit: 9c4b8d457ffb8d134c9d55c6d7682a0f22e2b9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/20/2017
---
# <a name="language-independence-and-language-independent-components"></a>Jazyková nezávislost a jazykově nezávislé komponenty
Rozhraní .NET Framework je závislý na jazyce. To znamená, že jako vývojář, můžete vyvíjet v jednom z mnoha jazycích, které cílí na rozhraní .NET Framework, jako je například C#, C + +/ CLI, Eiffel, F #, IronPython, IronRuby, aplikace PowerBuilder, Visual Basic, Visual COBOL a prostředí Windows PowerShell. Můžete přejít na typy a členy vytvořených pro rozhraní .NET Framework, aniž by museli znát jazyk, ve kterém byly se původně zapsán a bez nutnosti postupovat podle některého z původní jazyk konvence knihovny tříd. Pokud jste vývojář součásti, příslušné součásti jsou přístupné kteroukoli aplikací rozhraní .NET Framework, bez ohledu na jeho jazyk.  
  
> [!NOTE]
>  Tato první část Tento článek obsahuje informace o vytvoření jazykově nezávislé komponenty – to znamená, součásti, které mohou být spotřebovávána aplikace, které jsou napsané v libovolném jazyce. Můžete také vytvořit jedna součást nebo aplikace z zdrojový kód napsaný v několika jazycích; v tématu [vzájemná funkční spolupráce mezi jazyky](#CrossLang) v druhé části tohoto článku.  
  
 Plně pracovat s jinými objekty napsané v libovolném jazyce, musí objekty zpřístupnit volajícím jenom ty funkce, které jsou společné pro všechny jazyky. Tato společnou sadu funkcí je definována pomocí specifikace CLS (Common Language), což je sada pravidel, která se týkají vygenerované sestavení. Common Language Specification je definovaný v oddílu I klauzule 7 až 11 [standardy ECMA-335 standardní: Common Language Infrastructure](http://go.microsoft.com/fwlink/?LinkID=116487).  
  
 Pokud vaše součást splňuje Common Language Specification, se musí být kompatibilní se specifikací CLS a je přístupný z kódu v sestavení, které jsou napsané v žádný programovací jazyk, který podporuje specifikaci CLS. Můžete určit, zda příslušné součásti vyhovuje Common Language Specification při kompilaci s použitím <xref:System.CLSCompliantAttribute> atribut ke zdrojovému kódu. Další informace najdete v tématu [atributu CLSCompliantAttribute atribut](#CLSAttribute).  
  
 V tomto článku:  
  
-   [Pravidla dodržování předpisů se specifikací CLS](#Rules)  
  
    -   [Typy a typ člena podpisy](#Types)  
  
    -   [Zásady vytváření názvů](#naming)  
  
    -   [Převod typů](#conversion)  
  
    -   [Pole](#arrays)  
  
    -   [Rozhraní](#Interfaces)  
  
    -   [Výčty](#enums)  
  
    -   [Zadejte obecné členy](#members)  
  
    -   [Člen usnadnění](#MemberAccess)  
  
    -   [Obecné typy a členy](#Generics)  
  
    -   [Konstruktory](#ctors)  
  
    -   [Vlastnosti](#properties)  
  
    -   [Události](#events)  
  
    -   [Přetížení](#overloads)  
  
    -   [Výjimky](#exceptions)  
  
    -   [Atributy](#attributes)  
  
-   [Atributu CLSCompliantAttribute](#CLSAttribute)  
  
-   [Vzájemná funkční spolupráce mezi jazyky](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>Pravidla dodržování předpisů se specifikací CLS  
 Tato část popisuje pravidla pro vytváření komponentu kompatibilní se specifikací CLS. Úplný seznam pravidel, viz oddíl I 11 klauzule [standardy ECMA-335 standardní: Common Language Infrastructure](http://go.microsoft.com/fwlink/?LinkID=116487).  
  
> [!NOTE]
>  Common Language Specification popisuje každé pravidlo pro souladu se specifikací CLS, protože se vztahuje k příjemce (vývojáři, kteří mají přístup prostřednictvím kódu programu komponenty, která je kompatibilní se specifikací CLS), rozhraní (vývojáře, kteří používají k vytvoření kompilátoru jazyka CLS-compliant knihovny) a Extender (vývojáře, kteří jsou vytvoření nástroje, jako je kompilátor jazyka nebo analyzátor kódu, který vytváří kompatibilní se specifikací CLS součásti). Tento článek se zaměřuje na pravidla, protože se vztahují na rozhraní. Všimněte si ale, že některé z pravidel, která se týkají Extender může také použít sestavení, které jsou vytvořené pomocí Reflection.Emit.  
  
 K návrhu komponenty, která je nezávislá na jazyk, stačí použít pravidla pro souladu se specifikací CLS pro veřejné rozhraní příslušné součásti. Implementaci privátní tak, aby odpovídala specifikace nemá.  
  
> [!IMPORTANT]
>  Pravidla pro souladu se specifikací CLS platí pouze pro komponenty veřejné rozhraní, tak, aby jeho privátní implementace.  
  
 Například jiné než nepodepsané celá čísla <xref:System.Byte> nejsou kompatibilní se specifikací CLS. Protože `Person` třída v následujícím příkladu zpřístupňuje `Age` vlastnost typu <xref:System.UInt16>, následující kód zobrazí upozornění kompilátoru.  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 Můžete provést `Person` třídy kompatibilní se specifikací CLS změnou typu `Age` vlastnost z <xref:System.UInt16> k <xref:System.Int16>, který je kompatibilní se specifikací CLS, 16bitové znaménkem. Není nutné změnit typ privátní `personAge` pole.  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 Knihovny veřejné rozhraní se skládá z následujících akcí:  
  
-   Definice třídy veřejné.  
  
-   Definice veřejné členy veřejné třídy a definice členů, které jsou přístupné do odvozených tříd (tedy chráněné členy).  
  
-   Parametry a návratové typy veřejných metod veřejné třídy a parametry a návratové typy metod, které jsou přístupné pro odvozené třídy.  
  
 V následující tabulce jsou uvedena pravidla pro souladu se specifikací CLS. Text tohoto pravidla se provede typu verbatim z [standardy ECMA-335 standardní: Common Language Infrastructure](http://go.microsoft.com/fwlink/?LinkID=116487), což je Copyright 2012 Ecma mezinárodní. Podrobnější informace o těchto pravidel je najít v následujících částech.  
  
|Kategorie|Další informace naleznete v tématu|Pravidlo|Číslo pravidla|  
|--------------|---------|----------|-----------------|  
|Usnadnění|[Člen usnadnění](#MemberAccess)|Usnadnění přístupu se nezmění, pokud přepis zděděných metod, s výjimkou při přepsání metody zděděna z jiného sestavení pomocí usnadnění `family-or-assembly`. V takovém případě přepsání musí mít usnadnění `family`.|10|  
|Usnadnění|[Člen usnadnění](#MemberAccess)|Viditelnost a usnadnění typů a členů musí být tak, že typy v podpis kteréhokoli člena musí být viditelné a dostupné vždy, když je člena samotného viditelné a přístupné. Například veřejnou metodu, která je viditelná mimo jeho sestavení nebude mít argument s typem je viditelná pouze v rámci sestavení. Viditelnost a usnadnění typů skládání instanci obecného typu používá v podpis kteréhokoli člena musí být viditelné a dostupné vždy, když je člena samotného viditelné a přístupné. Například instanci obecného typu součástí podpis člena, který je viditelný mimo jeho sestavení nebude mít obecný argument s typem je viditelná pouze v rámci sestavení.|12|  
|Pole|[Pole](#arrays)|Pole musí obsahovat elementy s typem kompatibilní se specifikací CLS a všechny dimenze pole musí mít dolní meze nula. Pouze skutečnost, že je položka pole a typ elementu pole musí k rozlišení přetížení. Při přetížení je založena na dva nebo více pole typy typy elementů jmenuje typy.|16|  
|Atributy|[Atributy](#attributes)|Atributy musí být typu <xref:System.Attribute?displayProperty=nameWithType>, nebo typu, která dědí z něj.|41|  
|Atributy|[Atributy](#attributes)|Specifikace CLS umožňuje pouze podmnožinu kódování vlastních atributů. Jsou pouze typy, které se zobrazí v těchto kódování (viz oddíl IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , a jakýkoli typ výčtu založený na typu kompatibilní se specifikací CLS základní celé číslo.|34|  
|Atributy|[Atributy](#attributes)|Specifikace CLS neumožňuje veřejně viditelný požadované modifikátory (`modreq`, najdete v oddílu II), ale umožňuje volitelné modifikátory (`modopt`, najdete v oddílu II) nerozumí.|35|  
|Konstruktory|[Konstruktory](#ctors)|Před všechny přístupy dojde k data zděděné instance, musí volat konstruktor k objektu některé instance konstruktoru její základní třída. (To neplatí pro typy hodnot, které nemusí být konstruktory.)|21|  
|Konstruktory|[Konstruktory](#ctors)|K objektu konstruktor nebude volána s výjimkou v rámci vytváření objektu a objekt nebude inicializovat dvakrát.|22|  
|Výčty|[Výčty](#enums)|Podkladový typ výčtového musí být vestavěný typ celé číslo, název pole musí být "value__" a toto pole musí být označen `RTSpecialName`.|7|  
|Výčty|[Výčty](#enums)|Existují dva odlišné typy výčtů, indikován přítomnosti nebo absenci <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastních atributů (viz oddíl IV knihovny). Jeden představuje pojmenovanou celočíselné hodnoty; Další představuje s názvem bitové příznaky, které mohou být kombinovány ke generování nepojmenované hodnotu. Hodnota `enum` není omezeno na zadané hodnoty.|8|  
|Výčty|[Výčty](#enums)|Výčet literálu statické pole musí mít typ výčtu, sám sebe.|9|  
|Události|[Události](#events)|Metody, které implementují událost musí být označen `SpecialName` v themetadata.|29|  
|Události|[Události](#events)|Usnadnění událost a její přístupové objekty musí být stejné.|30|  
|Události|[Události](#events)|`add` a `remove` metody pro buď událost obě musí být přítomen nebo chybí.|31|  
|Události|[Události](#events)|`add` a `remove` metody pro událost každý přijme jeden parametr s typem definuje typ události a musí být odvozen od <xref:System.Delegate?displayProperty=nameWithType>.|32|  
|Události|[Události](#events)|Události musí splňovat specifické vzoru pro pojmenovávání. `SpecialName` Atribut uvedené v pravidle specifikací CLS 29 se ignorují v porovnávání odpovídající název a musí splňovat pravidla identifikátor.|33|  
|Výjimky|[Výjimky](#exceptions)|Objekty, které jsou vyvolány musí být typu <xref:System.Exception?displayProperty=nameWithType> , nebo typu, která dědí z něj. Nicméně kompatibilní se specifikací CLS metody nemusejí blokovat šíření jiných typů výjimek.|40|  
|Obecné|[Souladu se specifikací CLS: pravidla](#Rules)|Specifikací CLS pravidla použít pouze na ty části typu, které jsou přístupné nebo viditelné outsideof definující sestavení.|1|  
|Obecné|[Souladu se specifikací CLS: pravidla](#Rules)|Členové kompatibilní s typy specifikací CLS nebudou označeny za kompatibilní se specifikací CLS.|2|  
|Obecné typy|[Obecné typy a členy](#Generics)|Vnořené typy musí mít alespoň tolik obecné parametry jako nadřazených typů. Obecné parametry ve vnořené typy odpovídají umístěním obecné parametry v jeho nadřazených typů.|42|  
|Obecné typy|[Obecné typy a členy](#Generics)|Název obecného typu se kódovat počet parametrů typu deklarovaná u typu-nested nebo nově zavedených typ, pokud je vnořený podle z pravidel definovaných výše.|43|  
|Obecné typy|[Obecné typy a členy](#Generics)|Obecný typ se redeclare dostatečná omezení, aby zaručil, že žádná omezení na základní typ, nebo rozhraní by vyhovět omezení obecného typu.|4444|  
|Obecné typy|[Obecné typy a členy](#Generics)|Typy používané jako sami omezení obecné parametry musí být kompatibilní se specifikací CLS.|45|  
|Obecné typy|[Obecné typy a členy](#Generics)|Viditelnost a usnadnění přístupu členů (včetně vnořené typy) v instanci obecného typu se považuje být omezená na konkrétní instanci spíše než deklarace obecného typu jako celek. Za předpokladu, že to, viditelnost a usnadnění pravidla se specifikací CLS pravidla 12 stále platit.|46|  
|Obecné typy|[Obecné typy a členy](#Generics)|Pro každou abstraktní nebo virtuální obecné metodu musí být výchozí implementace konkrétní (neabstraktní).|47|  
|Rozhraní|[Rozhraní](#Interfaces)|Kompatibilní se specifikací CLS rozhraní nebude vyžadovat definici-specifikací CLS compliantmethods kvůli jejich implementaci.|18|  
|Rozhraní|[Rozhraní](#Interfaces)|Kompatibilní se specifikací CLS rozhraní nebude definovat statických metod, ani se definování polí.|19|  
|Členové|[Zadejte obecné členy](#members)|Globální statická pole a metody nejsou kompatibilní se specifikací CLS.|36|  
|Členové|--|Pomocí pole inicializace metadat je zadaná hodnota literálu statického. Kompatibilní se specifikací CLS literál musí mít zadaný v metadatech inicializace pole, které je stejného typu jako literál hodnotu (nebo základní typ, pokud je tento literál `enum`).|13|  
|Členové|[Zadejte obecné členy](#members)|Vararg omezení není součástí specifikaci CLS a pouze konvence volání podporuje specifikaci CLS je že standardní spravované konvence volání.|15|  
|Zásady vytváření názvů|[Zásady vytváření názvů](#naming)|Sestavení se řídí přílohy 7 z Technical Report 15 z Standard3.0 znakové sady Unicode, kterými se řídí sadu znaků povolených pro spuštění a být součástí identifikátory, k dispozici onlineat http://www.unicode.org/unicode/reports/tr15/tr15-18.html. Identifikátory musí být ve formátu thecanonical definované Unicode normalizaci formuláře C. Pro účely specifikací CLS, dvě identifiersare stejné, pokud jejich malá mapování (podle národního prostředí nezávislé, jeden toonelowercase mapování Unicode) jsou stejné. To znamená dva identifikátory, aby byla považována za differentunder specifikaci CLS se liší se pouze jejich případě. Ale aby bylo možné přepsat aninherited definice rozhraní příkazového řádku vyžaduje přesné kódování původní deklaraci použít.|4|  
|Přetížení|[Zásady vytváření názvů](#naming)|Všechny názvy, které se zavedly v kompatibilní se specifikací CLS oboru musí být odlišné nezávislé ofkind, s výjimkou případů, kdy jsou názvy identické a vyřešené prostřednictvím přetížení. To znamená, že při CTSallows jeden typ používat stejný název pro metodu a pole specifikaci CLS neexistuje.|5|  
|Přetížení|[Zásady vytváření názvů](#naming)|Vnořené typy a pole musí být odlišné podle porovnání identifikátoru samostatně, eventhough CTS umožňuje odlišné podpisy odlišit. Metody, vlastnosti a eventsthat mít stejný název (podle porovnání identifikátoru) se liší o více než jen návratový typ, s výjimkou zadané v 39 pravidlo specifikací CLS.|6|  
|Přetížení|[Přetížení](#overloads)|Mohou být přetíženy pouze vlastnosti a metody.|37|  
|Přetížení|[Přetížení](#overloads)|Vlastnosti a metody mohou být přetíženy na základě pouze na počtu a typů jejich parametrů, s výjimkou operátory převodu s názvem `op_Implicit` a `op_Explicit`, které mohou také být přetíženy podle jejich návratový typ.|38|  
|Přetížení|--|Pokud dva nebo více kompatibilní se specifikací CLS metody, které jsou deklarované v typu mají stejné nameand, pro konkrétní sadu konkretizací typ nemají stejný parametr a návratové typy, thenall tyto metody musí být v těchto typ konkretizací sémanticky ekvivalentní.|48|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|<xref:System.Object?displayProperty=nameWithType>je kompatibilní se specifikací CLS. Jiná kompatibilní se specifikací CLS třída musí dědit z třídu kompatibilní se specifikací CLS.|23|  
|Vlastnosti|[Vlastnosti](#properties)|Metody, které implementují metody getter a setter shallbe vlastnost označena `SpecialName` v metadatech.|24|  
|Vlastnosti|[Vlastnosti](#properties)|Přístupové objekty vlastnosti musí být statické, virtuální nebo být všechny instance.|26|  
|Vlastnosti|[Vlastnosti](#properties)|Typ vlastnosti musí být návratový typ metoda getter a typ poslední argument nastavovací metoda. Typy parametrů vlastnosti musí být typy parametrů metoda getter a všechny typy, ale konečný parametr nastavovací metoda. Všechny tyto typy musí být kompatibilní se specifikací CLS a nebude spravovaný ukazatele (tj, nebude předání odkazem).|27|  
|Vlastnosti|[Vlastnosti](#properties)|Vlastnosti musí splňovat specifické vzoru pro pojmenovávání. `SpecialName` Atribut podle specifikací CLS pravidlo 24 se ignorují v porovnávání odpovídající název a musí splňovat pravidla identifikátor. Vlastnost má metoda getter a setter metoda.|28|  
|Převod typů|[Převod typů](#conversion)|Pokud má jedna `op_Implicit` nebo `op_Explicit` je zadáno, musí být k dispozici alternativní způsob poskytování převod.|39|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|Pevně určené typy hodnot nejsou kompatibilní se specifikací CLS.|3|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|Všechny typy zobrazovaných v podpis musí být kompatibilní se specifikací CLS. Všechny typy skládání instanci obecného typu musí být kompatibilní se specifikací CLS.|11|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|Typové odkazy nejsou kompatibilní se specifikací CLS.|14|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|Nespravovaný ukazatel typy nejsou kompatibilní se specifikací CLS.|17|  
|Typy|[Zadejte a zadejte signaturách členu](#Types)|Kompatibilní se specifikací CLS třídy, hodnotové typy a rozhraní nebude vyžadovat provádění jiných kompatibilní se specifikací CLS členy.|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>Typy a typ člena podpisy  
 <xref:System.Object?displayProperty=nameWithType> Typ je kompatibilní se specifikací CLS a je základní typ všechny typy objektů v systému typ rozhraní .NET Framework. Dědičnost v rozhraní .NET Framework je buď implicitní (například <xref:System.String> třída implicitně dědí z <xref:System.Object> – třída) nebo explicitní (například <xref:System.Globalization.CultureNotFoundException> třída explicitně dědí z <xref:System.ArgumentException> třídy, které explicitně dědí z <xref:System.SystemException> třídy, která explicitně dědí z <xref:System.Exception> třídy). Odvozený typ jako kompatibilní se specifikací CLS jeho základní typ musí být kompatibilní se specifikací CLS.  
  
 Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se specifikací CLS. Definuje základní `Counter` třídu, která používá jako čítač 32bitové celé číslo bez znaménka. Protože třída poskytuje funkce čítač nástrojem pro zabalení celé číslo bez znaménka, třída je označena jako jiný kompatibilní se specifikací CLS. V důsledku toho odvozené třídy `NonZeroCounter`, je také není kompatibilní se specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 Všechny typy, které se zobrazují v signaturách členu, včetně metoda návratový typ nebo typ vlastnosti musí být kompatibilní se specifikací CLS. Kromě toho pro obecné typy:  
  
-   Všechny typy, které tvoří instanci obecného typu musí být kompatibilní se specifikací CLS.  
  
-   Všechny typy používané jako omezení obecné parametry musí být kompatibilní se specifikací CLS.  
  
 Rozhraní .NET Framework [obecný systém typů](../../docs/standard/base-types/common-type-system.md) zahrnuje několik předdefinovaných typů, které jsou podporované přímo z modulu CLR a speciálně zakódovaným v metadatech sestavení. Z těchto typů vnitřní typy uvedené v následující tabulce jsou kompatibilní se specifikací CLS.  
  
|Kompatibilní se specifikací CLS typu|Popis|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8bitové celé číslo bez znaménka|  
|<xref:System.Int16>|16bitové celé číslo se znaménkem|  
|<xref:System.Int32>|32bitové celé číslo se znaménkem|  
|<xref:System.Int64>|64bitové celé číslo se znaménkem|  
|<xref:System.Single>|Desetinnou čárkou s jednoduchou přesností|  
|<xref:System.Double>|Dvojitá přesnost s plovoucí desetinnou čárkou|  
|<xref:System.Boolean>|`true`nebo `false` typu hodnoty|  
|<xref:System.Char>|Kódování UTF-16 jednotka kódu|  
|<xref:System.Decimal>|Bez plovoucí čárkou desetinné číslo|  
|<xref:System.IntPtr>|Ukazatel nebo popisovač velikosti definované platformy|  
|<xref:System.String>|Kolekce nula, jednu nebo více <xref:System.Char> objekty|  
  
 Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se specifikací CLS.  
  
|Nekompatibilní typ|Popis|Kompatibilní se specifikací CLS alternativní|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|datový typ 8bitové celé číslo se znaménkem|<xref:System.Int16>|  
|<xref:System.TypedReference>|Ukazatel na objekt a její typ modulu runtime|Žádné|  
|<xref:System.UInt16>|16bitové celé číslo bez znaménka|<xref:System.Int32>|  
|<xref:System.UInt32>|32bitové celé číslo bez znaménka|<xref:System.Int64>|  
|<xref:System.UInt64>|64bitové celé číslo bez znaménka|<xref:System.Int64>(může přetečení), <xref:System.Numerics.BigInteger>, nebo<xref:System.Double>|  
|<xref:System.UIntPtr>|Nepodepsané ukazatel nebo popisovač|<xref:System.IntPtr>|  
  
 Knihovna tříd rozhraní .NET Framework nebo jiné knihovny tříd mohou zahrnovat jiné typy, které nejsou kompatibilní se specifikací CLS; například:  
  
-   Pevně určené typy hodnot. Následující příklad jazyka C# vytvoří třídy, která má veřejná vlastnost typu `int*` s názvem `Value`. Protože `int*` je typu zabalené hodnoty kompilátor flags se jako jiný kompatibilní se specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
-   Typové odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ. Typové odkazy jsou reprezentována v rozhraní .NET Framework pomocí <xref:System.TypedReference> třídy.  
  
 Pokud typ není kompatibilní se specifikací CLS, byste měli použít <xref:System.CLSCompliantAttribute> atribut s `isCompliant` hodnotu `false` k němu. Další informace najdete v tématu [atributu CLSCompliantAttribute atribut](#CLSAttribute) části.  
  
 Následující příklad ilustruje problém v podpis metody a vytváření instancí obecného typu se specifikací CLS. Definuje, `InvoiceItem` s vlastností typu <xref:System.UInt32>, vlastnost typu `Nullable(Of UInt32)`a konstruktor s parametry typu <xref:System.UInt32> a `Nullable(Of UInt32)`. Při pokusu o zkompilování tohoto příkladu získáte čtyři upozornění kompilátoru.  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 Chcete-li eliminovat upozornění kompilátoru, nahraďte jiný kompatibilní se specifikací CLS typy v `InvoiceItem` veřejné rozhraní s kompatibilní s typy:  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 Kromě konkrétní typy uvedený některé jsou typy není kompatibilní se specifikací CLS. Mezi ně patří nespravovaný ukazatel typy a typy ukazatel funkce. Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo pro vytvoření pole celých čísel.  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 Pro kompatibilní se specifikací CLS abstraktní třídy (tedy třídy označeny jako `abstract` v jazyce C# nebo jako `MustInherit` v jazyce Visual Basic), všichni členové třídy také musí být kompatibilní se specifikací CLS.  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>Zásady vytváření názvů  
 Vzhledem k tomu, že některé programovací jazyky jsou velká a malá písmena, identifikátory (například názvy oborů názvů, typy a členy) se musí lišit o více než případ. Dva identifikátory jsou považovány za ekvivalentní, pokud jejich malá mapování jsou stejné. Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person`. Protože se liší pouze v případě, kompilátor jazyka C# je označí jako není kompatibilní se specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 Programovací jazyk identifikátory, třeba názvů obory názvů, typy a členy, musí odpovídat [Unicode Standard 3.0, technické sestavy 15, přílohy 7](http://www.unicode.org/reports/tr15/tr15-18.html). To znamená, že:  
  
-   První znak identifikátoru můžete být žádné Unicode velké písmeno, malé písmeno, malá písmena title, modifikátor, jiné písmeno nebo číslo písmeno. Informace o kategoriích znakové sady Unicode, najdete v článku <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> výčtu.  
  
-   Následující znaky mohou být ze všech kategorií jako první znak a může také obsahovat bez mezer značky, mezer kombinování značky, desetinná čísla, spojovací interpunkci a formátování kódy.  
  
 Předtím, než můžete porovnat identifikátory, musí odfiltrovat formátování kódy a převést identifikátory Unicode normalizaci formuláře C, protože jeden znak může být reprezentovaný víc jednotek kódu kódování UTF-16. Sekvence znaků, které produkují stejné jednotky kódu v jazyce C formuláře normalizaci Unicode nejsou kompatibilní se specifikací CLS. V následujícím příkladu definuje vlastnost s názvem `Å`, která zahrnuje znaku značka ANGSTROM (U + 212B) a druhý vlastnost s názvem `Å`, který se skládá z znak LATIN velké písmeno A s PRSTENEC nad (U + 00 C 5). C# i kompilátory jazyka Visual Basic příznak zdrojový kód jako jiný kompatibilní se specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 Názvy členů v konkrétním oboru (například obory názvů v rámci sestavení, typů v rámci oboru názvů nebo členy v rámci typu) musí být jedinečný, s výjimkou názvy, které se vyřeší prostřednictvím přetížení. Tento požadavek je přísnější než obecný systém typů, která umožňuje více členů v rámci oboru mít identické názvy, dokud jsou různé druhy členy (například jeden je metoda a jedna je pole). Konkrétně pro členy typu:  
  
-   Vnořené typy a pole jsou rozlišené název samostatně.  
  
-   Metody, vlastnosti a události, které mají stejný název se musí lišit o více než jen návratový typ.  
  
 Následující příklad ilustruje požadavek, že názvy členů musí být jedinečný v rámci svého oboru. Definuje třídu s názvem `Converter` , který obsahuje čtyři členy s názvem `Conversion`. Tři způsoby, a jedna je vlastnost. Metoda, která zahrnuje <xref:System.Int64> parametr je jednoznačně s názvem, ale tyto dvě metody s <xref:System.Int32> parametr nejsou, protože návratová hodnota není součástí podpis člena. `Conversion` Vlastnost také porušuje tento požadavek, protože vlastnosti nemůže mít stejný název jako přetížené metody.  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 Jednotlivé jazyky zahrnují jedinečný klíčová slova, takže jazyky cílených modul common language runtime nutné také zadat některé mechanismus pro odkazování identifikátorů (například názvy typů), který se shoduje s klíčová slova. Například `case` je klíčové slovo v jak C# a Visual Basic. Následující příklad jazyka Visual Basic je však možné kvůli zajištění jednoznačnosti třídy s názvem `case` z `case` – klíčové slovo pomocí otvírání a zavírání složené závorky. V příkladu by jinak chybová zpráva, "– klíčové slovo není platný jako identifikátor," a nepovede zkompilovat.  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 Následující příklad jazyka C# je možné vytvořit instanci `case` pomocí `@` symbol, který má-li odstranit nejednoznačnost identifikátor z klíčové slovo jazyka. Bez toho by kompilátor jazyka C# zobrazí dvě chybové zprávy, "Očekáván typ" a "Neplatný výraz výraz 'case'."  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>Převod typů  
 Common Language Specification definuje dva operátory převodu:  
  
-   `op_Implicit`, který se používá pro rozšiřující převody, které není dojít ke ztrátě dat nebo přesnosti. Například <xref:System.Decimal> struktura zahrnuje přetížené `op_Implicit` operátor k převedení hodnoty celočíselných typů a <xref:System.Char> hodnoty k <xref:System.Decimal> hodnoty.  
  
-   `op_Explicit`, který se používá pro zúžení převodů, které může dojít ke ztrátě velikosti (hodnota je převést na hodnotu, která má menší oblast) nebo přesnosti. Například <xref:System.Decimal> struktura zahrnuje přetížené `op_Explicit` operátor převést <xref:System.Double> a <xref:System.Single> hodnoty k <xref:System.Decimal> a převést <xref:System.Decimal> hodnoty celočíselné hodnoty, <xref:System.Double>, <xref:System.Single>, a <xref:System.Char>.  
  
 Ne všechny jazyky však podporovat přetížení operátoru nebo definici vlastní operátory. Pokud zvolíte možnost implementovat tyto operátory převodu, musí zadat jiný způsob, jak provést převod. Doporučujeme, aby poskytovaly `From` *Xxx* a `To` *Xxx* metody.  
  
 V následujícím příkladu definuje implicitní a explicitní převody kompatibilní se specifikací CLS. Vytvoří `UDouble` třídu, která představuje podepsaný číslo s dvojitou přesností a s plovoucí desetinnou čárkou. Poskytuje pro implicitní převody z `UDouble` k <xref:System.Double> a explicitní převody z `UDouble` k <xref:System.Single>, <xref:System.Double> k `UDouble`, a <xref:System.Single> k `UDouble`. Také definuje `ToDouble` metoda jako alternativu k operátor implicitní převod a `ToSingle`, `FromDouble`, a `FromSingle` metody jako alternativy operátory explicitního převodu.  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>Pole  
 Kompatibilní se specifikací CLS pole splňovat následující pravidla:  
  
-   Všechny dimenze pole musí mít dolní mez 0. Následující příklad vytvoří jiný kompatibilní se specifikací CLS pole s dolní mez jednoho. Všimněte si, že, bez ohledu na přítomnost <xref:System.CLSCompliantAttribute> atribut kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metoda není kompatibilní se specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
-   Všechny elementy pole musí obsahovat typy kompatibilní se specifikací CLS. V následujícím příkladu definuje dvě metody, které vrátí pole jiný kompatibilní se specifikací CLS. Vrátí první pole <xref:System.UInt32> hodnoty. Druhý vrátí <xref:System.Object> pole, která zahrnuje <xref:System.Int32> a <xref:System.UInt32> hodnoty. I když kompilátor identifikuje první pole jako nevyhovující z důvodu jeho <xref:System.UInt32> typu, se nezdaří rozpoznat, že pole druhý obsahuje prvky jiný kompatibilní se specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
-   Řešení přetížení metody, které mají parametry pole je na základě toho, že jsou pole a na jejich typ elementu. Z tohoto důvodu následující definice přetížené `GetSquares` metoda je kompatibilní se specifikací CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Rozhraní  
 Kompatibilní se specifikací CLS rozhraní můžete definovat vlastnosti, události a virtuální metody (metody s žádnou implementaci). Rozhraní, které je kompatibilní se specifikací CLS nemůže mít některé z následujících:  
  
-   Statické metody nebo statických polí. C# i kompilátory jazyka Visual Basic vygenerovat chyby kompilátoru, pokud je statický člen definujete v rozhraní.  
  
-   Pole. C# i kompilátory jazyka Visual Basic vytvořit chyby kompilátoru, když definujete pole v rozhraní.  
  
-   Metody, které nejsou kompatibilní se specifikací CLS. Například následující definice rozhraní obsahuje metody, `INumber.GetUnsigned`, která je označena jako jiný kompatibilní se specifikací CLS. Tento příklad vytvoří upozornění kompilátoru.  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     Podle tohoto pravidla není nutné kompatibilní se specifikací CLS typy implementace jiných kompatibilní se specifikací CLS členů. Pokud kompatibilní se specifikací CLS framework vystavit třídu, která implementuje rozhraní kompatibilní-specifikací CLS, se musí zadat konkrétní implementace všech členů jiný kompatibilní se specifikací CLS.  
  
 Kompilátory jazyka kompatibilní se specifikací CLS musíte také povolit třídu zajistit samostatné implementace členů, které nemají se stejným názvem a podpis ve více rozhraní.  Jak C# a Visual Basic podporu [explicitní implementace rozhraní](~/docs/csharp/programming-guide/interfaces/explicit-interface-implementation.md) zajistit různými implementacemi stejně jako s názvem metod. Visual Basic podporuje také `Implements` implementuje – klíčové slovo, které umožňuje provádět explicitně určit které rozhraní a člen konkrétní člena. Následující příklad ilustruje tento scénář tak, že definujete `Temperature` třídu, která implementuje `ICelsius` a `IFahrenheit` rozhraní jako explicitní implementace rozhraní.  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>Výčty  
 Kompatibilní se specifikací CLS výčty nutné postupovat podle těchto pravidel:  
  
-   Základní typ výčtu musí být celé vnitřní kompatibilní se specifikací CLS (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, nebo <xref:System.Int64>). Například následující kód pokusí definovat výčet jejíž základní typ je <xref:System.UInt32> a vygeneruje upozornění kompilátoru.  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
-   Typ výčtu musí mít jednu instanci pole s názvem `Value__` , je označené <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> atribut. Můžete tak, aby odkazovaly hodnota pole implicitně.  
  
-   Výčet obsahuje literál statická pole, jejichž typy shodovat s typem výčtu sám sebe. Například pokud definujete `State` výčtu s hodnotami `State.On` a `State.Off`, `State.On` a `State.Off` jsou obě literálu statické pole s typem `State`.  
  
-   Existují dva druhy výčty:  
  
    -   Výčet, který představuje sadu navzájem vylučují s názvem celočíselné hodnoty. Tento typ výčtu je indikován absenci <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastních atributů.  
  
    -   Výčet, který představuje sadu bitové příznaky, které můžete kombinovat ke generování nepojmenované hodnotu. Tento typ výčtu je indikován přítomnost <xref:System.FlagsAttribute?displayProperty=nameWithType> vlastních atributů.  
  
     Další informace najdete v dokumentaci pro <xref:System.Enum> struktura.  
  
-   Hodnota výčtu není omezen na rozsah jeho zadané hodnoty. Jinými slovy rozsahu hodnot v výčet je rozsah jeho základní hodnoty. Můžete použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metoda k určení, zda je zadaná hodnota člena výčtu.  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>Zadejte obecné členy  
 Common Language Specification vyžaduje všechna pole a metody pro přístupná jako členy určité třídy. Globální statická pole a metody (tedy statických polí nebo metod, které jsou definovány kromě typu) proto nejsou kompatibilní se specifikací CLS. Pokud se pokusíte zahrnout globální pole nebo metoda ve zdrojovém kódu, jak C# a Visual Basic kompilátory vygenerována chyba kompilátoru.  
  
 Common Language Specification podporuje jenom standardní spravovaných konvence volání. Nepodporuje nespravované konvence volání a metody s seznam argumentů s proměnnou délkou označené jako `varargs` – klíčové slovo. Seznamy argumentů proměnných, které jsou kompatibilní s standardní spravované konvence volání, použijte <xref:System.ParamArrayAttribute> atribut nebo implementace tohoto jazyka, jako `params` – klíčové slovo v jazyce C# a `ParamArray` – klíčové slovo v jazyce Visual Basic.  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>Člen usnadnění  
 Přepsání zděděného členu nelze změnit pro usnadnění tohoto člena. Veřejná metoda v základní třídě například nelze přepsat privátní metoda v odvozené třídě. Existuje jedna výjimka: `protected internal` (v jazyku C#) nebo `Protected Friend` (v jazyce Visual Basic) člena v jedné sestavení, které je přepsat typu v jiném sestavení. V takovém případě je usnadnění mají přednost před `Protected`.  
  
 Následující příklad ukazuje chybu, která je generováno v případě <xref:System.CLSCompliantAttribute> je atribut nastaven na `true`, a `Person`, což je třída odvozená z `Animal`, pokusí změnit usnadnění přístupu `Species` vlastnost z veřejné do privátního. V příkladu zkompiluje úspěšně, pokud jeho usnadnění se změní na veřejné.  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 Typy v podpis člena musí být přístupné, vždy, když je dostupný tohoto člena. Například to znamená, že veřejné člena nelze zahrnout parametr, jehož typ je soukromý, chráněný nebo interní. Následující příklad ilustruje Chyba kompilátoru, která způsobí, že když `StringWrapper` konstruktoru třídy zpřístupní interní `StringOperationType` hodnota výčtu, která určuje, jak by měl být uzavřen hodnotu řetězce.  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>Obecné typy a členy  
 Vnořené typy mít vždy alespoň tolik obecné parametry jako názvy jejich nadřazených typů. Tyto odpovídají umístěním obecné parametry v nadřazených typů. Obecný typ dále můžete přidat nové obecné parametry.  
  
 Vztah mezi parametry obecného typu obsahující typu a jeho vnořené typy může být skrytý na základě syntaxe jednotlivé jazyky. V následujícím příkladu, obecného typu `Outer<T>` obsahuje dvě vnořené třídy `Inner1A` a `Inner1B<U>`. Volání `ToString` metodu, která každá třída dědí z <xref:System.Object.ToString%2A?displayProperty=nameWithType>, zobrazit, že každý vnořené třídy obsahuje parametry typu jeho obsahující třídy.  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 Ve formuláři jsou zakódovány obecného typu názvy *název\`n*, kde *název* je název typu \` znak je literál, a  *n*  je počet parametrů deklarovaná u typu nebo pro vnořené obecné typy, počet parametrů nově přináší typu. Toto kódování obecného typu názvy je primárně určen pro vývojáře, kteří pomocí reflexe kompatibilní se specifikací CLS obecné typy v knihovně.  
  
 Pokud omezení se použijí pro obecný typ, všechny typy používané jako omezení také musí být kompatibilní se specifikací CLS. Následující příklad definuje třídu s názvem `BaseClass` není kompatibilní se specifikací CLS a obecné třídy s názvem `BaseCollection` jehož typ parametru musí být odvozeny od `BaseClass`. Ale protože `BaseClass` není kompatibilní se specifikací CLS, kompilátor vydá upozornění.  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 Pokud obecný typ je odvozen od obecného typu základní, musí ho redeclare žádná omezení, tak, aby může zaručit, že jsou splněny také omezení u základního typu. V následujícím příkladu definuje `Number<T>` , může představovat libovolný číselného typu. Také definuje `FloatingPoint<T>` třídu, která představuje plovoucí bodu hodnotu. Ale zdrojového kódu se nepovede zkompilovat, protože jej nelze použít omezení na `Number<T>` (aby T musí být hodnota typu) k `FloatingPoint<T>`.  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 V příkladu zkompiluje úspěšně Pokud omezení je přidán do `FloatingPoint<T>` třídy.  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Common Language Specification ukládá konzervativní za konkretizaci model pro vnořené typy a chráněné členy. Otevřete obecné typy nemůže vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořené, chráněné obecného typu. Non obecné typy, které rozšiřují konkrétní instanci obecné základní třídy nebo rozhraní nemůže vystavovat pole nebo členy s podpisy, které obsahují různé konkretizaci vnořené, chráněné obecného typu.  
  
 V následujícím příkladu definuje obecného typu `C1<T>` (nebo `C1(Of T)` v jazyce Visual Basic) a chráněná třída `C1<T>.N` (nebo `C1(Of T).N` v jazyce Visual Basic). `C1<T>`má dvě metody, `M1` a `M2`. Ale `M1` není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` (nebo `C1(Of Integer).N`) objekt z C1\<T > (nebo `C1(Of T)`). Třídu sekundu `C2`, je odvozený od `C1<long>` (nebo `C1(Of Long)`). Nabízí dvě metody, `M3` a `M4`. `M3`není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` (nebo `C1(Of Integer).N`) objekt z podtřídou třídy `C1<long>`. Všimněte si, že můžou být i víc omezující kompilátory jazyka. V tomto příkladu jazyka Visual Basic zobrazí chybu při pokusu o zkompilovat `M4`.  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>Konstruktory  
 Konstruktory v kompatibilní se specifikací CLS třídy a struktury nutné postupovat podle těchto pravidel:  
  
-   Konstruktoru odvozené třídy musí volat konstruktoru instance její základní třída před přistupuje k data zděděné instance. Tento požadavek je skutečnost, že jejich odvozených tříd nejsou zdědí konstruktory základní třídy. Toto pravidlo se nevztahuje na struktury, které nepodporují přímý dědičnosti.  
  
     Kompilátory obvykle vynutit toto pravidlo nezávisle na souladu se specifikací CLS, jak ukazuje následující příklad. Vytvoří `Doctor` třídu, která je odvozená od `Person` třídy, ale `Doctor` třída nepodaří volání `Person` konstruktoru třídy k chybě při inicializaci instance zděděné pole.  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
-   S výjimkou vytvoření objektu nelze volat konstruktor k objektu. Objekt kromě toho nelze inicializovat dvakrát. Například to znamená, že <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> a metody, jako deserializace <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> konstruktory nesmějí provádět volání.  
  
<a name="properties"></a>   
### <a name="properties"></a>Vlastnosti  
 Vlastnosti v kompatibilní se specifikací CLS typy nutné postupovat podle těchto pravidel:  
  
-   Vlastnost musí mít setter, příjemce nebo obojí. V sestavení, ty jsou implementované jako speciální metody, což znamená, že se zobrazí jako samostatné metody (metoda getter jmenuje `get_` *propertyname* a nastavovací metoda je `set_` *propertyname*) označeno `SpecialName` v metadat sestavení. Kompilátory jazyka C# a Visual Basic vynutit toto pravidlo automaticky bez nutnosti použít <xref:System.CLSCompliantAttribute> atribut.  
  
-   Typ vlastnost je návratový typ metoda getter vlastnosti a poslední argument nastavovací metoda. Tyto typy musí být kompatibilní se specifikací CLS a argumenty nelze přiřadit k vlastnosti podle reference (to znamená, že nemůže být spravované ukazatele).  
  
-   Pokud vlastnost má metoda getter a setter, musí být obě virtuální, statické, nebo obě instance. C# a Visual Basic kompilátory automaticky vynutit toto pravidlo prostřednictvím jejich vlastnosti definice syntaxe.  
  
<a name="events"></a>   
### <a name="events"></a>Události  
 Událost je definována podle názvu a jeho typu. Typ události je delegáta, který slouží k označení události. Například <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí je typu <xref:System.ResolveEventHandler>. Kromě samotné události tři metody s názvy na základě názvu událostí zadejte implementace události a jsou označeny jako `SpecialName` v metadat sestavení:  
  
-   Metoda pro přidání obslužné rutiny události, s názvem `add_` *EventName*. Například metoda předplatného události pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí jmenuje `add_AssemblyResolve`.  
  
-   Metoda pro odebrání obslužné rutiny události, s názvem `remove_` *EventName*. Například metoda odebrání pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí jmenuje `remove_AssemblyResolve`.  
  
-   Metoda pro označující, že došlo k události, název `raise_` *EventName*.  
  
> [!NOTE]
>  Většina Common Language Specification pravidla týkající se událostí jsou implementované kompilátory jazyka a jsou transparentní pro vývojáře součásti.  
  
 Metody pro přidání, odebrání a vyvolání události musí mít stejné usnadnění. Musí také všechny být statické, instanci, nebo virtuální. Metody pro přidávání a odebírání událost mít jeden parametr, jehož typ je typ delegáta události. Obě metody přidat a odebrat musí být přítomen nebo obě chybět.  
  
 V následujícím příkladu definuje kompatibilní se specifikací CLS třídy s názvem `Temperature` , vyvolá `TemperatureChanged` událost, pokud změnu v hodnotě teploty mezi dvěma odečty rovná nebo překračuje prahovou hodnotu. `Temperature` Třída explicitně definuje `raise_TemperatureChanged` metoda proto to můžete provést selektivní obslužné rutiny událostí.  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Přetížení  
 Common Language Specification ukládá tyto požadavky na přetěžované členy:  
  
-   Členové mohou být přetíženy na základě počtu parametrů a typ libovolný parametr. Konvence, návratový typ volání vlastní modifikátory použít pro metodu nebo její parametr, a zda jsou parametry předány hodnotou nebo odkazem nejsou považovány za při rozlišování přetížení. Příklad, naleznete v části kód pro požadavek na názvy musí být jedinečný v rámci oboru v [konvence vytváření názvů](#naming) části.  
  
-   Mohou být přetíženy pouze vlastnosti a metody. Nemohou být přetíženy pole a události.  
  
-   Obecné metody mohou být přetíženy na základě počtu jejich obecné parametry.  
  
> [!NOTE]
>  `op_Explicit` a `op_Implicit` operátory jsou výjimky pro pravidlo, které vrací hodnotu není považovány za součást podpis metody pro rozlišení přetížení. Tyto dva operátory mohou být přetíženy na základě jejich parametrů a jejich návratovou hodnotu.  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>Výjimky  
 Objekty výjimek musí být odvozeny od <xref:System.Exception?displayProperty=nameWithType> nebo z jiného typu odvozeného z <xref:System.Exception?displayProperty=nameWithType>. Následující příklad ilustruje Chyba kompilátoru, který nastane, když vlastní třídu s názvem `ErrorClass` se používá pro zpracování výjimek.  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 Tuto chybu `ErrorClass` třída musí dědit z <xref:System.Exception?displayProperty=nameWithType>. Kromě toho `Message` vlastností se musí přepsat. Následující příklad vyřeší tyto chyby můžete definovat `ErrorClass` třída, která je kompatibilní se specifikací CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>Atributy  
 Sestavení In.NET architektury, vlastní atributy poskytují mechanismus extensible pro vlastní atributy ukládání a načítání metadat o programování objekty, například sestavení, typy, členů a parametry metody. Vlastní atributy musí být odvozeny od <xref:System.Attribute?displayProperty=nameWithType> nebo z typu odvozeného z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Toto pravidlo je v rozporu v následujícím příkladu. Definuje `NumericAttribute` třídu, která není odvozena od <xref:System.Attribute?displayProperty=nameWithType>. Všimněte si, že chyba kompilátoru výsledky, pouze když jiný kompatibilní se specifikací CLS atribut se použije, ne v případě, že je třída definovaná.  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 V konstruktoru nebo z vlastností kompatibilní se specifikací CLS atributu můžou zpřístupnit pouze následující typy:  
  
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
  
 V následujícím příkladu definuje `DescriptionAttribute` třídu odvozenou od <xref:System.Attribute>. Konstruktoru třídy má parametr typu `Descriptor`, takže třída není kompatibilní se specifikací CLS. Všimněte si, že kompilátor jazyka C# vydá upozornění ale zkompiluje úspěšně, zatímco Visual Basic – kompilátor vydá upozornění ani chyby.  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>Atributu CLSCompliantAttribute  
 <xref:System.CLSCompliantAttribute> Atribut slouží k označení, zda je program element v souladu s Common Language Specification. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Konstruktor obsahuje jeden požadovaný parametr `isCompliant`, která určuje, zda je program element kompatibilní se specifikací CLS.  
  
 Při kompilaci kompilátor zjistí nevyhovující prvky, které se předpokládá, že se kompatibilní se specifikací CLS a vydá upozornění. Kompilátor není emitování upozornění pro typy nebo členy, kteří jsou explicitně deklarované jako nevyhovující.  
  
 Součást vývojáři mohou použít <xref:System.CLSCompliantAttribute> atribut dvěma způsoby:  
  
-   Chcete-li definovat části veřejné rozhraní vystavené součásti, které jsou kompatibilní se specifikací CLS a částí, které nejsou kompatibilní se specifikací CLS. Pokud atribut slouží k označení určitého programu elementy jako kompatibilní se specifikací CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástroje, které cílí na rozhraní .NET Framework.  
  
-   K zajištění, že součást knihovny veřejné rozhraní zpřístupní pouze program prvky, které jsou kompatibilní se specifikací CLS. Pokud elementů nejsou kompatibilní se specifikací CLS, kompilátory obecně vydá upozornění.  
  
> [!WARNING]
>  V některých případech kompilátory jazyka vynutit kompatibilní se specifikací CLS pravidla bez ohledu na to, jestli <xref:System.CLSCompliantAttribute> je použit atribut. Například definování je statický člen v rozhraní porušuje pravidlo specifikací CLS. V tomto ohledu, pokud definujete `static` (v jazyku C#) nebo `Shared` (v jazyce Visual Basic) člena v rozhraní, jak kompilátory jazyka C# a Visual Basic, zobrazí se chybová zpráva a selhání kompilace aplikace.  
  
 <xref:System.CLSCompliantAttribute> Atribut je označen jako s <xref:System.AttributeUsageAttribute> atribut, který má hodnotu <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Tuto hodnotu můžete použít <xref:System.CLSCompliantAttribute> atribut žádné program elementu, včetně sestavení, moduly, typy (třídy, struktury, výčty, rozhraní a delegáti), zadejte členy (konstruktory, metody, vlastnosti, pole a události) parametry, obecné parametry a návratové hodnoty. Ale v praxi by se měly používat atribut pouze pro sestavení, typy a členy typu. Kompilátory, jinak hodnota ignorovat atribut a dále generovat upozornění kompilátoru, kdykoli se dojde k nevyhovující parametr, obecný parametr nebo vrátí hodnotu v veřejné rozhraní své knihovny.  
  
 Hodnota <xref:System.CLSCompliantAttribute> atribut zdědí prvky obsažené programu. Například pokud sestavení je označen jako kompatibilní se specifikací CLS, jeho typy jsou také kompatibilní se specifikací CLS. Pokud typ je označena jako kompatibilní se specifikací CLS, jeho vnořené typy a členy, jsou také kompatibilní se specifikací CLS.  
  
 Zděděné dodržování předpisů můžete přepsat explicitně použitím <xref:System.CLSCompliantAttribute> atribut elementu obsažené programu. Například můžete použít <xref:System.CLSCompliantAttribute> atribut s `isCompliant` hodnotu `false` k definování typu nevyhovující v kompatibilní sestavení a vy můžete použít atribut s `isCompliant` hodnotu `true` k definování typu kompatibilní v nekompatibilní sestavení. Můžete také definovat nevyhovující členů v typu kompatibilní. Však nekompatibilní typ nemůže mít členy kompatibilní, proto nemůžete použít atribut s `isCompliant` hodnotu `true` přepsat dědičnost z typu nevyhovující.  
  
 Při vývoji součásti, byste měli vždycky používat <xref:System.CLSCompliantAttribute> atribut označuje, zda je kompatibilní se specifikací CLS vaše sestavení, jeho typy a její členy.  
  
 Chcete-li vytvořit kompatibilní se specifikací CLS součásti:  
  
1.  Použití <xref:System.CLSCompliantAttribute> můžete označit sestavení jako kompatibilní se specifikací CLS.  
  
2.  Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se specifikací CLS jako nekompatibilní.  
  
3.  Označte všechny veřejně vystavené členy v kompatibilní se specifikací CLS typy jako nekompatibilní.  
  
4.  Zadejte kompatibilní se specifikací CLS alternativní pro členy jiné kompatibilní se specifikací CLS.  
  
 Byl úspěšně označen nekompatibilní typy a členy, by neměl vaší kompilátoru emitování všechna upozornění, porušení. Ale by měl být uveden členy, které nejsou kompatibilní se specifikací CLS seznam a jejich kompatibilní se specifikací CLS alternativy v dokumentaci k produktu.  
  
 Následující příklad používá <xref:System.CLSCompliantAttribute> atribut pro definování kompatibilní se specifikací CLS sestavení a typu, `CharacterUtilities`, který má dva členy jiné kompatibilní se specifikací CLS. Vzhledem k tomu, že jsou oba členy označené `CLSCompliant(false)` atribut, kompilátor vytváří žádná upozornění. Třída poskytuje kompatibilní se specifikací CLS alternativní pro obě metody. Normálně, doporučujeme stačí přidat dvě přetížení k `ToUTF16` metody můžete zajistit kompatibilní se specifikací CLS alternativy. Ale protože metody nemohou být přetíženy na základě návratové hodnoty, názvy kompatibilní se specifikací CLS metody se liší od názvy nevyhovující metod.  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 Pokud vyvíjíte aplikaci, nikoli knihovny (pokud nejsou vystavení typy nebo členy, kteří mohou být spotřebovávána jinými vývojáři aplikace), jsou souladu se specifikací CLS program prvků, které vaše aplikace využívá týkající se pouze v případě, že je váš jazyk nepodporuje . V takovém případě vaší kompilátoru jazyka dojde k chybě při pokusu použít element jiný kompatibilní se specifikací CLS.  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>Vzájemná funkční spolupráce mezi jazyky  
 Jazyková nezávislost má několik možných významů. Jeden význam, která je popsána v článku [jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md), zahrnuje bezproblémově využívání typy, které jsou napsané v jednom jazyce z aplikace v jiném jazyce. Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.  
  
 Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`. Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic. Zde je zdrojový kód pro StringUtil.vb, který obsahuje jeden člen, `ToTitleCase`, ve své třídě `StringLib`.  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů. Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:  
  
```  
vbc /t:module StringUtil.vb   
```  
  
 Další informace o syntaxi příkazového řádku kompilátoru jazyka Visual Basic najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
 Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:  
  
```  
csc /t:module NumberUtil.cs  
```  
  
 Další informace o syntaxi příkazového řádku kompilátoru jazyka C#, najdete v části [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
 Pak použijete [nástroj Link (Link.exe)](http://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129) zkompilovat dva moduly do sestavení:  
  
```  
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll   
```  
  
 Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`. Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.  
  
 [!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
 [!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]  
  
 Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:  
  
```  
vbc example.vb /r:UtilityLib.dll  
```  
  
 Kompilace pomocí C#, změňte název kompilátoru z **Vbc –** k **csc**a změňte příponu souboru z VB .cs:  
  
```  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.CLSCompliantAttribute>
