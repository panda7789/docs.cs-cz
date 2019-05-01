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
ms.openlocfilehash: bf4118c6e811f409715b7b6684851b8b3e8bbb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981367"
---
# <a name="xaml-syntax-in-detail"></a>Podrobná syntaxe XAML
Toto téma definuje podmínky, které se používají k popisu prvky syntaxe XAML. Tyto podmínky se často používají v celé zbývající části této dokumentace, i pro WPF dokumentaci, konkrétně a pro jiná rozhraní, které využívají XAML nebo o základních konceptech XAML povolená podpora jazyka XAML na úrovni oboru názvů System.Xaml. Toto téma rozšiřuje základní terminologii zavedené v tématu [přehled XAML (WPF)](xaml-overview-wpf.md).  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specifikace jazyka XAML  
 Terminologie syntaxe XAML lze tam definovat také je definována nebo odkazována v rámci specifikace jazyka XAML. XAML je jazyk založený na formát XML a následuje nebo rozšiřují strukturální pravidla jazyka XML. Terminologii sdílené z nebo podle terminologie běžně používají při popisu jazyka XML nebo modelu objektu dokumentu XML.  
  
 Další informace o specifikaci jazyka XAML, stáhněte si [ \[MS-XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525) z webu Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML a CLR  
 XAML je značkovací jazyk. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Jako implicitní podle názvu, umožňuje spuštění modulu runtime. XAML není samostatně jedním z běžných jazyků, které je přímo modulem CLR runtime. XAML můžete místo toho představit jako podpůrný svůj vlastní systém typů. Konkrétní XAML analýzy systému, který se používá ve WPF je založená na modulu CLR a systém typů CLR. Typy XAML jsou mapovány na typy CLR pro vytvoření instance reprezentaci doby běhu, když analyzovaný XAML pro WPF. Z tohoto důvodu se zbývající informace o syntaxi v tomto dokumentu obsahují odkazy na systém typů CLR, i když nejsou ekvivalentní syntax diskuse ve specifikaci jazyka XAML. (Na úrovni specifikace jazyka XAML, typy XAML může mapovat na jakémkoli jiném typu systému, který nemá být CLR, ale které by vyžadovaly vytvoření a použití různých analyzátoru XAML.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Členy typů a dědičnost tříd  
 Vlastnosti a události, jakmile se zobrazí jako členy XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu jsou často zděděné ze základních typů. Představte si třeba v tomto příkladu: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Vlastnost není okamžitě deklarované vlastnosti na <xref:System.Windows.Controls.Button> třídy, pokud byste chtěli podívejte se na definici třídy, výsledky reflexe nebo v dokumentaci. Místo toho <xref:System.Windows.Controls.Control.Background%2A> se dědí ze základní třídy <xref:System.Windows.Controls.Control> třídy.  
  
 Chování dědičnosti třídy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy XAML je významné odchýlení od schématu vynucená výklad kód XML. Dědičnost tříd může být složitá, zejména pokud zprostředkující základní třídy jsou abstraktní, nebo když jsou součástí rozhraní. Toto je jedním z důvodů, které se obtížně představují přesně a zcela pomocí typů schématu sady elementů XAML a jejich přípustné atributů, které se obvykle používají pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] programování, jako je formát souboru DTD nebo XSD. Dalším důvodem je, že rozšíření a funkce mapování typů jazyka XAML, samotný bránit úplnost jakékoli pevnou reprezentace přípustné typy a členy.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Syntaxe elementu objektu  
 *Syntaxe elementu objektu* je syntaxe značky XAML, který instancuje CLR třídu nebo strukturu deklarováním platný element XML. Tato syntaxe se podobá syntaxi elementu dalších jazycích značky, například HTML. Syntaxe elementu objektu začíná levou hranatou závorku (\<), bezprostředně následuje název typu třídy nebo struktury instance. Nula nebo více mezer, můžete postupovat podle názvu typu a mohou být deklarovány také nula nebo více atributů na elementu objektu jednoho nebo více mezer oddělení každý název atributu = "value" pár. Nakonec jeden z následujících musí mít hodnotu true:  
  
- Element a značky musí být uzavřel lomítkem (/) okamžitě následuje ostrá závorka (>).  
  
- Počáteční značka musí dokončit ostrá závorka (>). Další elementy objektu, vlastnost prvky nebo vnitřní text, můžete postupovat podle počáteční značka. Přesně obsahu mohou být obsaženy v tomto poli je obvykle omezená objektový model elementu. Odpovídající uzavírací značka pro object element musí existovat ve správné vnoření a vyvážit s ostatní kombinace otevírací a uzavírací značka.  
  
 XAML, jak je implementované .NET obsahuje sadu pravidel, která mapování elementů objektu do typů, atributů do vlastnosti nebo události a obory názvů XAML do oborů názvů CLR a sestavení. Pro WPF a .NET Framework, mapování elementů objektu XAML na [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] typy definované v odkazovaných sestavení a atributů mapování na členy z těchto typů. Při odkazování na typ CLR v XAML, máte přístup k zděděné členy tohoto typu také.  
  
 Například v následujícím příkladu je syntaxe elementu objektu, který vytvoří novou instanci třídy <xref:System.Windows.Controls.Button> třídy a také určuje <xref:System.Windows.FrameworkElement.Name%2A> atribut a hodnota atributu:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 V následujícím příkladu je syntaxe elementu objektu, který také obsahuje vlastnost obsahu syntaxe XAML. Nastavení se použije vnitřní text obsažen v rámci <xref:System.Windows.Controls.TextBox> vlastnost obsahu XAML, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modely obsahu  
 Třída může podporovat použití jako element objektu XAML z hlediska syntaxe, ale tento prvek bude pouze fungovat správně v aplikaci nebo stránky při umístění v očekávané umístění celého obsahu stromu modelu nebo element. Například <xref:System.Windows.Controls.MenuItem> by měl obvykle být umístěna pouze jako podřízený objekt <xref:System.Windows.Controls.Primitives.MenuBase> odvozené třídy jako <xref:System.Windows.Controls.Menu>. Obsahu modely pro konkrétních prvků, které jsou popsány jako součást poznámky na stránkách třída pro ovládací prvky a další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, které lze použít jako elementy XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Vlastnosti elementů objektu  
 Vlastnosti v XAML je nastavil širokou škálu možných syntaxe. Syntaxe, které lze použít pro určité vlastnosti budou lišit v závislosti na základní vlastnosti systému typu vlastnosti, která nastavujete.  
  
 Nastavením hodnoty vlastností přidáte funkce nebo vlastnosti objektů jako existují v době běhu objekt grafu. Počáteční stav vytvořený objekt z elementu objektu je založen na chování výchozí konstruktor. Obvykle bude aplikace používat něco jiného než zcela výchozí instanci libovolný daný objekt.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Syntaxe atributu (Vlastnosti)  
 Syntaxe značek XAML, která nastaví hodnotu pro vlastnost prohlášením atribut na existující prvek objektu, je syntaxe atributu. Název atributu musí odpovídat názvu člena CLR vlastnosti třídy, která zálohuje elementu příslušný objekt. Název atributu následuje operátor přiřazení (=). Hodnota atributu musí být řetězec uzavřený do uvozovek.  
  
> [!NOTE]
>  Střídání nabídky můžete umístit literální znak uvozovek v rámci atributu. Pro instanci můžete jednoduchých uvozovek a být jako prostředek k deklaraci, která obsahuje znak dvojité uvozovky uvnitř řetězce. Ať už používáte jednoduché nebo dvojité uvozovky, měli byste použít odpovídající dvojici pro otevírání a zavírání řetězcovou hodnotu atributu. K dispozici také řídicí sekvence nebo jiné techniky pro obejít omezení pro znaky stanovené žádné konkrétní syntaxe XAML. Zobrazit [znakové entity XML a XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby bylo možné nastavit pomocí syntaxe atributu, vlastnosti musí být veřejné a musí být zapisovatelný. Hodnota vlastnosti v systému základní typ musí být typ hodnoty, nebo musí být typ odkazu, který může být vytvořena instance nebo odkazuje na procesor XAML při přístupu k příslušné zálohování typu.  
  
 Pro WPF XAML události události, ke které je odkazováno jako název atributu musí být veřejný a mít veřejný delegát.  
  
 Vlastnost nebo událost, musíte být členem třídy nebo struktury, která je vytvořena instance tak nadřazeného elementu objektu.  
  
### <a name="processing-of-attribute-values"></a>Zpracování hodnot atributu  
 Řetězcová hodnota obsažená v rámci otevírací a uzavírací uvozovky je zpracovaných procesorem XAML. U vlastnosti je určena výchozí zpracování chování podle typu základní vlastnost CLR.  
  
 Hodnota atributu je vyplněna pomocí jedné z následujících akcí, pomocí tohoto pořadí zpracování:  
  
1. Pokud procesor XAML zaznamená složenou závorku nebo element objektu, který je odvozen z <xref:System.Windows.Markup.MarkupExtension>, pak rozšíření odkazovaného kódu je vyhodnocen jako první místo zpracování hodnotu jako řetězec a objekt vrácený rutinou rozšíření značek se používá jako hodnota. Objekt vrácený rutinou rozšíření značek v mnoha případech bude odkaz na existující objekt nebo výraz, který odloží vyhodnocení až do spuštění a není nově vytvořenou instanci objektu.  
  
2. Pokud je deklarována vlastnost s s atributy <xref:System.ComponentModel.TypeConverter>, nebo typ hodnoty této vlastnosti je deklarován pomocí s atributy <xref:System.ComponentModel.TypeConverter>řetězcovou hodnotu atributu se odešle službě konvertor typu jako vstup převodu a vrátí převaděč novou instanci objektu.  
  
3. Pokud není žádný <xref:System.ComponentModel.TypeConverter>, dojde k pokusu o přímý převod typu vlastnosti. Tento poslední úroveň je přímý převod na hodnotu native analyzátor mezi primitivní typy jazyka XAML, nebo zkontrolovat názvy pojmenovaných konstant ve výčtu (Analyzátor potom má přístup k odpovídající hodnoty).  
  
#### <a name="enumeration-attribute-values"></a>Výčet hodnot atributů  
 Výčty v XAML se zpracují vnitřně analyzátory XAML a členy výčtu by měl být zadané, určením řetězec název jedné z pojmenované konstanty výčtu.  
  
 Nativní chování pro hodnoty výčtu nonflag, je zpracovat řetězec hodnotu atributu a přeložte ho na jednu z hodnot výčtu. Ve formátu nezadáte výčtu *výčet*. *Hodnota*, stejně jako v kódu. Místo toho zadáte pouze *hodnotu*, a *výčet* vyvozena na základě typu vlastnosti, jsou nastavení. Pokud zadáte atribut v *výčet*. *Hodnota* formuláře, se nebudou správně přeložit.  
  
 Flagwise výčtů je na základě chování <xref:System.Enum.Parse%2A?displayProperty=nameWithType> metody. Můžete zadat více hodnot pro flagwise výčet tak, že jednotlivé hodnoty oddělíte čárkou. Nelze však kombinovat hodnot výčtu, která nejsou flagwise. Například nelze použít syntaxi čárkami k pokusu o vytvoření <xref:System.Windows.Trigger> , které fungují na více podmínek nonflag výčtu:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Flagwise výčty, které podporují atributy, které je možné v XAML se vyskytují jen vzácně v subsystému WPF. Je však jeden takový výčet <xref:System.Windows.Media.StyleSimulations>. Můžete je například použijte syntaxi oddělených čárkou flagwise atribut upravit v příkladu v poznámky pro <xref:System.Windows.Documents.Glyphs> třídy; `StyleSimulations = "BoldSimulation"` stát `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> je jiné vlastnosti, ve kterém můžete zadat více než jednu hodnotu výčtu. Ale tato vlastnost se stane, bude zvláštní případ, protože <xref:System.Windows.Input.ModifierKeys> výčet podporuje svůj vlastní typ převaděče. Konvertor typů pro modifikátory znaménko plus (+) používá jako oddělovač, nikoli čárku (,). Tento převod podporuje tradičnější syntaxe představující kombinace kláves v programování pro sadu Microsoft Windows, jako je například "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Vlastnosti a události člen název reference  
 Při zadávání atribut, můžete odkazovat na žádné vlastnosti nebo události, ke které existuje jako člen typu CLR, který je vytvořena instance pro nadřazeného elementu objektu.  
  
 Nebo může odkazovat na připojené vlastnosti nebo připojených událostí, nezávisle na nadřazeného elementu objektu. (Připojené vlastnosti jsou popsány v následující části).  
  
 Můžete také pojmenovat žádné události z libovolného objektu, který je přístupný prostřednictvím výchozí obor názvů s využitím *typeName*. *událost* částečně kvalifikované název; Tato syntaxe podporuje připojení obslužné rutiny pro směrované události kde obslužnou rutinu je určená pro zpracování událostí směrování z podřízených prvků, ale nadřazený element také nemá tuto událost v tabulce jeho členů. Tato syntaxe vypadá podobně jako syntaxi přidružená událost, ale událost není true přidružená událost. Místo toho jsou odkazující na události s kvalifikovaným názvem. Další informace najdete v tématu [směrovat Přehled událostí](routed-events-overview.md).  
  
 Pro některé scénáře jsou někdy názvy vlastností uvedený jako hodnota atributu, nikoli název atributu. Tuto vlastnost název může obsahovat také kvalifikátorů, jako je například vlastnost určenou ve formuláři *ownerType*. *dependencyPropertyName*. Tento postup je běžný při zápisu styly a šablony v XAML. Zpracování pravidla pro názvy vlastností, které jsou k dispozici jako hodnota atributu se liší a se řídí podle typu vlastnost nastavena nebo chování konkrétní subsystémů WPF. Podrobnosti najdete v tématu [styly a šablony](../controls/styling-and-templating.md).  
  
 Při hodnotě atributu popisuje vztah – vlastnost je další využití pro názvy vlastností. Tato funkce se používá pro vytváření datových vazeb a pro scénáře, cíle a zajišťuje <xref:System.Windows.PropertyPath> třídy a jeho konvertor typu. Úplný popis vyhledávání sémantiky najdete v tématu [propertypath – syntaxe XAML](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Syntax prvku vlastnosti  
 *Syntax prvku vlastnosti* je syntaxe, která diverges trochu ze základních pravidel syntaxe XML pro elementy. Ve formátu XML hodnota atributu je de facto stane řetězec, s jedinou možnou variace se, jaký formát kódování řetězec se používá. V XAML můžete přiřadit další elementy objektu bude hodnota vlastnosti. Tato funkce je povolená pomocí syntax prvku vlastnosti. Namísto vlastnosti zadané jako atribut ve značce elementu, vlastnost určena pomocí elementu počáteční značku *elementTypeName*. *Vlastnost propertyName* formuláře, hodnoty vlastnosti je zadán v rámci a pak zavření element vlastnosti.  
  
 Konkrétně syntaxe začíná levou hranatou závorku (\<), bezprostředně následuje název typu třída nebo struktura, která je součástí syntax prvku vlastnosti. Následují ihned jednu tečku (.), poté podle názvu vlastnosti, pak podle pravé ostré závorky (>). Stejně jako u syntaxe atributu tuto vlastnost musí existovat v rámci veřejné členy deklarované zadaného typu. Hodnota, která má být přiřazeno k vlastnosti je obsažena v elementu vlastnosti. Obvykle hodnota je uveden jako jeden nebo více elementů objektu, protože zadání objekty jako hodnoty je scénář syntaxe elementu vlastnosti má adresu. Nakonec odpovídající uzavírací značku zadáním stejné *elementTypeName*. *Vlastnost propertyName* kombinaci musí být uvedeny ve správné vnoření a rovnováze s další značky elementu.  
  
 Například tady je syntax prvku vlastnosti pro <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Hodnota v rámci elementu vlastnosti můžete taky jako vnitřní text v případech, kdy je primitivního hodnotového typu, typ vlastnosti zadané jako <xref:System.String>, nebo kde je zadán název výčtu. Tyto dva způsoby použití položek jsou poměrně neobvyklé, protože každé z těchto případech také použít jednodušší syntaxe atributu. Jeden scénář pro vyplnění prvek vlastnosti pomocí řetězce je pro vlastnosti, které nejsou vlastnost obsahu XAML, ale stále se používají pro reprezentaci textu uživatelského rozhraní a konkrétní prvky prázdné znaky, jako jsou přečtené je potřeba se zobrazí v textu uživatelského rozhraní. Syntaxe atributu nelze zachovat přečtené, ale můžete syntax prvku vlastnosti, tak dlouho, dokud je aktivní významné zachování prázdných znaků (podrobnosti najdete v tématu [v XAML je zpracování mezerových znaků](../../xaml-services/whitespace-processing-in-xaml.md)). Další možností je tak, aby [x: Uid – direktiva](../../xaml-services/x-uid-directive.md) lze použít u vlastnosti elementu a tím označit hodnotu v rámci jako výstup hodnotu, která musí být lokalizována do modulu WPF BAML nebo jiné techniky.  
  
 Prvek vlastnosti není zastoupen v logickém stromu WPF. Prvek vlastnosti je pro nastavení vlastnosti pouze konkrétní syntaxi a není element, který má instance nebo objekt jejich zálohování. (Podrobnosti o konceptu logického stromu, naleznete v tématu [stromy v subsystému WPF](trees-in-wpf.md).)  
  
 Pro vlastnosti, kde se podporují atribut a vlastnost syntax prvku mají dvě syntaxe obvykle stejný výsledek, i když odlišností například zpracování prázdných znaků se může mírně lišit mezi syntaxe.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Syntaxe kolekce  
 Specifikace XAML vyžaduje implementace XAML identifikovat vlastnosti, kde je typ hodnoty do kolekce. Obecná implementace procesoru XAML v rozhraní .NET je založená na spravovaném kódu a modul CLR a identifikuje kolekci typů prostřednictvím jednoho z následujících akcí:  
  
- Typ implementuje <xref:System.Collections.IList>.  
  
- Typ implementuje <xref:System.Collections.IDictionary>.  
  
- Typ je odvozen od <xref:System.Array> (Další informace o polích v XAML najdete v tématu [x: Array – rozšíření značek](../../xaml-services/x-array-markup-extension.md).)  
  
 Pokud typ vlastnosti je kolekce, pak typ odvozený kolekce nemusí být zadané ve značce jako element objektu. Místo toho prvky, které jsou určeny k položek v kolekci jsou specifikovány jako jeden nebo více podřízených elementů elementu vlastnosti. Každé takové položky vyhodnotí na objekt při načítání a přidá do kolekce se při volání `Add` metody implicitní kolekce. Například <xref:System.Windows.Style.Triggers%2A> vlastnost <xref:System.Windows.Style> přijímá typ specializované kolekce <xref:System.Windows.TriggerCollection>, která implementuje <xref:System.Collections.IList>. Není nutné k vytvoření instance <xref:System.Windows.TriggerCollection> objekt elementu v kódu. Místo toho zadat jednu nebo víc <xref:System.Windows.Trigger> položky jako prvky v rámci `Style.Triggers` vlastnost elementu, kde <xref:System.Windows.Trigger> (nebo z odvozené třídy) je očekáván jako typ položky pro silně typované a implicitní typ <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Vlastnost může být typu kolekce a vlastnost obsahu XAML pro daný typ a odvozené typy, které je popsáno v další části tohoto tématu.  
  
 Element implicitní kolekce vytvoří člena v reprezentaci Logická stromová struktura i v případě, že se nezobrazí ve značce jako element. Obvykle konstruktor nadřazený typ provádí instance pro kolekci, která je jedno z jeho vlastností a původně prázdná kolekce se stane součástí stromu objektů.  
  
> [!NOTE]
>  Obecná rozhraní seznamu a slovníku (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro zjišťování kolekce. Můžete však použít <xref:System.Collections.Generic.List%601> třídy jako základní třídu, protože implementuje <xref:System.Collections.IList> přímo, nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třídu, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 Na stránce .NET – referenční informace pro typy kolekcí je tato syntaxe se rozhodnout vědomě a záměrně vynechání elementu objektu pro kolekci uvedené v oddílech syntaxe XAML jako implicitní kolekce syntaxe čas od času.  
  
 S výjimkou kořenový element ve skutečnosti je každý prvek objektu v souboru XAML, která je vnořená jako podřízený prvek jiného elementu element, který je jedno nebo obě z následujících případech: člen vlastnosti implicitní kolekce objektů svého nadřízeného elementu , nebo element, který určuje hodnotu vlastnosti obsahu XAML pro nadřazený element (XAML obsahu vlastnosti budou popsané v následující části). Jinými slovy je relace prvků nadřazené a podřízené elementy na stránce označení ve skutečnosti jeden objekt v kořenovém adresáři a každý prvek objektu pod kořenový adresář je buď jednu instanci, která poskytuje hodnotu vlastnosti nadřazeného objektu, nebo jednu z položek v rámci sloupec běr, který je také hodnotu vlastnosti typu kolekce nadřazeného prvku. Tento koncept single-root je běžné, XML a je často posílit v chování rozhraní API, která například načíst XAML <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 V následujícím příkladu je syntaxe s elementem objekt pro kolekci (<xref:System.Windows.Media.GradientStopCollection>) zadat explicitně.  
  
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
  
 Všimněte si, že není vždy možné explicitně deklarovat kolekce. Například pokus o deklaraci <xref:System.Windows.TriggerCollection> explicitně v dříve zobrazených <xref:System.Windows.Style.Triggers%2A> příklad selže. Explicitní deklarace kolekce vyžaduje, kolekci třídy musí podporovat výchozí konstruktor a <xref:System.Windows.TriggerCollection> nemá výchozí konstruktor.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Vlastnosti obsahu XAML  
 Obsahu syntaxe XAML je syntaxe, která je povolena pouze u tříd, které určují, <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást svých deklarace třídy. <xref:System.Windows.Markup.ContentPropertyAttribute> Odkazuje na název vlastnosti, která je vlastnost obsahu pro daný typ prvku (včetně odvozené třídy). Při zpracování procesoru XAML, všechny podřízené elementy nebo vnitřní text, který se nachází mezi počátečními a ukončovacími značkami elementu objektu přiřadí hodnotu vlastnosti obsahu XAML pro daný objekt. Je povoleno jej dále zadejte explicitní vlastnost prvky pro vlastnost obsahu, ale toto využití obecně nezobrazuje v oddílech syntaxe XAML v referenční dokumentaci rozhraní .NET. Explicitní/verbose technika má občasné hodnotu pro přehlednost kódu nebo jako pár styl značky, ale obvykle je záměr vlastnost obsahu pro zjednodušení kódu tak, aby prvky, které se týkají intuitivně jako nadřazený podřízený, které mohou být vnořené přímo. Jako "obsah" na striktní definice jazyka XAML; nejsou přiřazené značky elementů vlastnost pro další vlastnosti pro element Tyto se dříve zpracovávají v pořadí zpracování analyzátoru XAML a nejsou považovány za "obsah".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Hodnoty XAML vlastnost obsahu musí být Spojití  
 Hodnota vlastnosti XAML obsahu se musí předávat zcela před nebo po další prvky vlastnost zcela na tento prvek objektu. To platí, jestli hodnota vlastnosti XAML obsahu je určený jako řetězec, nebo jako jeden nebo více objektů. Například následující kód analyzuje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 To je v podstatě neplatný protože pokud tato syntaxe byly provedeny pomocí syntax prvku vlastnosti pro vlastnost ContentProperty explicitní, pak vlastnost obsahu se nastavuje dvakrát:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobně neplatné příklad je-li vlastnost obsahu je kolekce a podřízených elementů jsou spolu s vlastností elementů:  
  
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
## <a name="content-properties-and-collection-syntax-combined"></a>Vlastnosti obsahu a kombinovat syntaxi kolekce  
 Pokud chcete přijmout více než jeden objekt element jako obsahu, typu obsahu vlastnosti musí konkrétně být typu kolekce. Podobně jako na syntax prvku vlastnosti pro typy kolekcí, procesor XAML musí identifikovat typy, které jsou typy kolekcí. Pokud element má vlastnost obsahu XAML a typu obsahu vlastnosti XAML je kolekce, není potřeba zadat v kódu jako element objektu typu implicitní kolekce a vlastnost obsahu XAML není nutné zadat jako vlastnost el ement. Proto zřejmý obsahu modelu v kódu můžete teď mít více než jeden podřízený element přiřazen jako obsah. Tady je syntaxe obsahu <xref:System.Windows.Controls.Panel> odvozené třídy. Všechny <xref:System.Windows.Controls.Panel> odvozené třídy vytvořit vlastnost obsahu XAML jako <xref:System.Windows.Controls.Panel.Children%2A>, což vyžaduje hodnotu typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Všimněte si, že žádná vlastnost elementu pro <xref:System.Windows.Controls.Panel.Children%2A> ani prvek pro <xref:System.Windows.Controls.UIElementCollection> je nutné v kódu. To je funkce návrhu XAML tak, aby obsahovala rekurzivně prvky, které definují [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jsou více intuitivně reprezentována jako strom vnořené elementy s bezprostřední nadřazený podřízený element relace bez značky elementů použité vlastnost nebo objekty kolekce. Ve skutečnosti <xref:System.Windows.Controls.UIElementCollection> nelze zadat explicitně v kódu jako element objektu záměrné. Vzhledem k tomu, že jeho pouze slouží jako implicitní kolekce <xref:System.Windows.Controls.UIElementCollection> nevystavuje veřejný výchozí konstruktor a proto se nedá vytvořit instance jako element objektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Kombinace vlastností prvků a elementů objektu v objektu s vlastnost obsahu  
 Specifikace XAML deklaruje, že procesor XAML můžete vynutit, musí být spojití elementů objektu, které jsou použity k vyplnění vlastnost obsahu v rámci elementu objektu XAML a nesmí být smíšené. Toto omezení proti kombinace elementy vlastnosti a obsah je vynucena [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML procesory.  
  
 Podřízený element objekt může mít jako první okamžité značek v rámci elementu objektu. Potom můžete zavést prvcích vlastností. Nebo můžete zadat jeden nebo více vlastností prvků, pak obsah a pak další elementy vlastnosti. Ale po prvek vlastnosti následuje obsah, nelze zavést jakýkoli další obsah, mohli byste přidávat pouze elementy vlastnosti.  
  
 Tento obsah / požadavek pořadí vlastnosti elementu se nedá použít u použít jako obsah vnitřní text. Je však stále styl dobré značek ponechat vnitřní text souvislé, protože významných mezer bude obtížné zjistit vizuálně v kódu, pokud vlastnost prvky jsou spolu s vnitřním textu.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Obory názvů jazyka XAML  
 Zadaný žádný z předchozí příklady syntaxe oboru názvů XAML jiné než výchozí obor názvů XAML. V typické [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, výchozí obor názvů XAML je zadán jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oboru názvů. Můžete určit obory názvů XAML jiné než výchozí obor názvů XAML a dál používat podobná syntaxe. Ale nakonec kdekoli kde třída má název, který není dostupný v rámci výchozí obor názvů XAML, tento název třídy musí před sebou mít předponu oboru názvů XAML jako mapované na odpovídající obor názvů CLR. Například `<custom:Example/>` je syntaxe elementu objektu pro vytvoření instance instance `Example` třídy, kde obor názvů CLR obsahující tuto třídu (a případně informace externího sestavení, který obsahuje základní typy) byla dříve namapována na `custom` předponu.  
  
 Další informace o oborech názvů XAML najdete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 XAML definuje rozšíření značek programování entita, která umožňuje řídicí sekvence z normálního zpracování procesoru XAML řetězcové hodnoty atributů nebo elementů objektu a odloží zpracování na základní třídu. Znak, který identifikuje rozšíření značek XAML procesor při použití syntaxe atributu je levou složenou závorku ({}), za nímž následuje jakéhokoliv znaku jiného než uzavírací složená závorka (}). První řetězec, který po otevření složené závorky musí odkazovat na třídu, která poskytuje konkrétní rozšíření chování, kde odkaz se dá vynechat podřetězec "Rozšíření", pokud tento dílčí řetězec je součástí názvu třídy true. Po tomto datu může se zobrazit jedna mezera a potom každý následující znak se používá jako vstup implementací rozšíření, dokud nebude nalezen uzavírací složenou závorku.  
  
 Implementace .NET XAML používá <xref:System.Windows.Markup.MarkupExtension> abstraktní třídu jako základ pro všechna rozšíření značek nepodporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a také další architektury nebo technologie. Rozšíření značek, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konkrétně implementuje často slouží jako prostředky odkazovat na jiné existující objekty nebo odložené odkazuje na objekty, které se vyhodnotí za běhu. Například je jednoduché datové vazby WPF provést zadáním `{Binding}` – rozšíření značek namísto hodnotu, která by obvykle provést určité vlastnosti. Mnohé z rozšíření značek WPF povolit syntaxe atributu pro vlastnosti, kde by jinak nebylo možné syntaxe atributu. Například <xref:System.Windows.Style> objekt je poměrně komplexní typ, který obsahuje řadu vnořených objektů a vlastností. Styly WPF se obvykle definují jako prostředek v <xref:System.Windows.ResourceDictionary>a pak na něj odkazovat prostřednictvím jednoho dvě přípony označení WPF, které vyžádat prostředek. Rozšíření značek odloží vyhodnocení hodnoty vlastností pro vyhledání prostředku a povolí poskytování hodnoty <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, přičemž typ <xref:System.Windows.Style>v atributu syntaxe jako v následujícím příkladu:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Tady `StaticResource` identifikuje <xref:System.Windows.StaticResourceExtension> třída poskytuje implementaci rozšíření značek. Další řetězec `MyStyle` slouží jako vstup pro jiné než výchozí <xref:System.Windows.StaticResourceExtension> konstruktoru, kde deklaruje požadovaného parametru, jak na základě řetězce přípon <xref:System.Windows.ResourceKey>. `MyStyle` Očekává se bude [x: Key](../../xaml-services/x-key-directive.md) hodnotu <xref:System.Windows.Style> definována jako prostředek. [– Rozšíření značek StaticResource](staticresource-markup-extension.md) využití požadavků k zajištění použít prostředek <xref:System.Windows.Style> hodnota vlastnosti prostřednictvím statických prostředků logika vyhledávání v okamžiku načtení.  
  
 Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md). Reference – rozšíření značek a dalších XAML programovací funkce povolené v obecných implementace .NET XAML, naleznete v tématu [Namespace XAML (x:) Funkce jazyka](../../xaml-services/xaml-namespace-x-language-features.md). Specifické pro WPF – rozšíření značek, naleznete v tématu [rozšíření WPF XAML](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Přidružené vlastnosti  
 Připojené vlastnosti jsou programovací koncept zavedené v XAML, kterým je možné vlastnosti ve vlastnictví a určené určitého typu, ale nastavit jako atributy nebo elementy vlastností jakéhokoli elementu. Primární scénáře, že jsou připojené vlastnosti určené pro je umožnit podřízené prvky ve struktuře značek k informacím o sestavu na nadřazený element bez nutnosti výrazně sdílené objektový model přes všechny prvky. Připojené vlastnosti je možné naopak nadřazené prvky sestavy informací podřízené prvky. Další informace o účelu připojené vlastnosti a tom, jak vytvořit svoje vlastní přidružené vlastnosti, najdete v části [přehled připojených vlastností](attached-properties-overview.md).  
  
 Připojené vlastnosti pomocí syntaxe podobná na první pohled syntax prvku vlastnosti v tom, že zadáváte *typeName*. *Vlastnost propertyName* kombinaci. Existují dva důležité rozdíly:  
  
- Můžete použít *typeName*. *Vlastnost propertyName* kombinaci, i když nastavení připojené vlastnosti prostřednictvím syntaxe atributu. Připojené vlastnosti jsou že pouze tam, kde kvalifikováním názvu vlastnosti je požadavek ve syntaxe atributu.  
  
- Můžete také používat syntax prvku vlastnosti pro připojené vlastnosti. Však pro syntax prvku vlastnosti typické *typeName* zadáte, je element objektu, který obsahuje element vlastnosti. Pokud odkazujete na připojené vlastnosti, pak bude *typeName* je třída, která definuje připojená vlastnost není nadřazeného elementu objektu.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Přidružené události  
 Připojené události jsou jiné programovací koncept zavedené v XAML, ve kterém události lze definovat pomocí konkrétního typu, ale mohou být obslužné rutiny připojeny u libovolného elementu objektu. V implementaci WOF často typ, který definuje přidružená událost je statický typ, který definuje službu a někdy jsou tyto připojené události vystavené alias směrované události v typech, které zpřístupňují služby. Obslužné rutiny pro připojené události jsou určeny pomocí syntaxe atributu. S připojené události, je syntaxe atributu rozbalené pro připojené události umožňující *typeName*. *eventName* využití, ve kterém *typeName* je třída, která poskytuje `Add` a `Remove` přístupových objektů obslužné rutiny událostí pro infrastrukturu přidružená událost a *eventName* je název události.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie kořenový prvek XAML  
 Následující tabulka ukazuje typické XAML kořenový element rozepsané zobrazující konkrétní atributy kořenový element:  
  
|||  
|-|-|  
|`<Page`|Otevření objektu element kořenového elementu|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Výchozí hodnota ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) obor názvů XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Obor názvů XAML jazyka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Částečné deklarace třídy, která se připojuje k žádné použití modelu code-behind značek definovaný pro částečné třídy|  
|`>`|Konec elementu objektu pro kořenový adresář. Objekt není ještě zavřít, protože obsahuje podřízené prvky prvku|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Použití volitelné a Nonrecommended XAML  
 Následující části popisují použití XAML technicky podporuje procesory XAML, ale které vyvolávají podrobností nebo jiné aesthetic problémy, které vás omezují zbývající lidsky čitelném při vývoji aplikací, které obsahují zdroje XAML soubory XAML.  
  
### <a name="optional-property-element-usages"></a>Použití elementu volitelné vlastnosti  
 Použití elementu volitelné vlastnosti zahrnují explicitně výpisu obsahu vlastnosti prvku, že procesor XAML bere v úvahu implicitní. Například, pokud deklarujete obsah <xref:System.Windows.Controls.Menu>, můžete se rozhodnout explicitně deklarovat <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce <xref:System.Windows.Controls.Menu> jako `<Menu.Items>` značky elementu vlastnosti a místo jednotlivých <xref:System.Windows.Controls.MenuItem> v rámci `<Menu.Items>`, a nikoli než při použití implicitního procesoru chování XAML, který všechny podřízené prvky prvku <xref:System.Windows.Controls.Menu> musí být <xref:System.Windows.Controls.MenuItem> a jsou umístěny v <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce. Volitelné použití někdy může pomoct vizuálně vysvětlení struktury objekt reprezentovaný v kódu. Nebo v některých případech můžete použití explicitní vlastnost elementu vyhnout kód, který je technicky funkční, ale vizuálně matoucí, jako je například rozšíření značek vnořené v rámci hodnotu atributu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Úplné typeName.memberName kvalifikovaný atributy  
 *TypeName*. *memberName* formulář pro atribut ve skutečnosti funguje univerzálně než jenom v případě směrované události. Ale v jiných situacích je nadbytečný, které tvoří a měli byste se vyhnout, pokud pouze z důvodů stylu kódu a čitelnost. V následujícím příkladu všechny tři odkazuje na <xref:System.Windows.Controls.Control.Background%2A> atribut jsou zcela ekvivalentní:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` postup funguje, protože kvalifikovaný vyhledávání pro tuto vlastnost na <xref:System.Windows.Controls.Button> úspěšné (<xref:System.Windows.Controls.Control.Background%2A> bylo zděděno z ovládacího prvku) a <xref:System.Windows.Controls.Button> je třída elementu, který objekt nebo základní třídy. `Control.Background` postup funguje, protože <xref:System.Windows.Controls.Control> třída definuje ve skutečnosti <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.Controls.Control> je <xref:System.Windows.Controls.Button> základní třídy.  
  
 Ale následující *typeName*. *memberName* příklad form nefunguje a proto zobrazuje komentářem:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> je jiný odvozená třída <xref:System.Windows.Controls.Control>, a pokud jste měli zadali `Label.Background` v rámci <xref:System.Windows.Controls.Label> elementu objektu, toto využití by jste již dříve pracovali. Ale protože <xref:System.Windows.Controls.Label> není třída nebo základní třídu <xref:System.Windows.Controls.Button>, zadané chování procesoru XAML je následně zpracovat `Label.Background` jako připojené vlastnosti. `Label.Background` není k dispozici připojené vlastnosti a použití těchto selže.  
  
### <a name="basetypenamemembername-property-elements"></a>Elementy vlastnosti baseTypeName.memberName  
 Obdobným způsobem jak *typeName*. *memberName* formuláře funguje pro syntaxi atributů *baseTypeName*. *memberName* syntaxe se dá použít pro syntax prvku vlastnosti. Například následující syntaxe funguje:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Tady, element vlastnosti byla poskytnuta jako `Control.Background` i v případě, že element vlastnosti se nacházely v `Button`.  
  
 Ale stejně jako *typeName*. *memberName* formuláře pro atributy, *baseTypeName*. *memberName* je nízký styl v kódu a neměli byste ho.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Namespace XAML (x:) Jazykové funkce](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozšíření WPF XAML](wpf-xaml-extensions.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [TypeConverters a XAML](typeconverters-and-xaml.md)
- [XAML a vlastní třídy pro WPF](xaml-and-custom-classes-for-wpf.md)
