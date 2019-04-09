---
title: Přehled fokusu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 72b866d714e6a77020bdb74843c3aaa0ba0c3278
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073881"
---
# <a name="focus-overview"></a>Přehled fokusu
V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existují dva hlavní koncepty, které se týkají fokus: klávesnice fokus a logický fokus.  Fokus klávesnice odkazují na elementu, který přijímá vstup z klávesnice a logický fokus na prvek fokus obor, který má právě fokus.  Tyto koncepty jsou podrobně popsány v tomto přehledu.  Vysvětlení rozdílu v těchto konceptů je důležité vytvářet komplexní aplikace, které mají více oblastí, kde lze získat fokus.  
  
 Hlavní třídy, které jsou součástí správy fokus <xref:System.Windows.Input.Keyboard> třídy, <xref:System.Windows.Input.FocusManager> třídy a element základní třídy, jako <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>.  Další informace o základní prvky, najdete v článku [přehled základních elementů](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Třídy se týká především fokus klávesnice a <xref:System.Windows.Input.FocusManager> jedná hlavně s logický fokus, ale nejedná se o absolutní odlišení.  Element, který má právě fokus klávesnice, bude také mít logický fokus, ale element, který má logický fokus nutně nemá fokus klávesnice.  Tím je zřejmé, pokud použijete <xref:System.Windows.Input.Keyboard> třída elementu, který má fokus klávesnice pro ni nastavit také nastaví logický fokus na prvku.  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Fokus klávesnice  
 Fokus klávesnice odkazuje na element, který přijímá vstup z klávesnice.  Může existovat na celém klasické pracovní plochy pouze jeden element, který má fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bude mít element, který má fokus klávesnice <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastavena na `true`.  Statická vlastnost <xref:System.Windows.Input.Keyboard.FocusedElement%2A> na <xref:System.Windows.Input.Keyboard> třídy získá prvek, který má právě fokus klávesnice.  
  
 Aby element, který má získat fokus klávesnice <xref:System.Windows.UIElement.Focusable%2A> a <xref:System.Windows.UIElement.IsVisible%2A> vlastnosti na základní elementy musí být nastaveno na `true`.  Některé třídy, jako <xref:System.Windows.Controls.Panel> základní třídy, mají <xref:System.Windows.UIElement.Focusable%2A> nastavena na `false` ve výchozím nastavení; proto je nutné nastavit <xref:System.Windows.UIElement.Focusable%2A> k `true` Pokud chcete takové element, který má být schopni získat fokus klávesnice.  
  
 Fokus klávesnice můžete získat prostřednictvím interakce uživatele s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jako je tabulátor na element nebo kliknutí myší na některé prvky.  Fokus klávesnice je také možné získat prostřednictvím kódu programu pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A> Metoda se pokusí fokusu klávesnice specifikovaný element.  Vrácený element je prvek, který má fokus klávesnice, což může být jiný prvek než je požadováno, pokud původní nebo novou zaměřit bloku objekt žádosti.  
  
 V následujícím příkladu <xref:System.Windows.Input.Keyboard.Focus%2A> metoda nastavit fokus klávesnice pro <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Vlastnost na základní element třídy získá hodnotu označující, zda prvek má fokus klávesnice.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Vlastnost na základní element třídy získá hodnotu označující, zda element nebo v jednom z jeho visual podřízené prvky má fokus klávesnice.  
  
 Při nastavování počáteční fokus při spuštění aplikace, elementu, který chcete aktivovat musí být ve vizuální strom počáteční okno načtený aplikací a element musí mít <xref:System.Windows.UIElement.Focusable%2A> a <xref:System.Windows.UIElement.IsVisible%2A> nastavena na `true`.  Probíhá doporučený místem, kde můžete nastavit počáteční fokus <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  A <xref:System.Windows.Threading.Dispatcher> zpětného volání lze také voláním <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Logický fokus  
 Logický fokus odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokus.  Obor fokus je element, který uchovává informace o <xref:System.Windows.Input.FocusManager.FocusedElement%2A> ve svém oboru.  Když fokus klávesnice opustí rozsah fokus, element s fokusem ztratí fokus klávesnice, ale zachová logický fokus.  Po návratu fokus klávesnice do oboru fokus, element s fokusem získá fokus klávesnice.  To umožňuje fokus klávesnice změnit mezi více obory fokus, ale zajišťuje, že cílené element v rámci fokus získá fokus klávesnice návratu do oboru fokus zaměření.  
  
 Může existovat více prvků, které mají logický fokus v aplikaci, ale může existovat pouze jeden element, který má logický fokus v konkrétní výběr oboru.  
  
 Element, který má právě fokus klávesnice, má logický fokus, do které patří do oboru fokus.  
  
 Element je možné zapnout do oboru fokus v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením <xref:System.Windows.Input.FocusManager> přidružená vlastnost <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> k `true`.  V kódu, je možné zapnout elementu do oboru fokus voláním <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Následující příklad provede <xref:System.Windows.Controls.StackPanel> do oboru fokus nastavíte <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> přidružená vlastnost.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> Vrátí obor fokus pro zadaný element.  
  
 Třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou obory fokus ve výchozím nastavení jsou <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, a <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> Získá element s fokusem pro obor zadaný fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> nastaví element s fokusem v rámci zadaného fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> Obvykle se používá k nastavení počáteční element s fokusem.  
  
 Následující příklad nastaví element s fokusem v oboru fokus a získá element s fokusem obor fokus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Navigace s použitím klávesnice  
 <xref:System.Windows.Input.KeyboardNavigation> Třídy je zodpovědná za implementace navigaci výběru aktivního elementu výchozí klávesnice, při stisknutí první jednu navigační klávesy.  Navigační klávesy jsou: Kláves TAB, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, UPARROW, šipka dolů, šipka vlevo a šipka vpravo.  
  
 Chování navigace kontejneru navigace lze změnit nastavením připojeného <xref:System.Windows.Input.KeyboardNavigation> vlastnosti <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, a <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Tyto vlastnosti jsou typu <xref:System.Windows.Input.KeyboardNavigationMode> a možné hodnoty jsou <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, a <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Výchozí hodnota je <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, což znamená, že element není kontejner navigace.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> s celou řadou <xref:System.Windows.Controls.MenuItem> objekty.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Připojená vlastnost nastavená na <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> na <xref:System.Windows.Controls.Menu>.  Při změně fokusu pomocí klávesy tab v rámci <xref:System.Windows.Controls.Menu>fokus se přesune od každého prvku a po dosažení posledního prvku fokus vrátí první prvek.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Navigace fokus prostřednictvím kódu programu  
 Další [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pro práci s fokus se <xref:System.Windows.UIElement.MoveFocus%2A> a <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> změny se soustředí na další prvek v aplikaci.  A <xref:System.Windows.Input.TraversalRequest> slouží k určení směru.   <xref:System.Windows.Input.FocusNavigationDirection> Předán <xref:System.Windows.UIElement.MoveFocus%2A> určuje výběru různých směrů lze přesunout, jako například <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> a <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.MoveFocus%2A> změnit element s fokusem.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> Vrátí objekt, který by být vybrán šlo má změnit fokus.  V současné době pouze <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, a <xref:System.Windows.Input.FocusNavigationDirection.Right> podporují <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Události fokusu  
 Události související s fokus klávesnice jsou <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> a <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Události jsou definované jako připojené události na <xref:System.Windows.Input.Keyboard> třídy, ale jsou snadněji přístupné jako ekvivalentní směrovaných událostí na základní element třídy.  Další informace o událostech najdete v článku [směrovat Přehled událostí](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> je aktivována, pokud prvek získá fokus klávesnice.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> je aktivována při přesunutí fokusu klávesnice mimo element.  Pokud <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> události nebo <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> zpracovává události a <xref:System.Windows.RoutedEventArgs.Handled%2A> je nastavena na `true`, pak nedojde ke změně fokusu.  
  
 Následující příklad připojí <xref:System.Windows.UIElement.GotKeyboardFocus> a <xref:System.Windows.UIElement.LostKeyboardFocus> obslužné rutiny událostí pro <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Když <xref:System.Windows.Controls.TextBox> získá fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> se změní na <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Když <xref:System.Windows.Controls.TextBox> ztratí fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> se změní zpět na bílou.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Události související s logický fokus se <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.  Tyto události jsou definovány na <xref:System.Windows.Input.FocusManager> jako připojené události, ale <xref:System.Windows.Input.FocusManager> nevystavuje obálky události CLR.  <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> snadněji vystavit tyto události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Přehled vstupu](input-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
