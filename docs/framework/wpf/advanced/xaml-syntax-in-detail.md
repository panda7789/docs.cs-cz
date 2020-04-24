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
ms.openlocfilehash: 5f8bb862ce443fd7397036b10f69cda65a6960bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646148"
---
# <a name="xaml-syntax-in-detail"></a>Podrobná syntaxe XAML
Toto téma definuje termíny, které se používají k popisu prvků syntaxe XAML. Tyto termíny se často používají ve zbývající části této dokumentace, a to jak pro wpf dokumentaci konkrétně a pro ostatní rámce, které používají XAML nebo základní xaml koncepty povolené podporou jazyka XAML na úrovni System.Xaml. Toto téma rozšiřuje základní terminologii zavedenou v tématu [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>Specifikace jazyka XAML  
 Zde definovaná syntaxe XAML je také definována nebo odkazována ve specifikaci jazyka XAML. XAML je jazyk založený na XML a následuje nebo rozšiřuje strukturální pravidla XML. Některé terminologie jsou sdíleny z terminologie běžně používané při popisu jazyka XML nebo objektového modelu dokumentu XML nebo jsou založeny na ní.  
  
 Další informace o specifikaci jazyka XAML získáte stažením [ \[ms-xaml\] ](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) ze služby Stažení softwaru.  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML a CLR  
 XAML je značkovací jazyk. Běžný jazyk runtime (CLR), jak je uvedeno jeho název, umožňuje spuštění za běhu. XAML není sám o sobě jedním z běžných jazyků, který je přímo spotřebován runtime CLR. Místo toho si můžete myslet XAML jako podporu vlastního systému typu. Konkrétní systém analýzy XAML, který používá WPF, je postaven na clr a systému typu CLR. XAML typy jsou mapovány na typy CLR k vytvoření instance reprezentace běhu při analýzy XAML pro WPF. Z tohoto důvodu bude zbývající část diskuse o syntaxi v tomto dokumentu obsahovat odkazy na systém typu CLR, přestože ekvivalentní diskuse o syntaxi ve specifikaci jazyka XAML nejsou. (Na úrovni specifikace jazyka XAML mohou být typy XAML mapovány na jiný typový systém, který nemusí být CLR, ale který by vyžadoval vytvoření a použití jiného analyzátoru XAML.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Členové typů a dědičnosti tříd  
 Vlastnosti a události tak, jak se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zobrazují jako členy XAML typu, jsou často zděděny ze základních typů. Zvažte například tento `<Button Background="Blue" .../>`příklad: . Vlastnost <xref:System.Windows.Controls.Control.Background%2A> není okamžitě deklarované <xref:System.Windows.Controls.Button> vlastnosti na třídu, pokud jste se podívat na definici třídy, výsledky reflexe nebo dokumentaci. Místo <xref:System.Windows.Controls.Control.Background%2A> toho je zděděn ze základní <xref:System.Windows.Controls.Control> třídy.  
  
 Chování dědičnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy prvků XAML je významným odklonem od interpretace značek XML vynucených schématem. Dědičnost třídy může být složitá, zejména pokud jsou zprostředkující základní třídy abstraktní nebo pokud se jedná o rozhraní. To je jeden z důvodů, že sada prvků XAML a jejich přípustné atributy je obtížné přesně a úplně reprezentovat pomocí typů schématu, které se obvykle používají pro programování XML, jako je například formát DTD nebo XSD. Dalším důvodem je, že rozšiřitelnost a funkce mapování typů samotného jazyka XAML vylučují úplnost jakékoli pevné reprezentace přípustných typů a členů.  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>Syntaxe prvku objektu  
 *Syntaxe prvku objektu* je syntaxe značek XAML, která inkasuje třídu nebo strukturu CLR deklarováním elementu XML. Tato syntaxe se podobá syntaxi elementu jiných značkovacích jazyků, jako je například HTML. Syntaxe prvku objektu začíná levou\<úhlovou závorkou ( ), za níž bezprostředně následuje název typu instance třídy nebo struktury. Nula nebo více mezer může následovat název typu a nula nebo více atributů může být také deklarována na elementu objektu, s jedním nebo více mezerami oddělujícími každý pár atributů name="value". Nakonec musí být splněna jedna z následujících skutečností:  
  
- Prvek a štítek musí být uzavřeny lomítkem (/) následovaným okamžitě pravou úhlovou závorkou (>).  
  
- Otevírací značka musí být doplněna pravým úhlem (>). Další prvky objektu, prvky vlastností nebo vnitřní text mohou následovat počáteční značku. Přesně jaký obsah zde může být obsažen, je obvykle omezen objektovým modelem prvku. Ekvivalentní uzavírací značka pro prvek objektu musí také existovat, ve správném vnoření a vyvážení s ostatními dvojicemi otevírací a uzavírací značky.  
  
 XAML implementované rozhraním .NET má sadu pravidel, která mapují prvky objektu do typů, atributů do vlastností nebo událostí a obory názvů XAML do oborů názvů CLR plus sestavení. Pro WPF a .NET, XAML objektové prvky mapovat na typy .NET, jak je definováno v odkazovaných sestaveních a atributy mapovat na členy těchto typů. Při odkazu na typ CLR v XAML, máte přístup k zděděné členy tohoto typu také.  
  
 Například následující příklad je syntaxe elementu objektu, která <xref:System.Windows.Controls.Button> inkonfikuje <xref:System.Windows.FrameworkElement.Name%2A> novou instanci třídy a také určuje atribut a hodnotu pro tento atribut:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Následující příklad je syntaxe elementu objektu, která obsahuje také syntaxi vlastnosti obsahu XAML. Vnitřní text obsažený v písmenu a) bude použit k nastavení vlastnosti <xref:System.Windows.Controls.TextBox> obsahu XAML <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modely obsahu  
 Třída může podporovat použití jako prvek objektu XAML z hlediska syntaxe, ale tento prvek bude fungovat správně pouze v aplikaci nebo na stránce, pokud je umístěn v očekávané pozici modelu celkového obsahu nebo stromu prvků. Například <xref:System.Windows.Controls.MenuItem> by měl být obvykle umístěn pouze <xref:System.Windows.Controls.Primitives.MenuBase> jako podřízený <xref:System.Windows.Controls.Menu>z odvozené třídy, jako je například . Modely obsahu pro určité prvky jsou dokumentovány jako součást poznámek na stránkách třídy pro ovládací prvky a další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, které lze použít jako prvky XAML.  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>Vlastnosti prvků objektu  
 Vlastnosti v XAML jsou nastaveny řadou možných syntaxí. Syntaxe, kterou lze použít pro určitou vlastnost, se bude lišit v závislosti na základních charakteristikách systému typu vlastnosti, kterou nastavujete.  
  
 Nastavením hodnot vlastností přidáte prvky nebo charakteristiky k objektům tak, jak existují v grafu objektů běhu. Počáteční stav vytvořeného objektu z prvku objektu je založen na chování konstruktoru bez parametrů. Aplikace obvykle použije něco jiného než zcela výchozí instanci daného objektu.  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>Syntaxe atributu (vlastnosti)  
 Syntaxe atributu je syntaxe značek XAML, která nastavuje hodnotu vlastnosti deklarováním atributu existujícího prvku objektu. Název atributu se musí shodovat s názvem člena CLR vlastnosti třídy, která podporuje příslušný prvek objektu. Za názvem atributu následuje operátor přiřazení (=). Hodnota atributu musí být řetězec uzavřený v uvozovkách.  
  
> [!NOTE]
> Střídání uvozovek můžete použít k umístění literálu uvozovky do atributu. Například můžete použít jednoduché uvozovky jako prostředek k deklarování řetězec, který obsahuje znak dvojité uvozovky v něm. Bez ohledu na to, zda používáte jednoduché nebo dvojité uvozovky, měli byste použít odpovídající dvojici pro otevření a zavření řetězce hodnoty atributu. K dispozici jsou také únikové sekvence nebo jiné techniky pro práci kolem omezení znaků, které jsou uloženy libovolnou konkrétní syntaxí XAML. Viz [Entity znaků XML a XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Aby bylo možné nastavit prostřednictvím syntaxe atributu, vlastnost musí být veřejné a musí být zapisovatelné. Hodnota vlastnosti v systému typu zálohování musí být typ hodnoty nebo musí být typ odkazu, který může být vytvořena instance nebo odkazována procesorem XAML při přístupu k příslušnému typu zálohování.  
  
 Pro události WPF XAML událost, která je odkazována jako název atributu, musí být veřejná a mít veřejného delegáta.  
  
 Vlastnost nebo událost musí být členem třídy nebo struktury, která je vytvořena pomocí elementu obsahujícího objektu.  
  
### <a name="processing-of-attribute-values"></a>Zpracování hodnot atributů  
 Hodnota řetězce obsažená v počátečních a závěrečných uvozovkách je zpracována procesorem XAML. Pro vlastnosti je výchozí chování zpracování určeno typem základní vlastnosti CLR.  
  
 Hodnota atributu je vyplněna jedním z následujících, pomocí tohoto pořadí zpracování:  
  
1. Pokud procesor XAML narazí na složené složená závorka nebo prvek objektu, který je odvozen z <xref:System.Windows.Markup.MarkupExtension>, pak odkazované rozšíření značky je vyhodnocena jako první místo zpracování hodnoty jako řetězec a objekt vrácený rozšíření značky se používá jako hodnota. V mnoha případech objekt vrácený rozšíření mnoství matné značky bude odkaz na existující objekt nebo výraz, který odkládá hodnocení až do běhu a není nově instance objektu.  
  
2. Pokud je vlastnost deklarována s přiřazeným <xref:System.ComponentModel.TypeConverter>nebo typ hodnoty <xref:System.ComponentModel.TypeConverter>této vlastnosti je deklarován s atributem , je řetězcová hodnota atributu odeslána převaděči typu jako vstup převodu a převaděč vrátí novou instanci objektu.  
  
3. Pokud není <xref:System.ComponentModel.TypeConverter>k dispozici , je pokus o přímý převod na typ vlastnosti. Tato konečná úroveň je přímý převod na parser nativní hodnotu mezi typy jazyka XAML primitivní nebo kontrola názvů pojmenovaných konstant ve výčtu (analyzátor pak přistupuje k odpovídající hodnoty).  
  
#### <a name="enumeration-attribute-values"></a>Hodnoty atributů výčtu  
 Výčty v XAML jsou zpracovány vnitřně analyzátory XAML a členy výčtu by měly být určeny zadáním názvu řetězce jedné z pojmenovaných konstant výčtu.  
  
 Pro hodnoty výčtu bez příznaku je nativní chování zpracovat řetězec hodnoty atributu a vyřešit jej na jednu z hodnot výčtu. Výčet ve formátu *Výčet*nezadáte . *Hodnota*, stejně jako v kódu. Místo toho zadáte pouze *Value*a *výčet* je odvozen podle typu vlastnosti, kterou nastavujete. Pokud zadáte atribut ve *výčtu*. *Hodnotový* formulář, nevyřeší správně.  
  
 Pro výčty ve výšce ve vlajkovém směru je chování založeno na metodě. <xref:System.Enum.Parse%2A?displayProperty=nameWithType> Můžete zadat více hodnot pro výčtu ve vlajkovém směru oddělením každé hodnoty čárkou. Nelze však kombinovat hodnoty výčtu, které nejsou ve samáza. Například nelze použít syntaxi čárky k pokusu <xref:System.Windows.Trigger> o vytvoření, který funguje na více podmínek výčtu bez příznaku:  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Počet výčtů ve wawise, které podporují atributy, které jsou v XAML nastaveny, jsou v WPF vzácné. Jeden takový výčet je <xref:System.Windows.Media.StyleSimulations>však . Můžete například použít syntaxi atributu flagwise oddělenou čárkou k úpravě příkladu <xref:System.Windows.Documents.Glyphs> uvedeného v poznámkách pro třídu; `StyleSimulations = "BoldSimulation"` by `StyleSimulations = "BoldSimulation,ItalicSimulation"`se mohla stát . <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>je jiná vlastnost, kde lze zadat více než jednu hodnotu výčtu. Tato vlastnost je však stane zvláštní <xref:System.Windows.Input.ModifierKeys> případ, protože výčet podporuje jeho vlastní převaděč typu. Převaděč typu pro modifikátory používá znaménko plus (+) jako oddělovač spíše než čárku (,). Tento převod podporuje tradiční syntaxi představující kombinace kláves v programování systému Microsoft Windows, například "Ctrl+Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Odkazy na názvy členů událostí a události  
 Při zadávání atributu můžete odkazovat na libovolnou vlastnost nebo událost, která existuje jako člen typu CLR, který jste instance pro prvek obsahující objekt.  
  
 Nebo můžete odkazovat na připojenou vlastnost nebo připojenou událost, nezávisle na prvku obsahujícího objektu. (Připojené vlastnosti jsou popsány v nadcházející části.)  
  
 Můžete také pojmenovat libovolnou událost z libovolného objektu, který je přístupný prostřednictvím výchozího oboru názvů pomocí *typeName*. *událost* částečně kvalifikovaný název; Tato syntaxe podporuje připojení obslužných rutin pro směrované události, kde je obslužná rutina určena ke zpracování směrování událostí z podřízených prvků, ale nadřazený prvek nemá tuto událost také v tabulce členů. Tato syntaxe se podobá připojené syntaxi události, ale událost zde není true attached událost. Místo toho odkazujete na událost s kvalifikovaným názvem. Další informace naleznete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 Pro některé scénáře jsou někdy názvy vlastností k dispozici jako hodnota atributu, nikoli jako název atributu. Tento název vlastnosti může také obsahovat kvalifikátory, například vlastnost zadaná ve formuláři *ownerType*. *dependencyPropertyName*. Tento scénář je běžné při psaní stylů nebo šablon v XAML. Pravidla zpracování pro názvy vlastností poskytované jako hodnota atributu se liší a řídí se typem nastavené vlastnosti nebo chováním konkrétních podsystémů WPF. Podrobnosti viz [Styling a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Jiné použití pro názvy vlastností je, když hodnota atributu popisuje vztah vlastnost-vlastnost. Tato funkce se používá pro datové vazby a pro <xref:System.Windows.PropertyPath> cíle scénáře a je povolena třídou a jeho převaděč typu. Podrobnější popis vyhledávací sémantiky naleznete v tématu [PropertyPath XAML Syntaxe](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>Syntaxe prvku vlastnosti  
 *Syntaxe prvku vlastnosti* je syntaxe, která se poněkud liší od základních pravidel syntaxe XML pro elementy. V jazyce XML je hodnota atributu de facto řetězcem, přičemž jedinou možnou variantou je, který formát kódování řetězců se používá. V XAML můžete přiřadit další prvky objektu jako hodnotu vlastnosti. Tato funkce je povolena syntaxí prvku vlastnosti. Místo vlastnosti, která je zadána jako atribut v rámci značky elementu, je vlastnost určena pomocí značky počátečního prvku v *elementu Name*. *propertyName* formulář, hodnota vlastnosti je zadán v rámci a pak je prvek vlastnosti uzavřen.  
  
 Konkrétně syntaxe začíná levou úhlovou\<závorkou ( ), následovanou bezprostředně názvem typu třídy nebo struktury, ve které je obsažena syntaxe prvku vlastnosti. Následuje bezprostředně jedna tečka (.), poté název vlastnosti, pak pravý úhel držáku (>). Stejně jako u syntaxe atributu musí tato vlastnost existovat v rámci deklarovaných veřejných členů zadaného typu. Hodnota, která má být přiřazena vlastnosti, je obsažena v elementu vlastnosti. Hodnota je obvykle uvedena jako jeden nebo více prvků objektu, protože určení objektů jako hodnot je scénář, který má syntaxe prvku vlastnosti adresovat. Nakonec ekvivalentní uzavírací značka určující stejný *elementTypeName*. *propertyName* kombinace musí být poskytnuta, ve správném vnoření a vyvážení s jinými značkami elementu.  
  
 Například následující je syntaxe elementu vlastnosti <xref:System.Windows.FrameworkElement.ContextMenu%2A> pro vlastnost . <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Hodnota v rámci elementu vlastnosti může být také uvedena jako vnitřní text, v případech, kdy je zadán typ vlastnosti primitivní typ hodnoty, například <xref:System.String>, nebo výčet, kde je zadán název. Tato dvě použití jsou poněkud neobvyklé, protože každý z těchto případů může také použít jednodušší atribut syntaxe. Jeden scénář pro vyplnění elementvlastnosti řetězcem je pro vlastnosti, které nejsou vlastností obsahu XAML, ale stále se používají pro reprezentaci textu uživatelského rozhraní a určité prázdné prvky, jako jsou linefeeds, se musí zobrazit v textu uživatelského rozhraní. Syntaxe atributu nemůže zachovat linefeeds, ale hodnota elementu vlastnosti může, pokud je aktivní významné zachování prázdného místa (podrobnosti viz [Zpracování prázdného místa v XAML).](../../../desktop-wpf/xaml-services/white-space-processing.md) Jiný scénář je tak, že [x:Uid směrnice](../../../desktop-wpf/xaml-services/xuid-directive.md) lze použít na element vlastnosti a proto označit hodnotu v rámci jako hodnotu, která by měla být lokalizována ve výstupu WPF BAML nebo jinými technikami.  
  
 Prvek vlastnosti není reprezentován v logickém stromu WPF. Element vlastnosti je pouze určitá syntaxe pro nastavení vlastnosti a není prvek, který má instanci nebo objekt, který ji podporuje. (Podrobnosti o konceptu logického stromu naleznete [v tématu Stromy v WPF](trees-in-wpf.md).)  
  
 Pro vlastnosti, kde jsou podporovány syntaxe atributu a elementu vlastností, mají dvě syntaxe obvykle stejný výsledek, i když jemnosti, jako je například zpracování prázdného místa, se mohou mírně lišit mezi syntaxemi.  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>Syntaxe kolekce  
 Specifikace XAML vyžaduje implementace procesoru XAML k identifikaci vlastností, kde je typ hodnoty kolekce. Obecná implementace procesoru XAML v rozhraní .NET je založena na spravovaném kódu a CLR a identifikuje typy kolekcí prostřednictvím jedné z následujících možností:  
  
- Typ implements <xref:System.Collections.IList>.  
  
- Typ implements <xref:System.Collections.IDictionary>.  
  
- Typ je <xref:System.Array> odvozen od (další informace o polích v XAML naleznete v tématu [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
 Pokud je typ vlastnosti kolekce, pak odvozený typ kolekce nemusí být zadán ve značkách jako element objektu. Místo toho prvky, které jsou určeny k tomu, aby se staly položkami v kolekci, jsou určeny jako jeden nebo více podřízených prvků elementu vlastnosti. Každá taková položka je vyhodnocena na objekt během `Add` načítání a přidána do kolekce voláním metody implicitní kolekce. Například <xref:System.Windows.Style.Triggers%2A> vlastnost <xref:System.Windows.Style> přebírá typ specializované kolekce <xref:System.Windows.TriggerCollection>, který <xref:System.Collections.IList>implementuje . Není nutné vytvořit instanci <xref:System.Windows.TriggerCollection> prvku objektu ve značkách. Místo toho zadáte jednu nebo <xref:System.Windows.Trigger> více `Style.Triggers` položek jako <xref:System.Windows.Trigger> prvky v rámci elementu vlastnosti, kde (nebo odvozené <xref:System.Windows.TriggerCollection>třídy) je typ očekávaný jako typ položky pro silně typované a implicitní .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Vlastnost může být typ kolekce a xaml content vlastnost pro tento typ a odvozené typy, který je popsán v další části tohoto tématu.  
  
 Implicitní prvek kolekce vytvoří člen v reprezentaci logického stromu, i když se nezobrazí ve značkách jako prvek. Obvykle konstruktor nadřazeného typu provádí instanci kolekce, která je jednou z jeho vlastností a zpočátku prázdná kolekce se stane součástí stromu objektů.  
  
> [!NOTE]
> Obecné seznam a slovníkrozhraní<xref:System.Collections.Generic.IList%601> ( <xref:System.Collections.Generic.IDictionary%602>a ) nejsou podporovány pro zjišťování kolekce. Třídu <xref:System.Collections.Generic.List%601> však můžete použít jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo nebo <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> jako základní třídu, protože implementuje přímo.  
  
 Na odkazových stránkách .NET pro typy kolekcí je tato syntaxe s záměrným vynecháním elementu objektu pro kolekci příležitostně zaznamenána v částech syntaxe XAML jako Implicitní syntaxe kolekce.  
  
 S výjimkou kořenového prvku je každý element objektu v souboru XAML, který je vnořen jako podřízený prvek jiného prvku, skutečně elementem, který je jedním nebo oběma následujícími případy: členem implicitní vlastnosti kolekce nadřazeného prvku nebo elementem, který určuje hodnotu vlastnosti obsahu XAML pro nadřazený prvek (vlastnosti obsahu XAML budou popsány v nadcházející části). Jinými slovy vztah nadřazených prvků a podřízených prvků na stránce značek je skutečně jeden objekt v kořenovém adresáři a každý prvek objektu pod kořenem je buď jedna instance, která poskytuje hodnotu vlastnosti nadřazeného, nebo jednu z položek v rámci kolekce, která je také hodnotou vlastnosti typu kolekce nadřazeného objektu. Tento koncept jednoho kořene je společný s XML a je často posílena v chování <xref:System.Windows.Markup.XamlReader.Load%2A>rozhraní API, která načítají XAML, například .  
  
 Následující příklad je syntaxe s elementem<xref:System.Windows.Media.GradientStopCollection>objektu pro kolekci ( ) zadanou explicitně.  
  
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
  
 Všimněte si, že není vždy možné explicitně deklarovat kolekce. Například pokus o <xref:System.Windows.TriggerCollection> deklarování <xref:System.Windows.Style.Triggers%2A> explicitně v dříve zobrazeném příkladu by se nezdaří. Explicitně deklarování kolekce vyžaduje, aby třída kolekce <xref:System.Windows.TriggerCollection> musí podporovat konstruktor bez parametrů a nemá konstruktor bez parametrů.  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>Vlastnosti obsahu XAML  
 Syntaxe obsahu XAML je syntaxe, která <xref:System.Windows.Markup.ContentPropertyAttribute> je povolena pouze u tříd, které určují jako součást deklarace třídy. Odkazuje <xref:System.Windows.Markup.ContentPropertyAttribute> na název vlastnosti, která je vlastností content pro tento typ prvku (včetně odvozených tříd). Při zpracování procesorem XAML budou všechny podřízené prvky nebo vnitřní text, které se nacházejí mezi otevírací a uzavírací tagy elementu objektu, přiřazeny hodnotě vlastnosti obsahu XAML pro daný objekt. Můžete zadat explicitní prvky vlastnosti pro vlastnost content, ale toto použití není obecně zobrazeno v částech syntaxe XAML v odkazu .NET. Explicitní/podrobné technika má příležitostnou hodnotu pro srozumitelnost značky nebo jako věc stylu značky, ale obvykle záměrem vlastnosti content je zefektivnit značky tak, aby prvky, které jsou intuitivně související jako nadřazené dítě může být vnořeno přímo. Tagy elementu vlastností pro jiné vlastnosti prvku nejsou přiřazeny jako "obsah" podle striktní definice jazyka XAML; jsou zpracovány dříve v pořadí zpracování analyzátoru XAML a nejsou považovány za "obsah".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Hodnoty vlastností obsahu XAML musí být souvislé.  
 Hodnota vlastnosti obsahu XAML musí být uvedena zcela před nebo zcela za jinými prvky vlastnosti v tomto elementu objektu. To platí bez ohledu na to, zda je hodnota vlastnosti obsahu XAML zadána jako řetězec nebo jako jeden nebo více objektů. Například následující značky neanalyzují:  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 To je v podstatě neplatné, protože pokud by tato syntaxe byla explicitně provedena pomocí syntaxe elementu vlastnosti pro vlastnost content, pak by vlastnost content byla nastavena dvakrát:  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobně nelegální příklad je, pokud je vlastnost content kolekce a podřízené prvky jsou proloženy prvky vlastností:  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>
## <a name="content-properties-and-collection-syntax-combined"></a>Kombinační vlastnosti obsahu a syntaxe kolekce  
 Chcete-li přijmout více než jeden prvek objektu jako obsah, musí být typ vlastnosti content konkrétně typ kolekce. Podobně jako syntaxe prvku vlastnosti pro typy kolekcí musí procesor XAML identifikovat typy, které jsou typy kolekcí. Pokud má prvek vlastnost obsahu XAML a typ vlastnosti obsahu XAML je kolekce, nemusí být implicitní typ kolekce zadán ve značkách jako element objektu a vlastnost obsahu XAML nemusí být zadána jako prvek vlastnosti. Proto zdánlivý obsah modelu ve značkách nyní může mít více než jeden podřízený prvek přiřazen jako obsah. Následuje syntaxe obsahu <xref:System.Windows.Controls.Panel> pro odvozenou třídu. Všechny <xref:System.Windows.Controls.Panel> odvozené třídy vytvářejí vlastnost obsahu <xref:System.Windows.Controls.Panel.Children%2A>XAML , <xref:System.Windows.Controls.UIElementCollection>která vyžaduje hodnotu typu .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Všimněte si, že <xref:System.Windows.Controls.Panel.Children%2A> ani element vlastnosti pro ani prvek pro <xref:System.Windows.Controls.UIElementCollection> je požadováno ve značkách. Toto je funkce návrhu XAML tak, aby rekurzivně obsažené prvky, které definují [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jsou intuitivně jistoly jako strom vnořených prvků s okamžitými vztahy elementu nadřazený podřízený, bez zasahování značky elementu vlastnosti nebo objekty kolekce. Ve skutečnosti <xref:System.Windows.Controls.UIElementCollection> nelze explicitně zadat ve značkách jako prvek objektu, podle návrhu. Vzhledem k tomu, že jeho <xref:System.Windows.Controls.UIElementCollection> pouze zamýšlené použití je jako implicitní kolekce, nezveřejňuje veřejný konstruktor bez parametrů a proto nelze vytvořit instanci jako element objektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Míchání prvků vlastností a prvků objektu v objektu s vlastností obsahu  
 Specifikace XAML deklaruje, že procesor XAML může vynutit, že prvky objektu, které se používají k vyplnění vlastnosti obsahu XAML v rámci prvku objektu, musí být souvislé a nesmí být smíšené. Toto omezení proti míchání prvků vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a obsahu je vynuceno procesory XAML.  
  
 Můžete mít podřízený prvek objektu jako první okamžité značky v rámci prvku objektu. Pak můžete zavést prvky vlastností. Nebo můžete zadat jeden nebo více prvků vlastností, pak obsah a pak další prvky vlastností. Ale jakmile element vlastnosti následuje obsah, nelze zavést žádný další obsah, můžete pouze přidat prvky vlastnosti.  
  
 Tento požadavek na pořadí obsahu / vlastností se nevztahuje na vnitřní text používaný jako obsah. Je však stále dobrý styl značky zachovat vnitřní text souvislý, protože významné prázdné místo bude obtížné zjistit vizuálně ve značkách, pokud jsou prvky vlastností proložené vnitřním textem.  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>Obory názvů jazyka XAML  
 Žádný z předchozích příkladů syntaxe nezadal jiný obor názvů XAML než výchozí obor názvů XAML. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typických aplikacích je výchozí obor názvů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML určen jako obor názvů. Můžete určit jiné obory názvů XAML než výchozí obor názvů XAML a stále používat podobnou syntaxi. Ale pak kdekoli, kde je pojmenována třída, která není přístupná v rámci výchozího oboru názvů XAML, tento název třídy musí předcházet předponu oboru názvů XAML jako mapována na odpovídající obor názvů CLR. Například `<custom:Example/>` je syntaxe prvku objektu k vytvoření `Example` instance třídy, kde byl obor názvů CLR obsahující tuto třídu (a případně `custom` informace o externím sestavení, které obsahuje typy zálohování) dříve mapován na předponu.  
  
 Další informace o oborech názvů XAML naleznete v [tématu XAML Namespaces and Namespace Mapping for WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>Rozšíření značek  
 XAML definuje programovací entitu rozšíření značek, která umožňuje únik z normálního procesoru XAML zpracování hodnot atributů řetězce nebo prvků objektu a odkládá zpracování na záložní třídu. Znak, který identifikuje rozšíření značek pro procesor XAML při použití syntaxe atributu, je otevírací složená závorka ({), následovaná libovolným znakem jiným než uzavírací složenou závorkou (}). První řetězec za počáteční složených závorky musí odkazovat na třídu, která poskytuje konkrétní chování rozšíření, kde odkaz může vynechat podřetězec "Rozšíření", pokud je tento podřetězec součástí názvu třídy true. Poté se může zobrazit jedna mezera a potom každý následující znak se používá jako vstup implementace rozšíření, až do uzavření složené závorky je zjištěna.  
  
 Implementace .NET XAML <xref:System.Windows.Markup.MarkupExtension> používá abstraktní třídu jako základ pro všechna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozšíření značek podporovaná stejně jako další architektury nebo technologie. Rozšíření značek, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konkrétně implementuje jsou často určeny k poskytnutí prostředků k odkazování na jiné existující objekty nebo k odložené odkazy na objekty, které budou vyhodnoceny za běhu. Například jednoduchá datová vazba WPF se `{Binding}` provádí zadáním rozšíření značek namísto hodnoty, která by obvykle trvat určitou vlastnost. Mnoho rozšíření značek WPF povolit syntaxi atributu pro vlastnosti, kde by jinak nebylo možné syntaxe atributu. <xref:System.Windows.Style> Například objekt je poměrně složitý typ, který obsahuje vnořenou řadu objektů a vlastností. Styly v WPF jsou obvykle definovány jako prostředek v <xref:System.Windows.ResourceDictionary>aplikaci a poté odkazovány prostřednictvím jednoho ze dvou rozšíření značek WPF, která požadují prostředek. Rozšíření značek odloží vyhodnocení hodnoty vlastnosti na vyhledávání prostředků a povolí <xref:System.Windows.FrameworkElement.Style%2A> zadání hodnoty <xref:System.Windows.Style>vlastnosti s typem , v syntaxi atributu jako v následujícím příkladu:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Zde `StaticResource` identifikuje třídu <xref:System.Windows.StaticResourceExtension> poskytující implementaci rozšíření značek. Další řetězec `MyStyle` se používá jako vstup pro <xref:System.Windows.StaticResourceExtension> nevýchozí konstruktor, kde parametr převzatý z <xref:System.Windows.ResourceKey>rozšiřujícího řetězce deklaruje požadovaný . `MyStyle`očekává se, že [hodnota x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) <xref:System.Windows.Style> definovaného jako prostředek. Požadavky na využití [rozšíření značky staticresource](staticresource-markup-extension.md) ustavený prostředek, které mají být použity k poskytnutí hodnoty <xref:System.Windows.Style> vlastnosti prostřednictvím logiky vyhledávání statických prostředků v době načítání.  
  
 Další informace o rozšířeních značek naleznete v [tématech Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md). Odkaz na rozšíření značek a další programovací funkce XAML povolené v obecné implementaci rozhraní .NET XAML naleznete v [tématu XAML Namespace (x:) Funkce jazyka](../../../desktop-wpf/xaml-services/namespace-language-features.md). Rozšíření značek specifická pro WPF naleznete v tématu [WPF XAML Extensions](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>Přidružené vlastnosti  
 Připojené vlastnosti jsou programovací koncept zavedený v XAML, kdy vlastnosti mohou být vlastněny a definovány určitým typem, ale nastaveny jako atributy nebo prvky vlastností na libovolném prvku. Primární scénář, který připojené vlastnosti jsou určeny pro je povolit podřízené prvky ve struktuře značek sestavy informace nadřazený prvek bez nutnosti rozsáhle sdílený objektový model napříč všemi prvky. Naopak připojené vlastnosti lze použít nadřazené prvky k hlášení informací podřízeným prvkům. Další informace o účelu připojených vlastností a o tom, jak vytvořit vlastní připojené vlastnosti, naleznete v tématu [Přehled připojených vlastností](attached-properties-overview.md).  
  
 Připojené vlastnosti používají syntaxi, která se povrchně podobá syntaxi prvku vlastnosti, v tom, že také zadáte *typeName*. *propertyName* kombinace. Existují dva důležité rozdíly:  
  
- Můžete použít *typeName*. *propertyName* kombinace i při nastavení připojené vlastnosti pomocí syntaxe atributu. Připojené vlastnosti jsou jediným případem, kdy je kvalifikace názvu vlastnosti požadavkem v syntaxi atributu.  
  
- Syntaxe prvku vlastnosti můžete také použít pro připojené vlastnosti. Pro syntaxi typického prvku vlastnosti je však zadaný *majedlo typeName* elementem objektu, který obsahuje element vlastnosti. Pokud odkazujete na připojenou vlastnost, pak *typeName* je třída, která definuje připojenou vlastnost, nikoli prvek obsahující objekt.  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>Přidružené události  
 Připojené události jsou další programovací koncept zavedený v XAML, kde události mohou být definovány určitým typem, ale obslužné rutiny mohou být připojeny k libovolnému prvku objektu. V implementaci WOF často typ, který definuje připojené události je statický typ, který definuje službu a někdy tyto připojené události jsou vystaveny alias směrované události v typech, které zveřejňují službu. Obslužné rutiny pro připojené události jsou určeny pomocí syntaxe atributu. Stejně jako u připojených událostí je syntaxe atributu rozšířena pro připojené události tak, aby umožňovala *typeName*. *eventName* usage, where *typeName* je `Add` `Remove` třída, která poskytuje a přistupující přístupové členy obslužné rutiny události pro infrastrukturu připojených událostí a *eventName* je název události.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie kořenového prvku XAML  
 V následující tabulce je uveden typický kořenový prvek XAML, který je rozdělen a který zobrazuje specifické atributy kořenového prvku:  
  
|||  
|-|-|  
|`<Page`|Otevření elementu objektu kořenového prvku|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Výchozí ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) obor názvů XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Obor názvů XAML jazyka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklarace částečné třídy, která spojuje značky s libovolným kódem na pozadí definovaným pro částečnou třídu|  
|`>`|Konec prvku objektu pro kořen. Objekt ještě není uzavřen, protože prvek obsahuje podřízené prvky.|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>Volitelné a nedoporučené použití XAML  
 Následující části popisují použití XAML, které jsou technicky podporovány procesory XAML, ale které vytvářejí podrobnostnebo jiné estetické problémy, které narušují soubory XAML, které zůstávají čitelné pro člověka při vývoji aplikací, které obsahují zdroje XAML.  
  
### <a name="optional-property-element-usages"></a>Použití volitelných prvků vlastností  
 Volitelné použití prvků vlastnosti zahrnují explicitní zápis vlastností obsahu prvku, které procesor XAML považuje za implicitní. Například při deklarování <xref:System.Windows.Controls.Menu>obsahu , můžete explicitně <xref:System.Windows.Controls.ItemsControl.Items%2A> deklarovat kolekci <xref:System.Windows.Controls.Menu> jako `<Menu.Items>` vlastnost <xref:System.Windows.Controls.MenuItem> `<Menu.Items>`element tag a umístit každý v rámci , spíše <xref:System.Windows.Controls.Menu> než <xref:System.Windows.Controls.MenuItem> pomocí implicitní <xref:System.Windows.Controls.ItemsControl.Items%2A> chování procesoru XAML, že všechny podřízené prvky musí být a jsou umístěny v kolekci. Někdy volitelné použití může pomoci vizuálně objasnit strukturu objektu, jak je znázorněno ve značkách. Nebo někdy explicitní vlastnost prvek použití můžete vyhnout značky, která je technicky funkční, ale vizuálně matoucí, jako je například vnořené značkovací rozšíření v rámci hodnoty atributu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Úplné atributy typeName.memberName Qualified  
 Název *typu*. *MemberName* formulář pro atribut ve skutečnosti funguje více univerzálně než jen směrované události případu. Ale v jiných situacích, které tvoří, je nadbytečné a měli byste se tomu vyhnout, i když jen z důvodů stylu značek a čitelnosti. V následujícím příkladu jsou všechny tři <xref:System.Windows.Controls.Control.Background%2A> odkazy na atribut zcela rovnocenné:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`funguje, protože kvalifikované vyhledávání pro <xref:System.Windows.Controls.Button> tuto<xref:System.Windows.Controls.Control.Background%2A> vlastnost na je úspěšný <xref:System.Windows.Controls.Button> (byl zděděn z Control) a je třída elementu objektu nebo základní třídy. `Control.Background`<xref:System.Windows.Controls.Control> funguje, protože třída <xref:System.Windows.Controls.Control.Background%2A> ve <xref:System.Windows.Controls.Control> skutečnosti <xref:System.Windows.Controls.Button> definuje a je základní třídy.  
  
 Následující *typeName*. *memberName* form example nefunguje, a je tedy zobrazen komentoval:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>je další odvozené <xref:System.Windows.Controls.Control>třídy , `Label.Background` a <xref:System.Windows.Controls.Label> pokud jste zadali v rámci elementu objektu, toto použití by fungovalo. Však <xref:System.Windows.Controls.Label> protože není třída nebo <xref:System.Windows.Controls.Button>základní třída , zadané chování procesoru `Label.Background` XAML je pak zpracovat jako připojené vlastnosti. `Label.Background`není k dispozici připojené vlastnosti a toto použití se nezdaří.  
  
### <a name="basetypenamemembername-property-elements"></a>elementy vlastností baseTypeName.memberName  
 Analogickým způsobem, jak *typeName*. *MemberName* formulář funguje pro syntaxi atributu, *baseTypeName*. syntaxe *memberName* funguje pro syntaxi prvku vlastnosti. Například následující syntaxe funguje:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Zde byl prvek vlastnosti `Control.Background` uveden jako přesto, že `Button`prvek vlastnosti byl obsažen v .  
  
 Ale stejně jako *typeName*. *memberName* formulář pro atributy, *baseTypeName*. *memberName* je špatný styl ve značkách a měli byste se mu vyhnout.  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Jazykové funkce kompatibility značek (mc:)](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [TypeConverters a XAML](typeconverters-and-xaml.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
