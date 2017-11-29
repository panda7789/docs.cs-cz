---
title: "Rozšíření značek a WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08cdc3dcb9e6d73b0d3b95915bf955ee27782782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozšíření značek a WPF XAML
Toto téma zavádí koncepci rozšíření značek pro jazyk XAML, včetně jejich syntaxe pravidel, účel a objektový model třídy, který je základem je. Rozšíření značek jsou obecné funkce jazyka XAML a implementace rozhraní .NET XAML services. Toto téma konkrétně podrobnosti rozšíření značek pro použití v jazyce XAML WPF.  
  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML a rozšíření značek  
 Obecně řečeno XAML můžete buď analyzátor hodnota atributu jako řetězcový literál, který může být převeden na primitivní, nebo ho převést na objekt některé prostředky. Jedním z takových prostředků je odkazem převaděče typů; To je najdete v tématu [TypeConverters a XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md). Existují však scénáře, kdy je potřeba různé chování. Například může být nastavena na procesor XAML, že by se neměly zobrazit hodnotu atributu nový objekt v grafu objektů. Místo toho atribut by měl mít za následek grafu objektu, který vytvoří odkaz na objekt již vytvořený v jiné části grafu nebo statický objekt. Další možností je, že procesor XAML můžete pokyn k použití syntaxe, který obsahuje jiné než výchozí argumenty pro konstruktor objektu. Toto jsou typy scénáře, kde můžete rozšíření značek poskytovat řešení.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Syntaxe rozšíření základní značek  
 Rozšíření značek se dá implementovat zadat hodnoty pro vlastnosti využití atribut, vlastnosti v použití elementu vlastnosti, nebo obojí.  
  
 Pokud se použije k poskytování hodnota atributu, syntaxe, která rozlišuje posloupnost rozšíření značek pro jazyk XAML procesor, které je přítomnost levou a pravou složené závorky ({a}). Typ rozšíření značek je pak identifikována token řetězcového okamžitě po otevření složené závorky.  
  
 Pokud se použije v syntaxi element vlastnost, rozšíření značek je vizuálně stejný jako jakýkoli další prvek použitý k poskytnutí hodnotu vlastnosti element: deklarace element XAML, který odkazuje na třídu rozšíření značek jako element uzavřené v lomených závorkách (<> ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaný XAML  
 Několik rozšíření značek existují, které nejsou specifické pro implementaci WPF XAML, ale místo toho budou implementace vnitřní objekty nebo funkce jazyka XAML jako jazyk. Tato rozšíření značek jsou implementované v sestavení System.Xaml jako součást obecné rozhraní .NET Framework XAML services a jsou v rámci oboru názvů jazyka XAML XAML. Z hlediska běžné použití značek, jsou obvykle poznáte ho podle těchto rozšíření značek `x:` předponu využití. <xref:System.Windows.Markup.MarkupExtension> Vzor, který všechna rozšíření značek by měly používat, aby byla podporována v XAML čtení a zápis XAML, včetně v jazyce XAML WPF poskytuje základní třídu (také definovanou v System.Xaml).  
  
-   `x:Type`poskytuje <xref:System.Type> objektu pro typ s názvem. Pokud tuto funkci se nejčastěji používá v styly a šablony. Podrobnosti najdete v tématu [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
-   `x:Static`Vytvoří statické hodnoty. Hodnoty pocházejí z entity kód typ hodnoty, které nejsou přímo typ hodnoty vlastnost target, ale lze vyhodnotit na typu. Podrobnosti najdete v tématu [x: Static – rozšíření značek](../../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
-   `x:Null`Určuje `null` jako hodnotu pro vlastnost a dá se použít buď pro atributy nebo element hodnot vlastností. Podrobnosti najdete v tématu [x: Null – rozšíření značek](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
-   `x:Array`poskytuje podporu pro vytvoření obecné pole v jazyce XAML syntaxi pro případy, kdy kolekce podporu poskytuje základní prvky WPF a modely ovládací prvek je úmyslně nepoužívá. Podrobnosti najdete v tématu [x: Array – rozšíření značek](../../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Předpona se používá pro typické mapování oboru názvů jazyka XAML XAML vnitřní jazyk funkce v kořenovém elementu souboru XAML nebo produkční. Například [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] zahájit soubor XAML pomocí této šablony pro aplikace WPF `x:` mapování. Může zvolit jinou předponu token v vlastní mapování oboru názvů jazyka XAML, ale tato dokumentace bude předpokládat výchozí `x:` mapování jako prostředek identifikace tyto entity, které jsou definované součástí oboru názvů jazyka XAML pro jazyk XAML, na rozdíl od svazků k WPF výchozí obor názvů nebo další obory názvů jazyka XAML nesouvisí s konkrétní rozhraní.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozšíření značek specifické pro grafický subsystém WPF  
 Nejběžnější rozšíření značek použít při programování WPF jsou ty, které podporují prostředků odkazy (`StaticResource` a `DynamicResource`) a ty, které podporují datová vazba (`Binding`).  
  
-   `StaticResource`poskytuje hodnotu pro vlastnost, přičemž nahradí hodnotu prostředek už definované. A `StaticResource` vyhodnocení nemá přístup do grafu, pro objekt v době běhu a nakonec poskytnuty čas načítání XAML. Podrobnosti najdete v tématu [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   `DynamicResource`poskytuje hodnotu pro vlastnost rozlišením tuto hodnotu na spuštění odkaz na prostředek. Odkaz na dynamické prostředků vynutí nové vyhledávání pokaždé, když, takový prostředek přistupuje a měl přístup ke grafu objektů za běhu. Chcete-li získat tento přístup `DynamicResource` koncept podporuje vlastností závislostí v systému vlastnost WPF a vyhodnocení výrazů. Proto můžete použít pouze `DynamicResource` pro cílovou vlastnost závislosti. Podrobnosti najdete v tématu [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
-   `Binding`poskytuje že data vázaná hodnota pro vlastnost, pomocí kontextu dat, která platí pro nadřazený objekt v době běhu. Toto rozšíření značek je poměrně složité, protože umožňuje výrazně vložené syntaxe pro určení datová vazba. Podrobnosti najdete v tématu [vazby – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
-   `RelativeSource`poskytuje informace o zdroji pro <xref:System.Windows.Data.Binding> , můžete přejít několik možných relací ve stromové struktuře běhového objektu. To poskytuje specializované sourcing u vazeb, které jsou vytvořena v rámci více použití šablon nebo v kódu bez úplné znalosti okolního stromu objektů. Podrobnosti najdete v tématu [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md).  
  
-   `TemplateBinding`umožňuje řízení šablonu, která má použít pro šablonované vlastnosti, které pocházejí z objektu modelu definované vlastnosti třídy, která bude použita šablona hodnoty. Jinými slovy vlastnost v definici šablony mají přístup k kontext, který existuje pouze po bude použita šablona. Podrobnosti najdete v tématu [TemplateBinding – rozšíření značek](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md). Další informace o praktická použití `TemplateBinding`, najdete v části [styly s ukázkou ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
-   `ColorConvertedBitmap`podporuje scénáři relativně pokročilé vytváření bitové kopie. Podrobnosti najdete v tématu [ColorConvertedBitmap – rozšíření značek](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md).  
  
-   `ComponentResourceKey`a `ThemeDictionary` podporují aspekty vyhledávání prostředků, zejména pro zdroje a motivy, které jsou součástí vlastní ovládací prvky. Další informace najdete v tématu [ComponentResourceKey – rozšíření značek](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md), [ThemeDictionary – rozšíření značek](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md), nebo [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Rozšíření třídy  
 Pro obecné jazyk XAML i WPF konkrétní rozšíření značek, chování jednotlivých – rozšíření značek identifikovat procesor XAML prostřednictvím `*Extension` třídu odvozenou od <xref:System.Windows.Markup.MarkupExtension>a představuje implementaci objektu <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> Metoda. Tato metoda pro každé rozšíření obsahuje objekt, který je vrácena, pokud je vyhodnocován rozšíření značek. Vráceného objektu obvykle vyhodnotí podle různých řetězec tokeny, které se budou předávat rozšíření značek.  
  
 Například <xref:System.Windows.StaticResourceExtension> třída poskytuje prostor implementace vyhledávání skutečné prostředků tak, aby jeho <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementace vrátí objekt, který je požadovaný se vstupem této konkrétní implementace, právě řetězec, který se používá ke vyhledání prostředků pomocí jeho `x:Key`. Velká část této implementaci jsou podrobně popsané není důležitý, pokud používáte stávající rozšíření značek.  
  
 Některé rozšíření značek nepoužívejte tokenu argumenty řetězce. Toto je vzhledem k tomu, že budou vracet hodnotu statickou nebo konzistentní, nebo protože kontext pro jaké je hodnota, je k dispozici prostřednictvím jedné ze služeb předána `serviceProvider` parametr.  
  
 `*Extension` Vzoru pro pojmenovávání je kvůli pohodlí a konzistence. Není nutné, aby XAML procesoru k identifikaci této třídy, jako je podpora pro rozšíření značek. Tak dlouho, dokud vaše codebase zahrnuje System.Xaml a používá implementace rozhraní .NET Framework XAML Services, všechny možnosti, které je potřeba rozpoznat jako přípona značky XAML je odvozena od <xref:System.Windows.Markup.MarkupExtension> a pro podporu vytváření syntaxe. WPF definuje povolení rozšíření třídy značek, které se neřídí `*Extension` pojmenování vzor, například <xref:System.Windows.Data.Binding>. Obvykle důvodem je, že třída podporuje scénáře kromě čistý kód rozšíření podpory. U <xref:System.Windows.Data.Binding>, že třída podporuje spuštění přístup k metody a vlastnosti objektu pro scénáře, které nemají co dělat s XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Rozšíření třídy výklad inicializace textu  
 Řetězec tokeny následující rozšíření značek název a stále do závorek, se interpretují procesorem XAML v jednom z následujících způsobů:  
  
-   Čárkou vždy představuje oddělovač nebo oddělovač jednotlivých tokenů.  
  
-   Pokud jednotlivých oddělených tokenů neobsahují jakékoli projevy rovná, každý token, je zpracovaná jako argument konstruktoru. Každý parametr konstruktoru musí být zadána jako na typ očekávaný podle tohoto podpisu a ve správném pořadí očekávanou tento podpis.  
  
    > [!NOTE]
    >  Procesor XAML musí volat konstruktor, který odpovídá argument počet zadaný počet párů. Z tohoto důvodu při implementaci rozšíření vlastních značek, neposkytují několik parametrů s stejný počet argumentů. Není definován chování chování procesor XAML, pokud existuje více než jednu cestu konstruktor rozšíření značek s stejný počet parametrů, ale měli předpokládáte, že procesor XAML je umožnit vyvolat výjimku na využití, pokud v této situaci existuje definice pro typ rozšíření značek.  
  
-   Pokud jednotlivých oddělených tokenů obsahovat znak rovná se a potom procesor XAML nejprve volá výchozí konstruktor pro rozšíření značek. Potom každý dvojice název-hodnota = interpretována jako název vlastnosti, která existuje v rozšíření značek a hodnota pro přiřazení k dané vlastnosti.  
  
-   Pokud je paralelní výsledek mezi konstruktor chování a vlastnost nastavení chování v rozšíření značek, nezáleží na tom, jaké chování používáte. Je dnes běžné využití používat *vlastnost*`=`*hodnotu* páry pro rozšíření značek, které mají více než jednu nastavit vlastnost, pokud pouze, protože umožňuje váš kód více úmyslné a jste méně pravděpodobné, že omylem transponuje konstruktor parametry. (Pokud zadáte vlastnost = páry hodnota tyto vlastnosti mohou být v libovolném pořadí.) Navíc není zaručeno, že rozšíření značek poskytuje parametr konstruktor, který nastaví každých jeden z jeho nastavit vlastnosti. Například <xref:System.Windows.Data.Binding> je rozšíření značek, s mnoha nastavitelné prostřednictvím rozšíření ve vlastnosti *vlastnost*`=`*hodnotu* formuláře, ale <xref:System.Windows.Data.Binding> podporuje pouze dva konstruktory: výchozí konstruktor a ten, který nastaví počáteční cestu.  
  
-   Rozšíření značek bez escapement nelze předat literálu čárkami.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Řídicí sekvence a rozšíření značek  
 Atribut v jazyce XAML procesor používá složené závorky jako indikátory rozšíření pořadí značek. Je také možné vytvořit hodnota atributu literálu složené závorky znak, v případě potřeby tak, že zadáte v řídicí sekvenci pomocí dvojici prázdný složené závorky následované literálu složených závorek. V tématu [řídicí sekvence {} – rozšíření značek](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Vnoření rozšíření značek v jazyce XAML využití  
 Je podporováno vnoření více rozšíření značek a každý – rozšíření značek vyhodnotí nejhlubší nejdřív. Zvažte například následující využití:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 V této využití `x:Static` příkaz je první vyhodnocen a vrátí řetězec. Že se pak použije řetězec jako argument pro `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Vlastnost Element syntaxi a rozšíření značek  
 Když se použije jako objekt element, který vyplní celé element hodnotu vlastnosti, je vizuálně lišit od element typické podporovaný typ objektu, který lze použít v jazyce XAML třídu rozšíření značek. Praktické rozdíl mezi typické objekt elementu a rozšíření značek je, že rozšíření značek je buď vyhodnotit na hodnotu typu nebo odložení jako výraz. Mechanismy pro všechny možné typ chyby hodnot vlastností pro rozšíření značek proto bude jiný, podobně jako jak zpracovávají vlastnost pozdní vazba v jinými programovací modely. Element obyčejnou objektu se vyhodnotí pro match typu pro vlastnost target, který je nastavení, když je analyzovat XAML.  
  
 Většina rozšíření značek, když se používá v syntaxe element objektu k vyplnění element vlastnost, nebude mít syntaxi element obsahu nebo dalších vlastností v rámci. Proto by zavřete značky elementu objektu a poskytovat žádné podřízené elementy. Vždy, když libovolný element, objekt je zjištěna procesorem XAML, se nazývá v konstruktoru pro tuto třídu, která vytváří instanci objektu vytvořené z analyzovaných elementu. Rozšíření třídy značek se neliší: Pokud chcete, aby vaše – rozšíření značek možné používat v syntaxi element objekt, je nutné zadat výchozí konstruktor. Některé stávající rozšíření značek mají alespoň jednu hodnotu požadovanou vlastnost, musí být zadané pro efektivní inicializace. Pokud ano, je hodnota této vlastnosti obvykle zadána jako atribut vlastnost v objektu elementu. V [Namespace XAML (x:) Jazykové funkce](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md) a [WPF XAML rozšíření](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md) referenční stránky, kód bude zaznamenán rozšíření, které mají požadované vlastnosti (a názvy požadované vlastnosti). — Referenční stránky bude Všimněte si také, pokud je zakázaná syntaxe objektu element nebo atribut syntaxe pro rozšíření konkrétní značek. Významné případem je [x: Array – rozšíření značek](../../../../docs/framework/xaml-services/x-array-markup-extension.md), který nepodporuje atribut syntaxe, protože obsah tohoto pole musí být určeny označování jako obsah. Obsah pole jsou zpracovávány jako obecné objekty, proto je vhodná žádná výchozí typ převaděč pro atribut. Navíc [x: Array – rozšíření značek](../../../../docs/framework/xaml-services/x-array-markup-extension.md) vyžaduje `type` parametr.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Namespace XAML (x:) Jazykové funkce](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozšíření WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [– Rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [Vazby – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)  
 [– Rozšíření značek DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)  
 [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
