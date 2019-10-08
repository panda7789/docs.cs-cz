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
ms.openlocfilehash: a90c74542c1a6604ed27d37f882385b67402dd92
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005028"
---
# <a name="input-overview"></a>Přehled vstupu
<a name="introduction"></a>Podsystém [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje výkonné rozhraní API pro získání vstupu z nejrůznějších zařízení, včetně myši, klávesnice, dotyku a stylusu. Toto téma popisuje služby, které poskytuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a vysvětluje architekturu vstupních systémů.

<a name="input_api"></a>
## <a name="input-api"></a>Vstupní rozhraní API
 V základních třídách elementů se nachází primární vstupní rozhraní API: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement> a <xref:System.Windows.FrameworkContentElement>.  Další informace o základních elementech naleznete v tématu [Přehled základních prvků](base-elements-overview.md).  Tyto třídy poskytují funkce pro vstupní události, které souvisí s klíčovými klávesami, tlačítky myši, kolečkem myši, pohybem myši, správou fokusu a zachytáváním myši, pokud chcete pojmenovat několik. Vložením vstupního rozhraní API na základní prvky namísto zpracování všech vstupních událostí jako služby umožní vstupní architektura, aby se vstupní události nastavily konkrétním objektem v uživatelském rozhraní, a aby podporovaly schéma směrování událostí, kde je více než jeden prvek OPP. ortunity zpracování události vstupu. K mnoha vstupním událostem je přidružen pár událostí.  Například událost s klíčem dolů je přidružená k událostem <xref:System.Windows.Input.Keyboard.KeyDown> a <xref:System.Windows.Input.Keyboard.PreviewKeyDown>.  Rozdíl v těchto událostech je ve způsobu, jakým jsou směrovány do cílového prvku.  Události ve verzi Preview propojující strom elementů od kořenového elementu až po cílový element.  Probublávání události z cílového prvku do kořenového elementu.  Směrování událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je podrobněji popsáno dále v tomto přehledu a v tématu [Přehled směrovaných událostí](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Třídy klávesnice a myši
 Kromě vstupního rozhraní API na základních třídách prvků třídy <xref:System.Windows.Input.Keyboard> a třídy <xref:System.Windows.Input.Mouse> poskytují další rozhraní API pro práci s vstupy klávesnice a myši.

 Příklady vstupního rozhraní API pro třídu <xref:System.Windows.Input.Keyboard> jsou vlastností <xref:System.Windows.Input.Keyboard.Modifiers%2A>, která vrací aktuálně stisknutou <xref:System.Windows.Input.ModifierKeys> a metodu <xref:System.Windows.Input.Keyboard.IsKeyDown%2A>, která určuje, zda je zadaný klíč stisknut.

 Následující příklad používá metodu <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> k určení, zda je <xref:System.Windows.Input.Key> v nefunkčním stavu.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Příklady vstupního rozhraní API pro třídu <xref:System.Windows.Input.Mouse> jsou <xref:System.Windows.Input.Mouse.MiddleButton%2A>, které získávají stav pravého tlačítka myši, a <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, který získá prvek ukazatel myši v tuto chvíli.

 Následující příklad určuje, zda je <xref:System.Windows.Input.Mouse.LeftButton%2A> na myší ve stavu <xref:System.Windows.Input.MouseButtonState.Pressed>.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 Třídy <xref:System.Windows.Input.Mouse> a <xref:System.Windows.Input.Keyboard> jsou podrobněji popsány v tomto přehledu.

### <a name="stylus-input"></a>Vstup stylusu
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má integrovanou podporu pro <xref:System.Windows.Input.Stylus>.  @No__t-0 je vstup perem, který je oblíbený tabletovým počítačem.  aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohou pomocí rozhraní Mouse API považovat Stylus za myš, ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také zpřístupňuje abstrakci zařízení stylusem, která používá model podobný klávesnici a myši.  Všechna rozhraní API související s stylusem obsahují slovo Stylus.

 Vzhledem k tomu, že Stylus může fungovat jako myš, aplikace, které podporují jenom vstupy myši, můžou dál získávat automaticky určitou úroveň podpory stylusem. Pokud je Stylus použit takovým způsobem, aplikace je dána příležitostí ke zpracování příslušné události stylus a poté zpracuje příslušnou událost myši. Kromě toho jsou k dispozici také služby vyšší úrovně, jako je například vstup z inkoustu, a to prostřednictvím abstrakce zařízení stylus.  Další informace o rukopisu jako vstup naleznete v tématu [Začínáme with Ink](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Směrování událostí
 @No__t-0 může obsahovat další prvky jako podřízené elementy ve svém modelu obsahu, který tvoří strom elementů.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se nadřazený prvek může účastnit vstupu směrovaného na jeho podřízené prvky nebo jiné následníky prostřednictvím předání událostí. To je užitečné hlavně při sestavování ovládacích prvků z menších ovládacích prvků, což je proces známý jako "složení ovládacího prvku" nebo "skládání". Další informace o stromech elementů a o tom, jak struktury prvků souvisejí s trasami událostí, naleznete v tématu [stromy v WPF](trees-in-wpf.md).

 Směrování událostí je proces předávání událostí více prvkům, aby určitý objekt nebo prvek podél trasy mohl nabízet významnou odpověď (prostřednictvím zpracování) k události, která by mohla být zadávána jiným prvkem.  Směrované události používají jeden ze tří mechanismů směrování: přímé, probublávání a tunelové propojení.  V přímém směrování je zdrojový prvek jediným oznámeným prvkem a událost není směrována na žádné jiné prvky. Nicméně přímá směrovaná událost stále nabízí některé další možnosti, které jsou k dispozici pouze pro směrované události na rozdíl od standardních událostí CLR. Probublávání sestaví strom elementů pomocí prvního upozorňování elementu, který zdroj události nastavil, pak nadřazeného elementu a tak dále.  Tunelové propojení začíná v kořenovém adresáři stromu prvků a funguje dolů a končí původním zdrojovým elementem.  Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).

 vstupní události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obecně přicházejí do párů, které se skládají z tunelové události a události probublávání.  Události tunelování se odlišují od probublávání událostí s předponou Preview.  Například <xref:System.Windows.Input.Mouse.PreviewMouseMove> je tunelovou verzí události přesunutí myši a <xref:System.Windows.Input.Mouse.MouseMove> je probublávání verze této události. Toto párování událostí je konvence, která je implementována na úrovni prvku a není podstatou funkcí systému událostí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Podrobnosti najdete v oddílu události vstupu WPF v tématu [směrované události – přehled](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Zpracování událostí vstupu
 Pro příjem vstupu elementu musí být obslužná rutina události přidružena k této konkrétní události.  V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je to jednoduché: odkazujete na název události jako atribut prvku, který bude pro tuto událost naslouchat.  Potom nastavíte hodnotu atributu na název obslužné rutiny události, kterou definujete, na základě delegáta.  Obslužná rutina události musí být napsána v C# kódu, například a může být obsažena v souboru kódu na pozadí.

 K událostem klávesnice dojde v případě, že operační systém hlásí klíčové akce, ke kterým dojde, když je fokus klávesnice na prvku. Události myši a tužky spadají do dvou kategorií: události, které oznamují změny v pozici ukazatele vzhledem k elementu, a události, které oznamují změny ve stavu tlačítek zařízení.

### <a name="keyboard-input-event-example"></a>Příklad události vstupu z klávesnice
 Následující příklad naslouchá stisknutí klávesy šipka vlevo.  Vytvoří se <xref:System.Windows.Controls.StackPanel> s <xref:System.Windows.Controls.Button>.  Obslužná rutina události k naslouchání stisknutí klávesy šipka vlevo je připojena k instanci <xref:System.Windows.Controls.Button>.

 První část příkladu vytvoří <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> a připojí obslužnou rutinu události pro <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 Druhá část je zapsána v kódu a definuje obslužnou rutinu události.  Když se stiskne klávesová šipka vlevo a <xref:System.Windows.Controls.Button> má fokus klávesnice, spustí se obslužná rutina a změní se barva <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>.  Pokud se klávesa stiskne, ale není to klávesa šipka vlevo, barva <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní zpět na počáteční barvu.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Příklad události vstupu myši
 V následujícím příkladu se barva <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> změní, když ukazatel myši vstoupí do <xref:System.Windows.Controls.Button>.  Barva <xref:System.Windows.Controls.Control.Background%2A> se obnoví, když myš opustí <xref:System.Windows.Controls.Button>.

 První část příkladu vytvoří ovládací prvek <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Button> a připojí obslužné rutiny událostí pro události <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> do <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Druhá část příkladu je zapsána v kódu a definuje obslužné rutiny událostí.  Když ukazatel myši vstoupí do <xref:System.Windows.Controls.Button>, barva <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Když ukazatel myši opustí <xref:System.Windows.Controls.Button>, barva <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní zpět na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Zadávání textu
 Událost <xref:System.Windows.ContentElement.TextInput> umožňuje naslouchat textovému zadání způsobem nezávislým na zařízení. Klávesnice je primárním prostředkem textového vstupu, ale řeč, rukopis a jiná vstupní zařízení mohou také vygenerovat textový vstup.

 Pro vstup z klávesnice [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nejprve odešle příslušné události <xref:System.Windows.ContentElement.KeyDown> @ no__t-2 @ no__t-3. Nejsou-li tyto události zpracovány a klíč je text (spíše než řídicí klíč, například směrové šipky nebo funkční klávesy), je vyvolána událost <xref:System.Windows.ContentElement.TextInput>.  Mezi událostmi typu <xref:System.Windows.ContentElement.KeyDown> @ no__t-1 @ no__t-2 a <xref:System.Windows.ContentElement.TextInput> není vždy jednoduché mapování 1:1, protože více klávesových úhozů může generovat jeden znak textového vstupu a jednoduchých klávesových úhozů, které mohou generovat řetězce více znaků.  To platí zejména pro jazyky, jako jsou čínština, japonština a korejština, které používají editory IME (Input Method editory) k vygenerování tisíců možných znaků v odpovídajících abecedách.

 Když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pošle událost <xref:System.Windows.ContentElement.KeyUp> @ no__t-2 @ no__t-3, <xref:System.Windows.Input.KeyEventArgs.Key%2A> je nastavená na <xref:System.Windows.Input.Key.System?displayProperty=nameWithType>, pokud by se stisknutí klávesy staly součástí události <xref:System.Windows.ContentElement.TextInput> (například stisknutím ALT + S). To umožňuje kódu v obslužné rutině události <xref:System.Windows.ContentElement.KeyDown> kontrolu <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> a pokud se najde, ponechá zpracování obslužné rutiny následně vyvolané události <xref:System.Windows.ContentElement.TextInput>. V těchto případech lze pomocí různých vlastností argumentu <xref:System.Windows.Input.TextCompositionEventArgs> určit původní stisknutí kláves. Podobně pokud je editor IME aktivní, <xref:System.Windows.Input.Key> má hodnotu <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType> a <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> poskytuje původní klávesovou zkratku nebo stisknutí kláves.

 Následující příklad definuje obslužnou rutinu pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> a obslužnou rutinu události <xref:System.Windows.UIElement.KeyDown>.

 První segment kódu nebo značek vytvoří uživatelské rozhraní.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Druhý segment kódu obsahuje obslužné rutiny událostí.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Vzhledem k tomu, že vstupní události doplní trasu události, <xref:System.Windows.Controls.StackPanel> přijme vstup bez ohledu na to, který prvek má fokus klávesnice. Nejprve se oznámí ovládací prvek <xref:System.Windows.Controls.TextBox> a obslužná rutina `OnTextInputKeyDown` je volána pouze v případě, že <xref:System.Windows.Controls.TextBox> nezpracovává vstup. Je-li namísto události <xref:System.Windows.UIElement.KeyDown> použita událost <xref:System.Windows.UIElement.PreviewKeyDown>, je nejprve volána obslužná rutina `OnTextInputKeyDown`.

 V tomto příkladu je logika zpracování zapsána dvakrát – jednou pro klávesovou zkratku CTRL + O a znovu pro událost Click tlačítka. To se dá zjednodušit pomocí příkazů namísto přímého zpracování událostí vstupu.  Příkazy jsou popsány v tomto přehledu a v tématu [Přehled příkazů](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dotykové ovládání a manipulace
 Nový hardware a rozhraní API v operačním systému Windows 7 poskytují aplikacím možnost přijímat vstupy z několika dotyků současně. @no__t – 0 umožňuje aplikacím rozpoznávat a reagovat na dotykové ovládání podobným způsobem jako reakce na jiné vstupy, jako je myš nebo klávesnice, a to tak, že se při dotyku dostanou události.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpřístupňuje dva typy událostí, když dojde k dotyku: události dotyku a události manipulace. Události dotykového ovládání poskytují hrubá data o jednotlivých prstech na dotykové obrazovce a jejich přesun. Události manipulace interpretují vstup jako určité akce. V této části jsou popsány oba typy událostí.

### <a name="prerequisites"></a>Požadavky
 Pro vývoj aplikací, které reagují na dotykové ovládání, potřebujete tyto komponenty.

- Visual Studio 2010.

- Systém Windows 7.

- Zařízení, jako je dotyková obrazovka, která podporuje dotykové ovládání systému Windows.

### <a name="terminology"></a>Terminologie
 Následující výrazy se použijí, když je prodiskutován dotyk.

- **Dotykové ovládání** je typ uživatelského vstupu, který je rozpoznáván systémem Windows 7. Dotyková obrazovka se většinou zahajuje tím, že se na dotykové obrazovce přidává prsty. Všimněte si, že zařízení, jako je například touchpad, který je běžný pro přenosné počítače, nepodporují dotykové ovládání, pokud zařízení jednoduše převede polohu a pohyb prstu jako vstup myši.

- **Multitouch** je dotykové ovládání, ke kterému dochází z více než jednoho bodu současně. Windows 7 a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje multitouch. Pokaždé, když je v dokumentaci k dis[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], koncepty platí pro multitouch.

- K **manipulaci** dojde, když je dotykové ovládání interpretováno jako fyzická akce, která je použita na objekt. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události manipulace interpretují vstup jako převod, rozšíření nebo manipulaci s rotací.

- @No__t-0 představuje zařízení, které vytváří dotykové vstupy, jako je například jediný prst na dotykové obrazovce.

### <a name="controls-that-respond-to-touch"></a>Ovládací prvky, které reagují na dotykové ovládání
 Následující ovládací prvky lze procházet přetáhnutím prstem přes ovládací prvek, pokud má obsah, který se posouvá mimo zobrazení.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 @No__t-0 definuje vlastnost s vlastností <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType>, která umožňuje určit, zda je povoleno posouvání dotykového ovládání horizontálně, vertikálně, obojího nebo ani jednou. Vlastnost <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> určuje, jak rychle se posune zpomalení, když uživatel z dotykové obrazovky zaznamená prst. @No__t-0 připojená vlastnost určuje poměr posunutí posunu k posunu manipulace.

### <a name="touch-events"></a>Události dotykové ovládání
 Základní třídy, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D> a <xref:System.Windows.ContentElement>, definují události, které se můžou přihlásit k odběru, takže vaše aplikace bude reagovat na dotykové ovládání. Události dotykové ovládání jsou užitečné v případě, že vaše aplikace interpretuje dotykové ovládání s jinou výjimkou manipulace s objektem. Například aplikace, která umožňuje uživateli kreslit jedním nebo více prsty, by mohla přihlašovat se k odběru událostí dotykové ovládání.

 Všechny tři třídy definují následující události, které se chovají podobně bez ohledu na definiční třídu.

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

 Podobně jako události klávesnice a myši jsou události dotykového ovládání směrovány událostmi. Události, které začínají na `Preview`, jsou tunelové události a události začínající `Touch` jsou probublávání události. Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md). Při zpracování těchto událostí lze získat pozici vstupu relativní k libovolnému prvku voláním metody <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> nebo <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A>.

 Pro pochopení interakce mezi událostmi dotykového ovládání Zvažte situaci, kdy uživatel vloží jeden prst na prvek, přesune prst v prvku a poté vytvoří prst z prvku. Následující ilustrace znázorňuje provádění probubláváních událostí (události tunelování jsou vynechány pro zjednodušení).

 ![Posloupnost událostí dotykového ovládání.](./media/ndp-touchevents.png "NDP_TouchEvents") Události dotykové ovládání

 Následující seznam popisuje pořadí událostí na předchozí ilustraci.

1. Událost <xref:System.Windows.UIElement.TouchEnter> probíhá jednou, když uživatel umístí prst na prvek.

2. Událost <xref:System.Windows.UIElement.TouchDown> nastane jednou.

3. Událost <xref:System.Windows.UIElement.TouchMove> probíhá několikrát, protože uživatel přesouvá prst v rámci elementu.

4. Událost <xref:System.Windows.UIElement.TouchUp> nastane jednou, když uživatel zavýtahí prst z prvku.

5. Událost <xref:System.Windows.UIElement.TouchLeave> nastane jednou.

 Při použití více než dvou prsty dojde k událostem u každého prstu.

### <a name="manipulation-events"></a>Události manipulace
 V případech, kdy aplikace umožňuje uživateli manipulovat s objektem, třída <xref:System.Windows.UIElement> definuje události manipulace. Na rozdíl od událostí dotyku, které jednoduše hlásí pozici dotyku, se události manipulace vydávají, jak lze interpretovat. Existují tři typy manipulace, překladu, rozšiřování a rotace. Následující seznam popisuje, jak vyvolat tři typy manipulace.

- Umístěte prst na objekt a pohybujte prstem přes dotykovou obrazovku, aby se vyvolala manipulace s překladem. Tím se obvykle přesune objekt.

- K vyvolání rozšíření můžete použít dva prsty na objekt a přesunout prsty blíže k sobě nebo více než další. Tím se obvykle změní velikost objektu.

- Přidejte dva prsty na objekt a otáčejte prsty kolem sebe, aby se vyvolala manipulace s rotací. Tím se obvykle otáčí objekt.

 Současně může probíhat více než jeden typ manipulace.

 Když způsobíte, že objekty budou reagovat na manipulace, je možné, že se objekt jeví jako nájezdový. Díky tomu mohou vaše objekty simulovat fyzický svět. Když například vložíte knihu do tabulky, pokud budete mít dostatek volného místa, bude kniha po jejím vydání nadále přesunuta. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje simulovat toto chování tím, že vyvolává události manipulace po tom, co uživatel uvolňuje objekt.

 Informace o tom, jak vytvořit aplikaci, která umožňuje uživateli přesunout, změnit velikost a otočit objekt, najdete v tématu [Návod: Vytvoření první aplikace dotykového ovládání](walkthrough-creating-your-first-touch-application.md).

 @No__t-0 definuje následující události manipulace.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Ve výchozím nastavení <xref:System.Windows.UIElement> tyto události manipulace nepřijímá. Pokud chcete přijímat události manipulace na @no__t 0, nastavte <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> na `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>Cesta spuštění pro události manipulace
 Vezměte v úvahu scénář, kdy uživatel vyvolá objekt. Uživatel vloží prst na objekt, přesune prst na dotykovou obrazovku po krátkou vzdálenost a pak při přesunu zavolá prst. Výsledkem je to, že se objekt přesune v rámci prstu uživatele a nadále se přesune, jakmile uživatel dostane prst.

 Následující ilustrace znázorňuje cestu spuštění pro události manipulace a důležité informace o každé události.

 ![Sekvence událostí manipulace.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Události manipulace

 Následující seznam popisuje pořadí událostí na předchozí ilustraci.

1. K události <xref:System.Windows.UIElement.ManipulationStarting> dojde, když uživatel umístí prst na objekt. Tato událost umožňuje mimo jiné nastavit vlastnost <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. V následných událostech bude poloha manipulace relativní vzhledem k <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. V jiných událostech než <xref:System.Windows.UIElement.ManipulationStarting> je tato vlastnost jen pro čtení, takže událost <xref:System.Windows.UIElement.ManipulationStarting> je jediná doba, kterou můžete nastavit v této vlastnosti.

2. V dalším kroku dojde k události <xref:System.Windows.UIElement.ManipulationStarted>. Tato událost oznamuje původ manipulace.

3. Událost <xref:System.Windows.UIElement.ManipulationDelta> probíhá několikrát, protože prsty uživatele se pohybují na dotykové obrazovce. Vlastnost <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> třídy <xref:System.Windows.Input.ManipulationDeltaEventArgs> hlásí, zda je manipulace interpretována jako pohyb, rozšíření nebo překlad. To je místo, kde provádíte většinu práce při manipulaci s objektem.

4. K události <xref:System.Windows.UIElement.ManipulationInertiaStarting> dojde, když prsty uživatele ztratí kontakt s objektem. Tato událost umožňuje určit zpomalení manipulace během setrvačné hmotnosti. To znamená, že váš objekt může emulovat různé fyzické prostory nebo atributy, pokud zvolíte. Předpokládejme například, že vaše aplikace má dva objekty, které reprezentují položky ve fyzickém světě, a jeden je těžší než druhý. Nejslabším objektem můžete zvýšit zpomalení rychleji než světlejší objekt.

5. Událost <xref:System.Windows.UIElement.ManipulationDelta> dochází vícekrát, protože dojde k nájezdu. Všimněte si, že tato událost nastane, když se prsty uživatele pohybují po dotykové obrazovce a když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simuluje setrvačné hmotnosti. Jinými slovy <xref:System.Windows.UIElement.ManipulationDelta> proběhne před a po události <xref:System.Windows.UIElement.ManipulationInertiaStarting>. Vlastnost <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> hlásí, zda událost <xref:System.Windows.UIElement.ManipulationDelta> probíhá během setrvačné hmotnosti, takže můžete tuto vlastnost kontrolovat a provádět různé akce, a to v závislosti na její hodnotě.

6. K události <xref:System.Windows.UIElement.ManipulationCompleted> dojde při manipulaci a na koncích setrvačné hmotnosti. To znamená, že po výskytu všech událostí <xref:System.Windows.UIElement.ManipulationDelta> dojde k události <xref:System.Windows.UIElement.ManipulationCompleted> k signalizaci, že manipulace byla dokončena.

 @No__t-0 také definuje událost <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>. Tato událost nastane, pokud je v události <xref:System.Windows.UIElement.ManipulationDelta> volána metoda <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A>. Událost <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> umožňuje aplikacím nebo komponentám poskytovat vizuální zpětnou vazbu, když objekt narazí na hranici. Například třída <xref:System.Windows.Window> zpracovává událost <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>, která způsobí, že se okno při zjištění jeho hrany mírně přesune.

 Manipulaci můžete zrušit voláním metody <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> u argumentů události v jakékoli události manipulace s výjimkou události <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>. Když zavoláte <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, události manipulace již nejsou vyvolány a při dotyku dojde k událostem myši. Následující tabulka popisuje vztah mezi časem zrušení manipulace a událostmi myši, ke kterým dojde.

|Událost, která se zruší, se volá v|Události myši, které se vyskytují u vstupu, ke kterému již došlo|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> a <xref:System.Windows.UIElement.ManipulationStarted>|Události myši.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Události myši a přesunutí myši.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> a <xref:System.Windows.UIElement.ManipulationCompleted>|Myš dolů, pohyb myši a události myši nahoru|

 Všimněte si, že pokud zavoláte <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, když je manipulace v nenájezdovém umístění, metoda vrátí `false` a vstup nevyvolává události myši.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Vztah mezi událostmi dotykového a manipulačního události
 @No__t-0 může vždy přijímat události dotykového ovládání. Pokud je vlastnost <xref:System.Windows.UIElement.IsManipulationEnabled%2A> nastavena na hodnotu `true`, může <xref:System.Windows.UIElement> přijímat události dotyku i manipulace.  Pokud událost <xref:System.Windows.UIElement.TouchDown> není zpracována (to znamená, že vlastnost <xref:System.Windows.RoutedEventArgs.Handled%2A> je `false`), logika manipulace zachytí dotyk na prvek a generuje události manipulace. Pokud je vlastnost <xref:System.Windows.RoutedEventArgs.Handled%2A> v události <xref:System.Windows.UIElement.TouchDown> nastavená na hodnotu `true`, logika manipulace negeneruje události manipulace. Následující ilustrace znázorňuje vztah mezi událostmi dotykového ovládání a událostmi manipulace.

 ![Vztah mezi událostmi dotykového a manipulačního](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") události a událostmi manipulace

 Následující seznam popisuje vztah mezi událostmi dotykového ovládání a manipulací, které jsou uvedeny na předchozím obrázku.

- Když první dotykové zařízení vygeneruje událost <xref:System.Windows.UIElement.TouchDown> na <xref:System.Windows.UIElement>, logika manipulace zavolá metodu <xref:System.Windows.UIElement.CaptureTouch%2A>, která generuje událost <xref:System.Windows.UIElement.GotTouchCapture>.

- Pokud dojde k <xref:System.Windows.UIElement.GotTouchCapture>, logika manipulace zavolá metodu <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType>, která generuje událost <xref:System.Windows.UIElement.ManipulationStarting>.

- Když dojde k událostem <xref:System.Windows.UIElement.TouchMove>, logika manipulace generuje události <xref:System.Windows.UIElement.ManipulationDelta>, ke kterým dojde před událostí <xref:System.Windows.UIElement.ManipulationInertiaStarting>.

- Když poslední dotykové zařízení na elementu vyvolá událost <xref:System.Windows.UIElement.TouchUp>, logika manipulace vygeneruje událost <xref:System.Windows.UIElement.ManipulationInertiaStarting>.

<a name="focus"></a>
## <a name="focus"></a>Vybrána
 Existují dva hlavní koncepty, které se týkají fokusu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: fokus klávesnice a logický fokus.

### <a name="keyboard-focus"></a>Fokus klávesnice
 Fokus klávesnice odkazuje na prvek, který přijímá vstup z klávesnice.  Na celém počítači může být pouze jeden element, který má fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude mít element, který má fokus klávesnice, <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastavenou na `true`.  Statická metoda <xref:System.Windows.Input.Keyboard> <xref:System.Windows.Input.Keyboard.FocusedElement%2A> vrátí prvek, který aktuálně má fokus klávesnice.

 Fokus klávesnice lze získat pomocí klávesy Tabulátor pro element nebo kliknutím na tlačítko myši u určitých prvků, například <xref:System.Windows.Controls.TextBox>.  Fokus klávesnice lze také získat programově pomocí metody <xref:System.Windows.Input.Keyboard.Focus%2A> na třídě <xref:System.Windows.Input.Keyboard>.  <xref:System.Windows.Input.Keyboard.Focus%2A> se pokusí zadat fokus na klávesnici zadaného elementu.  Element vrácený <xref:System.Windows.Input.Keyboard.Focus%2A> je prvek, který aktuálně má fokus klávesnice.

 Aby element získal fokus klávesnice, vlastnost <xref:System.Windows.UIElement.Focusable%2A> a vlastnosti <xref:System.Windows.UIElement.IsVisible%2A> musí být nastaveny na **hodnotu true**.  Některé třídy, například <xref:System.Windows.Controls.Panel>, mají ve výchozím nastavení <xref:System.Windows.UIElement.Focusable%2A> nastavenou na `false`. Proto může být nutné nastavit tuto vlastnost na `true`, pokud chcete, aby byl tento prvek schopný získat fokus.

 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> k nastavení fokusu klávesnice na <xref:System.Windows.Controls.Button>.  Doporučeným místem pro nastavení prvotního zaměření v aplikaci je obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded>.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Další informace o fokusu klávesnice najdete v tématu [Přehled fokusu](focus-overview.md).

### <a name="logical-focus"></a>Logický fokus
 Logický fokus odkazuje na <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokusu.  V aplikaci může být více elementů, které mají logický fokus, ale může existovat pouze jeden prvek, který má logický fokus v rámci konkrétního oboru fokusu.

 Rozsah fokusu je prvek kontejneru, který v rámci svého oboru sleduje <xref:System.Windows.Input.FocusManager.FocusedElement%2A>.  Když fokus opustí rozsah fokusu, bude mít fokus na klávesnici fokus, ale zachová se tím logický fokus.  Když se fokus vrátí do oboru fokusu, fokus získá fokus klávesnice.  To umožňuje změnit fokus klávesnice mezi více rozsahy fokusu, ale zajistěte, aby element fokus v rámci oboru fokusu zůstal při návratu fokusu fokusem elementu.

 Element může být převeden do oboru fokusu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením vlastnosti <xref:System.Windows.Input.FocusManager> připojené vlastnosti <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> na `true` nebo v kódu nastavením připojené vlastnosti pomocí metody <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.

 Následující příklad vytvoří <xref:System.Windows.Controls.StackPanel> do oboru fokusu nastavením vlastnosti <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> připojené.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které jsou ve výchozím nastavení obory výběru, jsou <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar> a <xref:System.Windows.Controls.ContextMenu>.

 Element, který má fokus klávesnice, bude mít také logický fokus pro rozsah fokusu, ke kterému patří. Proto nastavení fokusu na element s metodou <xref:System.Windows.Input.Keyboard.Focus%2A> na třídě <xref:System.Windows.Input.Keyboard> nebo třídy základního elementu se pokusí přidělit fokus prvku klávesnice a logickému zaměření.

 K určení prvku s fokusem v oboru fokusu použijte <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Chcete-li změnit element s fokusem pro rozsah výběru, použijte <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Další informace o logickém výběru najdete v tématu [Přehled fokusu](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Pozice myši
 Vstupní rozhraní API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje užitečné informace, pokud jde o souřadnici prostorů.  Například souřadnice `(0,0)` je levá horní souřadnice, ale v levém horním rohu elementu stromu? Prvek, který je vstupním cílem? Prvek, na který jste připojenou obslužnou rutinu události? Nebo něco jiného? Aby nedocházelo k omylům, vyžaduje vstupní rozhraní API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zadání rámce reference při práci s souřadnicemi získanými pomocí myši. Metoda <xref:System.Windows.Input.Mouse.GetPosition%2A> vrátí souřadnici ukazatele myši relativně k zadanému prvku.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Zachycení myši
 Zařízení myši speciálně drží modální charakteristiku, která se označuje jako zachycení myši. K uchování přechodného vstupního stavu, když se spustí operace přetažení, se zachytí myš, aby se nemusely vyskytovat další operace, které se týkají jmenovité pozice ukazatele myši. Během přetahování nemůže uživatel kliknout na bez přerušení přetahování, což způsobí, že většina mouseoverch upozornění není vhodná, zatímco je zachycení myši drženo zdrojem přetažení. Vstupní systém zveřejňuje rozhraní API, která mohou určovat stav zachycení myši, a také rozhraní API, která mohou vynutit zachycení myši na konkrétní prvek nebo Vymazat stav zachycení myši. Další informace o operacích přetažení najdete v tématu [Přehled](drag-and-drop-overview.md)přetažení.

<a name="commands"></a>
## <a name="commands"></a>Příkazy
 Příkazy umožňují zpracování vstupu na sémantické úrovni než vstup zařízení.  Příkazy jsou jednoduché direktivy, například `Cut`, `Copy`, `Paste` nebo `Open`.  Příkazy jsou užitečné pro centralizaci logiky příkazů.  Ke stejnému příkazu může být přihlášený z <xref:System.Windows.Controls.Menu>, v <xref:System.Windows.Controls.ToolBar> nebo prostřednictvím klávesové zkratky. Příkazy také poskytují mechanismus pro vypnutí ovládacích prvků v případě, že příkaz nebude k dispozici.

 <xref:System.Windows.Input.RoutedCommand> je implementace <xref:System.Windows.Input.ICommand> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Když se spustí <xref:System.Windows.Input.RoutedCommand>, v cíli příkazu se vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a událost <xref:System.Windows.Input.CommandManager.Executed>, která vytvoří tunel a bublinový prvek pomocí stromu elementu, jako je jiný vstup.  Pokud není nastaven cíl příkazu, bude element s fokusem klávesnice cílem příkazu.  Logika, která provede příkaz, je připojena k <xref:System.Windows.Input.CommandBinding>.  Když událost <xref:System.Windows.Input.CommandManager.Executed> dosáhne <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz, zavolá se <xref:System.Windows.Input.ExecutedRoutedEventHandler> na <xref:System.Windows.Input.CommandBinding>.  Tato obslužná rutina provádí akci příkazu.

 Další informace o příkazech najdete v tématu [Přehled příkazů](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které se skládají z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands> a <xref:System.Windows.Documents.EditingCommands>, případně můžete definovat vlastní.

 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, že když na ni kliknete, vyvolá příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox> za předpokladu, že <xref:System.Windows.Controls.TextBox> má fokus klávesnice.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Další informace o příkazech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najdete v tématu [Přehled příkazů](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Vstupní systém a základní prvky
 Vstupní události, jako jsou připojené události definované <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard> a <xref:System.Windows.Input.Stylus>, jsou vyvolány vstupním systémem a vloženy do konkrétní pozice v objektovém modelu na základě testu přístupů ve vizuálním stromu v době běhu.

 Každé události, které <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard> a <xref:System.Windows.Input.Stylus> definované jako připojená událost, jsou také znovu zpřístupněny třídami základního elementu <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> jako nová směrovaná událost. Základní element směrované události jsou generovány třídami, které zpracovávají původní připojenou událost a znovu používají data události.

 Když je vstupní událost přidružena k určitému zdrojovému elementu prostřednictvím implementace vstupní události základního elementu, může být směrována přes zbytek trasy události, která je založena na kombinaci logických a vizuálních objektů a zpracována kód aplikace.  Obecně je pohodlnější zpracovávat tyto události vstupu související s zařízením pomocí směrovaných událostí na <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>, protože můžete použít intuitivnější syntaxi obslužných rutin událostí jak v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tak v kódu. Můžete se rozhodnout, že chcete zpracovat připojenou událost, která iniciovala proces, ale měli byste se setkat s několika problémy: připojená událost může být označena zpracováním základní třídy elementu a vy budete muset použít přístupové metody místo skutečné syntaxe události v daném pořadí. pro připojení obslužných rutin pro připojené události.

<a name="whats_next"></a>
## <a name="whats-next"></a>Co dál
 Nyní máte několik postupů, jak zpracovávat vstup v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Měli byste taky mít lepší přehled o různých typech vstupních událostí a směrovaných mechanismech událostí, které používá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 K dispozici jsou další prostředky, které vysvětlují @no__t – 0 prvků architektury a směrování událostí podrobněji. V následujících přehledech najdete další informace, [Přehled příkazů](commanding-overview.md), přehled [fokusu](focus-overview.md), [Přehled základních prvků](base-elements-overview.md), [stromy v](trees-in-wpf.md)subsystému WPF a [směrované události](routed-events-overview.md).

## <a name="see-also"></a>Viz také:

- [Přehled fokusu](focus-overview.md)
- [Přehled příkazů](commanding-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti](properties-wpf.md)
