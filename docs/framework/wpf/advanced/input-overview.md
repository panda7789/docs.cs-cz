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
ms.openlocfilehash: 9553a66538297db9c2fa134e018f35ab9e2ddf37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001529"
---
# <a name="input-overview"></a>Přehled vstupu
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Subsystému poskytuje výkonný [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] získávání vstupu z nejrůznějších zařízení, včetně myši, klávesnice, dotykové ovládání a stylus. Toto téma popisuje služby poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a vysvětlení architektury vstupní systémy.

<a name="input_api"></a>
## <a name="input-api"></a>Vstupní rozhraní API
 Primární vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] expozice se nachází na základní element třídy: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.FrameworkContentElement>.  Další informace o základní prvky, naleznete v tématu [přehled základních elementů](base-elements-overview.md).  Tyto třídy nakonfigurovánu vstupní události související s stisknutí kláves, tlačítka myši, kolečka myši, pohybu myši, fokus správy a zachycení myši, pár. Tak, že vstup [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na základní prvky, místo považuje všechny vstupní události jako služba, vstupní architektura umožňuje použít jako zdroj podle určitého objektu v uživatelském rozhraní a pro podporu schématu směrování událostí, kterým vstupní události více než jeden element má příležitost pro zpracování vstupních událostí. Mnoho vstupní události mají dvojice událostí spojených s nimi.  Například je přidružený klíč událost vypnutí <xref:System.Windows.Input.Keyboard.KeyDown> a <xref:System.Windows.Input.Keyboard.PreviewKeyDown> události.  Rozdíl v těchto událostí je v tom, jak se směrují do cílového elementu.  Tunelové propojení událostí ve verzi Preview dolů stromem prvků z kořenový element do cílového elementu.  Šíření událostí vyvolat z cílového elementu do kořenového elementu.  Směrování událostí ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je podrobněji dále v tomto přehledu a v [směrovat Přehled událostí](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Klávesnice a myši třídy
 Kromě vstupu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] u tříd base element <xref:System.Windows.Input.Keyboard> třídy a <xref:System.Windows.Input.Mouse> třídy poskytují další [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] pro práci s klávesnicí a myší vstup.

 Příklady vstupu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Keyboard> třídy jsou <xref:System.Windows.Input.Keyboard.Modifiers%2A> vlastnost, která vrací <xref:System.Windows.Input.ModifierKeys> aktuálně stisknutí a <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metoda, která určuje, zda je zadaný klíč se stiskne.

 Následující příklad používá <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metodu k určení, zda <xref:System.Windows.Input.Key> je ve stavu dolů.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Příklady vstupu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] na <xref:System.Windows.Input.Mouse> třídy jsou <xref:System.Windows.Input.Mouse.MiddleButton%2A>, která získá stav prostřední tlačítko myši, a <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, který získá prvek ukazatel myši nad je aktuálně.

 Následující příklad určuje, zda <xref:System.Windows.Input.Mouse.LeftButton%2A> myši probíhá <xref:System.Windows.Input.MouseButtonState.Pressed> stavu.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 <xref:System.Windows.Input.Mouse> a <xref:System.Windows.Input.Keyboard> třídy jsou podrobně popsané v další uvedených v tomto přehledu.

### <a name="stylus-input"></a>Vstup pomocí pera
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je integrovaná podpora <xref:System.Windows.Input.Stylus>.  <xref:System.Windows.Input.Stylus> Pera vstup provedené pomocí oblíbených [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace lze považovat za stylus myši pomocí myši [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje abstrakce zařízení stylus, která používají model podobný klávesnici a myš.  Všechny související stylus [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] obsahovat slovo "Stylus".

 Vzhledem k tomu stylus může fungovat jako myš, aplikace, které podporují pouze vstup z myši může stále získat určitou úroveň podpory stylus automaticky. Pokud se stylus slouží takovým způsobem, aplikace je příležitost pro zpracování události odpovídající stylus a poté zpracuje odpovídající událost myši. Kromě toho jsou vyšší úrovně služeb, jako je vstupu inkoustu také k dispozici prostřednictvím abstrakce stylus zařízení.  Další informace o inkoustu jako vstup, naleznete v tématu [Začínáme s rukopisem](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Směrování událostí
 A <xref:System.Windows.FrameworkElement> může obsahovat další prvky jako podřízené prvky v jeho obsahu modelu, které tvoří stromové struktuře prvků.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], nadřazeného elementu mohl podílet na vstup směrované do jeho podřízených prvků nebo jiných následníky ve zpracování událostí. To je obzvláště užitečná při vytváření ovládacích prvků z menších ovládací prvky, tento proces se označuje jako "kompozice ovládacích prvků" nebo "skládání." Další informace o elementu stromy a vztah element stromů trasy události najdete v tématu [stromy v subsystému WPF](trees-in-wpf.md).

 Směrování událostí je proces předávání událostí do více prvků, aby mohli nabízet výrazné odpověď na událost, která může mít jiný element Source (prostřednictvím zpracování) vybrat určitý objekt nebo element na trase.  Směrované události použijte jednu z tři mechanismy směrování: přímé, šíření a tunelové propojení.  V přímé směrování, source element je jediným prvkem upozornění a události se nesměruje na další prvky. Však s přímým přístupem směrované události stále nabízí některé další možnosti, které jsou k dispozici pro směrovaných událostí na rozdíl od standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. Šíření funguje nahoru stromem prvků tak, že první upozornění elementu, který zdroj události, pak nadřazeného elementu a tak dále.  Tunelové propojení začíná v kořenovém adresáři strom prvku a funguje dolů, s původní element source.  Další informace o směrované události najdete v tématu [směrovat Přehled událostí](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní události obvykle dodáváno v párech, které se skládá z tunelového propojení událost a šíření událostí.  Šíření událostí s předponou "Preview" rozlišit tunelového propojení události.  Například <xref:System.Windows.Input.Mouse.PreviewMouseMove> je verze tunelového propojení událost pohybu myší a <xref:System.Windows.Input.Mouse.MouseMove> šíření verze této události. Tato událost párování je konvence, která se implementuje na úrovni elementu a není přináší schopnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí. Podrobnosti najdete v tématu v části WPF vstupní události [směrovat Přehled událostí](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Zpracování vstupních událostí
 Pro vstup na element, musí být obslužná rutina události spojené s danou událost.  V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Toto je jednoduchý: referenční název události jako atribut prvku, který bude naslouchat pro tuto událost.  Potom nastavte hodnotu atributu název obslužné rutiny události, který určíte, založené na delegáta.  Obslužná rutina události musí být napsaný v kódu, jako je C# a mohou být zahrnuty v souboru kódu na pozadí.

 Události klávesnice dojít, když operační systém sestavy klíčových akcí, ke kterým dochází při fokusu klávesnice na elementu. Události myši a stylus každý spadají do dvou kategorií: událostí, které sestavu se změnami polohy ukazatele vzhledem k elementu a události, které sestavu se změnami stavu zařízení tlačítka.

### <a name="keyboard-input-event-example"></a>Příklad událost vstupu klávesnice
 Následující příklad naslouchá stisknutí klávesy Šipka dolů.  A <xref:System.Windows.Controls.StackPanel> je vytvořen, který má <xref:System.Windows.Controls.Button>.  Obslužná rutina události pro naslouchání stisknutí klávesy šipka doleva je připojen k <xref:System.Windows.Controls.Button> instance.

 První část tento příklad vytvoří <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> a připojí obslužnou rutinu události pro <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 Druhá část je napsána v kódu a definuje obslužnou rutinu události.  Se stiskla klávesa Šipka vlevo a <xref:System.Windows.Controls.Button> má fokus klávesnice, spustí obslužnou rutinu a <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.Controls.Button> se změnilo.  Pokud se stiskne klávesu, ale není klávesu šipka dolů <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.Controls.Button> se změní zpět na svůj počáteční barvu.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Příklad událost vstupu myší
 V následujícím příkladu <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.Controls.Button> se změní, pokud kurzor myši vstoupí <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.Control.Background%2A> Barva se obnoví, když ukazatel myši opustí <xref:System.Windows.Controls.Button>.

 První část tento příklad vytvoří <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> řídit a připojí obslužné rutiny událostí pro <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> události <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Druhá část v příkladu je napsána v kódu a definuje obslužné rutiny událostí.  Pokud ukazatel myši vstoupí <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.Controls.Button> se změní na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Když ukazatel myši opustí <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.Controls.Button> se změní zpět na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Zadávání textu
 <xref:System.Windows.ContentElement.TextInput> Událostí umožňuje naslouchat vstupní text způsobem nezávislým na zařízení. Klávesnice je hlavním prostředkem rukopisného textu vstupu, ale řeči, a ostatní vstupní zařízení můžete vygenerovat textový vstup také.

 Vstup z klávesnice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poprvé odešle odpovídající <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> události. Pokud nejsou zpracovány tyto události a klíčem je textový místo (ovládací prvek klíč jako je směrové šipky) nebo funkční klávesy, o <xref:System.Windows.ContentElement.TextInput> událost se vyvolá.  Není vždy jednoduché mapování 1: 1 mezi <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> a <xref:System.Windows.ContentElement.TextInput> události protože více stisknutí kláves můžete generovat jeden znak z textové zadání a jeden stisknutí kláves můžete generovat více znak řetězce.  To platí zejména pro jazyků, které používají, jako je čínštiny, japonštiny a korejštiny [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] generovat tisíce možných znaků v jejich odpovídající písmena abecedy.

 Při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odešle <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> události, <xref:System.Windows.Input.KeyEventArgs.Key%2A> je nastavena na <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> Pokud stisknutí kláves stát součástí <xref:System.Windows.ContentElement.TextInput> události (Pokud ALT + S například stisknutí). To umožňuje kód v <xref:System.Windows.ContentElement.KeyDown> obslužná rutina události ke kontrole <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> a, pokud je nalezen, ponechte zpracování pro obslužnou rutinu následně vyvolanou <xref:System.Windows.ContentElement.TextInput> událostí. V těchto případech se různé vlastnosti objektu <xref:System.Windows.Input.TextCompositionEventArgs> argument můžete použít k určení původní stisknutí kláves. Podobně pokud [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] je aktivní, <xref:System.Windows.Input.Key> má hodnotu <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, a <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> poskytuje původní stisk klávesy nebo stisknutí kláves.

 Následující příklad definuje obslužnou rutinu pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události a obslužné rutiny pro <xref:System.Windows.UIElement.KeyDown> událostí.

 První segment kódu nebo značky vytvoří uživatelské rozhraní.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Druhý segment kódu obsahuje obslužné rutiny událostí.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Vzhledem k tomu, že vstupní události vyvolat trasa událostí <xref:System.Windows.Controls.StackPanel> přijímá vstup bez ohledu na to, který prvek má fokus klávesnice. <xref:System.Windows.Controls.TextBox> Ovládací prvek nejprve obdrží oznámení a `OnTextInputKeyDown` je obslužná rutina volána pouze v případě, <xref:System.Windows.Controls.TextBox> nedošlo ke zpracování vstupu. Pokud <xref:System.Windows.UIElement.PreviewKeyDown> události se použije namísto <xref:System.Windows.UIElement.KeyDown> událostí, `OnTextInputKeyDown` obslužná rutina se nazývá nejprve.

 V tomto příkladu logika zpracování vytvořená dvakrát – jednou pro CTRL + O a znovu pro tlačítka. Kliknutím na událost. To se dá zjednodušit pomocí příkazů, namísto zpracování vstupních událostí přímo.  Příkazy jsou popsané v tomto přehledu a [přehled příkazů](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dotykové ovládání a manipulaci s
 Nový hardware a rozhraní API v operačním systému Windows 7 poskytují aplikace možnost přijímat vstup z více dotyků současně. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje aplikacím detekovat a reagovat na dotykové ovládání v podobně, jak reagovat na jiného vstupu, například myš či klávesnice, vyvoláním události, když dojde k dotykové ovládání.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje dva typy událostí, když dojde k dotykové ovládání: touch události a manipulace s událostmi. Události touch poskytují nezpracovaná data o každé prstem na k tomu dotykovou obrazovku a její pohyb. Manipulace s událostmi interpretace vstupu jako určité akce. Oba typy událostí, které jsou popsány v této části.

### <a name="prerequisites"></a>Požadavky
 Budete potřebovat následující komponenty pro vývoj aplikací, který reaguje na dotyk.

- Visual Studio 2010.

- Windows 7.

- Zařízení, např. k tomu dotykovou obrazovku, který podporuje Windows Touch.

### <a name="terminology"></a>Terminologie
 Pokud tady nezvládneme probrat touch se používají následující termíny.

- **Touch** je typ vstupu uživatele, který je rozpoznán Windows 7. Obvykle je zahájeno touch vložením prsty na dotykovou obrazovku. Všimněte si, že zařízení, jako jsou touchpadu, která je společná pro přenosné počítače nepodporují dotykového ovládání, pokud se zařízení převede pouze umístění a přesun jako vstup z myši prstem.

- **Vícedotykové** je dotykového ovládání, ke které dochází z více než jeden bod současně. Windows 7 a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje vícedotykové. Vždy, když touch je podrobněji popsána v dokumentaci k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], koncepty platí pro platformu.

- A **manipulaci s** nastane, pokud dotykovou interpretována jako fyzické akci, která je použita na objekt. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], manipulace s událostmi interpretace vstupu jako manipulaci s překladem, rozšíření nebo otočení.

- A `touch device` představuje zařízení, která vytváří dotykové ovládání, jako je jednotné prstem na k tomu dotykovou obrazovku.

### <a name="controls-that-respond-to-touch"></a>Ovládací prvky, které reagují na dotykové ovládání
 Následující ovládací prvky můžete posouvat přetažením prstem přes ovládací prvek, pokud má obsah, který je posunu mimo zobrazení.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 <xref:System.Windows.Controls.ScrollViewer> Definuje <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> přidružená vlastnost, která umožňuje určit, jestli touch je povoleno posouvání vodorovně, svisle, obou nebo ani jeden. <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Vlastnost určuje, jak rychle posouvání zpomalí, když uživatel zruší prstem z dotykovou obrazovku. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Připojená vlastnost určuje poměr posouvání posun pro převod manipulaci s posun.

### <a name="touch-events"></a>Události dotyku
 Základní třídy <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, a <xref:System.Windows.ContentElement>, definovat události, které se k odběru tak vaše aplikace bude reagovat na dotykového ovládání. Dotykové ovládání události jsou užitečné, pokud vaše aplikace interpretuje dotykové ovládání jako něco jiného než objekt manipulace s. Aplikace, která umožňuje uživateli pro kreslení prsty na jeden nebo více by předplatit události dotyku.

 Všechny tři třídy definují následující události, které se chovají podobně, bez ohledu na to definující třídy.

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 Události dotykové ovládání jako události klávesnice a myši, jsou směrované události. Události, které začínají `Preview` jsou tunelování události a události, které začínají `Touch` jsou šíření událostí. Další informace o směrované události najdete v tématu [směrovat Přehled událostí](routed-events-overview.md). Při zpracování těchto událostí můžete získat pozice vstupu, vzhledem k libovolný prvek voláním <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> nebo <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> metody.

 Informace o tom interakce mezi události dotykového ovládání, vezměte v úvahu scénář, kde uživatel umístí jedním prstem na element, přesune prstu v elementu a pak zruší prstem z elementu. Následující obrázek znázorňuje provedení šíření událostí (pro zjednodušení jsou vynechány tunelového propojení událostí).

 ![Posloupnost událostí dotykové ovládání. ](./media/ndp-touchevents.png "NDP_TouchEvents") události dotyku

 Následující seznam popisuje posloupnost událostí v předchozí ilustraci.

1. <xref:System.Windows.UIElement.TouchEnter> Události dojde jednou, když uživatel přepne prstem na elementu.

2. <xref:System.Windows.UIElement.TouchDown> Jednou dojde k události.

3. <xref:System.Windows.UIElement.TouchMove> Dojde k události více než jednou, jak uživatel přesouvá prstu v rámci elementu.

4. <xref:System.Windows.UIElement.TouchUp> Události dojde jednou, když uživatel zruší prstem z elementu.

5. <xref:System.Windows.UIElement.TouchLeave> Jednou dojde k události.

 Pokud jsou používány více než dvěma prsty, dochází k události pro každý prstem.

### <a name="manipulation-events"></a>Manipulace s událostmi
 Pro případy, kdy aplikace umožňuje uživateli manipulovat s objektu <xref:System.Windows.UIElement> třída definuje manipulace s událostmi. Na rozdíl od touch události, které se ohlásí pozice dotykového ovládání manipulace s událostmi zprávu, jak se dá interpretovat vstupu. Existují tři typy manipulace, překlad, rozšíření a otočení. Následující seznam popisuje tři typy manipulace vyvolat.

- Vložit prstem na objekt a sdílením dotykovou obrazovku k vyvolání manipulaci s překladem prstu. To obvykle přesune objekt.

- Umístit dvěma prsty na objekt a přesunout prsty blíže společně nebo jsou kromě navzájem k vyvolání manipulaci s rozšíření. To obvykle změní velikost objektu.

- Vložit dvěma prsty na objekt a otočit prsty kolem vzájemně k vyvolání manipulaci s otočení. To obvykle otočí objektu.

 Manipulace s více než jeden typ může probíhají souběžně.

 Až způsobíte reagovat na manipulaci s objekty, budete mít objekt pravděpodobně nečinnost. Díky tomu se objekty simulovat fyzického světa. Například při vkládání knize napříč tabulku, pak možné nabídnout pevné dostatečně adresáře bude dál přecházejí po jeho uvolnění. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje simulovat toto chování vyvolání manipulace s událostí po uživatele prsty uvolní objekt.

 Informace o tom, jak vytvořit aplikaci, která umožňuje uživateli přesunutí, změna velikosti a otočení objektu najdete v tématu [názorný postup: Vytvoření vaší první aplikace Touch](walkthrough-creating-your-first-touch-application.md).

 <xref:System.Windows.UIElement> Definuje následující manipulace s událostmi.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Ve výchozím nastavení <xref:System.Windows.UIElement> neobdrží tyto manipulace s událostmi. Pro příjem manipulace s událostmi <xref:System.Windows.UIElement>, nastavte <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> k `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Cesta provedení manipulace s událostí
 Představte si třeba situaci, kdy uživatel "vyvolá" objekt. Uživatel umístí prstem na objekt, přesune prstu přes dotykovou obrazovku na krátké vzdálenosti a pak zruší prstu, zatímco se přesouvá. Výsledek tohoto je, že objekt bude přesouvat pod prstem uživatele a dál přecházejí po uživatel zruší prstu.

 Následující obrázek znázorňuje cesta provedení manipulace s událostmi a důležité informace o každé události.

 ![Pořadí zpracování událostí. ](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") manipulace s událostmi

 Následující seznam popisuje posloupnost událostí v předchozí ilustraci.

1. <xref:System.Windows.UIElement.ManipulationStarting> Události dojde, když uživatel umístí prstem na objekt. Tato událost mimo jiné umožňuje nastavit <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost. V následných událostech pozice manipulace bude relativně k <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. V události jiných než <xref:System.Windows.UIElement.ManipulationStarting>, tato vlastnost je jen pro čtení, proto <xref:System.Windows.UIElement.ManipulationStarting> událost je jenom čas, který tuto vlastnost lze nastavit.

2. <xref:System.Windows.UIElement.ManipulationStarted> Dále dojde k události. Tato událost hlásí původu manipulaci.

3. <xref:System.Windows.UIElement.ManipulationDelta> Více než jednou jako přesunutí uživatele prsty na dotykové obrazovce dojde k události. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Vlastnost <xref:System.Windows.Input.ManipulationDeltaEventArgs> třídy hlásí, zda manipulace je interpretován jako přesun, rozšíření nebo překlad. To je, kde provádět většinu práce manipulace s objektu.

4. <xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když uživatele prsty ztratí kontaktu s objektem. Tato událost vám umožňuje určit zpomalení manipulace při nečinnosti. Jedná se proto objektu může emulovat různých fyzických mezery nebo atributy, pokud se rozhodnete. Předpokládejme například, že vaše aplikace má dva objekty, které představují položky ve skutečnosti a jeden je těžší než ten druhý. Můžete vytvořit objekt těžší zpomalení rychleji než světlejší objektu.

5. <xref:System.Windows.UIElement.ManipulationDelta> Jako nečinnost dojde k výskytu události více než jednou. Všimněte si, že k této události dojde při prsty uživatele přesouvat v rámci dotykovou obrazovku a při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simuluje nečinnost. Jinými slovy <xref:System.Windows.UIElement.ManipulationDelta> dojde před a po <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> Vlastnosti sestavy, zda <xref:System.Windows.UIElement.ManipulationDelta> dojde k události při nečinnosti, vám umožní zkontrolovat vlastnosti a provádět různé akce, v závislosti na jeho hodnotu.

6. <xref:System.Windows.UIElement.ManipulationCompleted> Výskytu události po ukončení manipulaci a jakékoli nečinnost. To znamená, že po všech <xref:System.Windows.UIElement.ManipulationDelta> dojde k událostem, <xref:System.Windows.UIElement.ManipulationCompleted> dojde k události na signál, manipulaci s je dokončena.

 <xref:System.Windows.UIElement> Také definuje <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> událostí. Této události dojde, když <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> metoda je volána <xref:System.Windows.UIElement.ManipulationDelta> událostí. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Událostí umožňuje aplikace nebo součásti poskytují vizuální zpětnou vazbu, pokud objekt narazí na hranici. Například <xref:System.Windows.Window> třídy obslužné rutiny <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> události a způsobit, že v okně mírně přesunout, pokud dojde k jeho okraj.

 Manipulace s můžete zrušit po zavolání <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metodu na argumenty události v každém případě manipulace s výjimkou <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> událostí. Při volání <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, už jsou vyvolány manipulace s událostmi a události myši se generují pro dotykové ovládání. Následující tabulka popisuje vztah mezi čas, kdy se zruší manipulaci a události myši, ke kterým dochází.

|Událost, která se nazývá zrušit v|Události myši, ke kterým dochází pro vstup, který již došlo k chybě|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> a <xref:System.Windows.UIElement.ManipulationStarted>|Myš dolů události.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Pohybu myší dolů a události pohybu myši.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> a <xref:System.Windows.UIElement.ManipulationCompleted>|Pohybu myší dolů, přesuňte myš a pohybu myší nahoru události.|

 Všimněte si, že pokud zavoláte <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> při manipulaci s je v nečinnosti, metoda vrátí `false` a vstup nevyvolává události myši.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Vztah mezi dotykového ovládání a manipulace s událostmi
 A <xref:System.Windows.UIElement> vždy může přijímat události dotykové ovládání. Když <xref:System.Windows.UIElement.IsManipulationEnabled%2A> je nastavena na `true`, <xref:System.Windows.UIElement> může přijímat dotykového ovládání a manipulace s událostí.  Pokud <xref:System.Windows.UIElement.TouchDown> nezpracovává události (to znamená <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost je `false`), logika zpracování touch na prvek zachytí a vygeneruje manipulace s událostmi. Pokud <xref:System.Windows.RoutedEventArgs.Handled%2A> je nastavena na `true` v <xref:System.Windows.UIElement.TouchDown> událostí, zpracování logiky negeneruje manipulace s událostmi. Následující ilustrace znázorňuje vztah mezi dotyků a manipulace s událostmi.

 ![Vztah mezi dotykového ovládání a manipulace s událostmi](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") dotykového ovládání a manipulace s událostí

 Následující seznam popisuje vztah mezi dotykového ovládání a manipulace s událostí, které je znázorněno na předchozím obrázku.

- Při první dotykové ovládání zařízení generuje <xref:System.Windows.UIElement.TouchDown> událostí na <xref:System.Windows.UIElement>, volání logiku zpracování <xref:System.Windows.UIElement.CaptureTouch%2A> metodu, která generuje <xref:System.Windows.UIElement.GotTouchCapture> událostí.

- Když <xref:System.Windows.UIElement.GotTouchCapture> dojde k volání logiku zpracování <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> metodu, která generuje <xref:System.Windows.UIElement.ManipulationStarting> událostí.

- Když <xref:System.Windows.UIElement.TouchMove> dojde k událostem, generuje logiku zpracování <xref:System.Windows.UIElement.ManipulationDelta> události, ke kterým dochází před <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí.

- Po poslední touch zařízení element vyvolá <xref:System.Windows.UIElement.TouchUp> generuje logiku zpracování událostí, <xref:System.Windows.UIElement.ManipulationInertiaStarting> událostí.

<a name="focus"></a>
## <a name="focus"></a>fokus
 Existují dva hlavní koncepty, které se týkají fokus v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: klávesnice fokus a logický fokus.

### <a name="keyboard-focus"></a>Fokus klávesnice
 Fokus klávesnice odkazuje na element, který přijímá vstup z klávesnice.  Může existovat na celém klasické pracovní plochy pouze jeden element, který má fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bude mít element, který má fokus klávesnice <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastavena na `true`.  Statické <xref:System.Windows.Input.Keyboard> metoda <xref:System.Windows.Input.Keyboard.FocusedElement%2A> vrátí prvek, který má právě fokus klávesnice.

 Fokus klávesnice můžete získat, procházení tabulátorem element nebo kliknutím myši na některé prvky <xref:System.Windows.Controls.TextBox>.  Fokus klávesnice je také možné získat prostřednictvím kódu programu pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A> pokusy o fokus klávesnice specifikovaný element.  Element vrácen podle <xref:System.Windows.Input.Keyboard.Focus%2A> je prvek, který má právě fokus klávesnice.

 Aby se element, který má získat fokus klávesnice <xref:System.Windows.UIElement.Focusable%2A> vlastnost a <xref:System.Windows.UIElement.IsVisible%2A> vlastnosti musí být nastaveno na **true**.  Některé třídy, jako například <xref:System.Windows.Controls.Panel>, mají <xref:System.Windows.UIElement.Focusable%2A> nastavena na `false` ve výchozím nastavení; proto bude pravděpodobně nutné tuto vlastnost nastavte na `true` Pokud chcete tento element být schopni získat fokus.

 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> nastavit fokus klávesnice pro <xref:System.Windows.Controls.Button>.  Nastavit počáteční fokus v aplikaci je doporučené místo <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Další informace o fokus klávesnice, naleznete v tématu [detailní přehled](focus-overview.md).

### <a name="logical-focus"></a>Logický fokus
 Logický fokus odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokus.  Může existovat více prvků, které mají logický fokus v aplikaci, ale může existovat pouze jeden element, který má logický fokus v konkrétní výběr oboru.

 Obor fokus je prvek kontejneru, který uchovává informace o <xref:System.Windows.Input.FocusManager.FocusedElement%2A> ve svém oboru.  Při deaktivaci obor fokus, element s fokusem ztratí fokus klávesnice, ale zachová logický fokus.  Když se fokus vrátí do oboru fokus, element s fokusem získá fokus klávesnice.  To umožňuje fokus klávesnice změnit mezi více obory fokus, ale díky, cílených element v rámci oboru fokus zůstane element s fokusem, když se fokus vrátí.

 Elementu je možné zapnout do oboru fokus v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením <xref:System.Windows.Input.FocusManager> přidružená vlastnost <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> k `true`, nebo v kódu tak, že nastavíte vlastnost připojené pomocí <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> metody.

 Následující příklad provede <xref:System.Windows.Controls.StackPanel> do oboru fokus nastavíte <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> přidružená vlastnost.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou obory fokus ve výchozím nastavení jsou <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, a <xref:System.Windows.Controls.ContextMenu>.

 Element, který má právě fokus klávesnice, budou také mít logický fokus pro obor fokus, do které patří. Proto nastavení fokusu na element s <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídu nebo třídy base element se pokusí získá fokus klávesnice elementu a logický fokus.

 Zjistíte element s fokusem v oboru fokus <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Chcete-li změnit element s fokusem pro obor fokus, použijte <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Další informace o logický fokus, naleznete v tématu [detailní přehled](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Pozice myši
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] obsahuje užitečné informace z hlediska souřadnicových prostorech.  Například koordinaci `(0,0)` souřadnice levého horního, ale levou horní které element ve stromové struktuře? Prvek, který je cílem vstupní? Prvek, který jste připojili vaše obslužná rutina události? Nebo něco jiného? Aby nedocházelo k záměně, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] vyžaduje zadání vašeho referenčním rámcem při práci s souřadnice získaných myši. <xref:System.Windows.Input.Mouse.GetPosition%2A> Metoda vrátí souřadnic ukazatele myši relativně vzhledem k zadanému prvku.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Zachycení myši
 Zařízení myši výslovně uložení modální charakteristiku označované jako zachycení myši. Zachycení myši slouží k udržování přechodný stav vstupní při zahájení operace přetažení myší, aby další operace, které zahrnují o nominálních na obrazovce pozice ukazatele myši nedojde nutně. Při přetažení nemůže uživatel kliknout bez přerušení přetažení myší, díky nevhodný většina mouseover pomůcky, dokud je držen zachycení myši přetáhněte původním umístění. Poskytuje vstupní systém [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , které můžete určit stav zachycení myši, stejně jako [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , která vynutí zachycení myši konkrétní elementu nebo vymazat stav zachycení myši. Další informace o operací přetažení myší, naleznete v tématu [vyřadit přehled a přetáhněte](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Příkazy
 Příkazy povolí vstupní zpracování více sémantických úrovni, než vstupní zařízení.  Příkazy jsou jednoduché direktivy, jako je například `Cut`, `Copy`, `Paste`, nebo `Open`.  Příkazy jsou užitečné pro centrální správu logiky příkazu.  Ten samý příkaz by mohly být přístupné z <xref:System.Windows.Controls.Menu>na <xref:System.Windows.Controls.ToolBar>, nebo pomocí klávesové zkratky. Příkazy taky mělo poskytovat mechanismus pro zakázání ovládacích prvků při příkazu stane nedostupným.

 <xref:System.Windows.Input.RoutedCommand> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění <xref:System.Windows.Input.ICommand>.  Když <xref:System.Windows.Input.RoutedCommand> provádí, <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> na daném cíli příkazu, které tunelové propojení a bubliny prostřednictvím stromem prvků, jako jsou ostatní vstupy jsou vyvolány události.  Pokud cíl příkazu není nastavena, bude prvek s fokus klávesnice cíli příkazu.  Logika, která provede příkaz je připojen k <xref:System.Windows.Input.CommandBinding>.  Při <xref:System.Windows.Input.CommandManager.Executed> dosáhne událostí <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding> je volána.  Tato obslužná rutina provede akci příkazu.

 Další informace o příkazů najdete v tématu [přehled příkazů](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které se skládá z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, a <xref:System.Windows.Documents.EditingCommands>, nebo můžete definovat vlastní.

 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, aby po kliknutí se vyvolá <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz <xref:System.Windows.Controls.TextBox>, předpokládá <xref:System.Windows.Controls.TextBox> má fokus klávesnice.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Další informace o příkazech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [přehled příkazů](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Vstupní systém a základní elementy
 Vstupní události, například připojené události definované <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, a <xref:System.Windows.Input.Stylus> třídy jsou vyvolané vstupní systémem a vloží na konkrétní pozici v objektu model založený na přístupů k testování vizuální strom za běhu.

 Všechny události, která <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, a <xref:System.Windows.Input.Stylus> definovat jako připojených událostí je také znovu vystavené třídy základní element <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> jako nové směrované události. Element base směrovat události se generují z tříd zpracování původní připojené události a opětovné použití data události.

 Jakmile je vstupní události spojené s konkrétní zdrojového elementu prostřednictvím implementace její základní prvek vstupní události, jde ho směrovat pomocí zbytek trasy události, která je založena na kombinaci logické a vizuální strom objektů a zpracovat kód aplikace.  Obecně je vhodnější pro zpracování těchto zařízení: vstupní události použití směrovaných událostí na <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>, protože používáte intuitivnější události syntaxe obslužné rutiny i v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a v kódu. Můžete se rozhodnout zpracování připojené události, která iniciovala proces místo toho, ale bude mít několik potíže s: přidružená událost může být označena zpracováván zpracování element základní třídy a je třeba použít přístupové metody spíše než syntaxe true událost v pořadí připojení obslužných rutin pro připojené události.

<a name="whats_next"></a>
## <a name="whats-next"></a>Co se chystá
 Teď máte několik postupů pro zpracování vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Také byste měli mít lepší pochopení různých typů vstupních událostí a směrovaných událostí mechanismů používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Jsou k dispozici další prostředky, které popisují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky rozhraní framework a směrování událostí podrobněji. Následující přehledy pro další informace najdete v tématu [přehled příkazů](commanding-overview.md), [detailní přehled](focus-overview.md), [základní prvky přehled](base-elements-overview.md), [stromy v subsystému WPF](trees-in-wpf.md), a [směrovat Přehled událostí](routed-events-overview.md).

## <a name="see-also"></a>Viz také:

- [Přehled fokusu](focus-overview.md)
- [Přehled příkazů](commanding-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti](properties-wpf.md)
