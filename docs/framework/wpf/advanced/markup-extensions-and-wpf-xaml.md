---
title: Rozšíření značek a XAML
ms.date: 03/30/2017
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
ms.openlocfilehash: c288055a27cbab75a5cdf541e539ea20e490c965
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141052"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozšíření značek a WPF XAML
Toto téma představuje koncept rozšíření značek pro XAML, včetně jejich syntaktická pravidla, účel a objektový model třídy, který je základem. Rozšíření značek jsou obecnou funkcí jazyka XAML a implementace služby XAML .NET. Toto téma konkrétně podrobnosti značkovací rozšíření pro použití v WPF XAML.  

<a name="XAML_Processors_and_Markup_Extensions"></a>
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML a rozšíření pro značky  
 Obecně řečeno, analyzátor XAML může interpretovat hodnotu atributu jako literálový řetězec, který lze převést na primitivní, nebo jej nějakým způsobem převést na objekt. Jedním z takových prostředků je odkazování na typový převaděč; to je zdokumentováno v tématu [TypeConverters a XAML](typeconverters-and-xaml.md). Existují však scénáře, kde je vyžadováno různé chování. Procesor XAML může být například instruován, že hodnota atributu by neměla mít za následek nový objekt v grafu objektu. Místo toho by měl atribut vést k grafu objektu, který odkazuje na již vytvořený objekt v jiné části grafu nebo statický objekt. Dalším scénářem je, že procesor XAML může být instruován k použití syntaxe, která poskytuje konstruktoru objektu, který není výchozí. Jedná se o typy scénářů, kde rozšíření značky může poskytnout řešení.  
  
<a name="Basic_Markup_Extension_Syntax"></a>
## <a name="basic-markup-extension-syntax"></a>Syntaxe základního rozšíření značek  
 Rozšíření značek lze implementovat poskytnout hodnoty pro vlastnosti v použití atributu, vlastnosti v použití prvku vlastnosti nebo obojí.  
  
 Při použití k zadání hodnoty atributu je syntaxe, která rozlišuje sekvenci rozšíření značek od procesoru XAML, přítomnost počátečních a uzavíracích složených závorek ({ a }). Typ rozšíření značky je pak identifikován tokenem řetězce bezprostředně za počáteční složenou závorkou.  
  
 Při použití v syntaxi prvku vlastnosti je rozšíření značek vizuálně stejné jako jakýkoli jiný prvek použitý k poskytnutí hodnoty prvku vlastnosti: deklarace prvku XAML, která odkazuje na třídu rozšíření značek jako na prvek uzavřený v úhlových závorkách (<>).  
  
<a name="XAML_Defined_Markup_Extensions"></a>
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaná xAML  
 Existuje několik rozšíření značek, které nejsou specifické pro implementaci WPF XAML, ale jsou místo toho implementace vnitřních částí nebo funkce XAML jako jazyk. Tato rozšíření značek jsou implementována v sestavení System.Xaml jako součást obecných služeb XAML rozhraní .NET Framework a jsou v oboru názvů XAML jazyka XAML. Pokud jde o běžné použití značek, tato rozšíření značek jsou `x:` obvykle identifikovatelné podle předpony v použití. Základní <xref:System.Windows.Markup.MarkupExtension> třída (také definována v System.Xaml) poskytuje vzor, který by měl použít všechna rozšíření značek, aby byly podporovány v čtecích programech XAML a zapisovačích XAML, včetně WPF XAML.  
  
- `x:Type`dodává <xref:System.Type> objekt pro pojmenovaný typ. Toto zařízení se používá nejčastěji ve stylech a šablonách. Podrobnosti naleznete v [tématu x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md).  
  
- `x:Static`vytváří statické hodnoty. Hodnoty pocházejí z entit kódu typu hodnoty, které nejsou přímo typem hodnoty cílové vlastnosti, ale mohou být vyhodnoceny pro tento typ. Podrobnosti naleznete v [tématu x:Static Markup Extension](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md).  
  
- `x:Null`určuje `null` jako hodnotu vlastnosti a lze ji použít pro atributy nebo hodnoty prvků vlastnosti. Podrobnosti naleznete v [tématu x:Null Markup Extension](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
- `x:Array`poskytuje podporu pro vytváření obecných polí v syntaxi XAML pro případy, kdy podpora kolekce poskytované wpf základní prvky a modely ovládacích prvků záměrně nepoužívá. Podrobnosti naleznete v [tématu x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).  
  
> [!NOTE]
> Předpona se `x:` používá pro typické mapování oboru názvů XAML jazykových jazyků XAML, v kořenovém prvku souboru XAML nebo výroby. Například šablony sady Visual Studio pro aplikace WPF iniciují soubor XAML pomocí tohoto `x:` mapování. Ve vlastním mapování oboru názvů XAML můžete zvolit jiný token předpony, `x:` ale tato dokumentace předpokládá výchozí mapování jako prostředek k identifikaci těch entit, které jsou definovanou součástí oboru názvů XAML pro jazyk XAML, na rozdíl od výchozího oboru názvů WPF nebo jiných oborů názvů XAML, které nesouvisejí s určitým rámcem.  
  
<a name="WPF_Specific_Markup_Extensions"></a>
## <a name="wpf-specific-markup-extensions"></a>Rozšíření pro značky specifické pro WPF  
 Nejběžnější značkovací rozšíření používaná v programování WPF jsou ta, která podporují odkazy na prostředky (`StaticResource` a `DynamicResource`), a ty, které podporují datovou vazbu (`Binding`).  
  
- `StaticResource`poskytuje hodnotu vlastnosti nahrazením hodnoty již definovaného prostředku. Hodnocení `StaticResource` se nakonec provádí v době načítání XAML a nemá přístup k grafu objektů za běhu. Podrobnosti naleznete v tématu [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- `DynamicResource`poskytuje hodnotu vlastnosti odložením této hodnoty jako odkaz za běhu na prostředek. Dynamický odkaz na prostředek vynutí nové vyhledávání pokaždé, když je k takovému prostředku přistupováno a má přístup k grafu objektů za běhu. Chcete-li získat tento `DynamicResource` přístup, koncept je podporován vlastnostmi závislostí v systému vlastností WPF a vyhodnocenými výrazy. Proto můžete použít `DynamicResource` pouze pro cíl vlastnosti závislosti. Podrobnosti naleznete v tématu [DynamicResource Markup Extension](dynamicresource-markup-extension.md).  
  
- `Binding`poskytuje datovou hodnotu pro vlastnost pomocí kontextu dat, který se vztahuje na nadřazený objekt za běhu. Toto rozšíření značek je poměrně složité, protože umožňuje podstatnou vložkou syntaxi pro určení datové vazby. Podrobnosti naleznete v [tématu Rozšíření o vazby .](binding-markup-extension.md)  
  
- `RelativeSource`poskytuje zdrojové <xref:System.Windows.Data.Binding> informace, které mohou procházet několik možných relací ve stromu objektů za běhu. To poskytuje specializované zdroje pro vazby, které jsou vytvořeny ve víceúčelových šablonách nebo vytvořeny v kódu bez úplné znalosti okolního stromu objektů. Podrobnosti naleznete [v tématu RelativeSource MarkupExtension](relativesource-markupextension.md).  
  
- `TemplateBinding`umožňuje šabloně ovládacího prvku použít hodnoty pro šablony vlastnosti, které pocházejí z vlastností definovaných objektovým modelem třídy, která bude šablonu používat. Jinými slovy vlastnost v rámci definice šablony můžete získat přístup k kontextu, který existuje pouze po použití šablony. Podrobnosti naleznete v [tématu TemplateBinding Markup Extension](templatebinding-markup-extension.md). Další informace o praktickém `TemplateBinding`použití aplikace naleznete v [tématu Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`podporuje relativně pokročilý scénář zobrazování. Podrobnosti naleznete v tématu [ColorConvertedBitmap Markup Extension](colorconvertedbitmap-markup-extension.md)Extension .  
  
- `ComponentResourceKey`a `ThemeDictionary` podporují aspekty vyhledávání prostředků, zejména pro zdroje a motivy, které jsou zabaleny s vlastní ovládací prvky. Další informace naleznete v tématu [Rozšíření značek ComponentResourceKey](componentresourcekey-markup-extension.md), [Rozšíření značek ThemeDictionary](themedictionary-markup-extension.md)nebo [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>
## <a name="extension-classes"></a>\*Třídy rozšíření  
 Pro obecný jazyk XAML a wpf specifické značky rozšíření chování každé rozšíření značky je identifikován `*Extension` procesoru XAML prostřednictvím třídy, která je odvozena od <xref:System.Windows.Markup.MarkupExtension>, a poskytuje implementaci <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> metody. Tato metoda na každé rozšíření poskytuje objekt, který je vrácenpři vyhodnocení rozšíření značky. Vrácený objekt je obvykle vyhodnocena na základě různých tokenů řetězce, které jsou předány rozšíření značky.  
  
 Například <xref:System.Windows.StaticResourceExtension> třída poskytuje povrchovou implementaci skutečného vyhledávání <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> prostředků tak, aby jeho implementace vrátí požadovaný objekt, přičemž vstup této konkrétní implementace `x:Key`je řetězec, který se používá k vyhledání prostředku jeho . Velká část tohoto podrobností implementace není důležitá, pokud používáte existující rozšíření značek.  
  
 Některá rozšíření značek nepoužívají argumenty tokenu řetězce. Je to buď proto, že vrátí statickou nebo konzistentní hodnotu, nebo proto, že `serviceProvider` kontext pro jakou hodnotu by měl být vrácen, je k dispozici prostřednictvím jedné ze služeb předávaných parametrem.  
  
 Vzor `*Extension` pojmenování je pro pohodlí a konzistenci. Není nutné, aby procesor XAML k identifikaci této třídy jako podporu pro rozšíření značky. Tak dlouho, dokud váš základ kódu obsahuje System.Xaml a používá implementace služby .NET Framework XAML Services, vše, co je nezbytné k rozpoznání jako rozšíření značek XAML, je odvodit z <xref:System.Windows.Markup.MarkupExtension> syntaxe konstrukce a podporovat ji. WPF definuje třídy umožňující rozšíření značek, `*Extension` které nedodržují <xref:System.Windows.Data.Binding>například vzor pojmenování . Obvykle důvodem je, že třída podporuje scénáře nad rámec podpory rozšíření čisté značky. V případě <xref:System.Windows.Data.Binding>, tato třída podporuje run-time přístup k metodám a vlastnostem objektu pro scénáře, které nemají nic společného s XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Interpretace inicializačního textu třídy rozšíření  
 Tokeny řetězce za názvem rozšíření značky a stále v rámci složených závorek jsou interpretovány procesorem XAML jedním z následujících způsobů:  
  
- Čárka vždy představuje oddělovač nebo oddělovač jednotlivých tokenů.  
  
- Pokud jednotlivé oddělené tokeny neobsahují žádné znaky rovná se, každý token je považován za argument konstruktoru. Každý parametr konstruktoru musí být uveden jako typ očekávaný tímto podpisem a ve správném pořadí očekávaném tímto podpisem.  
  
    > [!NOTE]
    > Procesor XAML musí volat konstruktor, který odpovídá počtu argumentů počtu párů. Z tohoto důvodu pokud implementujete vlastní rozšíření značek, neposkytují více konstruktory se stejným počtem argumentů. Chování chování procesoru XAML, pokud existuje více než jedna cesta konstruktoru rozšíření značek se stejným počtem parametrů, ale měli byste předpokládat, že procesor XAML je povolen vyvolat výjimku při použití, pokud tato situace existuje v definice typu rozšíření značek.  
  
- Pokud jednotlivé oddělené tokeny obsahují rovná se znaménko, pak procesor XAML nejprve volá konstruktor bez parametrů pro rozšíření značek. Potom každý název =hodnota dvojice je interpretován jako název vlastnosti, která existuje na rozšíření značky a hodnotu přiřadit této vlastnosti.  
  
- Pokud existuje paralelní výsledek mezi chování konstruktoru a chování nastavení vlastností v rozšíření značky, nezáleží na tom, které chování používáte. Je běžnější použití dvojice*hodnot* *vlastností*`=`pro rozšíření značek, které mají více než jednu vlastnost settable, i když jen proto, že vaše značky více úmyslné a je méně pravděpodobné, že omylem transponovat parametry konstruktoru. (Když zadáte dvojice vlastností=hodnota, mohou být tyto vlastnosti v libovolném pořadí.) Také neexistuje žádná záruka, že rozšíření značky poskytuje parametr konstruktoru, který nastaví každý z jeho settable vlastnosti. <xref:System.Windows.Data.Binding> Například je rozšíření značky s mnoha vlastnostmi, které jsou nastaveny <xref:System.Windows.Data.Binding> prostřednictvím rozšíření ve formě*hodnoty* *vlastnosti,*`=`ale podporuje pouze dva konstruktory: konstruktor bez parametrů a ten, který nastaví počáteční cestu.  
  
- Literál čárka nelze předat rozšíření značky bez escapement.  
  
<a name="EscapeSequences"></a>
## <a name="escape-sequences-and-markup-extensions"></a>Sekvence escape a rozšíření značek  
 Zpracování atributů v procesoru XAML používá složené závorky jako indikátory sekvence rozšíření značek. Je také možné v případě potřeby vytvořit hodnotu atributu znaku složených složených závorek doslovně zadáním sekvence pomocí prázdného páru složených závorek následovaných literální složených závorkou. Viz [ {} Escape Sequence - Markup Extension](../../../desktop-wpf/xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Vnoření rozšíření značek v použití XAML  
 Vnoření více rozšíření značek je podporována a každé rozšíření značky budou vyhodnoceny jako nejhlubší jako první. Zvažte například následující použití:  
  
```xaml  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 V tomto použití `x:Static` je příkaz vyhodnocen jako první a vrátí řetězec. Tento řetězec se pak používá `DynamicResource`jako argument pro .  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozšíření značek a syntaxe prvku vlastnosti  
 Při použití jako prvek objektu, který vyplňuje hodnotu prvku vlastnosti, třída rozšíření značek je vizuálně k nerozeznání od typického prvku objektu se zálohovaným typem, který lze použít v XAML. Praktický rozdíl mezi typickým objektovým prvkem a rozšířením značek spoáži, že rozšíření značek je buď vyhodnoceno na zadalicí hodnotu, nebo odloženo jako výraz. Proto mechanismy pro všechny možné chyby typu hodnoty vlastností pro rozšíření značky se bude lišit, podobně jako jak pozdní vázané vlastnosti je zpracována v jiných programovacích modelech. Běžný prvek objektu bude vyhodnocen pro shodu typu s cílovou vlastností, kterou je nastavuje při souhřešnosti xaml.  
  
 Většina rozšíření značek, pokud se používá v syntaxi prvku objektu k vyplnění prvku vlastnosti, nebude mít obsah ani žádnou další syntaxi prvku vlastnosti. Proto byste zavřeli značku elementu objektu a nezadali žádné podřízené prvky. Vždy, když je jakýkoli prvek objektu zjištěn procesorem XAML, je volán konstruktor pro tuto třídu, který vytváří instance objektu vytvořeného z analyzovaného prvku. Třída rozšíření značek se nijak neliší: pokud chcete, aby vaše rozšíření značek bylo použitelné v syntaxi prvku objektu, musíte zadat konstruktor bez parametrů. Některá existující rozšíření značek mají alespoň jednu požadovanou hodnotu vlastnosti, která musí být určena pro efektivní inicializaci. Pokud ano, tato hodnota vlastnosti je obvykle uveden jako atribut vlastnosti prvku objektu. V [oboru názvů XAML (x:) Funkce jazyka](../../../desktop-wpf/xaml-services/namespace-language-features.md) a [WPF XAML rozšíření](wpf-xaml-extensions.md) referenční stránky, značky rozšíření, které mají požadované vlastnosti (a názvy požadovaných vlastností) budou zaznamenány. Referenční stránky také zaznamenají, že syntaxe prvku objektu nebo syntaxe atributu je pro konkrétní rozšíření značek zakázána. Významným případem je [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md), který nemůže podporovat syntaxi atributu, protože obsah tohoto pole musí být zadán v rámci označování jako obsah. Obsah pole jsou zpracovány jako obecné objekty, proto žádný výchozí převaděč typu pro atribut je možné. Také [x:Array Markup](../../../desktop-wpf/xaml-services/xarray-markup-extension.md) Extension `type` vyžaduje parametr.  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Jazykové funkce oboru názvů jazyka XAML (x:)](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [StaticResource – rozšíření značek](staticresource-markup-extension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
- [DynamicResource – rozšíření značek](dynamicresource-markup-extension.md)
- [x:Type – rozšíření značek](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
