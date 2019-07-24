---
title: Rozšíření značek a WPF XAML
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
ms.openlocfilehash: 25f6cbbc1df8a4a2b4ad9025b2381d26153e4b66
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364438"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozšíření značek a WPF XAML
Toto téma představuje koncept rozšíření značek pro jazyk XAML, včetně pravidel jejich syntaxe, účelu a modelu objektu třídy, který je v nich umístěn. Rozšíření značek jsou obecná funkce jazyka XAML a implementace .NET služeb XAML. Toto téma konkrétně popisuje rozšíření značek pro použití v jazyce WPF XAML.  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML a rozšíření značek  
 Obecně řečeno, analyzátor XAML může buď interpretovat hodnotu atributu jako řetězcový literál, který lze převést na primitivní, nebo převést na objekt pomocí nějakých prostředků. Jedním z těchto způsobů je odkazování na konvertor typu; Tato dokumentace je dokumentována v tématech [TypeConverter a XAML](typeconverters-and-xaml.md). Existují však situace, kdy je vyžadováno jiné chování. Například procesor XAML může dát pokyn, že hodnota atributu by neměla mít za následek nový objekt v grafu objektů. Místo toho by měl mít atribut v grafu objektů, který vytvoří odkaz na již konstruovaný objekt v jiné části grafu, nebo na statický objekt. Dalším scénářem je, že procesor XAML může mít pokyn k použití syntaxe, která poskytuje jiné než výchozí argumenty konstruktoru objektu. Jedná se o typy scénářů, kde může rozšíření značek poskytnout řešení.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Základní syntaxe rozšíření značek  
 Rozšíření značek lze implementovat k poskytnutí hodnot pro vlastnosti v použití atributu, vlastnosti v použití prvku vlastnosti nebo obojí.  
  
 Při použití k poskytnutí hodnoty atributu syntaxe, která rozlišuje sekvenci rozšíření značek na procesor XAML, je přítomnost počátečních a uzavíracích složených závorek ({a}). Typ rozšíření označení je poté identifikován tokenem řetězce hned za levou složenou závorku.  
  
 Při použití v syntaxi elementu vlastnosti je rozšíření značek vizuálně stejné jako jakýkoli jiný prvek použitý k poskytnutí hodnoty prvku vlastnosti: Deklarace elementu XAML, která odkazuje na třídu rozšíření značek jako element uzavřený v lomených závorkách (< > ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaná v jazyce XAML  
 Existuje několik rozšíření značek, která nejsou specifická pro implementaci WPF jazyka XAML, ale jsou místo toho implementace vnitřních prvků nebo funkcí jazyka XAML jako jazyk. Tato rozšíření značek jsou implementována v sestavení System. XAML jako součást obecných .NET Framework služeb XAML a jsou v oboru názvů XAML jazyka XAML. V souvislosti s běžným používáním značek jsou tato rozšíření značek obvykle identifikovatelná `x:` předponou v použití. <xref:System.Windows.Markup.MarkupExtension> Základní třída (také definovaná v System. XAML) poskytuje vzor, který by měla používat všechna rozšíření značek, aby byla podporována v prohlížečích XAML a zapisovačích XAML, včetně v jazyce WPF XAML.  
  
- `x:Type`<xref:System.Type> poskytuje objekt pro pojmenovaný typ. Toto zařízení se často používá v šablonách a stylech. Podrobnosti najdete v tématu [rozšíření značek x:Type](../../xaml-services/x-type-markup-extension.md).  
  
- `x:Static`Vytvoří statické hodnoty. Hodnoty pocházejí z entit kódu typu hodnoty, které nejsou přímo typu hodnoty cílové vlastnosti, ale lze je vyhodnotit na tento typ. Podrobnosti najdete v tématu [rozšíření značek x:static](../../xaml-services/x-static-markup-extension.md).  
  
- `x:Null`Určuje `null` jako hodnotu pro vlastnost a lze ji použít buď pro atributy, nebo hodnoty prvků vlastností. Podrobnosti najdete v tématu [rozšíření značek x:null](../../xaml-services/x-null-markup-extension.md).  
  
- `x:Array`poskytuje podporu pro vytváření obecných polí v syntaxi jazyka XAML pro případy, kdy podpora kolekce poskytovaná základními prvky WPF a modely ovládacích prvků není použita záměrně. Podrobnosti najdete v tématu [rozšíření značek x:Array](../../xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Předpona se používá pro typické mapování oboru názvů XAML vnitřních prvků jazyka XAML, v kořenovém elementu souboru XAML nebo v produkčním prostředí. Například šablony sady Visual Studio pro aplikace WPF inicializují soubor XAML pomocí tohoto `x:` mapování. Můžete zvolit jiný token předpony ve vlastním mapování oboru názvů XAML, ale tato dokumentace bude předpokládat výchozí `x:` mapování jako způsob identifikace těch entit, které jsou definovanou součástí oboru názvů XAML pro jazyk XAML, a to na rozdíl od na výchozí obor názvů WPF nebo jiné obory názvů jazyka XAML, které nesouvisí s konkrétním rozhraním.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozšíření značek specifická pro WPF  
 Nejběžnější rozšíření značek používané v programování WPF jsou ta, která podporují odkazy na prostředky (`StaticResource` a `DynamicResource`) a ty, které podporují datovou vazbu`Binding`().  
  
- `StaticResource`poskytuje hodnotu pro vlastnost nahrazením hodnoty již definovaného prostředku. `StaticResource` Vyhodnocení je nakonec provedeno v době načítání XAML a nemá přístup k grafu objektů v době běhu. Podrobnosti najdete v tématu [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- `DynamicResource`poskytuje hodnotu pro vlastnost odložením této hodnoty jako běhového odkazu na prostředek. Dynamický odkaz na prostředek vynutí nové vyhledávání pokaždé, když je takový prostředek přístupný a má přístup k grafu objektů v době běhu. Aby bylo možné získat tento přístup, `DynamicResource` je koncept podporován vlastnostmi závislosti v systému vlastností WPF a vyhodnocenými výrazy. Proto můžete použít `DynamicResource` pouze pro cíl vlastnosti závislosti. Podrobnosti najdete v tématu [rozšíření značek DynamicResource](dynamicresource-markup-extension.md).  
  
- `Binding`poskytuje hodnotu pro datovou vazbu pro vlastnost pomocí kontextu dat, který se vztahuje na nadřazený objekt v době běhu. Toto rozšíření značek je poměrně složité, protože umožňuje značnou vloženou syntaxi pro určení datové vazby. Podrobnosti najdete v tématu [rozšíření značek vazby](binding-markup-extension.md).  
  
- `RelativeSource`poskytuje informace o zdroji pro <xref:System.Windows.Data.Binding> objekt, který může procházet několik možných vztahů ve stromu objektů za běhu. To poskytuje specializované zdroje pro vazby, které jsou vytvořeny v šablonách s více použitími nebo vytvořeny v kódu bez úplného vědomí okolního stromu objektu. Podrobnosti najdete v tématu [RelativeSource MarkupExtension](relativesource-markupextension.md).  
  
- `TemplateBinding`umožňuje šabloně ovládacího prvku používat hodnoty pro vlastnosti šablony, které pocházejí z vlastností objektu definovaného modelem třídy, která bude šablonu používat. Jinými slovy, vlastnost v rámci definice šablony má přístup ke kontextu, který existuje pouze po použití šablony. Podrobnosti najdete v tématu [rozšíření značek TemplateBinding](templatebinding-markup-extension.md). Další informace o praktickém použití `TemplateBinding`nástroje naleznete v tématu [stylování with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`podporuje poměrně pokročilý scénář pro vytváření imagí. Podrobnosti najdete v tématu [rozšíření značek ColorConvertedBitmap](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey`a `ThemeDictionary` podporují aspekty vyhledávání prostředků, zejména pro prostředky a motivy, které jsou zabaleny s vlastními ovládacími prvky. Další informace najdete v tématu [rozšíření značek ComponentResourceKey](componentresourcekey-markup-extension.md), [rozšíření značek ThemeDictionary](themedictionary-markup-extension.md)nebo [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>\* Třídy rozšíření  
 Pro obecné kódování kódu XAML a pro rozšíření značek specifických pro WPF je chování jednotlivých rozšíření značek identifikováno pro procesor XAML prostřednictvím `*Extension` třídy, která je odvozena z <xref:System.Windows.Markup.MarkupExtension>a <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> poskytuje implementaci Metoda. Tato metoda pro každé rozšíření poskytuje objekt, který je vrácen při vyhodnocování rozšíření značek. Vrácený objekt je obvykle vyhodnocován v závislosti na různých tokenech řetězců, které jsou předány příponě značek.  
  
 Například <xref:System.Windows.StaticResourceExtension> Třída poskytuje plochu pro skutečné vyhledávání prostředků, aby jeho <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementace vrátila požadovaný objekt, se vstupem této konkrétní implementace je řetězec, který se používá k Vyhledejte prostředek podle jeho `x:Key`. Většina této podrobnosti implementace je neimportovaná, pokud používáte existující rozšíření značek.  
  
 Některá rozšíření značek nepoužívají argumenty řetězcového tokenu. To je způsobeno tím, že vrací statickou nebo konzistentní hodnotu, nebo protože kontext, který má být vrácen, je k dispozici prostřednictvím jedné ze služeb předaných prostřednictvím `serviceProvider` parametru.  
  
 Vzor `*Extension` pojmenování je pro pohodlí a konzistenci. Není nutné, aby procesor XAML identifikoval tuto třídu jako podporu pro rozšíření značek. Pokud váš základ kódu zahrnuje System. XAML a používá implementace .NET Framework XAML Services, vše, co je nutné rozpoznat jako rozšíření značek XAML, je odvozeno z <xref:System.Windows.Markup.MarkupExtension> a na podporu syntaxe konstrukce. WPF definuje rozšíření značek – povoluje třídy, které `*Extension` neodpovídají vzoru pojmenování, <xref:System.Windows.Data.Binding>například. Obvykle je důvodem to, že třída podporuje scénáře nad rámec podpory čistého rozšíření značek. V případě <xref:System.Windows.Data.Binding>, tato třída podporuje přístup za běhu k metodám a vlastnostem objektu pro scénáře, které nemají žádnou akci s XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Interpretace třídy rozšíření inicializačního textu  
 Řetězcové tokeny za názvem rozšíření značek a stále v rámci složených závorek jsou interpretovány procesorem XAML jedním z následujících způsobů:  
  
- Čárka vždy představuje oddělovač nebo oddělovač jednotlivých tokenů.  
  
- Pokud jednotlivé oddělené tokeny neobsahují žádné rovnítko, každý token je považován za argument konstruktoru. Každý parametr konstruktoru musí být uveden jako typ očekávaný tímto podpisem a ve správném pořadí očekávaném daným podpisem.  
  
    > [!NOTE]
    >  Procesor XAML musí volat konstruktor, který odpovídá počtu argumentů v počtu párů. Z tohoto důvodu, Pokud implementujete vlastní rozšíření značek, Neposkytněte více konstruktorů se stejným počtem argumentů. Chování pro způsob, jakým se procesor XAML chová, pokud více než jedna cesta konstruktoru rozšíření značek se stejným počtem parametrů je nedefinovaná, ale měli byste předpokládat, že procesor XAML smí vyvolat výjimku při použití, pokud tato situace existuje v definice typu rozšíření značek.  
  
- Pokud jednotlivé samostatné tokeny obsahují znaménka rovná se, pak procesor XAML nejprve zavolá konstruktor bez parametrů pro rozšíření značek. Pak každá dvojice název = hodnota je interpretována jako název vlastnosti, který existuje v rozšíření značek, a hodnotu, která se má přiřadit k této vlastnosti.  
  
- Pokud dojde k paralelnímu výsledku mezi chováním konstruktoru a chováním nastavení vlastnosti v rozšíření značek, nezáleží na tom, jaké chování používáte. Je běžné použití pro `=`rozšíření značek, které má více než jednu nastavitelnou vlastnost, pokud je to pouze proto, že je váš kód přesnější a že je méně pravděpodobně úmyslně transponovat parametry konstruktoru (Pokud zadáte páry Property = hodnota, tyto vlastnosti mohou být v libovolném pořadí.) Navíc není nijak zaručeno, že rozšíření značek poskytuje parametr konstruktoru, který nastaví každou ze svých vlastností. Například <xref:System.Windows.Data.Binding> je rozšíření značek s mnoha vlastnostmi, které lze nastavit prostřednictvím rozšíření ve formuláři*hodnoty* <xref:System.Windows.Data.Binding> *vlastnosti*`=`, ale podporuje pouze dva konstruktory: konstruktor bez parametrů a jeden který nastaví počáteční cestu.  
  
- Literálovou čárku nelze předat rozšíření značek bez řídicího znaku.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Řídicí sekvence a rozšíření značek  
 Zpracování atributů v procesoru XAML používá složené závorky jako indikátory sekvence rozšíření kódu. V případě potřeby je také možné vytvořit literálovou hodnotu atributu znak složené závorky, a to tak, že zadáte řídicí sekvenci s použitím prázdné páry složené závorky, za kterou následuje literální složená závorka. [ Viz{} řídicí sekvence – rozšíření značek](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Vnořování rozšíření značek v použití XAML  
 Je podporováno vnořování více rozšíření značek a každé rozšíření značek bude nejprve vyhodnoceno jako nejdůkladnější. Zvažte například následující použití:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 V tomto použití `x:Static` je příkaz vyhodnocen jako první a vrátí řetězec. Tento řetězec se pak použije jako argument pro `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozšíření značek a syntaxe elementu vlastnosti  
 Při použití jako prvku objektu, který vyplní hodnotu prvku vlastnosti, je třída rozšíření značek vizuálně neodlišená od typického elementu, který je v jazyce back-Type, který lze použít v jazyce XAML. Praktický rozdíl mezi typickým prvkem objektu a příponou značek je, že rozšíření značek je buď vyhodnoceno na zadanou hodnotu, nebo odloženo jako výraz. Proto se mechanismy pro jakékoli možné chyby typu pro rozšíření značek liší, podobně jako vlastnost s pozdní vazbou je zpracována v jiných programovacích modelech. Běžný prvek objektu bude vyhodnocen pro shodu typu s cílovou vlastností, která je nastavena při analýze XAML.  
  
 Většina rozšíření značek, pokud se používá v syntaxi elementu objektu pro vyplnění elementu Property, by neměla mít obsah nebo žádnou další syntaxi elementu Property v rámci. Proto byste zavřeli značku prvku objektu a neposkytovali žádné podřízené prvky. Vždy, když je nalezen libovolný element objektu procesorem XAML, je volán konstruktor této třídy, který vytvoří instanci objektu vytvořeného z analyzovaného prvku. Třída rozšíření značek se neliší: Pokud chcete, aby bylo rozšíření značek použitelné v syntaxi elementu Object, je nutné poskytnout konstruktor bez parametrů. Některá existující rozšíření značek mají alespoň jednu požadovanou hodnotu vlastnosti, která musí být zadána pro efektivní inicializaci. Pokud ano, hodnota této vlastnosti je obvykle dána jako atribut vlastnosti prvku Object. V oboru názvů XAML (x:) [ V případě](../../xaml-services/xaml-namespace-x-language-features.md) jazykových funkcí a referenčních stránek [rozšíření WPF XAML](wpf-xaml-extensions.md) jsou uvedena rozšíření značek, která mají požadované vlastnosti (a názvy požadovaných vlastností). Referenční stránky také označují, zda je pro konkrétní rozšíření značek zakázána buď syntaxe elementu objektu, nebo syntaxe atributu. Významným případem je [rozšíření značek x:Array](../../xaml-services/x-array-markup-extension.md), které nepodporuje syntaxi atributu, protože obsah tohoto pole musí být zadaný v označení jako obsah. Obsah pole je zpracováván jako obecné objekty, proto není vhodný žádný výchozí konvertor typu pro atribut. [Rozšíření značek x:Array](../../xaml-services/x-array-markup-extension.md) vyžaduje `type` také parametr.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Obor názvů XAML (x:) Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
