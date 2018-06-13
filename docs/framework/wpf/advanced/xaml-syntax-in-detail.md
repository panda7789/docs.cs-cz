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
ms.openlocfilehash: d98141c0ad96ef1bd3958ae8d3166aedde76f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549474"
---
# <a name="xaml-syntax-in-detail"></a>Podrobná syntaxe XAML
Toto téma definuje termíny, které se používají k popisu elementů XAML syntaxe. Tyto podmínky se často používají v dalších částech této dokumentace pro dokumentace WPF, konkrétně a pro ostatní rozhraní, využívající XAML nebo se základními koncepty XAML ve podporu jazyka XAML na úrovni System.Xaml povolené. Toto téma rozšíří na základní terminologii zavedená v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specifikace jazyka XAML  
 Terminologie syntaxe jazyka XAML, zde definované je také definován nebo je odkazované v rámci specifikace jazyka XAML. XAML je jazyk podle XML a následuje nebo je jejich rozšířením strukturální pravidla XML. Některé terminologie sdíleného ze nebo podle terminologie běžně používané při popisu jazyka XML nebo objektu modelu dokumentu XML.  
  
 Další informace o specifikaci jazyka XAML, stáhněte si [ \[MS-XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525) z webu Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML a CLR  
 XAML je jazyk značek. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Jako předpokládané jeho název, umožňuje spuštění modulu runtime. XAML není sám o sobě jednou z běžných jazyky, které se využívá přímo za běhu CLR. Místo toho si můžete představit XAML jako podpora svůj vlastní systém typů. Konkrétní XAML analýzy systém, který je používán WPF je založený na modulu CLR a systém typů CLR. XAML typy jsou namapované na typy CLR pro vytvoření instance znázornění běhu, když je analyzovat XAML pro grafický subsystém WPF. Z tohoto důvodu bude zbytek diskuzi o syntaxe v tomto dokumentu obsahovat odkazy na systém typů CLR, i když nemusí diskusí ekvivalentní syntaxe v specifikace jazyka XAML. (Na úrovni specifikace jazyka XAML, typy XAML mapovat všechny ostatní typ systémy, které nemusí být modulu CLR, ale které by vyžadovaly vytváření a použití různých analyzátor jazyka XAML.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Členové typy a dědičnosti tříd  
 Vlastnosti a události se zobrazí jako členové XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu se často dědí ze základních typů. Představte si třeba tento příklad: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Vlastnost není okamžitě deklarovanou vlastností v <xref:System.Windows.Controls.Button> třídy kdyby se podívat na definici třídy, výsledky reflexe nebo v dokumentaci. Místo toho <xref:System.Windows.Controls.Control.Background%2A> je zděděn ze základní <xref:System.Windows.Controls.Control> třídy.  
  
 Chování dědičnosti třídy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů XAML je významné odchýlení od schématu vynucená výklad značek XML. Dědičnost třídy se může stát komplexní, zvláště pokud zprostředkující základní třídy jsou abstraktní, nebo když se podílejí rozhraní. Toto je jeden důvod sadu elementů XAML a jejich atributy povolenou je obtížně představují přesně a úplně pomocí typy schémat, které se obvykle používají pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] programování, jako je například ve formátu souboru DTD protokolu nebo XSD. Dalším důvodem je, že rozšíření a mapování typu funkce jazyka XAML, samotné vylučují úplnost všechny pevné reprezentace povolenou typů a členů.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Syntaxe objektu – Element  
 *Objekt elementu syntaxe* je syntaxe značek XAML, která vytvoří instanci CLR třídu nebo strukturu deklarováním elementu XML. Tato syntaxe vypadá takto: element syntaxe jiných jazyků značek, například HTML. Syntaxe objektu element začíná levou hranatou závorku (\<), hned následuje název typu třídu nebo strukturu, vytváření instancí. Mezery v počtu nula či více můžete postupujte podle název typu a počtu nula či více atributů může být také deklarován v elementu objektu prostory jeden nebo více oddělení každý atribut name = "value" pair. Nakonec jednu z následujících musí být splněné:  
  
-   Element a značky musí být uzavřeny lomítkem (/) vzápětí pravé ostré závorky (>).  
  
-   Počáteční značka musí dokončit pravé ostré závorky (>). Další prvky objektu, vlastnost elementy nebo vnitřní text, můžete postupovat podle počáteční značka. Přesně jaké obsahu mohou být obsaženy v tomto poli je obvykle omezené objektový model elementu. Ekvivalentní ukončovací značka pro object element musí existovat správný vnořování a vyvážit s další otevírací a uzavírací značka párů.  
  
 XAML, jak je implementované .NET je sada pravidel, které mapují elementy objektu do typů atributů do vlastnosti nebo události a obory názvů jazyka XAML pro obory názvů CLR plus sestavení. WPF a rozhraní .NET Framework, elementů XAML objekt mapování na [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] typy definované v odkazovaná sestavení a atributy mapování na členy z těchto typů. Když odkazujete na typ CLR v jazyce XAML, máte přístup k zděděné členy tohoto typu také.  
  
 Například v následujícím příkladu je syntaxe element objektu, který vytvoří novou instanci třídy <xref:System.Windows.Controls.Button> třídy a také určuje <xref:System.Windows.FrameworkElement.Name%2A> atribut a hodnotu pro tento atribut:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 V následujícím příkladu je syntaxe element objektu, který také obsahuje vlastnost obsahu syntaxe jazyka XAML. Vnitřní text obsažené v se použije k nastavení <xref:System.Windows.Controls.TextBox> vlastnost obsahu XAML <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Obsahu modely  
 Třída může podporovat použití jako element XAML objekt z hlediska syntaxe, ale tohoto prvku bude pouze fungovat správně v aplikaci nebo stránce Pokud je umístěn v očekávané poloze celého obsahu stromu modelu nebo elementu. Například <xref:System.Windows.Controls.MenuItem> by měl obvykle být umístěna pouze jako podřízenou <xref:System.Windows.Controls.Primitives.MenuBase> odvozené třídy, jako <xref:System.Windows.Controls.Menu>. Obsahu modely pro konkrétní prvky popsané v rámci poznámky na stránkách třídy pro ovládací prvky a dalších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, které lze použít jako elementů XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Vlastnosti elementů v objektu  
 Řadu možných syntaxe jsou nastavit vlastnosti v jazyce XAML. Syntaxe, které lze použít pro konkrétní vlastnosti budou lišit v závislosti na základní charakteristiky systému typu vlastnosti, která nastavíte.  
  
 Nastavením hodnoty vlastností můžete přidat funkce nebo vlastnosti na objekty, které jsou v době běhu objekt grafu. Počáteční stav vytvořený objekt z objektu prvku je založena na výchozí konstruktor chování. Obvykle se vaše aplikace bude používat něco jiného než úplně výchozí instance libovolného objektu.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Atribut syntaxe (Vlastnosti)  
 Atribut syntaxe je syntaxe značek XAML, která nastaví hodnotu pro vlastnost deklarováním atribut na existující objekt elementu. Název atributu musí odpovídat názvu člen CLR vlastnosti třídy, která zálohuje relevantní objekt elementu. Operátor přiřazení (=) následuje název atributu. Hodnota atributu musí být řetězec uzavřena v uvozovkách.  
  
> [!NOTE]
>  Střídání uvozovky můžete umístit do atribut literálu uvozovky. Například můžete jednoduchých uvozovek a být jako prostředek deklarovat řetězec, který obsahuje znak dvojitých uvozovek v něm. Jestli používáte jednoduché nebo dvojité uvozovky, měli byste použít pár odpovídající pro otvírání a zavírání řetězec hodnotu atributu. Existují také řídicí sekvence nebo jinými technikami, k dispozici pro obcházet omezení znaků, které nevyžaduje žádnou konkrétní syntaxi XAML. V tématu [znakové entity XML a jazyk XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby bylo možné nastavit pomocí syntaxe atributu, vlastnosti musí být veřejné a musí být zapisovatelný. Hodnota vlastnosti v systému základní typ musí být typ hodnoty, nebo musí být odkazového typu, který se dá vytvořit instance nebo odkazuje na procesor XAML při přístupu k příslušné zálohování typu.  
  
 Pro události WPF XAML událost, která je odkazováno jako název atributu musí být veřejné a mít veřejný delegát.  
  
 Vlastnost nebo události musí být členem skupiny třídu nebo strukturu, která je vytvořena instance obsahující objekt elementu.  
  
### <a name="processing-of-attribute-values"></a>Zpracování hodnot atributu  
 Řetězcová hodnota obsažených v otevírání a uzavírací uvozovky zpracovává procesor XAML. Výchozí zpracování chování pro vlastnosti, je dáno typ základní vlastnosti CLR.  
  
 Hodnota atributu je vyplněno pomocí jedné z následujících pomocí tohoto pořadí zpracování:  
  
1.  Pokud procesor XAML zaznamená složené závorky, nebo objekt element, který je odvozen od <xref:System.Windows.Markup.MarkupExtension>, pak rozšíření odkazované značek vyhodnotí první místo zpracování hodnota jako řetězec a objekt vrácený rozšíření značek se používá jako hodnota. Objekt vrácený rozšíření značek v mnoha případech bude odkaz na existující objekt nebo výraz, který odkládat údaje vyhodnocení až při spuštění a není nově vytvořenou instanci objektu.  
  
2.  Pokud je deklarovaná vlastnost se s atributy <xref:System.ComponentModel.TypeConverter>, nebo typ hodnoty této vlastnosti je deklarovaný s s atributy <xref:System.ComponentModel.TypeConverter>, řetězcovou hodnotu atributu, je odeslána převaděče typů jako vstup převodu, a vrátí převaděč nové instance objektu.  
  
3.  Pokud není žádná <xref:System.ComponentModel.TypeConverter>, dojde k pokusu o přímé převod na typ vlastnosti. Tento poslední úroveň je přímé převodu na hodnotu analyzátor nativní mezi primitivní typy jazyka XAML, nebo zkontrolovat pro názvy pojmenované konstanty v výčet (Analyzátor pak odpovídající hodnoty přistupuje k).  
  
#### <a name="enumeration-attribute-values"></a>Hodnoty atributů – výčet  
 Výčty v jazyce XAML vnitřně zpracovává analyzátory jazyka XAML a členy výčtu by měl zadat tak, že zadáte název řetězce objektu jeden z pojmenované konstanty výčtu.  
  
 Nativní chování pro hodnoty výčtu nonflag, je zpracovat řetězec hodnotu atributu a přeložte ho na jednu z hodnot výčtu. Ve formátu nezadáte výčtu *výčtu*. *Hodnota*, stejně jako v kódu. Místo toho zadat pouze *hodnotu*, a *výčtu* odvodí typ vlastnosti nastavíte. Pokud zadáte atribut v *výčtu*. *Hodnota* formulář, se nevyřeší správně.  
  
 Pro flagwise výčty chování na základě <xref:System.Enum.Parse%2A?displayProperty=nameWithType> metoda. Můžete zadat více hodnot pro flagwise výčet jednotlivé hodnoty oddělíte čárkou. Však nelze kombinovat hodnot výčtu, která nejsou flagwise. Například nemůžete použít syntaxi čárkami k pokusu o vytvoření <xref:System.Windows.Trigger> , který funguje na více podmínek na výčet nonflag:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Flagwise výčty, které podporují atributy, které jsou v jazyce XAML nastavit vyskytují jen vzácně v grafickém subsystému WPF. Je však jeden takový výčet <xref:System.Windows.Media.StyleSimulations>. Může například použijte syntaxi oddělených čárkou flagwise atribut upravit v příkladu v poznámky pro <xref:System.Windows.Documents.Glyphs> třídy; `StyleSimulations = "BoldSimulation"` může být `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> je jinou vlastnost, kde lze zadat více než jednu hodnotu výčtu. Ale tato vlastnost se stane být zvláštní případ, protože <xref:System.Windows.Input.ModifierKeys> výčet podporuje vlastní typ převaděče. Převaděč typů pro modifikátory znaménko plus (+) používá jako oddělovač, nikoli čárkou (,). Tento převod podporuje tradičnější syntaxe představují kombinace kláves při programování pro Microsoft Windows, jako je například "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Vlastnosti a události člen název odkazy  
 Při zadávání atribut, můžete odkazovat na všechny vlastnosti nebo událostí, který již existuje jako člena typu CLR, která je vytvořena instance pro element obsahující objektu.  
  
 Nebo můžete odkazovat přidružená vlastnost nebo připojených událostí, nezávisle na obsahující element object. (Přidružené vlastnosti jsou popsané v následující části).  
  
 Můžete také název žádné události z libovolného objektu, která je přístupná prostřednictvím výchozí obor názvů pomocí *typeName*. *událost* částečně kvalifikovaný název; Tato syntaxe podporuje připojení obslužné rutiny pro směrované události, kde je záměrem obslužná rutina pro zpracování události směrování z podřízených elementů, ale nadřazeného elementu také nemá tuto událost v tabulce její členy. Tato syntaxe vypadá takto: syntaxe přidružená událost, ale událost zde není true přidružená událost. Místo toho je odkazováno na událost kvalifikovaný název. Další informace najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 V některých případech jsou názvy vlastností někdy zadaný jako hodnota atributu, nikoli název atributu. Název této vlastnosti může také obsahovat kvalifikátory, jako je například vlastnost zadat ve tvaru *ownerType*. *dependencyPropertyName*. Tento scénář je běžný, při zápisu styly nebo šablony v jazyce XAML. Zpracování pravidla pro názvy vlastností, které jsou k dispozici jako hodnota atributu se liší a se řídí podle typu vlastnost Probíhá nastavení nebo prostřednictvím chování konkrétní subsystémy WPF. Podrobnosti najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Další využití pro názvy vlastností je, když hodnota atributu popisuje vztah – vlastnost. Tato funkce se používá pro datovou vazbu a pro scénáře cíle a je povolen jako <xref:System.Windows.PropertyPath> třídy a její typ převaděče. Podrobnější popis sémantiku vyhledávání, najdete v části [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Vlastnost Element syntaxe  
 *Vlastnost element syntaxe* je syntaxe, která diverges poněkud ze základní pravidla syntaxe jazyka XML pro elementy. V XML hodnota atributu je fakticky řetězec, s jedinou možnou variace se používá formát kódování řetězec. V jazyce XAML můžete přiřadit další elementy objektu jako hodnota vlastnosti. Tato funkce je ve syntaxe element vlastnost povolena. Místo vlastnost specifikované jako atribut ve značce elementu, je zadána vlastnost pomocí elementu otevírání značky v *elementTypeName*. *propertyName* formuláře, hodnota vlastnosti je zadán v rámci a pak je uzavřený element vlastnosti.  
  
 Konkrétně syntaxe začíná levou hranatou závorku (\<), hned následuje název typu třídy nebo struktura, která syntaxe element vlastnost je obsažena v. Následují okamžitě jedna tečka (.) a potom podle názvu vlastnosti, pak pravém úhlu závorku (>). Stejně jako u atributu Syntaxe této vlastnosti musí existovat v rámci deklarované veřejné členy zadaného typu. Hodnota, která má být přiřazeno k vlastnosti je obsažených v elementu vlastnost. Obvykle se hodnota je zadána jako jeden či více elementů objekt, protože zadání objekty jako hodnoty je tento scénář element Syntaxe této vlastnosti je určená adresu. Nakonec ekvivalentní uzavírací značku zadání stejné *elementTypeName*. *propertyName* kombinace musí být zadáno v správné vnoření a vyrovnávat s jiné značky elementu.  
  
 Například následující je vlastnost element syntaxe <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Hodnota v rámci elementu vlastnost také je možné přidělit jako vnitřní text v případech, kdy se zadaný typ primitivní hodnota typu, například <xref:System.String>, nebo výčet tam, kde je zadán název. Tyto dvě použití jsou poněkud neobvyklé, protože každý z těchto případech může také použít jednodušší syntaxe atribut. Jeden scénář pro vyplnění element vlastnosti pomocí řetězce se pro vlastnosti, které nejsou vlastnost obsahu XAML, ale stále používají k reprezentaci textu uživatelského rozhraní a konkrétní prázdné prvky, jako jsou například přečtené se musí uvést v tomto textu uživatelského rozhraní. Syntaxe atributu nelze zachovat přečtené, ale vlastnost element syntaxe můžete tak dlouho, dokud písmen a zachovávání významný mezerový znak je aktivní (podrobnosti najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)). Další možností je, aby [x: Uid – direktiva](../../../../docs/framework/xaml-services/x-uid-directive.md) může být použita vlastnost prvek a jako hodnotu, která by měl být lokalizovaný v WPF výstup BAML nebo jinými technikami, proto označit na hodnotu v rámci.  
  
 Vlastnost element není uvedeno v logickém stromu WPF. Vlastnost element je právě specifickou syntaxi pro nastavení vlastnosti a není element, který má instance nebo objekt jejich zálohování. (Podrobnosti v logickém stromu koncept najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).)  
  
 U vlastností, kde je podporováno atribut i pro vlastnost element syntaxe dvě syntaxe obecně mít stejný výsledek, i když odlišnosti například zpracování prázdných znaků se může mírně lišit mezi syntaxe.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Syntaxe kolekce  
 Specifikace jazyka XAML vyžaduje implementace zpracovatelů XAML pro určení vlastností, kde typ hodnoty je kolekce. Obecné implementace procesoru XAML v rozhraní .NET je založená na spravovaný kód a modulu CLR a identifikuje typy kolekcí prostřednictvím jednoho z následujících akcí:  
  
-   Zadejte implementuje <xref:System.Collections.IList>.  
  
-   Zadejte implementuje <xref:System.Collections.IDictionary>.  
  
-   Typ je odvozena z <xref:System.Array> (Další informace o pole v jazyce XAML najdete v tématu [x: Array – rozšíření značek](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
 Pokud je typ vlastnosti kolekce, pak typ odvozené kolekce nemusí být zadané ve značce jako element objektu. Místo toho prvky, které jsou určeny k položky v kolekci jsou zadané jako jeden nebo více podřízených elementů element vlastnosti. Každé takové položky je vyhodnocena jako objekt během načítání a přidat do kolekce voláním `Add` metoda předpokládané kolekce. Například <xref:System.Windows.Style.Triggers%2A> vlastnost <xref:System.Windows.Style> trvá typ specializované kolekce <xref:System.Windows.TriggerCollection>, který implementuje <xref:System.Collections.IList>. Není nutné k vytváření instancí <xref:System.Windows.TriggerCollection> element object ve značkách. Místo toho zadat jednu nebo několik <xref:System.Windows.Trigger> položky jako elementů v rámci `Style.Triggers` vlastnost elementu, kde <xref:System.Windows.Trigger> (nebo v odvozené třídě) je na typ očekávaný jako typ položky pro silného typu a implicitní <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Vlastnost může být typ kolekce a vlastnost XAML pro tento typ obsahu a odvozené typy, které je popsané v další části tohoto tématu.  
  
 Element implicitní kolekce vytvoří člen v logickém stromu reprezentace, i když v kód jako element nezobrazí. Obvykle konstruktoru nadřazený typ provede instance pro kolekci, která je jedna z vlastností a původně prázdné kolekce stane součástí stromu objektů.  
  
> [!NOTE]
>  Obecná rozhraní seznamu a slovníku (<xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IDictionary%602>) nejsou podporovány pro zjišťování kolekce. Můžete však použít <xref:System.Collections.Generic.List%601> třídy jako základní třída, protože implementuje <xref:System.Collections.IList> přímo, nebo <xref:System.Collections.Generic.Dictionary%602> jako základní třída, protože implementuje <xref:System.Collections.IDictionary> přímo.  
  
 Na stránkách .NET – referenční informace pro typy kolekcí této syntaxe s záměrné vynechání element object pro kolekci je občas si poznamenali v části Syntaxe jazyka XAML jako implicitní syntaxe kolekce.  
  
 S výjimkou kořenový element každý element v souboru XAML, který je vnořený jako podřízený prvek elementu jiného, objekt je ve skutečnosti element, který je jedno nebo obě následující případy: členem ve vlastnosti implicitní kolekce objektů svého nadřízeného elementu , nebo element, který určuje hodnotu vlastnosti obsahu XAML pro nadřazený element (XAML obsahu vlastnosti budou popsané v následující části). Jinými slovy relace elementů nadřazené a podřízené elementy na stránce kód je ve skutečnosti jeden objekt v kořenovém adresáři, a každý element object pod kořenovou je buď jednu instanci, která poskytuje hodnotu vlastnosti nadřazeného objektu, nebo jedné z položek v rámci sloupec běr, která je také hodnotu vlastnosti typu kolekce nadřazeného objektu. Tento koncept single-root je obvyklé u XML a je často zesílené v chování rozhraní API, která načíst XAML, jako <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Následující příklad je syntaxe s elementem objekt v kolekci (<xref:System.Windows.Media.GradientStopCollection>) explicitně zadané.  
  
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
  
 Všimněte si, že není vždy možné explicitně deklarovat kolekce. Například se pokouší deklarovat <xref:System.Windows.TriggerCollection> explicitně v dříve uvedené <xref:System.Windows.Style.Triggers%2A> příklad skončí s chybou. Explicitní deklarace kolekce vyžaduje, aby třídě kolekce musí podporující výchozí konstruktor, a <xref:System.Windows.TriggerCollection> nemá výchozí konstruktor.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Vlastnosti obsahu XAML  
 Syntaxe obsahu XAML není syntaxi, která je povolena pouze v třídy, které určují <xref:System.Windows.Markup.ContentPropertyAttribute> jako součást jejich deklaraci třídy. <xref:System.Windows.Markup.ContentPropertyAttribute> Odkazuje na název vlastnosti, která je vlastnost obsahu pro tento typ elementu (včetně odvozené třídy). Při zpracování procesoru XAML, všechny podřízené elementy nebo vnitřní text, který se nachází mezi počáteční a koncové značky elementu objektu bude přiřazen jako hodnota vlastnosti obsahu XAML pro tento objekt. Jsou povoleny pro určení prvků explicitní vlastnost pro vlastnost obsahu, ale toto použití není zobrazena, obvykle v oddílech syntaxe XAML v odkaz na rozhraní .NET. Explicitní/verbose technika má příležitostně hodnotu pro přehlednost značek nebo jako řádu styl značky, ale obvykle obsahu vlastnosti je cílem zjednodušit kód, aby elementy, které souvisejí se intuitivně jako nadřazený podřízený, které mohou být vnořené přímo. Vlastnost element značky pro ostatní vlastnosti v elementu nejsou přiřazeny jako "obsah" za striktní definici jazyka XAML; Tyto jsou zpracovány dříve v pořadí zpracování analyzátor jazyka XAML a nejsou považovány za "obsah".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Hodnoty XAML vlastnost obsahu musí být Spojití  
 Hodnota vlastnosti XAML obsahu musí být uvedeny zcela před nebo po další prvky vlastnost zcela na tento element object. To platí, zda je zadaná hodnota vlastnosti obsahu XAML, jako řetězec, nebo jako jeden nebo více objektů. Například následující kód neanalyzuje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Toto je neplatný v podstatě vzhledem k tomu, že pokud pomocí syntaxe element vlastnost pro vlastnost obsahu byly provedeny explicitní této syntaxe, pak vlastnost obsahu se nastavuje dvakrát:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobně jako neplatný příklad je-li vlastnost obsahu je kolekce a podřízené elementy jsou spolu s vlastností elementů:  
  
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
## <a name="content-properties-and-collection-syntax-combined"></a>Kolekce syntaxi kombinaci a vlastnosti obsahu  
 Chcete-li přijímat více než jeden objekt element jako obsahu, typu obsahu vlastnosti konkrétně nutné typu kolekce. Podobně jako u vlastnosti element syntaxe pro typy kolekcí, procesor XAML musí identifikovat typy, které jsou typy kolekcí. Pokud element má vlastnost XAML obsahu a typu obsahu vlastnosti XAML je kolekce, není potřeba zadat ve značce jako element objektu typu předpokládané kolekce a vlastnost obsahu XAML není potřeba zadat jako vlastnost el ement. Proto zřejmá modelu obsahu do kódu nyní mít více než jeden podřízený element přiřazen jako obsah. Toto je syntaxe obsahu <xref:System.Windows.Controls.Panel> odvozené třídy. Všechny <xref:System.Windows.Controls.Panel> odvozené třídy navázat obsahu vlastnost XAML jako <xref:System.Windows.Controls.Panel.Children%2A>, což vyžaduje, aby se hodnota typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Všimněte si, že ani vlastnost element pro <xref:System.Windows.Controls.Panel.Children%2A> ani element pro <xref:System.Windows.Controls.UIElementCollection> je potřeba ve značkách. Toto je funkce návrhu XAML tak, aby obsahovala rekurzivně prvky, které definují [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jsou více intuitivně reprezentována jako strom vnořených elementů okamžitou nadřazený podřízený element relace, bez použité značky elementu vlastnost nebo kolekce objektů. Ve skutečnosti <xref:System.Windows.Controls.UIElementCollection> nesmí být zadána explicitně v kódu jako element objektu podle návrhu. Protože jeho jedinou slouží jako kolekci implicitní <xref:System.Windows.Controls.UIElementCollection> nevystavuje veřejný výchozí konstruktor a proto nelze vytvořit instanci jako objekt elementu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Kombinování vlastnost elementy a objekt elementy v objektu s obsahu vlastností  
 Specifikace jazyka XAML deklaruje, že procesor XAML můžete vynutit, musí být souvislá objekt elementy, které se používají k vyplnění vlastnost XAML obsahu v rámci elementu objektu a nesmí kombinovat. Je toto omezení proti kombinování elementy vlastnosti a obsah vynucené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML procesory.  
  
 Podřízený element object může mít jako první okamžitou značka v rámci objektu elementu. Potom můžou představovat vlastnost elementy. Nebo můžete zadat jeden či více elementů vlastnost pak obsah a další prvky vlastnost. Ale po elementu vlastnost odpovídá obsahu, nesmíte také provést žádné další obsah, můžete přidat jenom elementy vlastnost.  
  
 Tento obsah / vlastnost element pořadí požadavek se nevztahuje na vnitřní text, který slouží jako obsah. Je však stále dobrý značek styl ponechat vnitřní text souvislý, protože významný mezerový znak bude obtížné zjistit vizuálně do kódu, pokud jsou vlastnost elementy spolu s vnitřní text.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Obory názvů jazyka XAML  
 Zadaný žádný z předchozí příklady syntaxe oboru názvů jazyka XAML než výchozí obor názvů jazyka XAML. V typické [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, výchozí hodnota oboru názvů jazyka XAML je zadán jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oboru názvů. Můžete zadat obory názvů jazyka XAML než výchozí obor názvů jazyka XAML a dál používat podobné syntaxe. Ale pak kdekoli třídu kde jmenuje, není dostupný v rámci oboru názvů jazyka XAML výchozí název této třídy musí předcházet předponu oboru názvů jazyka XAML jako namapované na odpovídající obor názvů CLR. Například `<custom:Example/>` se vytvoří instanci objektu element syntaxe `Example` třídy, kde bylo CLR obor názvů obsahuje třídy (a případně informací o externí sestavení, která obsahuje základní typy) dříve mapováno na `custom` předponu.  
  
 Další informace o obory názvů jazyka XAML najdete v tématu [obory názvů jazyka XAML a Namespace mapování pro jazyk XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozšíření značek  
 XAML definuje – programování entita, která umožňuje úniku z normálního zpracování procesoru XAML hodnoty atributu řetězec nebo objekt elementy a odkládat údaje zpracování základní třídy rozšíření značek. Znak, který identifikuje rozšíření značek pro jazyk XAML procesor pomocí syntaxe atribut po otevření složené závorky ({}), za nímž následuje libovolný znak než uzavírací složená závorka (}). První řetězec po otevření složené závorky musí odkazovat na třídu, která poskytuje chování konkrétní rozšíření, kde může odkaz na vynechejte dílčí řetězec "Rozšíření", pokud tento dílčí řetězec je součástí názvu třídy hodnotu true. Následně a jedna mezera, může se zobrazit, a potom každý všechna následující znak se používá jako vstup implementací rozšíření, dokud složené závorky uzavírací je došlo.  
  
 Implementace rozhraní .NET XAML používá <xref:System.Windows.Markup.MarkupExtension> abstraktní třída jako základ pro všechna rozšíření značek nepodporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a také další rozhraní nebo technologie. Rozšíření značek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konkrétně implementuje jsou často určené k poskytnutí znamená, chcete-li jiné existující objekty, nebo pokud chcete udělat odložené odkazy na objekty, které se vyhodnotí v době běhu. Například je jednoduché datové vazby WPF provést zadáním `{Binding}` – rozšíření značek místo hodnotu, která by obvykle trvat určité vlastnosti. Řadu rozšíření značek WPF povolit atributu syntaxe vlastností, kde atributu syntaxe jinak nebude možné. Například <xref:System.Windows.Style> objekt je poměrně složité typu, který obsahuje řadu vnořených objektů a vlastností. Styly v grafickém subsystému WPF jsou obvykle definovány jako prostředek v <xref:System.Windows.ResourceDictionary>a potom na něj odkazovat prostřednictvím jednoho z dvě rozšíření značek WPF, které požadují prostředku. Rozšíření značek odkládat údaje vyhodnocení hodnoty vlastnosti k vyhledávání prostředků a umožňuje poskytování hodnotu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, přičemž typ <xref:System.Windows.Style>v atributu syntaxe jako v následujícím příkladu:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Zde `StaticResource` identifikuje <xref:System.Windows.StaticResourceExtension> třída poskytuje implementaci rozšíření značek. Další řetězec `MyStyle` se používá jako vstup pro jiné než výchozí <xref:System.Windows.StaticResourceExtension> konstruktoru, kde parametr přijato z řetězce rozšíření deklaruje požadované <xref:System.Windows.ResourceKey>. `MyStyle` je očekáván [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) hodnotu <xref:System.Windows.Style> definována jako prostředek. [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) využití požadavky, že prostředek se použít k zajištění <xref:System.Windows.Style> hodnotu vlastnosti prostřednictvím statických prostředků vyhledávání logiku v okamžiku načtení.  
  
 Další informace o rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md). Referenční rozšíření značek a dalších XAML programování Funkce povolené v obecné .NET XAML implementaci, najdete v části [Namespace XAML (x:) Jazykové funkce](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). WPF konkrétní rozšíření značek, najdete v části [WPF XAML rozšíření](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Přidružené vlastnosti  
 Přidružené vlastnosti jsou programovací koncept zavedená v jazyce XAML, kterým můžete vlastnosti ve vlastnictví a definované konkrétní typ, ale nastavené jako atributy nebo vlastnost elementy u libovolného elementu. Primární scénář, přidružené vlastnosti jsou určené pro je umožnit podřízené elementy ve struktuře značek na sestavu informace na nadřazený element bez nutnosti hojně sdílené objektový model napříč všechny elementy. Naopak přidružené vlastnosti lze nadřazené elementy na sestavu informace pro podřízené elementy. Další informace o účelu přidružené vlastnosti a jak vytvořit vlastní přidružené vlastnosti, najdete v části [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Přidružené vlastnosti použijte syntaxi, která na první pohled se podobá vlastnost element syntaxe, v tom, že zadáte také *typeName*. *propertyName* kombinaci. Existují dva důležité rozdíly:  
  
-   Můžete použít *typeName*. *propertyName* kombinace, i když nastavení přidružená vlastnost prostřednictvím syntaxe atributu. Přidružené vlastnosti jsou že pouze tam, kde kvalifikující název vlastnosti je vyžadováno v syntaxi atributu.  
  
-   Můžete také vlastnost element syntaxe pro přidružené vlastnosti. Pro typické vlastnost syntaxe elementu, ale *typeName* zadáte, je objekt elementu, který obsahuje element vlastnosti. Pokud jsou odkazy na přidružená vlastnost, pak se *typeName* je třída, která definuje přidružená vlastnost není obsahující element object.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Přidružené události  
 Přidružené události jsou jiné programovací koncept zavedená v jazyce XAML, kdy události lze definovat pomocí určitého typu, ale mohou být spojeny obslužné rutiny u libovolného elementu objektu. K implementaci WOF často typ, který definuje přidružená událost je statický typ, který definuje službu a někdy jsou tyto přidružené události vystavené alias směrované události v typy, které službu vystavit. Obslužné rutiny pro přidružené události jsou určeny pomocí syntaxe atributu. Jako s přidružené události je rozšířena syntaxe atributu pro přidružené události umožňující *typeName*. *eventName* využití, kde *typeName* je třída, která poskytuje `Add` a `Remove` přístupových objektů událostí obslužná rutina přidružená událost infrastruktury a *eventName* je název události.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomie kořenový Element XAML  
 Následující tabulka obsahuje typické XAML kořenový element rozdělení, zobrazující konkrétní atributy kořenový element:  
  
|||  
|-|-|  
|`<Page`|Element object otevírání kořenového prvku|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Výchozí hodnota ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) oboru názvů jazyka XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Oboru názvů jazyka XAML jazyka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklarace třídu, která se připojuje k žádné kódu značek definovaný pro třídu|  
|`>`|Koncový element object pro kořenový adresář. Objekt není uzavřený ještě, protože element obsahuje podřízené elementy|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Použití volitelné a Nonrecommended XAML  
 Následující části popisují XAML použití technicky podporované aplikací XAML procesory, ale který vytvořit podrobností nebo jiných estetické problémů, které narušovat soubory XAML zbývající čitelný, když vaše vyvíjet aplikace, které obsahují zdroje XAML .  
  
### <a name="optional-property-element-usages"></a>Použití elementu volitelná vlastnost  
 Použití elementu volitelná vlastnost zahrnují explicitně zápis obsahu vlastností elementů, považuje implicitní procesoru XAML. Například když deklarovat obsah <xref:System.Windows.Controls.Menu>, můžete zadat, aby explicitně deklarovat <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce <xref:System.Windows.Controls.Menu> jako `<Menu.Items>` značky elementu vlastnosti a místo jednotlivých <xref:System.Windows.Controls.MenuItem> v rámci `<Menu.Items>`, místo než pomocí implicitní chování procesoru XAML, všech podřízených elementů <xref:System.Windows.Controls.Menu> musí být <xref:System.Windows.Controls.MenuItem> a jsou umístěny v <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce. Volitelné použití někdy může pomoci vizuálně vysvětlení strukturu objekt reprezentovaný ve značkách. Nebo někdy použití elementu explicitní vlastnosti se můžete vyhnout kód, který je technicky funkční ale vizuálně složitá, jako je například rozšíření vnořené značek v rámci hodnotu atributu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Úplné typeName.memberName kvalifikovaný atributy  
 *TypeName*. *memberName* formuláři pro atribut skutečně funguje všeobecně než právě případ směrované události. Ale v jiných situacích je tato forma nadbytečné a neměli byste ji, pokud pouze z důvodů styl značek a přehlednosti. V následujícím příkladu každý ze tří odkazuje na <xref:System.Windows.Controls.Control.Background%2A> atribut zcela odpovídají:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` funguje, protože kvalifikovaný vyhledávání pro tuto vlastnost na <xref:System.Windows.Controls.Button> úspěšné (<xref:System.Windows.Controls.Control.Background%2A> bylo zděděno z ovládacího prvku) a <xref:System.Windows.Controls.Button> je elementu objektu nebo základní třída. `Control.Background` funguje, protože <xref:System.Windows.Controls.Control> třída ve skutečnosti definuje <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.Controls.Control> je <xref:System.Windows.Controls.Button> základní třídy.  
  
 Ale následující *typeName*. *memberName* příklad formuláře nefunguje a je proto zobrazen komentáři:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> je jiné třídy odvozené z <xref:System.Windows.Controls.Control>, a pokud jste měli zadali `Label.Background` v rámci <xref:System.Windows.Controls.Label> object element by už pracovali toto použití. Ale protože <xref:System.Windows.Controls.Label> není třídu nebo základní třídu <xref:System.Windows.Controls.Button>, zadaného chování procesoru XAML se pak zpracuje `Label.Background` jako přidružená vlastnost. `Label.Background` není k dispozici přidružená vlastnost a toto použití selže.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName vlastností elementů  
 V podobá způsob jak *typeName*. *memberName* formuláře funguje pro atribut syntaxe *baseTypeName*. *memberName* syntaxe funguje pro syntaxi element vlastnosti. Pro instanci lze použít následující syntaxi:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Zde element vlastnosti byla zadána jako `Control.Background` to i v případě, že byl součástí element vlastnosti `Button`.  
  
 Ale stejně jako *typeName*. *memberName* formuláře pro atributy, *baseTypeName*. *memberName* je nízký styl v značek a neměli byste ji.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Jazykové funkce oboru názvů jazyka XAML (x:)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozšíření WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters a XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [XAML a vlastní třídy pro WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
