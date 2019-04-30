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
ms.openlocfilehash: 46539f0cfdcc478e2f5e4cd7aecf16ac059e6332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804582"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozšíření značek a WPF XAML
Toto téma zavádí koncepci rozšíření značek pro XAML, včetně jejich syntaxe pravidla, účelu a model objektu třídy, které je základem je. Rozšíření značek jsou obecné funkce jazyka XAML a implementace .NET XAML služeb. Toto téma podrobně popisuje konkrétně – rozšíření značek pro použití v WPF XAML.  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML procesory a rozšíření značek  
 Obecně řečeno analyzátoru XAML může buď interpretovat hodnotu atributu jako řetězcový literál, který lze převést na primitivní nebo převeďte jej na objekt některé prostředky. Jedním z těchto prostředků je odkazem konvertor typu; je to popsané v tématu [TypeConverters a XAML](typeconverters-and-xaml.md). Existují ale scénáře, ve kterém jsou vyžadována různé chování. Například může být nastavena procesoru XAML, že hodnota atributu by se neměly zobrazit nový objekt v grafu objektů. Místo toho atribut by měl mít za následek grafu objektu, který odkazuje na objekt už vytvořeného v jiné části grafu nebo statický objekt. Další možností je, že procesor XAML můžete nastaven na použití syntaxe, která obsahuje jiné než výchozí argumenty pro konstruktor objektu. Toto jsou typy scénáře, ve kterém rozšíření značek můžete zadat toto řešení.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Rozšíření syntaxe základní značek  
 Rozšíření značek, je možné implementovat k poskytnutí hodnot pro vlastnosti využití atribut, vlastnosti v použití elementu vlastnosti nebo obojí.  
  
 Při použití zadejte hodnotu atributu, syntaxe, která odlišuje posloupnosti rozšíření značek XAML procesoru je přítomnost levou a pravou složenou závorkou ({a}). Typ – rozšíření značek je pak identifikován řetězec s tokenem hned za otevírající složenou závorku.  
  
 Při použití v syntax prvku vlastnosti, rozšíření značek je vizuálně shodný s jakýmkoli jiným prvkem, který se používá k poskytování hodnoty vlastnosti elementu: deklaraci elementu XAML, který odkazuje třída rozšíření značek jako element, uzavřené v lomených závorkách (<> ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek XAML definovaný  
 Existuje několik rozšíření značek, které nejsou specifické pro implementaci WPF XAML, ale místo toho jsou implementace vnitřní objekty nebo funkce XAML jako jazyk. Tato rozšíření značek jsou implementovány v oboru názvů System.Xaml sestavení jako součást obecné rozhraní .NET Framework XAML services a jsou v rámci oboru názvů XAML jazyka XAML. Z hlediska běžné použití značky jsou obvykle poznáte ho podle těchto rozšíření značek `x:` předponu ve využití. <xref:System.Windows.Markup.MarkupExtension> Poskytuje základní třídu (také definované v oboru názvů System.Xaml) vzor, který všechna rozšíření značek by měl používat, aby byla podporována v XAML čtečky a zapisovače XAML, včetně v WPF XAML.  
  
- `x:Type` dodává <xref:System.Type> objekt s názvem typu. Toto zařízení se nejčastěji používá v styly a šablony. Podrobnosti najdete v tématu [x: Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md).  
  
- `x:Static` vytváří statické hodnoty. Hodnoty pocházejí z typu hodnoty kódu entity, které nejsou přímo typu cílovou vlastnost hodnotu, ale lze vyhodnotit na typu. Podrobnosti najdete v tématu [x: Static – rozšíření značek](../../xaml-services/x-static-markup-extension.md).  
  
- `x:Null` Určuje `null` jako hodnotu pro vlastnost a lze je použít pro atributy nebo element hodnoty vlastností. Podrobnosti najdete v tématu [x: Null – rozšíření značek](../../xaml-services/x-null-markup-extension.md).  
  
- `x:Array` poskytuje podporu pro vytváření obecné polí v syntaxe XAML pro případy, kde kolekce podporu poskytuje základní prvky WPF a ovládací prvek modelů je záměrně nepoužívá se. Podrobnosti najdete v tématu [x: Array – rozšíření značek](../../xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Předpona se používá pro typické mapování oboru názvů XAML uvnitř jazyka XAML, v kořenového elementu souboru XAML nebo produkčního prostředí. Například zahájit šablony sady Visual Studio pro aplikace WPF XAML soubor pomocí tohoto `x:` mapování. Můžete se rozhodnout token jinou předponu ve vlastním XAML mapování oboru názvů, ale tato dokumentace se předpokládá výchozí `x:` mapování jako způsob identifikace těchto entit, které jsou definované součástí oboru názvů XAML pro jazyk XAML, nikoli do modulu WPF výchozí obor názvů nebo jiných oborech názvů XAML nesouvisí s konkrétním rozhraním.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozšíření značek specifické pro WPF  
 Nejčastěji používané přípony označení používá při programování pro WPF jsou ty, které podporují odkazy na prostředky (`StaticResource` a `DynamicResource`) a ty, které podporují vytváření datových vazeb (`Binding`).  
  
- `StaticResource` poskytuje hodnotu pro vlastnost nahrazením hodnoty již definovaných prostředků. A `StaticResource` hodnocení, takže v konečném důsledku se provádí v okamžiku načtení XAML a nemá přístup do grafu objektu v době běhu. Podrobnosti najdete v tématu [– rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- `DynamicResource` poskytuje hodnotu pro vlastnost odložením tato hodnota bude za běhu referenci na prostředek. Dynamický prostředek odkaz vynutí nové vyhledávání pokaždé, když, že takový prostředek přistupuje a má přístup k grafu objektů v době běhu. Pokud chcete získat přístup, `DynamicResource` koncept podporuje vlastnosti závislosti v systému vlastností WPF a vyhodnocení výrazů. Proto můžete použít pouze `DynamicResource` pro cílovou vlastnost závislosti. Podrobnosti najdete v tématu [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md).  
  
- `Binding` poskytuje že hodnotu pro vlastnost, pomocí kontextu dat, která se vztahuje na nadřazený objekt v době běhu s vazbou na data. Tohoto rozšíření značek je poměrně složité, protože umožňuje podstatné vložená syntaxe pro určení datové vazby. Podrobnosti najdete v tématu [vazby – rozšíření značek](binding-markup-extension.md).  
  
- `RelativeSource` poskytuje informace o zdroji <xref:System.Windows.Data.Binding> , které se můžete dostat několika možných relací v rámci stromů objektů za běhu. Získáte specializovaná sourcing u vazeb, které jsou vytvořena ve více použití šablon nebo v kódu bez znalostí okolního strom objektů. Podrobnosti najdete v tématu [rozšíření značek RelativeSource](relativesource-markupextension.md).  
  
- `TemplateBinding` Umožňuje použít hodnoty vlastností bez vizuálního vzhledu, které pocházejí z objektu modelu definované vlastnosti třídy, která bude použita šablona šablony ovládacího prvku. Jinými slovy vlastnosti v rámci definice šablony mají přístup k kontext, který existuje pouze když je šablona použita. Podrobnosti najdete v tématu [– rozšíření značek TemplateBinding](templatebinding-markup-extension.md). Další informace o praktické použití `TemplateBinding`, naleznete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap` podporuje relativně pokročilý scénář pro vytváření bitových kopií. Podrobnosti najdete v tématu [– rozšíření značek ColorConvertedBitmap](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey` a `ThemeDictionary` podporují aspektů vyhledání prostředku, zejména pro prostředky a motivy, které jsou součástí vlastní ovládací prvky. Další informace najdete v tématu [– rozšíření značek ComponentResourceKey](componentresourcekey-markup-extension.md), [– rozšíření značek ThemeDictionary](themedictionary-markup-extension.md), nebo [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Rozšíření třídy  
 Obecné jazyka XAML i specifické pro WPF – rozšíření značek, je identifikován chování jednotlivých – rozšíření značek XAML procesoru prostřednictvím `*Extension` třídu odvozenou od <xref:System.Windows.Markup.MarkupExtension>a poskytuje implementaci <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> Metoda. Tato metoda v každé rozšíření obsahuje objekt, který je vrácen při vyhodnocování rozšíření značek. Vrácený objekt je obvykle vyhodnocen podle různých řetězec tokeny, které jsou předány do rozšíření značek.  
  
 Například <xref:System.Windows.StaticResourceExtension> třída poskytuje surface implementaci vlastního prostředku vyhledávání tak, aby jeho <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementace vrátí objekt, který je požadovaný se vstupem tuto konkrétní implementaci je řetězec, který se používá k vyhledat zdroj podle jeho `x:Key`. Velká část těchto podrobných informací implementace není důležitý, pokud používáte existující rozšíření značek.  
  
 Některé přípony označení nepoužívejte řetězec tokenu argumenty. Toto je vzhledem k tomu, že vracejí hodnotu statické nebo konzistentní vzhledem k aplikacím nebo protože je k dispozici prostřednictvím jedné služby předává kontext pro jakou hodnotu má být vrácen `serviceProvider` parametru.  
  
 `*Extension` Vzor pro pojmenování se pro pohodlí a konzistence. Není nutné v pořadí pro procesor identifikovat tuto třídu jako podpora pro rozšíření značek XAML. Tak dlouho, dokud vašeho základu kódu obsahuje oboru názvů System.Xaml a používá rozhraní .NET Framework XAML Services implementace, všechny možnosti, které je potřeba získat renomé jako rozšíření značek XAML je odvozena z <xref:System.Windows.Markup.MarkupExtension> a pro podporu syntaxe konstrukce. Povolení rozšíření třídy značek, které se neřídí definuje WPF `*Extension` pojmenování vzor, například <xref:System.Windows.Data.Binding>. Obvykle důvodem je, že třída podporuje scénáře kromě čistě značek rozšíření podpory. V případě třídy <xref:System.Windows.Data.Binding>, že třída podporuje přístup k metodám a vlastnostem objektu pro scénáře, které nesouvisí s XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Rozšíření třídy výklad inicializace Text  
 Řetězec tokenů následující rozšíření značek, název a stále v rámci složené závorky jsou interpretovány procesorem XAML v jednom z následujících způsobů:  
  
- Čárkou vždy představuje oddělovač nebo oddělovač jednotlivé tokeny.  
  
- Pokud jednotlivé oddělených tokenů neobsahují žádné symboly rovná se, považuje za každý token jako argument konstruktoru. Každý parametr konstruktoru se musí předávat typ, byl očekáván podpis a ve správném pořadí očekávání tím, že k podpisu.  
  
    > [!NOTE]
    >  Procesor XAML musí volat konstruktor, který odpovídá argumentu počtu dvojice. Z tohoto důvodu se při implementaci rozšíření vlastních značek, se neposkytuje více konstruktorů s stejný počet argumentů. Chování pro chování XAML procesoru, pokud existuje více než jeden konstruktor cestu k rozšíření značek se stejný počet parametrů není definován, ale měli očekáváte, že procesor XAML oprávnění k vyvolání výjimky na využití, pokud tato situace existuje v definice typu rozšíření značek.  
  
- Pokud oddělené jednotlivých tokeny obsahovat symboly rovná se a potom XAML procesoru nejprve volá výchozí konstruktor pro rozšíření značek. Potom každý pár název = hodnota interpretována jako název vlastnosti, která existuje na rozšíření značek a hodnota pro přiřazení k dané vlastnosti.  
  
- Pokud je výsledkem paralelní mezi chování konstruktor a vlastnost nastavení chování v příponě označení, nezáleží chování, které používáte. Je běžné použití používat *vlastnost*`=`*hodnotu* páry u parametru rozšíření značek, které mají více než jednu nastavitelnou vlastnost, pokud je to pouze, protože je váš kód více úmyslné a vy jste méně pravděpodobné, že omylem transponuje parametry konstruktoru. (Pokud zadáte vlastnost = dvojice hodnot, tyto vlastnosti mohou být v libovolném pořadí.) Také není zaručeno, že rozšíření značek poskytuje parametr konstruktoru, který nastaví každý, jeho nastavitelné vlastnosti. Například <xref:System.Windows.Data.Binding> je rozšíření značek, mnoho vlastností, které je možné prostřednictvím rozšíření v *vlastnost*`=`*hodnotu* formuláře, ale <xref:System.Windows.Data.Binding> podporuje pouze dvě konstruktory: výchozí konstruktor a ten, který nastaví počáteční cestu.  
  
- Rozšíření značek bez escapement nelze předat literálu čárkami.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Řídicí sekvence a rozšíření značek  
 Zpracování v editoru XAML atribut používá složené závorky jako indikátory pořadí rozšíření značek. Je také možné vytvořit hodnotu literálu složenou závorku znak atributu v případě potřeby tak, že zadáte sekvence escape pomocí páru prázdné složené závorky, za nímž následuje literálu složenou závorku. Zobrazit [ {} řídicí sekvence – rozšíření značek](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Vnoření – rozšíření značek XAML využití  
 Je podporováno vnoření více rozšíření značek a každý – rozšíření značek se vyhodnotí nejhlubší nejprve. Zvažte například následující použití:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 V tomto použití `x:Static` příkaz je vyhodnocen jako první a vrátí hodnotu typu string. Řetězec je pak použít jako argument pro `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozšíření značek a Syntax prvku vlastnosti  
 Když se použije jako element objektu, který vyplní hodnotu vlastnosti elementu, je třída rozšíření značek vizuálně nerozeznatelná od element typické podporovaný typ objektu, který lze použít v XAML. Praktické rozdíl mezi typické objekt elementu a rozšíření značek je, že rozšíření značek je vyhodnocen na hodnotu typu nebo odloženo jako výraz. Proto mechanismy pro všechny chyby možných typů hodnot vlastností pro rozšíření značek budou různé, podobně jako jak vlastnost s pozdní vazbou zpracovávají v jiných programovacích modelů. Element běžné objektu se vyhodnotí pro typ metodu match pro vlastnost target, který je nastavení, když je analyzován XAML.  
  
 Většina rozšíření značek při použití v syntaxi elementu objektu tak, aby vyplnil prvek vlastnosti nemusí syntax prvku vlastnosti obsahu nebo dalších v rámci. Proto by zavření značky elementu objektu a poskytovat žádné podřízené prvky. Pokaždé, když procesorem XAML nalezen element libovolný objekt, se nazývá konstruktor pro danou třídu, která vytvoří instanci objektu vytvořeného z analyzovaného elementu. Třída rozšíření značek se nijak neliší: Pokud chcete být použitelné v syntaxi elementu objektu rozšíření značek, je nutné zadat výchozí konstruktor. Některá existující rozšíření značek mají alespoň jednu hodnotu požadovanou vlastnost, musí být zadané pro platné inicializace. Pokud ano, tuto hodnotu vlastnosti obvykle uvedeny jako vlastnost atributu na elementu objektu. V [Namespace XAML (x:) Funkce jazyka](../../xaml-services/xaml-namespace-x-language-features.md) a [rozšíření WPF XAML](wpf-xaml-extensions.md) odkazují na stránky, značky, bude zaznamenán rozšíření, které mají požadované vlastnosti (a názvy požadovaných vlastností). Stránky s referenčními informacemi bude Všimněte si také, pokud rozšíření konkrétní značek není povolena syntaxe elementu objektu nebo syntaxe atributu. Je důležité případ [x: Array – rozšíření značek](../../xaml-services/x-array-markup-extension.md), který nepodporuje syntaxe atributu, protože obsah pole musí být určeny označování jako obsah. Obsah pole jsou zpracovány jako obecné objekty, proto je vhodná žádný výchozí převaděč typu atributu. Navíc [x: Array – rozšíření značek](../../xaml-services/x-array-markup-extension.md) vyžaduje `type` parametru.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Namespace XAML (x:) Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
