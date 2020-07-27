---
title: Přehled fokusu
description: 'Přečtěte si o dvou hlavních konceptech v Windows Presentation Foundation, které se týkají fokusu: fokus klávesnice a logický fokus.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165103"
---
# <a name="focus-overview"></a>Přehled fokusu
V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existují dva hlavní koncepty, které se týkají fokusu: fokus klávesnice a logický fokus.  Fokus klávesnice odkazuje na element, který přijímá vstup z klávesnice a logický fokus odkazuje na element v oboru fokusu, který má fokus.  Tyto koncepty jsou podrobně popsány v tomto přehledu.  Porozumění rozdílům v těchto konceptech je důležité pro vytváření složitých aplikací, které mají více oblastí, kde lze získat fokus.  
  
 Hlavní třídy, které se účastní správy fokusu, jsou <xref:System.Windows.Input.Keyboard> třídy, <xref:System.Windows.Input.FocusManager> třídy a základní třídy prvků, jako jsou <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> .  Další informace o základních elementech naleznete v tématu [Přehled základních prvků](base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard>Třída je primárně zaměřená na fokus klávesnice a je primárně zaměřená na <xref:System.Windows.Input.FocusManager> logický fokus, ale toto není absolutní rozlišení.  Prvek, který má fokus klávesnice, bude mít také logický fokus, ale element, který má logický fokus, nemusí mít fokus klávesnice.  To je zřejmé při použití <xref:System.Windows.Input.Keyboard> třídy k nastavení prvku, který má fokus klávesnice, pro něj také nastaví logický fokus na prvek.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Fokus klávesnice  
 Fokus klávesnice odkazuje na prvek, který aktuálně přijímá vstup z klávesnice.  Na celém počítači může být pouze jeden element, který má fokus klávesnice.  V nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude element, který má fokus klávesnice, <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastaven na `true` .  Statická vlastnost <xref:System.Windows.Input.Keyboard.FocusedElement%2A> <xref:System.Windows.Input.Keyboard> třídy Získá prvek, který aktuálně má fokus klávesnice.  
  
 Aby element získal fokus klávesnice, <xref:System.Windows.UIElement.Focusable%2A> <xref:System.Windows.UIElement.IsVisible%2A> musí být vlastnosti a vlastností základních prvků nastaveny na `true` .  Některé třídy, jako je <xref:System.Windows.Controls.Panel> základní třída, jsou <xref:System.Windows.UIElement.Focusable%2A> nastaveny na `false` výchozí hodnoty. proto je nutné nastavit na hodnotu, <xref:System.Windows.UIElement.Focusable%2A> `true` Pokud chcete, aby takový prvek mohl získat fokus klávesnice.  
  
 Fokus klávesnice lze získat prostřednictvím interakce s uživatelem s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jako je například procházení tabulátorem k elementu nebo kliknutí myší na určité prvky.  Fokus klávesnice lze také získat programově pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metody <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A>Metoda se pokusí předat fokus na klávesnici zadaného elementu.  Vrácený element je prvek, který má fokus klávesnice, což může být jiný element, než je požadováno, pokud starý nebo nový objekt fokus zablokuje požadavek.  
  
 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> metodu pro nastavení fokusu klávesnice na <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>Vlastnost u tříd základních prvků získá hodnotu, která označuje, zda má prvek fokus klávesnice.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>Vlastnost u tříd základních prvků získá hodnotu, která označuje, zda má element nebo kterýkoli z jeho prvků vizuálu fokus na klávesnici.  
  
 Při nastavování počátečního fokusu při spuštění aplikace musí být element pro příjem fokus ve vizuálním stromu počátečního okna načteného aplikací a element musí mít <xref:System.Windows.UIElement.Focusable%2A> a <xref:System.Windows.UIElement.IsVisible%2A> nastaven na `true` .  Doporučeným místem pro nastavení prvotního zaměření je <xref:System.Windows.FrameworkElement.Loaded> obslužná rutina události.  <xref:System.Windows.Threading.Dispatcher>Zpětné volání lze také použít voláním <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Logický fokus  
 Logický fokus odkazuje na <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokusu.  Rozsah fokusu je prvek, který uchovává sledování v <xref:System.Windows.Input.FocusManager.FocusedElement%2A> rámci jeho oboru.  Když fokus klávesnice opustí rozsah fokusu, bude mít fokus na klávesnici fokus, ale zachová se tak logický fokus.  Když se fokus klávesnice vrátí do oboru fokusu, fokus získá fokus klávesnice.  To umožňuje měnit fokus klávesnice mezi více rozsahy fokusu, ale zajišťuje, že element s fokusem v oboru fokusu znovu získá fokus klávesnice, když se fokus vrátí do oboru fokusu.  
  
 V aplikaci může být více elementů, které mají logický fokus, ale může existovat pouze jeden prvek, který má logický fokus v rámci konkrétního oboru fokusu.  
  
 Element, který má fokus klávesnice, má logický fokus pro rozsah fokusu, ke kterému patří.  
  
 Element může být převeden do oboru fokusu v rámci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením <xref:System.Windows.Input.FocusManager> připojené vlastnosti <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> na `true` .  V kódu může být element převeden do oboru fokusu voláním <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> .  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.StackPanel> do oboru fokus nastavením <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> připojené vlastnosti.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>Vrátí rozsah fokusu pro zadaný element.  
  
 Třídy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ve kterých jsou standardně zaměřeny <xref:System.Windows.Window> na rozsahy, jsou, <xref:System.Windows.Controls.MenuItem> , <xref:System.Windows.Controls.ToolBar> a <xref:System.Windows.Controls.ContextMenu> .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>získá fokus elementu pro zadaný obor fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>nastaví fokus elementu v zadaném oboru fokusu.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>se obvykle používá k nastavení prvotního prvku s fokusem.  
  
 Následující příklad nastaví prioritní element v oboru fokusu a získá element s fokusem oboru fokusu.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Navigace s použitím klávesnice  
 <xref:System.Windows.Input.KeyboardNavigation>Třída zodpovídá za implementaci výchozí navigace fokusu klávesnice při stisknutí některého z navigačních kláves.  Navigační klíče jsou: TAB, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, disšipka, DOWNARROW, LEFTARROW a RIGHTARROW Keys.  
  
 Navigační chování kontejneru navigace lze změnit nastavením připojených <xref:System.Windows.Input.KeyboardNavigation> vlastností <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> , <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> a <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> .  Tyto vlastnosti jsou typu <xref:System.Windows.Input.KeyboardNavigationMode> a možné hodnoty jsou <xref:System.Windows.Input.KeyboardNavigationMode.Continue> ,,, <xref:System.Windows.Input.KeyboardNavigationMode.Local> <xref:System.Windows.Input.KeyboardNavigationMode.Contained> , a <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once> <xref:System.Windows.Input.KeyboardNavigationMode.None> .  Výchozí hodnota je <xref:System.Windows.Input.KeyboardNavigationMode.Continue> , což znamená, že prvek není navigační kontejner.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> s několika <xref:System.Windows.Controls.MenuItem> objekty.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>Připojená vlastnost je nastavena na hodnotu <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> v <xref:System.Windows.Controls.Menu> .  Když se fokus změní pomocí klávesy TAB v rámci <xref:System.Windows.Controls.Menu> , fokus se přesune z každého prvku a když se poslední prvek dosáhne fokusu, vrátí se k prvnímu prvku.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Programové procházení fokusu  
 Další rozhraní API pro práci s fokusem jsou <xref:System.Windows.UIElement.MoveFocus%2A> a <xref:System.Windows.UIElement.PredictFocus%2A> .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>změní fokus na další prvek v aplikaci.  <xref:System.Windows.Input.TraversalRequest>Slouží k určení směru.   <xref:System.Windows.Input.FocusNavigationDirection>Předaný do <xref:System.Windows.UIElement.MoveFocus%2A> Určuje, že lze přesunout fokus různých směrů, například <xref:System.Windows.Input.FocusNavigationDirection.First> , <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> a <xref:System.Windows.Input.FocusNavigationDirection.Down> .  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.MoveFocus%2A> ke změně elementu s fokusem.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>Vrátí objekt, který získá fokus, pokud se má změnit zaměření.  V současné době <xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left> <xref:System.Windows.Input.FocusNavigationDirection.Right> jsou podporovány pouze,, a <xref:System.Windows.FrameworkElement.PredictFocus%2A> .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Události fokusu  
 Události týkající se fokusu klávesnice jsou <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> , <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> a <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> .  Události jsou definovány jako připojené události <xref:System.Windows.Input.Keyboard> třídy, ale jsou snadněji přístupné jako ekvivalentní směrované události na základních třídách prvků.  Další informace o událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>je vyvolána, když prvek získá fokus klávesnice.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>je vyvolána, když prvek ztratí fokus klávesnice.  Pokud <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> je událost nebo <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> událost zpracována a <xref:System.Windows.RoutedEventArgs.Handled%2A> je nastavena na `true` , pak se fokus nezmění.  
  
 Následující příklad připojí <xref:System.Windows.UIElement.GotKeyboardFocus> <xref:System.Windows.UIElement.LostKeyboardFocus> obslužné rutiny události a <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Když se <xref:System.Windows.Controls.TextBox> fokus klávesnice získá, změní se <xref:System.Windows.Controls.Control.Background%2A> vlastnost na <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Media.Brushes.LightBlue%2A> .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Při <xref:System.Windows.Controls.TextBox> ztrátě fokusu klávesnice se <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> změní zpět na bílou.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Události související s logickým fokusem jsou <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> .  Tyto události jsou definovány <xref:System.Windows.Input.FocusManager> jako připojené události, ale <xref:System.Windows.Input.FocusManager> nezveřejňují obálky událostí CLR.  <xref:System.Windows.UIElement>a <xref:System.Windows.ContentElement> vystavte tyto události pohodlnější.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Přehled vstupu](input-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
