---
title: Přehled vstupu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: 00a1f25546bb8dd4f8a587c8a5f03f1043632e08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549526"
---
# <a name="input-overview"></a>Přehled vstupu
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Subsystému poskytuje výkonný [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pro získání vstupu z mnoha různých zařízení, včetně myši, klávesnice, touch a pera. Toto téma popisuje služeb poskytovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a vysvětluje architektuře vstupní systémy.  
  
  
<a name="input_api"></a>   
## <a name="input-api"></a>Vstup rozhraní API  
 Primární vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ohrožení nachází na třídy base element: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.FrameworkContentElement>.  Další informace o základní prvky najdete v tématu [základní přehled elementy](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  Tyto třídy poskytují funkce pro vstupní události související s stisknutí klávesy, tlačítka myši, kolečka myši, pohybu myši, fokus správy a zachycení myši, a další. Tím, že vstup [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na základní prvky místo považuje všechny vstupní události jako služba, vstupní architektura umožňuje vstupních událostech se, která byla vytvořena pomocí konkrétního objektu v uživatelském rozhraní a které podporují příslušné události směrování schéma více než jeden element má příležitost zpracovat vstupní události. Mnoho událostí vstupní mít pár události související s nimi.  Například klíč událost vypnutí přidružen <xref:System.Windows.Input.Keyboard.KeyDown> a <xref:System.Windows.Input.Keyboard.PreviewKeyDown> události.  Rozdíl ve tyto události je v tom, jak se směrují do cílového elementu.  Tunelové propojení, události Preview dolů stromu element z kořenového prvku do cílového elementu.  Probublávání události vyvolat z cílového elementu pro kořenový element.  Událost směrování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je podrobněji popsána dále v tomto přehledu a v [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="keyboard-and-mouse-classes"></a>Klávesnice a myši třídy  
 Kromě vstup [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na třídy base element <xref:System.Windows.Input.Keyboard> třídy a <xref:System.Windows.Input.Mouse> třídy poskytují další [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] pro práci s klávesnici a myš vstup.  
  
 Příklady vstupu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Keyboard> třídy jsou <xref:System.Windows.Input.Keyboard.Modifiers%2A> vlastnost, která vrací <xref:System.Windows.Input.ModifierKeys> aktuálně stisknutí a <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metoda, která určuje, zda je zadaný klíč stisknutí.  
  
 Následující příklad používá <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metoda k určení, zda <xref:System.Windows.Input.Key> je ve stavu dolů.  
  
 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]  
  
 Příklady vstupu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Mouse> třídy jsou <xref:System.Windows.Input.Mouse.MiddleButton%2A>, který získá stav tlačítko myši střední a <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, který získá element ukazatel myši nad právě.  
  
 Následující příklad určuje, zda <xref:System.Windows.Input.Mouse.LeftButton%2A> v myší <xref:System.Windows.Input.MouseButtonState.Pressed> stavu.  
  
 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]  
  
 <xref:System.Windows.Input.Mouse> a <xref:System.Windows.Input.Keyboard> třídy jsou popsané v tomto přehledu podrobněji.  
  
### <a name="stylus-input"></a>Vstup pera  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má integrovaná podpora <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Pera vstup, provedené pomocí Oblíbené [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace může považovat za pera myš pomocí myši [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taky zpřístupňuje abstrakce pera zařízení, které používají model podobná klávesnici a myš.  Všechny související s pera [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] obsahovat slovo "Pera".  
  
 Protože pera může fungovat jako myš, aplikace, které podporují pouze vstup z myši můžete stále získat určité úrovně podpory pera automaticky. Když pera slouží takovým způsobem, aplikace je zadána možnost zpracování události odpovídající pera a pak zpracovává odpovídající událost myší. Kromě toho jsou vyšší úrovně služeb, jako je vstup rukopisu také k dispozici prostřednictvím abstrakce pera zařízení.  Další informace o rukopisu jako vstup najdete v tématu [Začínáme s rukopisu](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).  
  
<a name="event_routing"></a>   
## <a name="event-routing"></a>Směrování událostí  
 A <xref:System.Windows.FrameworkElement> může obsahovat další prvky jako podřízené prvky v jeho obsahu modelu, které tvoří je strom z elementů.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], nadřazeného elementu mohl účastnit vstup pokyn k její podřízené elementy nebo jiných následníky od blokováním události. Toto je užitečná zejména při vytváření ovládacích prvků mimo menší ovládacích prvků, tento proces se označuje jako "řízení složení" nebo "skládání." Další informace o elementu stromy a jak element stromy vztahují k události trasy najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 Událost směrování je proces předávání událostí více elementů, aby mohli nabízet významné odpovědí (prostřednictvím zpracování) na událost, která může mít různé elementem Source vybrat určitý objekt nebo elementu na trase.  Směrované události pomocí jednoho z tři směrování mechanismů: přímo, šíření a tunelové propojení.  V přímé směrování, source element je jediným prvkem upozornění a události není směruje na další prvky. Však přímé směrované události stále nabízí některé další možnosti, které jsou k dispozici pro směrované události oproti standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. Šíření funguje nahoru k element tak, že první upozornění elementu, který pak jako zdroj událostí, nadřazeného elementu a tak dále.  Tunelové propojení spustí v kořenu stromu elementu a funguje dolů, s původní element source.  Další informace o směrované události najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní události obvykle mají páry, které se skládá z tunelu událostí a probublávání událostí.  Tunelové události jsou rozlišeny určeny z probublávání událostí s předponou "Náhled".  Například <xref:System.Windows.Input.Mouse.PreviewMouseMove> je tunelové verze událost pohybu myší a <xref:System.Windows.Input.Mouse.MouseMove> je probublávání verze této události. Tato událost párování je konvence prováděné na úrovni elementu a není vyplývajících funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému. Podrobnosti najdete v části události vstup grafického subsystému WPF v [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="handling_input_events"></a>   
## <a name="handling-input-events"></a>Vstupní zpracování událostí  
 Pokud chcete získat vstup na element, musí být přidružen danou událost obslužné rutiny události.  V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Toto je jednoduchá: odkazovat na název události jako atribut elementu, který bude naslouchat pro tuto událost.  Potom nastavte hodnotu atributu název obslužné rutiny události, které definujete, podle delegáta.  Obslužné rutiny události musí být napsaný v kódu, například C# a může být zahrnutý v souboru kódu na pozadí.  
  
 Události klávesnice nastane, když operační systém sestavy klíče akce, ke kterým dojde během fokus klávesnice je v elementu. Události myši a pera každý rozdělit do dvou kategorií: události, které sestavy změny v umístění ukazatele vzhledem k elementu a události, které sestavy změny ve stavu tlačítek zařízení.  
  
### <a name="keyboard-input-event-example"></a>Příklad vstupní události klávesnice  
 Následující příklad naslouchá na stisknutí klávesy šipka doleva.  A <xref:System.Windows.Controls.StackPanel> je vytvořen, který má <xref:System.Windows.Controls.Button>.  Obslužné rutiny události pro naslouchání stisknutí klávesy šipka doleva je připojen k <xref:System.Windows.Controls.Button> instance.  
  
 První část příkladu vytvoří <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> a připojí obslužné rutiny události pro <xref:System.Windows.UIElement.KeyDown>.  
  
 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]  
  
 Druhá část je napsána v kódu a definuje obslužnou rutinu události.  Po stisknutí klávesy šipka doleva a <xref:System.Windows.Controls.Button> má právě fokus klávesnice, spustí obslužnou rutinu a <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změnilo.  Pokud stisknutí klávesy, ale není klávesu šipka vlevo <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změní zpět na jeho počáteční barvu.  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]  
  
### <a name="mouse-input-event-example"></a>Příklad vstupní událostí myši  
 V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změní, když ukazatel myši vstoupí <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Barva se obnoví, když opustí myší <xref:System.Windows.Controls.Button>.  
  
 První část příkladu vytvoří <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> řízení a připojí obslužné rutiny událostí <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> události <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]  
  
 Druhá část v příkladu je napsána v kódu a definuje obslužné rutiny událostí.  Při přesunutí myši zadá <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změní na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Když opustí myší <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změní zpět na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]  
  
<a name="text_input"></a>   
## <a name="text-input"></a>Zadávání textu  
 <xref:System.Windows.ContentElement.TextInput> Událostí umožňuje naslouchat pro zadávání textu způsobem nezávislé na zařízení. Klávesnice je primární způsob rukopisu vstupu, ale rozpoznávání řeči, text a další vstupní zařízení mohou generovat textový vstup také.  
  
 Pro vstup z klávesnice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poprvé odešle odpovídající <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> události. Pokud nejsou zpracovány tyto události a klíč je textový místo (řízení klíč například směrové šipky) nebo funkční klávesy, pak <xref:System.Windows.ContentElement.TextInput> událost se vyvolá.  Není vždy jednoduché mapování 1: 1 mezi <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> a <xref:System.Windows.ContentElement.TextInput> události protože více stisknutí kláves může generovat jednoho znaku zadávání textu a jeden stisknutí kláves může generovat více znaků řetězce.  To platí hlavně pro jazyky, jako je například čínština, japonština nebo korejština, které používají [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] ke generování tisíce možné znaků v jejich odpovídající abeced.  
  
 Když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odešle <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> událostí, <xref:System.Windows.Input.KeyEventArgs.Key%2A> je nastaven na <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> Pokud stisknutí kláves může být součástí <xref:System.Windows.ContentElement.TextInput> události (Pokud ALT + S stisknutí, například). To umožňuje kód <xref:System.Windows.ContentElement.KeyDown> obslužné rutiny události zkontrolujte <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> a, pokud je nalezen, nechte zpracování pro obslužnou rutinu následně vyvolané <xref:System.Windows.ContentElement.TextInput> událostí. V těchto případech různé vlastnosti <xref:System.Windows.Input.TextCompositionEventArgs> argument můžete použít k určení původní stisknutí kláves. Podobně pokud [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] je aktivní, <xref:System.Windows.Input.Key> má hodnotu <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, a <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> dává původní klávesu nebo stisknutí kláves.  
  
 V následujícím příkladu definuje obslužnou rutinu pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události a obslužné rutiny pro <xref:System.Windows.UIElement.KeyDown> událostí.  
  
 První segment kódu nebo značek vytvoří uživatelské rozhraní.  
  
 [!code-xaml[InputOvw#Input_OvwTextInputXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]  
  
 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]  
  
 Druhý segment kódu obsahuje obslužné rutiny událostí.  
  
 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]  
  
 Protože vstupních událostech vyvolat událost na základě trasy, <xref:System.Windows.Controls.StackPanel> obdrží vstup bez ohledu na to, který element má fokus klávesnice. <xref:System.Windows.Controls.TextBox> Řízení nejprve upozornění a `OnTextInputKeyDown` obslužná rutina je volán, pouze pokud <xref:System.Windows.Controls.TextBox> se nepodařilo zpracovat vstup. Pokud <xref:System.Windows.UIElement.PreviewKeyDown> událostí se používá místo <xref:System.Windows.UIElement.KeyDown> událostí, `OnTextInputKeyDown` jako první obslužná rutina.  
  
 V tomto příkladu je zapsán logiku zpracování dvakrát – jednou pro CTRL + O a znovu na tlačítko click – událost. To můžete zjednodušit pomocí příkazů, místo zpracování vstupních událostech přímo.  Příkazy jsou popsané v tomto přehledu a v [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="touch_and_manipulation"></a>   
## <a name="touch-and-manipulation"></a>Dotykové ovládání a manipulace  
 Nový hardware a rozhraní API v operačním systému Windows 7 poskytují aplikace možnost přijímat vstup z více úpravy současně. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje aplikacím zjistit a reagovat na touch způsobem podobná neodpovídá na požadavky jiného vstupu, například myši nebo klávesnice, podle vyvolávání událostí, když dojde k dotykového ovládání.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje dva typy událostí, když dojde k touch: touch události a zpracování události. Události touch poskytují nezpracovaná data o každém prstem na dotykovou obrazovku a jeho přesunu. Zpracování událostí interpretace vstupu jako určité akce. Oba typy událostí, které jsou popsané v této části.  
  
### <a name="prerequisites"></a>Požadavky  
 Je nutné následující součásti vyvíjet aplikace, která reaguje na touch.  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Zařízení, například dotykovou obrazovku, který podporuje Windows Touch.  
  
### <a name="terminology"></a>Terminologie  
 Když je popsána touch, se používají následující termíny.  
  
-   **Touch** je typ vstupu uživatele, který rozpozná Windows 7. Obvykle je touch inicializovat umístěním prsty, které na obrazovce touch-velká a malá písmena. Všimněte si, že zařízení, jako jsou dotykové, které je běžné pro přenosné počítače nepodporují dotykového ovládání, pokud zařízení jenom převede prstem pozice a přesun jako vstup z myši.  
  
-   **Vícedotykové** je dotykového ovládání, ke kterému dochází z více než jeden bod současně. Windows 7 a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje vícedotykové. Vždy, když je touch popsané v dokumentaci k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], koncepty, na které se týkají vícedotykové.  
  
-   A **manipulaci s** nastane, když touch interpretována jako fyzické akce, který se použije pro objekt. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zpracování události interpretace vstupu jako manipulaci s překlad, rozšíření nebo otočení.  
  
-   A `touch device` představuje zařízení, která vytváří touch vstupu, například jeden prstem na dotykovou obrazovku.  
  
### <a name="controls-that-respond-to-touch"></a>Ovládací prvky, které reagují na dotykového ovládání  
 Ovládací prvky posunout tak, že přetáhnete prstem napříč ovládacího prvku, pokud má obsah, který je přesunut mimo zobrazení oblasti.  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.DataGrid>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
 <xref:System.Windows.Controls.ScrollViewer> Definuje <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> přidružená vlastnost, která umožňuje určit, jestli touch je povoleno posouvání ve vodorovném směru, ve svislém směru, oba nebo ani jeden z nich. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Vlastnost určuje, jak rychle posouvání zpomalí, když uživatel zruší prstem z dotykovou obrazovku. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Přidružená vlastnost určuje poměr posouvání posun přeložit posun manipulaci.  
  
### <a name="touch-events"></a>Touch – události  
 Základní třídy, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, a <xref:System.Windows.ContentElement>, definovat události, které můžete odebírat, vaše aplikace bude odpovídat touch. Touch události jsou užitečné, když vaše aplikace interpretuje touch jako něco jiného než manipulace s objekt. Například by se aplikace, která umožňuje uživatelům kreslení prsty jeden nebo více přihlásit k touch události.  
  
 Všechny tři třídy definovat následující události, které se chovají podobně, bez ohledu na to definující třídu.  
  
-   <xref:System.Windows.UIElement.TouchDown>  
  
-   <xref:System.Windows.UIElement.TouchMove>  
  
-   <xref:System.Windows.UIElement.TouchUp>  
  
-   <xref:System.Windows.UIElement.TouchEnter>  
  
-   <xref:System.Windows.UIElement.TouchLeave>  
  
-   <xref:System.Windows.UIElement.PreviewTouchDown>  
  
-   <xref:System.Windows.UIElement.PreviewTouchMove>  
  
-   <xref:System.Windows.UIElement.PreviewTouchUp>  
  
-   <xref:System.Windows.UIElement.GotTouchCapture>  
  
-   <xref:System.Windows.UIElement.LostTouchCapture>  
  
 Podobně jako události klávesnice a myši jsou události touch směrované události. Události, které začínají `Preview` tunel události a události, které začínají `Touch` probublávání události. Další informace o směrované události najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md). Při zpracování těchto událostí můžete získat pozici vstupu, relativně k libovolný element, voláním <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> nebo <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> metoda.  
  
 Zjistit, interakce mezi události dotykového ovládání, představte si situaci, kde uživatel vloží jedním prstem na element, přesune prstu v elementu a pak zruší prstu ze elementu. Následující obrázek znázorňuje spuštění probublávání události (tunelu události, které byly vynechány pro jednoduchost).  
  
 ![Posloupnost událostí dotykového ovládání. ] (../../../../docs/framework/wpf/advanced/media/ndp-touchevents.png "NDP_TouchEvents")  
Touch – události  
  
 Následující seznam popisuje posloupnost událostí na předchozím obrázku.  
  
1.  <xref:System.Windows.UIElement.TouchEnter> Události dojde jednou, když uživatel uloží prstem v elementu.  
  
2.  <xref:System.Windows.UIElement.TouchDown> Události dojde jednou.  
  
3.  <xref:System.Windows.UIElement.TouchMove> Událostí vyskytuje opakovaně, protože uživatel přesune prstu v rámci elementu.  
  
4.  <xref:System.Windows.UIElement.TouchUp> Události dojde jednou, pokud uživatel zruší prstu ze elementu.  
  
5.  <xref:System.Windows.UIElement.TouchLeave> Události dojde jednou.  
  
 Pokud jsou použity více než dva prsty, dochází k události pro každý prstu.  
  
### <a name="manipulation-events"></a>Zpracování událostí  
 Pro případy, kdy aplikace umožňuje uživateli upravit objekt <xref:System.Windows.UIElement> třída definuje zpracování událostí. Na rozdíl od události dotykového ovládání, které jednoduše sestavy pozici dotykového ovládání událostí zpracování sestavy, jak jde interpretovat vstup. Existují tři typy manipulace, překlad, rozšíření a otočení. Následující seznam popisuje, jak má být vyvolán tři typy manipulace.  
  
-   Vložit prstem objektu a přesouvat mezi dotykovou obrazovku k vyvolání manipulaci s překlad prstu. To obvykle přesune objekt.  
  
-   Vložit dvěma prsty objektu a přesunout prsty blíže společně nebo dále kromě navzájem k vyvolání manipulaci s rozšíření. To obvykle změní velikost objektu.  
  
-   Vložit dvěma prsty objektu a otočit prsty kolem druhým k vyvolání manipulaci s otočení. To obvykle otočí objekt.  
  
 Více než jeden typ zpracování může dojít současně.  
  
 Pokud jste způsobit reagovat na manipulaci s objekty, můžete mít objekt pravděpodobně nečinnosti. To můžete provést vašich objektů simulovat fyzické world. Například když push knihy napříč tabulku, pokud nabízené pevný dostatečně adresáře budou nadále přesunout po jeho uvolnění. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje simulovat toto chování zobrazením zpracování událostí po prsty, které uživatele uvolní objekt.  
  
 Informace o tom, jak vytvořit aplikaci, která umožňuje uživatelům přesunout, změnit velikost a otočení objektu najdete v tématu [návod: vytváření vaše první Touch aplikaci](../../../../docs/framework/wpf/advanced/walkthrough-creating-your-first-touch-application.md).  
  
 <xref:System.Windows.UIElement> Definuje následující události manipulaci.  
  
-   <xref:System.Windows.UIElement.ManipulationStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationStarted>  
  
-   <xref:System.Windows.UIElement.ManipulationDelta>  
  
-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationCompleted>  
  
-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>  
  
 Ve výchozím nastavení <xref:System.Windows.UIElement> neobdrží tyto události manipulaci. Pro příjem událostí zpracování na <xref:System.Windows.UIElement>, nastavte <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> k `true`.  
  
#### <a name="the-execution-path-of-manipulation-events"></a>Cesta spuštění zpracování událostí  
 Představte si třeba situaci, kdy uživatel "vyvolá" objekt. Uživatel uloží prstem na objekt, přesune prstu napříč dotykovou obrazovku pro krátkou vzdálenost a pak zruší prstu, když je přesunutí. Důsledkem je, že bude objekt přesunout pod prstem uživatele a nadále přesunout po uživatel zruší prstu.  
  
 Následující obrázek znázorňuje cestu spuštění zpracování události a důležité informace o jednotlivých událostí.  
  
 ![Pořadí zpracování událostí. ] (../../../../docs/framework/wpf/advanced/media/ndp-manipulationevents.png "NDP_ManipulationEvents")  
Zpracování událostí  
  
 Následující seznam popisuje posloupnost událostí na předchozím obrázku.  
  
1.  <xref:System.Windows.UIElement.ManipulationStarting> Události dojde, když uživatel umístí prstem na objekt. Tato událost mimo jiné umožňuje nastavit <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost. V následných událostech pozici manipulaci bude vzhledem k <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. V události s výjimkou <xref:System.Windows.UIElement.ManipulationStarting>, tato vlastnost je jen pro čtení, proto <xref:System.Windows.UIElement.ManipulationStarting> událost je jenom jednou, kterou můžete nastavit tuto vlastnost.  
  
2.  <xref:System.Windows.UIElement.ManipulationStarted> Vedle dojde k události. Tato událost hlásí původ manipulaci.  
  
3.  <xref:System.Windows.UIElement.ManipulationDelta> Událostí vyskytuje opakovaně jako přesunutí prsty, které uživatele na dotykovou obrazovku. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Vlastnost <xref:System.Windows.Input.ManipulationDeltaEventArgs> třída hlásí, zda manipulaci se interpretuje jako přesun, rozšíření nebo překlad. Toto je, kde můžete provést většinu práce manipulace s objekt.  
  
4.  <xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když prsty, které uživatele přerušení spojení se objekt. Tato událost umožňuje určit zpomalení manipulace při nečinnosti. To je proto objektu mohou napodobovat různých fyzických mezery nebo atributy, pokud si zvolíte. Předpokládejme například, že aplikace obsahuje dva objekty, které představují položky na fyzické světě a jedna je větší než druhý. Můžete nastavit objekt větší zpomalení rychleji než světlejší objekt.  
  
5.  <xref:System.Windows.UIElement.ManipulationDelta> Událostí vyskytuje opakovaně, protože dojde k nečinnosti. Všimněte si, že k této události dochází při přesunutí prsty, které uživatele v rámci dotykovou obrazovku a při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simuluje nečinnosti. Jinými slovy <xref:System.Windows.UIElement.ManipulationDelta> dojde před a po <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Vlastnost sestavy jestli <xref:System.Windows.UIElement.ManipulationDelta> dojde k události při nečinnosti, abyste mohli zkontrolovat vlastnosti a provádět různé akce, v závislosti na jeho hodnotu.  
  
6.  <xref:System.Windows.UIElement.ManipulationCompleted> Dojde k události při manipulaci a všechny nečinnost ukončení. To znamená, že po všech <xref:System.Windows.UIElement.ManipulationDelta> dojde k události, <xref:System.Windows.UIElement.ManipulationCompleted> na signalizaci dokončení manipulaci dojde k události.  
  
 <xref:System.Windows.UIElement> Definuje také <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> událostí. K této události dochází při <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> metoda je volána <xref:System.Windows.UIElement.ManipulationDelta> událostí. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Událostí umožňuje aplikace nebo součásti, které slouží k poskytnutí zpětné vazby visual, pokud se objekt dotkne hranici. Například <xref:System.Windows.Window> třídu obslužné rutiny <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> událost způsobí okno mírně přejít, když dojde k jeho hrany.  
  
 Můžete zrušit manipulaci voláním <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metodu argumenty událostí v každém případě manipulaci s výjimkou <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> událostí. Při volání <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, události manipulaci už jsou vyvolány a myš k událostem pro dotykového ovládání. Následující tabulka popisuje vztah mezi době, kdy je zrušená manipulaci a události myši, ke kterým dochází.  
  
|Událost, která se nazývá zrušit v|Události myši, které nastaly pro vstup, který již došlo k chybě|  
|----------------------------------------|-----------------------------------------------------------------|  
|<xref:System.Windows.UIElement.ManipulationStarting> A <xref:System.Windows.UIElement.ManipulationStarted>|Myš dolů události.|  
|<xref:System.Windows.UIElement.ManipulationDelta>|Události myši přesunutí a pohybu myší dolů.|  
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> A <xref:System.Windows.UIElement.ManipulationCompleted>|Pohybu myší dolů, přesuňte myš a pohybu myší nahoru události.|  
  
 Všimněte si, že při volání <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> při manipulaci se nachází v nečinnosti, vrátí metoda `false` a vstup nevyvolá událostí myši.  
  
### <a name="the-relationship-between-touch-and-manipulation-events"></a>Vztah mezi Touch a zpracování událostí  
 A <xref:System.Windows.UIElement> může vždy přijímat události dotykového ovládání. Když <xref:System.Windows.UIElement.IsManipulationEnabled%2A> je nastavena na `true`, <xref:System.Windows.UIElement> může přijímat touch a zpracování události.  Pokud <xref:System.Windows.UIElement.TouchDown> událost není zpracována (to znamená, <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost je `false`), logiku zpracování zaznamená touch do elementu a generuje zpracování události. Pokud <xref:System.Windows.RoutedEventArgs.Handled%2A> je nastavena na `true` v <xref:System.Windows.UIElement.TouchDown> událostí, zpracování logiky negeneruje zpracování událostí. Následující obrázek znázorňuje vztah mezi touch události a zpracování události.  
  
 ![Vztah mezi touch a zpracování události](../../../../docs/framework/wpf/advanced/media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")  
Dotykové ovládání a zpracování událostí  
  
 Následující seznam popisuje vztah mezi touch a zpracování události, které je vidět na předchozím obrázku.  
  
-   Vygeneruje-li první zařízení touch <xref:System.Windows.UIElement.TouchDown> událostí na <xref:System.Windows.UIElement>, volání logiku zpracování <xref:System.Windows.UIElement.CaptureTouch%2A> metodu, která generuje <xref:System.Windows.UIElement.GotTouchCapture> událostí.  
  
-   Při <xref:System.Windows.UIElement.GotTouchCapture> dojde, volání logiku zpracování <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> metodu, která generuje <xref:System.Windows.UIElement.ManipulationStarting> událostí.  
  
-   Při <xref:System.Windows.UIElement.TouchMove> k událostem, vygeneruje zpracování logiky <xref:System.Windows.UIElement.ManipulationDelta> události, které nastaly před <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí.  
  
-   Při poslední touch zařízení element vyvolá <xref:System.Windows.UIElement.TouchUp> generuje logiku zpracování událostí, <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí.  
  
<a name="focus"></a>   
## <a name="focus"></a>Fokus  
 Existují dvě hlavní koncepty, které se týkají fokusu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: fokus a logické fokus klávesnice.  
  
### <a name="keyboard-focus"></a>Fokus klávesnice  
 Fokus klávesnice odkazuje na element, který přijímá vstup z klávesnice.  Může existovat pouze jeden element celkově plochy, který má právě fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bude mít elementu, který má právě fokus klávesnice <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastavena na `true`.  Statické <xref:System.Windows.Input.Keyboard> metoda <xref:System.Windows.Input.Keyboard.FocusedElement%2A> vrátí elementu, který má právě fokus klávesnice.  
  
 Pomocí klávesy tabulátor do elementu nebo klepněte na tlačítko myši na některé prvky, jako například lze získat fokus klávesnice <xref:System.Windows.Controls.TextBox>.  Fokus klávesnice jsou k dispozici prostřednictvím kódu programu pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A> pokusí se poskytnout fokus klávesnice zadaný element.  Vrácený element <xref:System.Windows.Input.Keyboard.Focus%2A> je elementu, který má právě fokus klávesnice.  
  
 Aby se element získat fokus klávesnice <xref:System.Windows.UIElement.Focusable%2A> vlastnost a <xref:System.Windows.UIElement.IsVisible%2A> vlastnosti musí být nastavena na **true**.  Některé třídy, jako například <xref:System.Windows.Controls.Panel>, mají <xref:System.Windows.UIElement.Focusable%2A> nastavena na `false` ve výchozím nastavení; proto možná budete muset nastavit tuto vlastnost na `true` Pokud chcete být schopni získat fokus daný element.  
  
 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> nastavit fokus klávesnice na <xref:System.Windows.Controls.Button>.  Nastavit počáteční fokusu v aplikaci je doporučené místo <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Další informace o fokus klávesnice najdete v tématu [fokus přehled](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
### <a name="logical-focus"></a>Logické fokusu  
 Logické fokus odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokus.  Může být více elementů, které mají logické fokusu v aplikaci, ale může existovat pouze jeden element, který má právě fokus logické v konkrétní výběr oboru.  
  
 Fokus obor je kontejnerový element, který sleduje <xref:System.Windows.Input.FocusManager.FocusedElement%2A> ve svém oboru.  Při deaktivaci obor fokus, cílených elementu dojde ke ztrátě fokus klávesnice, ale zachová logické fokus.  Když se fokus vrátí do oboru fokus, bude cílených element získat fokus klávesnice.  To umožňuje fokus klávesnice změnit mezi více obory fokus, ale zajistí, že cílených element v rámci oboru fokus zůstane cílených element když se fokus vrátí.  
  
 Element mohou být změněny na obor fokusu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením <xref:System.Windows.Input.FocusManager> přidružená vlastnost <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> k `true`, nebo v kódu pomocí nastavení přidružená vlastnost pomocí <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> metoda.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.StackPanel> do oboru fokus nastavením <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> přidružená vlastnost.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 Třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] který jsou obory fokus ve výchozím nastavení jsou <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, a <xref:System.Windows.Controls.ContextMenu>.  
  
 Element, který má právě fokus klávesnice, bude mít i logické fokus pro fokus oboru, který patří do; Proto nastavení fokusu na element s <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídu nebo třídy base element se pokusí o poskytnou element fokus klávesnice a logické fokus.  
  
 K určení cílených element v oboru fokus, použijte <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Můžete změnit cílených element pro obor fokus <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.  
  
 Další informace o logické fokus najdete v tématu [fokus přehled](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
<a name="mouse_position"></a>   
## <a name="mouse-position"></a>Pozice myši  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] poskytuje užitečné informace s ohledem na souřadnic prostory.  Například koordinaci `(0,0)` souřadnice levého horního, ale levém které elementy ve stromové struktuře? Element, který je cílem vstupní? Element připojit vaše obslužná rutina události? Nebo něco jiného? Aby nedocházelo k záměně, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] je potřeba zadat vaše rámec při práci s souřadnice získaných pomocí myši. <xref:System.Windows.Input.Mouse.GetPosition%2A> Metoda vrátí souřadnice ukazatele myši relativně k daného elementu.  
  
<a name="mouse_capture"></a>   
## <a name="mouse-capture"></a>Zachycení myši  
 Zařízení myši konkrétně nastaveno modální vlastnosti označuje jako zachycení myši. Zachycení myši slouží k udržování přechodném stavu vstupní při spuštění operace přetahování myší, tak, aby ostatní operací zahrnujících nominální na obrazovce umístění ukazatele myši nedojde k nutně. Při přetažení nelze kliknout uživatele bez přerušení a přetáhněte proto většinu upozornění myš nad nevhodných při zachycení myši drží přetáhněte počátek. Zpřístupní vstupní systému [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , můžete určit myši zaznamenat stav, a také [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] můžete vynutit zachycení myši na konkrétní element, nebo zrušte myši zaznamenat stav. Další informace o operací přetažení myší najdete v tématu [přetažení a vyřadit přehled](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md).  
  
<a name="commands"></a>   
## <a name="commands"></a>Příkazy  
 Příkazy Povolit vstupní zpracování více sémantického úrovni, než zařízení vstup.  Příkazy, jako jsou jednoduché direktivy `Cut`, `Copy`, `Paste`, nebo `Open`.  Příkazy jsou užitečné pro centrální správu logika příkaz.  Stejný příkaz může k němu přistupovat z <xref:System.Windows.Controls.Menu>na <xref:System.Windows.Controls.ToolBar>, nebo pomocí klávesové zkratky. Příkazy také poskytují mechanismus pro zakázat ovládacích prvků, když příkaz nedostupný.  
  
 <xref:System.Windows.Input.RoutedCommand> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace <xref:System.Windows.Input.ICommand>.  Když <xref:System.Windows.Input.RoutedCommand> proveden, <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> událost se vyvolá při cíl příkazu, který tunelové propojení a bublin prostřednictvím stromu element jako jiného vstupu.  Pokud příkaz cíl není nastavena, bude prvek s fokus klávesnice cíl příkazu.  Logiky, která k provedení příkazu je připojen k <xref:System.Windows.Input.CommandBinding>.  Při <xref:System.Windows.Input.CommandManager.Executed> dosáhne událostí <xref:System.Windows.Input.CommandBinding> pro tuto konkrétní příkaz <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding> je volána.  Tato rutina provede akci příkazu.  
  
 Další informace o tvorba příkazů najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které se skládá z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, a <xref:System.Windows.Documents.EditingCommands>, nebo můžete definovat vlastní.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, že když po kliknutí na bude vyvolán <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz na <xref:System.Windows.Controls.TextBox>, v případě <xref:System.Windows.Controls.TextBox> má fokus klávesnice.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
 Další informace o příkazech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="the_input_system_and_base_elements"></a>   
## <a name="the-input-system-and-base-elements"></a>Vstupní systému a základní prvky  
 Vstupní události, jako je například přidružené události definované <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, a <xref:System.Windows.Input.Stylus> třídy jsou vyvolané vstupní systémem a vložit do konkrétní pozici v modelu objektu podle vstupů do testování vizuálním stromu za běhu.  
  
 Všechny události, <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, a <xref:System.Windows.Input.Stylus> definovat, jak je přidružená událost je také znovu vystavené třídy base element <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> jako nový směrované události. Element base směrované události se generují třídy zpracování původní přidružená událost a opakovaného použití data události.  
  
 Pokud vstupní událost se sváže s konkrétní zdrojový prvek prostřednictvím implementace jeho base element vstupní událost, lze ho směrovat pomocí zbytek trasu událost, která je založena na kombinaci logické a vizuální stromu objektů a zpracovávat kód aplikace.  Obecně je pohodlnější ke zpracování těchto zařízení související vstupní událostí pomocí směrované události na <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>, protože můžete použít intuitivnější událostí syntaxe obslužné rutiny i v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a v kódu. Můžete zadat, aby zpracování připojené události, který spustil proces místo, ale by čelí několik výhrad: přidružená událost mohou být označeny zpracováván zpracování třídy base element a budete muset použít přístupových metod, nikoliv syntaxi true událostí v pořadí pro připojení obslužné rutiny pro přidružené události.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Co je další  
 Nyní máte několik postupů pro zpracování vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Také byste měli mít lepší představu o různé typy vstupních událostech a mechanismů směrované události používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Další prostředky jsou k dispozici, vysvětlují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework elementy a událostí směrování podrobněji. Najdete další informace najdete v následujících přehledech [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md), [fokus přehled](../../../../docs/framework/wpf/advanced/focus-overview.md), [základní prvky přehled](../../../../docs/framework/wpf/advanced/base-elements-overview.md), [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md), a [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled fokusu](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Přehled základních elementů](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Vlastnosti](../../../../docs/framework/wpf/advanced/properties-wpf.md)
