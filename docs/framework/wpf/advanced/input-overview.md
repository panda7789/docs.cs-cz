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
ms.openlocfilehash: 5eaf83f259abe4ee574dfd4d2269dfa1e9373c94
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869078"
---
# <a name="input-overview"></a>Přehled vstupu
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Podsystém poskytuje výkonné rozhraní API pro získání vstupu z nejrůznějších zařízení, včetně myši, klávesnice, dotyku a stylusu. Toto téma popisuje služby poskytované nástrojem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a vysvětluje architekturu vstupních systémů.

<a name="input_api"></a>
## <a name="input-api"></a>Vstupní rozhraní API
 V základních třídách elementů se nachází primární vstupní rozhraní API: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>a <xref:System.Windows.FrameworkContentElement>.  Další informace o základních elementech naleznete v tématu [Přehled základních prvků](base-elements-overview.md).  Tyto třídy poskytují funkce pro vstupní události, které souvisí s klíčovými klávesami, tlačítky myši, kolečkem myši, pohybem myši, správou fokusu a zachytáváním myši, pokud chcete pojmenovat několik. Vložením vstupního rozhraní API na základní prvky namísto zpracování všech vstupních událostí jako služby umožní vstupní architektura, aby se vstupní události nastavily konkrétním objektem v uživatelském rozhraní, a aby podporovaly schéma směrování událostí, kde je více než jeden prvek OPP. ortunity zpracování události vstupu. K mnoha vstupním událostem je přidružen pár událostí.  Například událost stisknutí klíče je přidružena <xref:System.Windows.Input.Keyboard.KeyDown> k událostem a. <xref:System.Windows.Input.Keyboard.PreviewKeyDown>  Rozdíl v těchto událostech je ve způsobu, jakým jsou směrovány do cílového prvku.  Události ve verzi Preview propojující strom elementů od kořenového elementu až po cílový element.  Probublávání události z cílového prvku do kořenového elementu.  Směrování událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nástroji je podrobněji popsáno dále v tomto přehledu a v tématu [Přehled směrovaných událostí](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Třídy klávesnice a myši
 Kromě vstupního rozhraní API na základních třídách <xref:System.Windows.Input.Keyboard> prvků poskytuje třída a <xref:System.Windows.Input.Mouse> třídy další rozhraní API pro práci s vstupy klávesnice a myši.

 Příklady vstupního rozhraní <xref:System.Windows.Input.Keyboard> API třídy <xref:System.Windows.Input.Keyboard.Modifiers%2A> jsou <xref:System.Windows.Input.ModifierKeys> vlastnost, která vrací aktuálně stisknutou a <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> metodu, která určuje, zda je zadaný klíč stisknut.

 Následující příklad používá <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> metodu k určení, <xref:System.Windows.Input.Key> zda je v nefunkčním stavu.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Příklady vstupního rozhraní API <xref:System.Windows.Input.Mouse> třídy jsou <xref:System.Windows.Input.Mouse.MiddleButton%2A>, které získá stav prostřední tlačítko myši a <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, které Získá prvek ukazatel myši v tuto chvíli.

 Následující příklad určuje, zda <xref:System.Windows.Input.Mouse.LeftButton%2A> je ukazatel myši <xref:System.Windows.Input.MouseButtonState.Pressed> ve stavu.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 Třídy <xref:System.Windows.Input.Mouse> a<xref:System.Windows.Input.Keyboard> jsou podrobněji popsány v rámci tohoto přehledu.

### <a name="stylus-input"></a>Vstup stylusu
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má integrovanou podporu pro <xref:System.Windows.Input.Stylus>.  Je vstup perem, který je oblíbený [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]pomocí. <xref:System.Windows.Input.Stylus>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace mohou používat Stylus jako myš pomocí rozhraní Mouse API, ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také zpřístupňuje abstrakci zařízení stylusu, která používá model podobný klávesnici a myši.  Všechna rozhraní API související s stylusem obsahují slovo Stylus.

 Vzhledem k tomu, že Stylus může fungovat jako myš, aplikace, které podporují jenom vstupy myši, můžou dál získávat automaticky určitou úroveň podpory stylusem. Pokud je Stylus použit takovým způsobem, aplikace je dána příležitostí ke zpracování příslušné události stylus a poté zpracuje příslušnou událost myši. Kromě toho jsou k dispozici také služby vyšší úrovně, jako je například vstup z inkoustu, a to prostřednictvím abstrakce zařízení stylus.  Další informace o rukopisu jako vstup naleznete v tématu [Začínáme with Ink](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Směrování událostí
 <xref:System.Windows.FrameworkElement> Může obsahovat další prvky jako podřízené elementy v jejím modelu obsahu, tvořící strom elementů.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji se nadřazený element může zúčastnit vstupu směrovaného na jeho podřízené prvky nebo jiné následníky pomocí předání událostí. To je užitečné hlavně při sestavování ovládacích prvků z menších ovládacích prvků, což je proces známý jako "složení ovládacího prvku" nebo "skládání". Další informace o stromech elementů a o tom, jak struktury prvků souvisejí s trasami událostí, naleznete v tématu [stromy v WPF](trees-in-wpf.md).

 Směrování událostí je proces předávání událostí více prvkům, aby určitý objekt nebo prvek podél trasy mohl nabízet významnou odpověď (prostřednictvím zpracování) k události, která by mohla být zadávána jiným prvkem.  Směrované události používají jeden ze tří mechanismů směrování: přímé, probublávání a tunelové propojení.  V přímém směrování je zdrojový prvek jediným oznámeným prvkem a událost není směrována na žádné jiné prvky. Nicméně přímá směrovaná událost stále nabízí některé další možnosti, které jsou k dispozici pouze pro směrované události na rozdíl od standardních událostí CLR. Probublávání sestaví strom elementů pomocí prvního upozorňování elementu, který zdroj události nastavil, pak nadřazeného elementu a tak dále.  Tunelové propojení začíná v kořenovém adresáři stromu prvků a funguje dolů a končí původním zdrojovým elementem.  Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]události vstupu obecně přicházejí do párů, které se skládají z tunelové události a události probublávání.  Události tunelování se odlišují od probublávání událostí s předponou Preview.  Například jedná se o tunelovou verzi události přesunutí myši a <xref:System.Windows.Input.Mouse.MouseMove> jedná se o verzi této události probublávání. <xref:System.Windows.Input.Mouse.PreviewMouseMove> Toto párování událostí je konvence, která je implementována na úrovni prvku a není podstatou funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému událostí. Podrobnosti najdete v oddílu události vstupu WPF v tématu [směrované události – přehled](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Zpracování událostí vstupu
 Pro příjem vstupu elementu musí být obslužná rutina události přidružena k této konkrétní události.  V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tomto případě je to jasné: odkazujete na název události jako atribut prvku, který bude pro tuto událost naslouchat.  Potom nastavíte hodnotu atributu na název obslužné rutiny události, kterou definujete, na základě delegáta.  Obslužná rutina události musí být napsána v C# kódu, například a může být obsažena v souboru kódu na pozadí.

 K událostem klávesnice dojde v případě, že operační systém hlásí klíčové akce, ke kterým dojde, když je fokus klávesnice na prvku. Události myši a tužky spadají do dvou kategorií: události, které oznamují změny v pozici ukazatele vzhledem k elementu, a události, které oznamují změny ve stavu tlačítek zařízení.

### <a name="keyboard-input-event-example"></a>Příklad události vstupu z klávesnice
 Následující příklad naslouchá stisknutí klávesy šipka vlevo.  Vytvoří <xref:System.Windows.Controls.StackPanel> se, který <xref:System.Windows.Controls.Button>má.  Obslužná rutina události, která má naslouchat klávesám šipka vlevo, je <xref:System.Windows.Controls.Button> připojena k instanci.

 První část příkladu vytvoří <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Button> a a připojí obslužnou rutinu události pro <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 Druhá část je zapsána v kódu a definuje obslužnou rutinu události.  Když je Stisknutá klávesa šipka vlevo a <xref:System.Windows.Controls.Button> má fokus klávesnice, obslužná rutina se spustí <xref:System.Windows.Controls.Control.Background%2A> a změní se <xref:System.Windows.Controls.Button> barva.  Pokud se klávesa stiskne, ale není to klávesa šipka vlevo, <xref:System.Windows.Controls.Control.Background%2A> barva <xref:System.Windows.Controls.Button> se změní zpátky na počáteční barvu.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Příklad události vstupu myši
 V následujícím příkladu se <xref:System.Windows.Controls.Control.Background%2A> barva a <xref:System.Windows.Controls.Button> změní, když ukazatel myši vstoupí do <xref:System.Windows.Controls.Button>.  Barva se obnoví, když myš <xref:System.Windows.Controls.Button>opustí. <xref:System.Windows.Controls.Control.Background%2A>

 První část <xref:System.Windows.Controls.StackPanel> příkladu vytvoří <xref:System.Windows.Controls.Button> a ovládací prvek a připojí obslužné rutiny události pro <xref:System.Windows.UIElement.MouseEnter> události a <xref:System.Windows.UIElement.MouseLeave> k <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 Druhá část příkladu je zapsána v kódu a definuje obslužné rutiny událostí.  Když ukazatel myši <xref:System.Windows.Controls.Button>vstoupí do <xref:System.Windows.Controls.Control.Background%2A> , barva ovládacího panelu <xref:System.Windows.Controls.Button> se změní na <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Když <xref:System.Windows.Controls.Button>myš opustí <xref:System.Windows.Controls.Control.Background%2A> , barva ovládacího panelu <xref:System.Windows.Controls.Button> se změní zpátky na <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Zadávání textu
 <xref:System.Windows.ContentElement.TextInput> Událost vám umožní naslouchat textovému zadání způsobem nezávislým na zařízení. Klávesnice je primárním prostředkem textového vstupu, ale řeč, rukopis a jiná vstupní zařízení mohou také vygenerovat textový vstup.

 V případě vstupu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesnice nejprve odešle / příslušné <xref:System.Windows.ContentElement.KeyDown> <xref:System.Windows.ContentElement.KeyUp> události. Pokud tyto události nejsou zpracovány a klíč je text (spíše než řídicí klíč, například směrovou šipku nebo funkční klávesy), <xref:System.Windows.ContentElement.TextInput> je vyvolána událost.  Mezi <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.TextInput> událostmi a není vždy jednoduché mapování 1:1, protože více klávesových úhozů může generovat jeden znak textového vstupu a jednoduché stisknutí kláves. může generovat více znaků. <xref:System.Windows.ContentElement.KeyUp> zobrazen.  To platí zejména pro jazyky, jako jsou čínština, japonština a korejština, které používají editory IME (Input Method editory) k vygenerování tisíců možných znaků v odpovídajících abecedách.

 Při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> <xref:System.Windows.ContentElement.TextInput> odeslání události je nastavena na<xref:System.Windows.Input.KeyEventArgs.Key%2A> hodnotu, pokud se stisknutí kláves změní na část události (Pokud je stisknuto ALT + S). <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> To umožňuje kódu v <xref:System.Windows.ContentElement.KeyDown> obslužné rutině události <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> kontrolovat a, pokud je nalezeno, opustit zpracování obslužné rutiny následně vyvolané <xref:System.Windows.ContentElement.TextInput> události. V těchto případech lze použít různé vlastnosti <xref:System.Windows.Input.TextCompositionEventArgs> argumentu k určení původních klávesových úhozů. Podobně, pokud je aktivní editor IME, <xref:System.Windows.Input.Key> má <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>hodnotu a <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> poskytuje původní klávesovou zkratku nebo stisknutí kláves.

 Následující příklad definuje obslužnou rutinu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události a obslužné rutiny <xref:System.Windows.UIElement.KeyDown> události.

 První segment kódu nebo značek vytvoří uživatelské rozhraní.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Druhý segment kódu obsahuje obslužné rutiny událostí.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Vzhledem k tomu, že vstupní události doplní trasu události, <xref:System.Windows.Controls.StackPanel> obdrží vstup bez ohledu na to, který prvek má fokus klávesnice. Ovládací prvek se nejdřív oznamuje `OnTextInputKeyDown` a obslužná rutina se volá jenom v <xref:System.Windows.Controls.TextBox> případě, že se vstup nezpracovává. <xref:System.Windows.Controls.TextBox> Pokud je namísto <xref:System.Windows.UIElement.KeyDown> události použita `OnTextInputKeyDown`událost, obslužná rutina je volána jako první. <xref:System.Windows.UIElement.PreviewKeyDown>

 V tomto příkladu je logika zpracování zapsána dvakrát – jednou pro klávesovou zkratku CTRL + O a znovu pro událost Click tlačítka. To se dá zjednodušit pomocí příkazů namísto přímého zpracování událostí vstupu.  Příkazy jsou popsány v tomto přehledu a v tématu [Přehled příkazů](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Dotykové ovládání a manipulace
 Nový hardware a rozhraní API v operačním systému Windows 7 poskytují aplikacím možnost přijímat vstupy z několika dotyků současně. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje aplikacím rozpoznávat a reagovat na dotykové ovládání podobným způsobem jako reakce na jiný vstup, jako je například myš nebo klávesnice, vyvoláním událostí, když dojde k dotyku.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zpřístupňuje dva typy událostí, když dojde k dotyku: události dotyku a události manipulace. Události dotykového ovládání poskytují hrubá data o jednotlivých prstech na dotykové obrazovce a jejich přesun. Události manipulace interpretují vstup jako určité akce. V této části jsou popsány oba typy událostí.

### <a name="prerequisites"></a>Požadavky
 Pro vývoj aplikací, které reagují na dotykové ovládání, potřebujete tyto komponenty.

- Visual Studio 2010.

- Windows 7.

- Zařízení, jako je dotyková obrazovka, která podporuje dotykové ovládání systému Windows.

### <a name="terminology"></a>Terminologie
 Následující výrazy se použijí, když je prodiskutován dotyk.

- **Dotykové ovládání** je typ uživatelského vstupu, který je rozpoznáván systémem Windows 7. Dotyková obrazovka se většinou zahajuje tím, že se na dotykové obrazovce přidává prsty. Všimněte si, že zařízení, jako je například touchpad, který je běžný pro přenosné počítače, nepodporují dotykové ovládání, pokud zařízení jednoduše převede polohu a pohyb prstu jako vstup myši.

- **Multitouch** je dotykové ovládání, ke kterému dochází z více než jednoho bodu současně. Windows 7 a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje multitouch. Pokaždé, když je popsána [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dotyková dokumentace pro, jsou koncepty uplatněny na multitouch.

- K **manipulaci** dojde, když je dotykové ovládání interpretováno jako fyzická akce, která je použita na objekt. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji události manipulace interpretují vstup jako převod, rozšíření nebo manipulaci s rotací.

- `touch device` Představuje zařízení, které vytváří dotykové vstupy, jako je například jeden prst na dotykové obrazovce.

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

 <xref:System.Windows.Controls.ScrollViewer> Definuje připojenou vlastnost, která umožňuje určit, zda je povoleno posouvání dotykového ovládání horizontálně, svisle, obojím nebo ani jednou. <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> Vlastnost určuje, jak rychle se posune v případě, že uživatel zaznamená prst z dotykové obrazovky. <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> Připojená vlastnost určuje poměr posunutí posunu, aby bylo možné přeložit posun manipulace.

### <a name="touch-events"></a>Události dotykové ovládání
 Základní třídy, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>a <xref:System.Windows.ContentElement>, definují události, které se můžou přihlásit k odběru, takže vaše aplikace bude reagovat na dotykové ovládání. Události dotykové ovládání jsou užitečné v případě, že vaše aplikace interpretuje dotykové ovládání s jinou výjimkou manipulace s objektem. Například aplikace, která umožňuje uživateli kreslit jedním nebo více prsty, by mohla přihlašovat se k odběru událostí dotykové ovládání.

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

 Podobně jako události klávesnice a myši jsou události dotykového ovládání směrovány událostmi. Události, které začínají `Preview` , jsou tunelové události a události, které `Touch` začínají, jsou probublávání události. Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md). Při zpracování těchto událostí lze získat pozici vstupu relativní k libovolnému prvku voláním <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> metody nebo. <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A>

 Pro pochopení interakce mezi událostmi dotykového ovládání Zvažte situaci, kdy uživatel vloží jeden prst na prvek, přesune prst v prvku a poté vytvoří prst z prvku. Následující ilustrace znázorňuje provádění probubláváních událostí (události tunelování jsou vynechány pro zjednodušení).

 ![Posloupnost událostí dotykového ovládání.](./media/ndp-touchevents.png "NDP_TouchEvents") Události dotykové ovládání

 Následující seznam popisuje pořadí událostí na předchozí ilustraci.

1. K <xref:System.Windows.UIElement.TouchEnter> události dojde jednou, když uživatel umístí prst na prvek.

2. <xref:System.Windows.UIElement.TouchDown> Událost probíhá jednou.

3. K <xref:System.Windows.UIElement.TouchMove> události dochází vícekrát, protože uživatel přesune prst v rámci elementu.

4. K <xref:System.Windows.UIElement.TouchUp> události dochází jednou, když uživatel z elementu zavýtahí prst.

5. <xref:System.Windows.UIElement.TouchLeave> Událost probíhá jednou.

 Při použití více než dvou prsty dojde k událostem u každého prstu.

### <a name="manipulation-events"></a>Události manipulace
 V případech, kdy aplikace umožňuje uživateli manipulovat s objektem, <xref:System.Windows.UIElement> třída definuje události manipulace. Na rozdíl od událostí dotyku, které jednoduše hlásí pozici dotyku, se události manipulace vydávají, jak lze interpretovat. Existují tři typy manipulace, překladu, rozšiřování a rotace. Následující seznam popisuje, jak vyvolat tři typy manipulace.

- Umístěte prst na objekt a pohybujte prstem přes dotykovou obrazovku, aby se vyvolala manipulace s překladem. Tím se obvykle přesune objekt.

- K vyvolání rozšíření můžete použít dva prsty na objekt a přesunout prsty blíže k sobě nebo více než další. Tím se obvykle změní velikost objektu.

- Přidejte dva prsty na objekt a otáčejte prsty kolem sebe, aby se vyvolala manipulace s rotací. Tím se obvykle otáčí objekt.

 Současně může probíhat více než jeden typ manipulace.

 Když způsobíte, že objekty budou reagovat na manipulace, je možné, že se objekt jeví jako nájezdový. Díky tomu mohou vaše objekty simulovat fyzický svět. Když například vložíte knihu do tabulky, pokud budete mít dostatek volného místa, bude kniha po jejím vydání nadále přesunuta. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje simulovat toto chování tím, že vyvolává události manipulace poté, co uživatel uvolňuje objekt.

 Informace o tom, jak vytvořit aplikaci, která umožňuje uživateli přesunout, změnit velikost a otočit objekt, najdete v tématu [Návod: Vytvoření první aplikace](walkthrough-creating-your-first-touch-application.md)dotykového ovládání.

 <xref:System.Windows.UIElement> Definuje následující události manipulace.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Ve výchozím nastavení <xref:System.Windows.UIElement> neobdrží tyto události manipulace. Chcete-li přijímat události <xref:System.Windows.UIElement>manipulace s, nastavte `true` <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> na.

#### <a name="the-execution-path-of-manipulation-events"></a>Cesta spuštění pro události manipulace
 Vezměte v úvahu scénář, kdy uživatel vyvolá objekt. Uživatel vloží prst na objekt, přesune prst na dotykovou obrazovku po krátkou vzdálenost a pak při přesunu zavolá prst. Výsledkem je to, že se objekt přesune v rámci prstu uživatele a nadále se přesune, jakmile uživatel dostane prst.

 Následující ilustrace znázorňuje cestu spuštění pro události manipulace a důležité informace o každé události.

 ![Sekvence událostí manipulace.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Události manipulace

 Následující seznam popisuje pořadí událostí na předchozí ilustraci.

1. K <xref:System.Windows.UIElement.ManipulationStarting> události dojde, když uživatel umístí prst na objekt. Mimo jiné tato událost umožňuje nastavit <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost. V následných událostech bude poloha manipulace relativní vzhledem k <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. V jiných událostech <xref:System.Windows.UIElement.ManipulationStarting>než je tato vlastnost jen pro čtení, <xref:System.Windows.UIElement.ManipulationStarting> takže událost je jediná doba, kterou můžete nastavit v této vlastnosti.

2. Dojde <xref:System.Windows.UIElement.ManipulationStarted> k události Next. Tato událost oznamuje původ manipulace.

3. K <xref:System.Windows.UIElement.ManipulationDelta> události dochází víckrát, protože prsty uživatele se přesunou na dotykovou obrazovku. <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> Vlastnost<xref:System.Windows.Input.ManipulationDeltaEventArgs> třídy hlásí, zda je manipulace interpretována jako pohyb, rozšíření nebo překlad. To je místo, kde provádíte většinu práce při manipulaci s objektem.

4. K <xref:System.Windows.UIElement.ManipulationInertiaStarting> události dojde, když prsty uživatele ztratí kontakt s objektem. Tato událost umožňuje určit zpomalení manipulace během setrvačné hmotnosti. To znamená, že váš objekt může emulovat různé fyzické prostory nebo atributy, pokud zvolíte. Předpokládejme například, že vaše aplikace má dva objekty, které reprezentují položky ve fyzickém světě, a jeden je těžší než druhý. Nejslabším objektem můžete zvýšit zpomalení rychleji než světlejší objekt.

5. K <xref:System.Windows.UIElement.ManipulationDelta> události dochází vícekrát jako setrvačné hmotnosti. Všimněte si, že tato událost nastane, když se prsty uživatele pohybují v dotykové [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obrazovce a při simulaci setrvačné hmotnosti. Jinými slovy, <xref:System.Windows.UIElement.ManipulationDelta> proběhne před a <xref:System.Windows.UIElement.ManipulationInertiaStarting> po události. Vlastnost hlásí, <xref:System.Windows.UIElement.ManipulationDelta> zda událost probíhá během setrvačné hmotnosti, takže můžete tuto vlastnost kontrolovat a provádět různé akce v závislosti na její hodnotě. <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType>

6. K <xref:System.Windows.UIElement.ManipulationCompleted> události dojde, když skončí manipulace a jakýkoliv setrvačná hmotnost. To znamená, že po výskytu <xref:System.Windows.UIElement.ManipulationDelta> <xref:System.Windows.UIElement.ManipulationCompleted> všech událostí dojde k události k signalizaci, že manipulace je dokončena.

 <xref:System.Windows.UIElement> Také<xref:System.Windows.UIElement.ManipulationBoundaryFeedback> definuje událost. Tato událost nastane, pokud <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> je <xref:System.Windows.UIElement.ManipulationDelta> v události volána metoda. <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> Událost umožňuje aplikacím nebo komponentám poskytovat vizuální zpětnou vazbu, když objekt narazí na hranici. Například <xref:System.Windows.Window> Třída<xref:System.Windows.UIElement.ManipulationBoundaryFeedback> zpracovává událost, která způsobí, že okno bude mírně přesunuto, když je jeho okraj zjištěn.

 Manipulaci můžete zrušit voláním <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> metody pro argumenty události v jakékoli události manipulace s výjimkou <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> události. Když zavoláte <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, události manipulace již nejsou vyvolány a dojde k události myši při dotyku. Následující tabulka popisuje vztah mezi časem zrušení manipulace a událostmi myši, ke kterým dojde.

|Událost, která se zruší, se volá v|Události myši, které se vyskytují u vstupu, ke kterému již došlo|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> a <xref:System.Windows.UIElement.ManipulationStarted>|Události myši.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Události myši a přesunutí myši.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> a <xref:System.Windows.UIElement.ManipulationCompleted>|Myš dolů, pohyb myši a události myši nahoru|

 Všimněte si, že pokud <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> zavoláte, když je manipulace v nenájezdovém umístění, metoda se vrátí `false` a vstup nevyvolává události myši.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Vztah mezi událostmi dotykového a manipulačního události
 <xref:System.Windows.UIElement> Může vždy přijímat události dotykového ovládání. Pokud je `true`vlastnost nastavena na, <xref:System.Windows.UIElement> může přijímat dotykové i manipulační události. <xref:System.Windows.UIElement.IsManipulationEnabled%2A>  Pokud událost není zpracována (tj <xref:System.Windows.RoutedEventArgs.Handled%2A> . vlastnost je `false`), logika manipulace zachytí dotykové ovládání a vygeneruje události manipulace. <xref:System.Windows.UIElement.TouchDown> Pokud je `true` vlastnost nastavena na hodnotu v <xref:System.Windows.UIElement.TouchDown> události, logika manipulace negeneruje události manipulace. <xref:System.Windows.RoutedEventArgs.Handled%2A> Následující ilustrace znázorňuje vztah mezi událostmi dotykového ovládání a událostmi manipulace.

 ![Vztah mezi událostmi dotykového a manipulačního události](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") Události dotyku a manipulace

 Následující seznam popisuje vztah mezi událostmi dotykového ovládání a manipulací, které jsou uvedeny na předchozím obrázku.

- Když první <xref:System.Windows.UIElement.TouchDown> dotykové zařízení vygeneruje událost <xref:System.Windows.UIElement>na, logika manipulace zavolá <xref:System.Windows.UIElement.CaptureTouch%2A> metodu, která <xref:System.Windows.UIElement.GotTouchCapture> událost vygeneruje.

- Když dojde k tomu, logika manipulace <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> volá <xref:System.Windows.UIElement.ManipulationStarting> metodu, která generuje událost. <xref:System.Windows.UIElement.GotTouchCapture>

- Při výskytu <xref:System.Windows.UIElement.ManipulationDelta>událostilogika manipulace generuje <xref:System.Windows.UIElement.ManipulationInertiaStarting> události, ke kterým dojde před událostí. <xref:System.Windows.UIElement.TouchMove>

- Když poslední dotykové zařízení na elementu vyvolá <xref:System.Windows.UIElement.TouchUp> událost, logika manipulace <xref:System.Windows.UIElement.ManipulationInertiaStarting> vygeneruje událost.

<a name="focus"></a>
## <a name="focus"></a>Vybrána
 Existují dva hlavní koncepty, které se týkají fokusu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: fokus klávesnice a logický fokus.

### <a name="keyboard-focus"></a>Fokus klávesnice
 Fokus klávesnice odkazuje na prvek, který přijímá vstup z klávesnice.  Na celém počítači může být pouze jeden element, který má fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `true` nástroji<xref:System.Windows.IInputElement.IsKeyboardFocused%2A> bude element, který má fokus klávesnice, nastaven na.  Statická <xref:System.Windows.Input.Keyboard> Metoda<xref:System.Windows.Input.Keyboard.FocusedElement%2A> vrátí prvek, který aktuálně má fokus klávesnice.

 Fokus klávesnice lze získat pomocí klávesy Tabulátor pro element nebo kliknutím na tlačítko myši u určitých prvků, jako je <xref:System.Windows.Controls.TextBox>například.  Fokus klávesnice lze také získat programově pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A>pokusy o poskytnutí fokusu klávesnice zadaného elementu.  Element vrácený funkcí <xref:System.Windows.Input.Keyboard.Focus%2A> je prvek, který aktuálně má fokus klávesnice.

 Aby element získal fokus klávesnice, <xref:System.Windows.UIElement.Focusable%2A> vlastnost <xref:System.Windows.UIElement.IsVisible%2A> a vlastnosti musí být nastaveny na **hodnotu true**.  Některé <xref:System.Windows.Controls.Panel>třídy, například, jsou <xref:System.Windows.UIElement.Focusable%2A> nastaveny na `false` výchozí hodnoty; proto může být nutné tuto vlastnost nastavit na `true` , pokud chcete, aby byl tento prvek schopný získat fokus.

 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> k nastavení fokusu klávesnice <xref:System.Windows.Controls.Button>na.  Doporučeným místem pro nastavení prvotního zaměření v aplikaci je <xref:System.Windows.FrameworkElement.Loaded> obslužná rutina události.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Další informace o fokusu klávesnice najdete v tématu [Přehled fokusu](focus-overview.md).

### <a name="logical-focus"></a>Logický fokus
 Logický fokus odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> na v oboru fokusu.  V aplikaci může být více elementů, které mají logický fokus, ale může existovat pouze jeden prvek, který má logický fokus v rámci konkrétního oboru fokusu.

 Rozsah fokusu je prvek kontejneru, který uchovává <xref:System.Windows.Input.FocusManager.FocusedElement%2A> informace v rámci jeho oboru.  Když fokus opustí rozsah fokusu, bude mít fokus na klávesnici fokus, ale zachová se tím logický fokus.  Když se fokus vrátí do oboru fokusu, fokus získá fokus klávesnice.  To umožňuje změnit fokus klávesnice mezi více rozsahy fokusu, ale zajistěte, aby element fokus v rámci oboru fokusu zůstal při návratu fokusu fokusem elementu.

 Element může být převeden [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do oboru <xref:System.Windows.Input.FocusManager> fokusu nastavením připojené vlastnosti <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> na `true` <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> nebo v kódu nastavením připojené vlastnosti pomocí metody.

 Následující příklad vytvoří <xref:System.Windows.Controls.StackPanel> do oboru fokus <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> nastavením připojené vlastnosti.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Třídy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve kterých jsou standardně zaměřeny <xref:System.Windows.Window>na rozsahy, <xref:System.Windows.Controls.ContextMenu>jsou, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>a.

 Element, který má fokus klávesnice, bude mít také logický fokus pro rozsah fokusu, ke kterému patří. Proto je nastavení fokusu u prvku s <xref:System.Windows.Input.Keyboard.Focus%2A> metodou <xref:System.Windows.Input.Keyboard> třídy nebo třídami základních prvků proveden pokus o poskytnutí fokusu klávesnice elementu a logického výběru.

 Chcete-li určit fokus prvku v oboru fokusu, <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>použijte. Chcete-li změnit element s fokusem pro rozsah výběru <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>, použijte.

 Další informace o logickém výběru najdete v tématu [Přehled fokusu](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Pozice myši
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vstupní rozhraní API poskytuje užitečné informace, pokud jde o souřadnici prostorů.  Například souřadnice `(0,0)` je levá horní souřadnice, ale v levém horním rohu elementu stromu? Prvek, který je vstupním cílem? Prvek, na který jste připojenou obslužnou rutinu události? Nebo něco jiného? Aby nedocházelo k nejasnostem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vstupní rozhraní API vyžaduje, abyste při práci s souřadnicemi získanými pomocí myši určili referenční rámec. <xref:System.Windows.Input.Mouse.GetPosition%2A> Metoda vrátí souřadnici ukazatele myši relativně k zadanému prvku.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Zachycení myši
 Zařízení myši speciálně drží modální charakteristiku, která se označuje jako zachycení myši. K uchování přechodného vstupního stavu, když se spustí operace přetažení, se zachytí myš, aby se nemusely vyskytovat další operace, které se týkají jmenovité pozice ukazatele myši. Během přetahování nemůže uživatel kliknout na bez přerušení přetahování, což způsobí, že většina mouseoverch upozornění není vhodná, zatímco je zachycení myši drženo zdrojem přetažení. Vstupní systém zveřejňuje rozhraní API, která mohou určovat stav zachycení myši, a také rozhraní API, která mohou vynutit zachycení myši na konkrétní prvek nebo Vymazat stav zachycení myši. Další informace o operacích přetažení najdete v tématu [Přehled](drag-and-drop-overview.md)přetažení.

<a name="commands"></a>
## <a name="commands"></a>Příkazy
 Příkazy umožňují zpracování vstupu na sémantické úrovni než vstup zařízení.  Příkazy jsou jednoduché direktivy, například `Cut`, `Copy`, `Paste`nebo `Open`.  Příkazy jsou užitečné pro centralizaci logiky příkazů.  Ke stejnému příkazu může být přistup <xref:System.Windows.Controls.Menu>z, <xref:System.Windows.Controls.ToolBar>nebo prostřednictvím klávesové zkratky. Příkazy také poskytují mechanismus pro vypnutí ovládacích prvků v případě, že příkaz nebude k dispozici.

 <xref:System.Windows.Input.RoutedCommand>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je implementací. <xref:System.Windows.Input.ICommand>  Při spuštění <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.CommandManager.Executed> je vyvolána událost aaudálostvcílipříkazu,kterávytvořítunelabublinovýprvekpomocístromuelementu,jako<xref:System.Windows.Input.CommandManager.PreviewExecuted> je jiný vstup.  Pokud není nastaven cíl příkazu, bude element s fokusem klávesnice cílem příkazu.  Logika, která provede příkaz, je připojena k <xref:System.Windows.Input.CommandBinding>.  Když událost dosáhne konkrétního příkazu, <xref:System.Windows.Input.ExecutedRoutedEventHandler> je volána na. <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.CommandManager.Executed>  Tato obslužná rutina provádí akci příkazu.

 Další informace o příkazech najdete v tématu [Přehled příkazů](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje knihovnu běžných příkazů, které se skládají z <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands> <xref:System.Windows.Input.NavigationCommands>, a <xref:System.Windows.Documents.EditingCommands>, nebo můžete definovat vlastní.

 Následující příklad ukazuje, jak <xref:System.Windows.Controls.MenuItem> nastavit, aby při kliknutí <xref:System.Windows.Input.ApplicationCommands.Paste%2A> vyvolal příkaz <xref:System.Windows.Controls.TextBox> v <xref:System.Windows.Controls.TextBox>, za předpokladu, že má fokus klávesnice.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Další informace o příkazech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji najdete v tématu [Přehled příkazů](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Vstupní systém a základní prvky
 Vstupní události, jako jsou připojené události definované <xref:System.Windows.Input.Mouse>třídou, <xref:System.Windows.Input.Keyboard>a <xref:System.Windows.Input.Stylus> , jsou vyvolány vstupním systémem a vloženy do konkrétní pozice v objektovém modelu na základě testu přístupů ve vizuálním stromu v době běhu.

 Každá událost, která <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, a <xref:System.Windows.Input.Stylus> definovaná jako připojená událost je také znovu zpřístupněna základními třídami <xref:System.Windows.UIElement> prvků a <xref:System.Windows.ContentElement> jako nová směrovaná událost. Základní element směrované události jsou generovány třídami, které zpracovávají původní připojenou událost a znovu používají data události.

 Když je vstupní událost přidružena k určitému zdrojovému elementu prostřednictvím implementace vstupní události základního elementu, může být směrována přes zbytek trasy události, která je založena na kombinaci logických a vizuálních objektů a zpracována kód aplikace.  Obecně je pohodlnější zpracovávat tyto události vstupu související se zařízením pomocí směrovaných událostí na <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>, protože můžete použít intuitivnější syntaxe obslužné rutiny událostí v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a v kódu. Můžete se rozhodnout, že chcete zpracovat připojenou událost, která iniciovala proces, ale měli byste se setkat s několika problémy: připojená událost může být označena zpracováním základní třídy elementu a vy budete muset použít přístupové metody místo skutečné syntaxe události v daném pořadí. pro připojení obslužných rutin pro připojené události.

<a name="whats_next"></a>
## <a name="whats-next"></a>Co dál
 Nyní máte několik technik pro zpracování vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Měli byste taky mít lepší přehled o různých typech vstupních událostí a mechanismech směrovanéch událostí, které používá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 K dispozici jsou další prostředky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které vysvětlují prvky architektury a směrování událostí podrobněji. V následujících přehledech najdete další informace, [Přehled příkazů](commanding-overview.md), přehled fokusu [](focus-overview.md), [Přehled základních prvků](base-elements-overview.md), [stromy v](trees-in-wpf.md)subsystému WPF a [směrované události](routed-events-overview.md).

## <a name="see-also"></a>Viz také:

- [Přehled fokusu](focus-overview.md)
- [Přehled příkazů](commanding-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
- [Vlastnosti](properties-wpf.md)
