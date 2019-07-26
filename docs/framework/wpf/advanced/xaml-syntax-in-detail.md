---
title: Podrobná syntaxe XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: 2c4e7213ddcffdb026d3d6e6b339bfc91b3c27c6
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400783"
---
# <a name="xaml-syntax-in-detail"></a>Podrobná syntaxe XAML
Toto téma definuje výrazy, které se používají k popisu prvků syntaxe jazyka XAML. Tyto výrazy se často používají během zbývající části této dokumentace, a to jak pro dokumentaci WPF, tak pro ostatní architektury, které používají XAML, nebo základní koncepty XAML povolené podporou jazyka XAML na úrovni System. XAML. Toto téma se rozbalí na základní terminologii představené v tématu [Přehled XAML (WPF)](xaml-overview-wpf.md).  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specifikace jazyka XAML  
 Terminologie syntaxe jazyka XAML definovaná zde je také definována nebo odkazována v rámci specifikace jazyka XAML. XAML je jazyk založený na XML a následuje nebo se rozšiřuje na strukturální pravidla XML. Některá z terminologie se sdílí z nebo je založena na terminologii, která se běžně používá, když popisuje jazyk XML nebo model objektu dokumentu XML.  
  
 Pokud chcete získat další informace o specifikaci jazyka XAML, stáhněte [ \[si MS\] -XAML](https://go.microsoft.com/fwlink/?LinkId=114525) z webu Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML a CLR  
 XAML je jazyk značek. Modul CLR (Common Language Runtime), jak je odvozený jeho název, umožňuje spuštění za běhu. Jazyk XAML není samotným jedním ze společných jazyků, které jsou přímo spotřebovány modulem runtime CLR. Místo toho si můžete kód XAML představit jako podpůrný systém svého vlastního typu. Konkrétní systém analýzy XAML, který je používán WPF, je postaven na CLR a systému typů CLR. Typy XAML jsou mapovány na typy CLR pro vytvoření instance běhového běhu při analýze XAML pro WPF. Z tohoto důvodu bude zbývající diskuze o syntaxi v tomto dokumentu obsahovat odkazy na systém typů CLR, a to i v případě, že ekvivalentní rozhovory syntaxe ve specifikaci jazyka XAML. (Na úrovni specifikace jazyka XAML mohou být typy XAML namapovány na jakýkoli jiný systém typů, který nemusí být CLR, ale to by vyžadovalo vytvoření a použití jiného analyzátoru XAML.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Členové typů a dědičnosti tříd  
 Vlastnosti a události tak, jak se zobrazují jako členy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML typu, jsou často děděny ze základních typů. Zvažte například tento příklad: `<Button Background="Blue" .../>`. Tato <xref:System.Windows.Controls.Control.Background%2A> vlastnost není okamžitě deklarovaná vlastnost <xref:System.Windows.Controls.Button> ve třídě, pokud byste se chtěli podívat na definici třídy, výsledky reflexe nebo dokumentaci. <xref:System.Windows.Controls.Control> Místo toho <xref:System.Windows.Controls.Control.Background%2A> je zděděn ze základní třídy.  
  
 Chování dědičnosti tříd prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML je významným odchodem z interpretace kódu XML vynucovaného schématu. Dědičnost tříd může být složitá, zejména v případě, že mezilehlé základní třídy jsou abstraktní nebo když jsou zapojená rozhraní. To je jeden z důvodů, proč sada prvků XAML a jejich přípustných atributů je obtížné reprezentovat přesně a kompletně pomocí typů schémat, které se obvykle používají [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pro programování, jako je například DTD nebo Formát XSD. Dalším důvodem je, že rozšiřitelnost a funkce mapování typů samotného jazyka XAML vylučuje úplnost jakékoli pevně reprezentace přípustných typů a členů.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Syntaxe elementů objektu  
 *Syntaxe elementu objektu* je syntaxe kódu XAML, která vytváří instanci CLR třídy nebo struktury DEKLARACÍ elementu XML. Tato syntaxe se podobá syntaxi elementu pro jiné jazyky označení, jako je například HTML. Syntaxe elementu objektu začíná levou ostrou závorkou (\<) následovaný bezprostředně názvem typu třídy nebo struktury, které se vytváří. Nula nebo více mezer může následovat za názvem typu a nula nebo více atributů může být také deklarováno v elementu Object, přičemž jeden nebo více mezer odděluje jednotlivé páry atributů Name = "hodnota". Nakonec musí být jedna z následujících hodnot pravdivá:  
  
- Element a tag musí být uzavřeny lomítkem (/) následovaným bezprostředně pravou ostrou závorkou (>).  
  
- Počáteční značka musí být dokončena pravou ostrou závorkou (>). Další prvky objektu, prvky vlastností nebo vnitřní text mohou následovat po počáteční značce. Přesně to, co může být obsaženo, je obvykle omezeno objektovým modelem elementu. Ekvivalentní uzavírací značka pro element Object musí existovat také ve správném vnořování a zůstatku s dalšími páry značek Open a závěrky.  
  
 Jazyk XAML, jak je implementován rozhraním .NET, obsahuje sadu pravidel, která mapují prvky objektů na typy, atributy na vlastnosti nebo události a obory názvů XAML na obory názvů CLR plus sestavení. Pro WPF a .NET Framework prvky objektu XAML mapují na [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] typy tak, jak jsou definovány v odkazovaných sestaveních a atributy jsou mapovány na členy těchto typů. Při odkazování typu CLR v jazyce XAML máte přístup i k zděděným členům tohoto typu.  
  
 Například následující příklad je syntaxe element objektu, který vytváří instanci nové instance <xref:System.Windows.Controls.Button> třídy a také <xref:System.Windows.FrameworkElement.Name%2A> určuje atribut a hodnotu pro tento atribut:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Následující příklad je syntaxe elementu objektu, která také obsahuje syntaxi vlastnosti obsahu XAML. Vnitřní text obsažený v rámci bude použit k nastavení <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox.Text%2A>vlastnosti obsahu XAML.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modely obsahu  
 Třída může podporovat použití jako prvek objektu XAML v souvislosti s syntaxí, ale tento prvek bude správně fungovat pouze v aplikaci nebo stránce, když je umístěn v očekávaném umístění celkového modelu obsahu nebo stromu elementu. Například <xref:System.Windows.Controls.MenuItem> by měl být obvykle umístěn jako podřízený <xref:System.Windows.Controls.Primitives.MenuBase> objekt odvozené třídy, jako je <xref:System.Windows.Controls.Menu>například. Modely obsahu pro konkrétní prvky jsou zdokumentovány jako součást poznámek na stránkách třídy pro ovládací prvky a další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, které lze použít jako prvky jazyka XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Vlastnosti prvků objektu  
 Vlastnosti v jazyce XAML jsou nastaveny pomocí nejrůznějších možných syntaxí. Která syntaxe se dá použít pro konkrétní vlastnost, se liší v závislosti na základních charakteristikách systému typů vlastnosti, kterou nastavujete.  
  
 Nastavením hodnot vlastností lze přidat funkce nebo vlastnosti do objektů, které jsou obsaženy v grafu objektu run time. Počáteční stav vytvořeného objektu z prvku objektu je založen na chování konstruktoru bez parametrů. Vaše aplikace obvykle používá jinou než zcela výchozí instanci libovolného daného objektu.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Syntaxe atributu (vlastnosti)  
 Syntaxe atributu je syntaxe kódu XAML, která nastavuje hodnotu pro vlastnost deklarováním atributu pro existující prvek objektu. Název atributu musí odpovídat názvu člena CLR vlastnosti třídy, která vrátí příslušný prvek objektu. Za názvem atributu následuje operátor přiřazení (=). Hodnota atributu musí být řetězec uzavřený v uvozovkách.  
  
> [!NOTE]
>  Pomocí střídajících se uvozovek můžete umístit literální znak citace do atributu. Například můžete použít jednoduché uvozovky jako způsob deklarace řetězce, který obsahuje znak dvojité uvozovky v rámci něj. Bez ohledu na to, jestli používáte jednoduché nebo dvojité uvozovky, byste měli použít párové dvojice pro otevření a zavření řetězce hodnoty atributu. K dispozici jsou také řídicí sekvence nebo jiné techniky, které jsou k dispozici pro práci s omezeními znaků zavedenými konkrétní syntaxí XAML. Viz [Entity znaků XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby bylo možné nastavit atribut pomocí syntaxe atributu, musí být vlastnost veřejná a musí být zapisovatelná. Hodnota vlastnosti v systému typů zálohování musí být typ hodnoty, nebo musí být odkazový typ, který může být vytvořen nebo odkazován procesorem XAML při přístupu k příslušnému typu zálohování.  
  
 Pro události WPF XAML musí být událost, na kterou se odkazuje jako na název atributu, veřejná a musí mít veřejný delegát.  
  
 Vlastnost nebo událost musí být členem třídy nebo struktury, které jsou vytvořeny pomocí elementu objektu, který jej obsahuje.  
  
### <a name="processing-of-attribute-values"></a>Zpracování hodnot atributů  
 Řetězcová hodnota obsažená v otevíracích a uzavíracích uvozovkách je zpracována procesorem XAML. U vlastností je výchozí chování zpracování určeno typem základní vlastnosti CLR.  
  
 Hodnota atributu je vyplněna jedním z následujících způsobů zpracování pomocí tohoto pořadí zpracování:  
  
1. Pokud procesor XAML narazí na složenou závorku nebo prvek objektu, který je odvozen z <xref:System.Windows.Markup.MarkupExtension>, pak je odkazované rozšíření značek nejprve vyhodnoceno, nikoli zpracování hodnoty jako řetězec a objekt vrácený příponou označení je použit jako osa. V mnoha případech je objekt vrácený příponou označení odkazem na existující objekt nebo výraz, který odloží vyhodnocení do doby běhu a není nově vytvořeným objektem.  
  
2. Je-li vlastnost deklarována s atributem <xref:System.ComponentModel.TypeConverter>nebo typ hodnoty této vlastnosti je deklarován s <xref:System.ComponentModel.TypeConverter>atributem, je řetězcová hodnota atributu odeslána do převaděče typu jako vstup převodu a konvertor vrátí Nová instance objektu.  
  
3. Pokud není <xref:System.ComponentModel.TypeConverter>k dispozici, dojde k pokusu o přímý převod na typ vlastnosti. Tato konečná úroveň je přímý převod na hodnotu analyzátoru Native mezi primitivními typy jazyka XAML nebo kontrolu názvů pojmenovaných konstant ve výčtu (Analyzátor pak přistupuje k hodnotám odpovídajícího typu).  
  
#### <a name="enumeration-attribute-values"></a>Hodnoty atributu výčtu  
 Výčty v jazyce XAML jsou zpracovávány vnitřně analyzátory XAML a členy výčtu by měly být zadány zadáním názvu řetězce jedné z pojmenovaných konstant výčtu.  
  
 U nepříznakních hodnot výčtu je nativní chování zpracování řetězce hodnoty atributu a jejich přeložení na jednu z hodnot výčtu. Neurčíte výčet ve *výčtu*Format. *Hodnota*, jak v kódu. Místo toho zadáte pouze *hodnotu*a *výčet* je odvozen podle typu vlastnosti, kterou nastavujete. Pokud zadáte atribut ve *výčtu*. Formulář *hodnoty* , nebude vyřešen správně.  
  
 Pro výčty flagwise je chování založené na <xref:System.Enum.Parse%2A?displayProperty=nameWithType> metodě. Pro výčet flagwise můžete zadat více hodnot tak, že každou hodnotu oddělíte čárkou. Nemůžete ale kombinovat hodnoty výčtu, které nejsou flagwise. Nemůžete například použít syntaxi čárky k pokusu o vytvoření <xref:System.Windows.Trigger> , který funguje na více podmínkách výčtu bez příznaku:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Výčty flagwise, které podporují atributy, které lze nastavit v jazyce XAML, jsou v subsystému WPF zřídka. Takový výčet je <xref:System.Windows.Media.StyleSimulations>však. Můžete například použít syntaxi atributu flagwise s oddělovači, abyste mohli upravit příklad uvedený v komentářích pro <xref:System.Windows.Documents.Glyphs> třídu; `StyleSimulations = "BoldSimulation"` může dojít`StyleSimulations = "BoldSimulation,ItalicSimulation"`k. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>je další vlastnost, kde lze zadat více než jednu hodnotu výčtu. Nicméně tato vlastnost se stane zvláštním případem, protože <xref:System.Windows.Input.ModifierKeys> výčet podporuje vlastní konvertor typu. Konvertor typu pro modifikátory používá znaménko plus (+) jako oddělovač místo čárky (,). Tento převod podporuje obecnější syntaxi pro reprezentaci kombinací kláves při programování systému Microsoft Windows, například CTRL + ALT.  
  
### <a name="properties-and-event-member-name-references"></a>Odkazy na vlastnosti a název člena události  
 Při zadávání atributu můžete odkazovat na jakoukoli vlastnost nebo událost, která existuje jako člen typu CLR, který je vytvořen pro objekt obsahující prvek.  
  
 Nebo můžete odkazovat na připojenou vlastnost nebo připojenou událost, nezávisle na objektu obsahujícího prvek. (Přiložené vlastnosti jsou popsány v nadcházející části.)  
  
 Jakoukoli událost můžete také pojmenovat z libovolného objektu, který je přístupný prostřednictvím výchozího oboru názvů pomocí *TypeName*. částečně kvalifikovaný název *události* ; Tato syntaxe podporuje připojení obslužných rutin pro směrované události, kde obslužná rutina zpracovává směrování událostí z podřízených prvků, ale nadřazený element tuto událost také nemá v tabulce členů. Tato syntaxe se podobá syntaxi připojené události, ale tato událost není skutečnou připojenou událostí. Místo toho odkazujete na událost s kvalifikovaným názvem. Další informace najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 V některých scénářích jsou názvy vlastností někdy k dispozici jako hodnota atributu namísto názvu atributu. Název této vlastnosti může také obsahovat kvalifikátory, jako je například vlastnost zadaná ve formě *OwnerType*. *vlastnost DependencyProperty*. Tento scénář je běžný při psaní stylů nebo šablon v jazyce XAML. Pravidla zpracování pro názvy vlastností, která jsou zadána jako hodnota atributu, jsou odlišná a řídí se typem vlastnosti nastavenou nebo chováním určitých subsystémů WPF. Podrobnosti najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).  
  
 Jiné použití pro názvy vlastností je, když hodnota atributu popisuje relaci vlastností vlastnost. Tato funkce se používá pro datové vazby a pro cíle scénáře a je povolena <xref:System.Windows.PropertyPath> třídou a jejím konvertorem typu. Úplnější popis sémantiky vyhledávání naleznete v tématu [PROPERTYPATH XAML Syntax](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Syntaxe elementu vlastnosti  
 *Syntaxe elementu vlastnosti* je syntaxe, která se poněkud odchyluje od základních pravidel syntaxe XML pro prvky. V jazyce XML je hodnota atributu de facto řetězec s jedinou možnou variací, který používá formát kódování řetězce. V jazyce XAML můžete přiřadit jiné prvky objektu jako hodnotu vlastnosti. Tato funkce je povolená syntaxí elementu vlastnosti. Namísto vlastnosti zadané jako atributu v rámci značky elementu je vlastnost zadána pomocí značky otevíracího elementu v *elementTypeName*. *PropertyName* – formulář, hodnota vlastnosti je určena v rámci a poté je zavřen prvek vlastnosti.  
  
 Konkrétně syntaxe začíná levou ostrou závorkou (\<) následovanou bezprostředně za názvem typu třídy nebo struktury, ve které je syntaxe elementu vlastnosti obsažena v. Následuje za ní bezprostředně jedna tečka (.), potom podle názvu vlastnosti a pak podle pravé lomené závorky (>). Stejně jako u syntaxe atributu musí tato vlastnost existovat v deklarovaných veřejných členech zadaného typu. Hodnota, která má být přiřazena vlastnosti, je obsažena v prvku vlastnosti. Obvykle je hodnota předána jako jeden nebo více prvků objektu, protože určením objektů jako hodnot je scénář, který je argumentem syntaxe elementu vlastnosti určena adresa. Nakonec ekvivalentní uzavírací značka, která určuje stejný *elementTypeName*. je nutné zadat kombinaci *PropertyName* ve správném vnořování a zůstatku s ostatními značkami elementu.  
  
 Například následující je syntaxe elementu vlastnosti pro <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Hodnota v rámci elementu vlastnosti může být také předána jako vnitřní text, v případech, kdy je typ vlastnosti určen jako primitivní typ hodnoty, například <xref:System.String>nebo výčet, kde je zadán název. Tato dvě použití jsou poněkud neobvyklá, protože každý z těchto případů může použít také jednodušší syntaxi atributu. Jeden scénář pro naplnění elementu Property s řetězcem je pro vlastnosti, které nejsou vlastností obsahu XAML, ale stále se používají pro reprezentace textu uživatelského rozhraní a specifické prázdné prvky, jako je například přeloženy, jsou požadovány pro zobrazení v tomto textu uživatelského rozhraní. Syntaxe atributu nemůže zachovat přeloženy, ale syntaxe elementu vlastnosti může být, pokud je aktivní zachování významného volného místa (podrobnosti najdete [v tématu Zpracování prázdných znaků v jazyce XAML](../../xaml-services/whitespace-processing-in-xaml.md)). Dalším scénářem je, že [direktiva x:UID –](../../xaml-services/x-uid-directive.md) lze použít na prvek vlastnosti, a tak označit hodnotu v rámci jako hodnotu, která by měla být lokalizována do výstupu WPF nebo jinými technikami.  
  
 Element Property není reprezentován v logickém stromu WPF. Prvek vlastnosti je pouze konkrétní syntaxí pro nastavení vlastnosti a není elementem, který obsahuje instanci nebo objekt, který ho má zálohovat. (Podrobnosti o konceptu logického stromu naleznete v tématu [stromy v](trees-in-wpf.md)subsystému WPF.)  
  
 Pro vlastnosti, kde jsou podporovány atributy atributu i elementu vlastnosti, mají tyto dvě syntaxe obvykle stejný výsledek, ačkoliv odlišností, jako je například zpracování prázdných míst, se může mírně lišit mezi syntaxmi.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Syntaxe kolekce  
 Specifikace jazyka XAML vyžaduje implementace procesoru XAML k identifikaci vlastností, kde typ hodnoty je kolekce. Obecná implementace procesoru XAML v rozhraní .NET je založena na spravovaném kódu a CLR a identifikuje typy kolekcí pomocí jedné z následujících akcí:  
  
- Implementuje <xref:System.Collections.IList>typ.  
  
- Implementuje <xref:System.Collections.IDictionary>typ.  
  
- Typ odvozeno z <xref:System.Array> (pro další informace o polích v jazyce XAML, viz [rozšíření značek x:Array](../../xaml-services/x-array-markup-extension.md).)  
  
 Pokud typ vlastnosti je kolekce, pak typ odvozený kolekce nemusí být specifikován v označení jako element Object. Místo toho prvky, které mají být položky v kolekci, jsou zadány jako jeden nebo více podřízených prvků prvku vlastnosti. Každá taková položka je vyhodnocena na objekt během načítání a přidána do kolekce voláním `Add` metody odvozené kolekce. Například <xref:System.Windows.Style.Triggers%2A> <xref:System.Windows.TriggerCollection>vlastnost přebírá specializovaný typ kolekce, který implementuje <xref:System.Collections.IList>. <xref:System.Windows.Style> Není nutné vytvářet instance <xref:System.Windows.TriggerCollection> elementu Object ve značce. Místo toho zadáte jednu nebo více <xref:System.Windows.Trigger> položek jako prvky `Style.Triggers` v rámci elementu Property, kde <xref:System.Windows.Trigger> (nebo odvozená třída) je typ očekávaný jako typ položky pro silně typované a implicitní <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Vlastnost může být typu kolekce i vlastností obsahu XAML pro daný typ a odvozené typy, které jsou popsány v další části tohoto tématu.  
  
 Implicitní prvek kolekce vytvoří člena v logickém znázornění stromové struktury, i když se nezobrazí v označení jako element. Obvykle konstruktor nadřazeného typu provádí instanci pro kolekci, která je jednou z jejích vlastností, a prvotní prázdná kolekce se stává součástí stromu objektu.  
  
> [!NOTE]
>  Obecný seznam a rozhraní slovníku (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro detekci kolekce. <xref:System.Collections.Generic.List%601> Třídu však můžete použít jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třídu, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 V referenčních stránkách .NET pro typy kolekcí je tato syntaxe s záměrné opomenutím elementu objektu pro kolekci občas uvedena v oddílech Syntaxe XAML jako implicitní syntaxe kolekce.  
  
 S výjimkou kořenového elementu je každý prvek objektu v souboru XAML, který je vnořen jako podřízený prvek jiného prvku, ve skutečnosti prvkem, který je jedním nebo oběma následujícími případy: člen vlastnosti implicitní kolekce nadřazeného elementu. nebo prvek, který určuje hodnotu vlastnosti obsahu XAML pro nadřazený element (vlastnosti obsahu XAML budou popsány v nadcházející části). Jinými slovy, vztah nadřazených prvků a podřízených prvků na stránce s označením je ve skutečnosti jeden objekt v kořenu a každý prvek objektu pod kořenem je buď jediná instance, která poskytuje hodnotu nadřazené vlastnosti, nebo jedna z položek v rámci sloupce. lection, což je také hodnota vlastnosti typu kolekce nadřazeného objektu. Tento koncept s jedním kořenovým adresářem je společný s XML a často se posiluje v chování rozhraní API, která načítají XAML <xref:System.Windows.Markup.XamlReader.Load%2A>, jako je například.  
  
 Následující příklad je syntaxe s prvkem objektu pro kolekci (<xref:System.Windows.Media.GradientStopCollection>) zadanou explicitně.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Všimněte si, že není vždy možné explicitně deklarovat kolekci. Například pokus o explicitní deklaraci <xref:System.Windows.TriggerCollection> v předchozím zobrazeném <xref:System.Windows.Style.Triggers%2A> příkladu selže. Explicitní deklarace kolekce vyžaduje, aby třída kolekce podporovala konstruktor bez parametrů a <xref:System.Windows.TriggerCollection> nemá konstruktor bez parametrů.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Vlastnosti obsahu XAML  
 Syntaxe obsahu XAML je syntaxe, která je povolena pouze pro třídy, které určují <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást jejich deklarace třídy. <xref:System.Windows.Markup.ContentPropertyAttribute> Odkazuje na název vlastnosti, která je vlastností obsahu pro daný typ elementu (včetně odvozených tříd). Při zpracování procesorem XAML budou všechny podřízené elementy nebo vnitřní text, které jsou nalezeny mezi otevírací a uzavírací značky elementu Object, přiřazeny jako hodnota vlastnosti obsahu XAML pro daný objekt. Je povoleno zadat explicitní prvky vlastností pro vlastnost Content, ale toto použití není obecně zobrazeno v oddílech Syntaxe XAML v referenci .NET. Metoda Explicit/verbose má příležitostnou hodnotu pro přehlednost kódu nebo jako druh značky, ale obvykle záměrem vlastnosti obsahu je zjednodušit označení tak, aby prvky, které lze intuitivním způsobem souvisejícím s nadřazeným a podřízeným, mohly být vnořeny přímo. Značky prvků vlastností pro jiné vlastnosti elementu nejsou přiřazeny jako "obsah" na striktní definici jazyka XAML; jsou zpracovávány dříve v pořadí zpracování analyzátoru XAML a nejsou považovány za "content".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Hodnoty vlastností obsahu XAML musí být souvislé.  
 Hodnota vlastnosti obsahu XAML musí být předána zcela před nebo zcela po všech ostatních prvcích vlastností na daném objektovém prvku. To platí bez ohledu na to, zda je hodnota vlastnosti obsahu XAML zadána jako řetězec, nebo jako jeden nebo více objektů. Například následující kód neanalyzuje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 To je v podstatě neplatné, protože pokud byla tato syntaxe vytvořena explicitně pomocí syntaxe elementu vlastnosti pro vlastnost Content, pak bude vlastnost content nastavena dvakrát:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobně neplatný příklad je, pokud je vlastnost content kolekce a podřízené prvky jsou procházejí s prvky vlastností:  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>Kombinované vlastnosti obsahu a syntaxe kolekce  
 Aby bylo možné přijmout více než jeden prvek objektu jako obsah, musí být typ vlastnosti obsahu specificky typem kolekce. Podobně jako syntaxe elementu vlastnosti pro typy kolekcí musí procesor XAML identifikovat typy, které jsou typy kolekcí. Pokud má element vlastnost obsahu XAML a typ vlastnosti obsahu XAML je kolekce, pak není nutné zadat typ implicitní kolekce v označení jako prvek objektu a vlastnost obsahu XAML není nutné zadávat jako El-Property. ement. Proto je možné, že obsahový model v označení nyní má přiřazen více než jeden podřízený prvek jako obsah. Následuje syntaxe obsahu pro <xref:System.Windows.Controls.Panel> odvozenou třídu. Všechny <xref:System.Windows.Controls.Panel> odvozené třídy vytvoří vlastnost obsahu XAML, která má <xref:System.Windows.Controls.Panel.Children%2A>být, což vyžaduje hodnotu typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Všimněte si, že ani element <xref:System.Windows.Controls.Panel.Children%2A> Property pro, <xref:System.Windows.Controls.UIElementCollection> ani element pro není v označení požadováno. Toto je návrhová funkce jazyka XAML tak, aby rekurzivní prvky, které definují a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , byly intuitivnější jako strom vnořených elementů s přímými vztahy mezi nadřazenými a podřízenými prvky, aniž by se musely zasáhnout značky prvků vlastností nebo objekty kolekce. Ve skutečnosti <xref:System.Windows.Controls.UIElementCollection> nelze zadat explicitně v označení jako prvek Object, a to designem. Vzhledem k tomu, že jeho zamýšlené použití je jako implicitní <xref:System.Windows.Controls.UIElementCollection> kolekce, nevystaví veřejný konstruktor bez parametrů, a proto nemůže být vytvořen jako prvek objektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Kombinování prvků vlastností a elementů objektů v objektu s vlastností obsahu  
 Specifikace jazyka XAML deklaruje, že procesor XAML může vynucuje, aby prvky objektu, které jsou použity k vyplnění vlastnosti obsahu XAML v rámci elementu Object, musí být souvislé a nesmí být smíšená. Toto omezení proti kombinování prvků vlastností a obsahu je vynutilo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesory XAML.  
  
 Podřízený prvek objektu můžete mít jako první Bezprostřední značku v rámci elementu Object. Pak můžete zavést prvky vlastností. Nebo můžete určit jeden nebo více prvků vlastností, pak obsah a další prvky vlastností. Ale jakmile prvek vlastnosti sleduje obsah, nelze zavést žádný další obsah, lze přidat pouze prvky vlastností.  
  
 Požadavek na řazení obsahu nebo vlastnosti se nevztahuje na vnitřní text použitý jako obsah. Je však stále dobrý styl značek pro zachování vnitřního textu souvisle, protože významné prázdné znaky budou obtížné detekovat vizuálně v kódu, pokud jsou prvky vlastností překryty vnitřním textem.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Obory názvů jazyka XAML  
 Žádná z předchozích příkladů syntaxe neurčila obor názvů XAML jiný než výchozí obor názvů XAML. V typických [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacích je výchozí obor názvů XAML určen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako obor názvů. Můžete zadat obory názvů XAML jiné než výchozí obor názvů XAML a nadále používat podobnou syntaxi. Ale potom kdekoli, kde je třída pojmenována, která není přístupná v rámci výchozího oboru názvů XAML, musí před název třídy být předpona oboru názvů XAML namapována na odpovídající obor názvů CLR. Například `<custom:Example/>` je syntaxe elementu objektu pro vytvoření instance instance `Example` třídy, kde obor názvů CLR obsahující tuto třídu (a případně i informace o externím sestavení, který obsahuje typy zálohování) byl dříve namapován na `custom` prefix.  
  
 Další informace o oborech názvů XAML naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 XAML definuje jazykovou entitu rozšíření značek, která umožňuje únik z normálního zpracování procesoru XAML pro hodnoty řetězcových atributů nebo prvků objektu a odkládá zpracování na záložní třídu. Znak, který identifikuje rozšíření značek pro procesor jazyka XAML při použití syntaxe atributu, je otevírací složená závorka ({) následovaná jakýmkoli znakem, který není uzavírací složená závorka (}). První řetězec následující za levou složenou závorku musí odkazovat na třídu, která poskytuje konkrétní chování rozšíření, kde odkaz může vynechat podřetězec "rozšíření", pokud je tento podřetězec součástí názvu skutečné třídy. Následně se může zobrazit jedna mezera a pak každý následující znak se použije jako vstup v rámci implementace rozšíření až do doby, než se narazí na pravou složenou závorku.  
  
 Implementace .NET XAML používá <xref:System.Windows.Markup.MarkupExtension> abstraktní třídu jako základ pro všechny přípony značek podporované nástrojem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a dalšími rozhraními nebo technologiemi. Rozšíření značek, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konkrétně implementují, mají často k dispozici prostředky pro odkazování na jiné existující objekty nebo pro odložení odkazů na objekty, které budou vyhodnoceny za běhu. Například jednoduchou datovou vazbu WPF je dosaženo `{Binding}` zadáním rozšíření označení místo hodnoty, kterou by určitá vlastnost měla obvykle trvat. Řada rozšíření značek WPF umožňuje syntaxi atributu pro vlastnosti, kde by jinak nebyla možná žádná syntaxe atributu. Například <xref:System.Windows.Style> objekt je poměrně komplexní typ, který obsahuje vnořenou řadu objektů a vlastností. Styly v jazyce WPF jsou obvykle definovány jako prostředek v <xref:System.Windows.ResourceDictionary>a poté odkazovány prostřednictvím jednoho ze dvou rozšíření pro označení WPF, která požadují prostředek. Rozšíření značek odloží vyhodnocení hodnoty vlastnosti na vyhledávání prostředků a povolí zadání hodnoty <xref:System.Windows.FrameworkElement.Style%2A> vlastnosti <xref:System.Windows.Style>v syntaxi atributu jako v následujícím příkladu:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 `StaticResource` Zde<xref:System.Windows.StaticResourceExtension> identifikuje třídu, která poskytuje implementaci rozšíření značek. Následující řetězec `MyStyle` je použit jako vstup pro nevýchozí <xref:System.Windows.StaticResourceExtension> konstruktor, kde parametr, který je pořízen z řetězce přípony, deklaruje požadované <xref:System.Windows.ResourceKey>. `MyStyle`očekává se, že bude [](../../xaml-services/x-key-directive.md) hodnota <xref:System.Windows.Style> x:Key – definovaná jako prostředek. Použití [rozšíření značek StaticResource](staticresource-markup-extension.md) vyžaduje, aby se prostředek použil k poskytnutí <xref:System.Windows.Style> hodnoty vlastnosti prostřednictvím logiky vyhledávání statických prostředků v době načítání.  
  
 Další informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md). Odkaz na rozšíření značek a jiné programovací funkce XAML povolené v obecné implementaci .NET XAML naleznete v tématu [obor názvů XAML (x:). Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md). Pro rozšíření značek specifická pro WPF naleznete informace v tématu [rozšíření WPF XAML](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Přidružené vlastnosti  
 Připojené vlastnosti jsou programovací pojem představený v jazyce XAML, který umožňuje vlastnictví a definování vlastností konkrétního typu, ale nastavuje se jako atributy nebo prvky vlastností libovolného elementu. Primární scénář, pro který jsou připojené vlastnosti určeny, je povolit podřízeným elementům ve struktuře značek, aby byly informace na nadřazený element, aniž by bylo nutné mít rozsáhlý model sdíleného objektu napříč všemi prvky. Naopak připojené vlastnosti mohou být použity nadřazenými prvky k hlášení informací podřízeným elementům. Další informace o účelu připojených vlastností a o tom, jak vytvořit vlastní připojené vlastnosti, najdete v tématu [připojené vlastnosti – přehled](attached-properties-overview.md).  
  
 Připojené vlastnosti používají syntaxi, která napodobuje syntaxi elementu vlastnosti v tom, že zadáte také *TypeName*. kombinace *PropertyName* . Existují dva důležité rozdíly:  
  
- Můžete použít *TypeName*. parametr *PropertyName* i při nastavení připojené vlastnosti prostřednictvím syntaxe atributu Připojené vlastnosti jsou jediným případem, kde je název vlastnosti kvalifikován, je požadavek v syntaxi atributu.  
  
- Můžete také použít syntaxi elementu Property pro připojené vlastnosti. Pro typickou syntaxi prvku vlastnosti však zadaný název *TypeName* je prvek Object, který obsahuje element Property. Pokud odkazujete na připojenou vlastnost, pak *TypeName* je třída, která definuje připojenou vlastnost, nikoli objekt obsahující element.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Přidružené události  
 Připojené události jsou další programovací pojem představený v jazyce XAML, kde mohou být události definovány konkrétním typem, ale obslužné rutiny mohou být připojeny na libovolný prvek objektu. V implementaci WOF je často typ, který definuje připojenou událost, statický typ, který definuje službu, a někdy jsou tyto připojené události vystavené aliasem směrované události v typech, které tuto službu zveřejňují. Obslužné rutiny pro připojené události jsou zadány prostřednictvím syntaxe atributu. Stejně jako u připojených událostí je syntaxe atributu rozbalena pro připojené události, aby bylo možné použít *TypeName*. *EventName* Usage, kde *TypeName* je třída, která poskytuje `Add` a `Remove` přístupové objekty obslužné rutiny události pro připojenou infrastrukturu událostí a *EventName* je název události.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie kořenového elementu XAML  
 V následující tabulce je zobrazen typický kořenový prvek XAML, který zobrazuje konkrétní atributy kořenového prvku:  
  
|||  
|-|-|  
|`<Page`|Otevření elementu objektu kořenového elementu|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Výchozí ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) obor názvů XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Obor názvů XAML jazyka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Částečná deklarace třídy, která připojuje značky k jakémukoli kódu na pozadí definovanému pro částečnou třídu|  
|`>`|Konec elementu objektu pro kořen Objekt ještě není uzavřen, protože element obsahuje podřízené elementy.|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Volitelné a nedoporučené použití XAML  
 Následující části popisují použití XAML, která jsou technicky podporována procesory XAML, ale která vytváří podrobné možnosti nebo jiné estetické problémy, které jsou v konfliktu se soubory jazyka XAML, když vyvíjíte aplikace, které obsahují zdroje XAML.  
  
### <a name="optional-property-element-usages"></a>Volitelné použití prvků vlastností  
 Volitelné použití prvků vlastností zahrnuje explicitní zápis vlastností obsahu elementu, které procesor XAML považuje za implicitní. <xref:System.Windows.Controls.Menu>Například při deklaraci obsahu, se můžete rozhodnout explicitně <xref:System.Windows.Controls.ItemsControl.Items%2A> deklarovat `<Menu.Items>` kolekci <xref:System.Windows.Controls.Menu> jako značku prvku vlastnosti a umístit každou <xref:System.Windows.Controls.MenuItem> v rámci `<Menu.Items>`místo než použijete implicitní chování procesoru XAML, že všechny podřízené elementy <xref:System.Windows.Controls.Menu> musí <xref:System.Windows.Controls.MenuItem> být <xref:System.Windows.Controls.ItemsControl.Items%2A> a umístěné v kolekci. Někdy mohou volitelné používání pomáhat vizuálně objasnit strukturu objektu, jak je znázorněno v označení. Nebo někdy explicitní použití prvku vlastnosti se může vyhnout kódu, který je technicky funkční, ale vizuálně matoucí, jako jsou například vnořená rozšíření značek v rámci hodnoty atributu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Úplný název typu typeName. Members – kvalifikované atributy  
 *TypeName*. formulář *člena* pro atribut ve skutečnosti pracuje obecnější, než pouze směrovaný případ události. V jiných situacích je však formulář nadbytečný a měli byste se vyhnout, pokud jde pouze o důvody pro styl značek a čitelnost. V následujícím příkladu jsou všechny tři odkazy na <xref:System.Windows.Controls.Control.Background%2A> atribut zcela ekvivalentní:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`funguje, protože kvalifikované vyhledávání pro tuto vlastnost na <xref:System.Windows.Controls.Button> je úspěšné (<xref:System.Windows.Controls.Control.Background%2A> bylo zděděno z ovládacího prvku <xref:System.Windows.Controls.Button> ) a je třída elementu objektu nebo základní třídy. `Control.Background`funguje, protože <xref:System.Windows.Controls.Control> třída je ve <xref:System.Windows.Controls.Control.Background%2A> skutečnosti <xref:System.Windows.Controls.Control> definována a <xref:System.Windows.Controls.Button> je základní třídou.  
  
 Nicméně následující *TypeName*. Příklad formuláře *člena* nefunguje a je tak zobrazen s komentářem:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>je jinou odvozenou třídou třídy <xref:System.Windows.Controls.Control>, a pokud jste zadali `Label.Background` v <xref:System.Windows.Controls.Label> rámci prvku objektu, toto použití by fungovalo. Vzhledem k tomu <xref:System.Windows.Controls.Label> , že se nejedná o třídu nebo <xref:System.Windows.Controls.Button>základní třídu třídy, je v zadaném chování procesoru XAML `Label.Background` zpracována jako připojená vlastnost. `Label.Background`není dostupná připojená vlastnost a toto použití se nezdařilo.  
  
### <a name="basetypenamemembername-property-elements"></a>baseType. Member – vlastnost Elements  
 Podobným způsobem jako *TypeName*.  atribut membere pracuje pro syntaxi atributu, *BaseType*. syntaxe *Member* je funkční pro syntaxi elementu vlastnosti. Například následující syntaxe funguje:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Zde byl prvek vlastnosti zadán `Control.Background` , i když byl element Property obsažen v. `Button`  
  
 Ale stejně jako *TypeName*. formulář *Member* pro atributy, *BaseType* *člen* má špatný styl ve značce a Vy byste se ho měli vyhnout.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Obor názvů XAML (x:) Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [TypeConverters a XAML](typeconverters-and-xaml.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
