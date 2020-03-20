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
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186671"
---
# <a name="focus-overview"></a>Přehled fokusu
V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existují dva hlavní pojmy, které se připojou k zaměření: fokus klávesnice a logické zaměření.  Fokus klávesnice odkazuje na prvek, který přijímá vstup z klávesnice a logické fokus odkazuje na prvek v oboru fokus, který má fokus.  Tyto koncepty jsou podrobně popsány v tomto přehledu.  Pochopení rozdílu v těchto konceptech je důležité pro vytváření složitých aplikací, které mají více oblastí, kde lze získat fokus.  
  
 Hlavní třídy, které se <xref:System.Windows.Input.Keyboard> účastní správy <xref:System.Windows.Input.FocusManager> fokusu jsou třídy, <xref:System.Windows.UIElement> třídy a základní element třídy, například a <xref:System.Windows.ContentElement>.  Další informace o základních prvcích naleznete v přehledu [základních prvků](base-elements-overview.md).  
  
 Třída <xref:System.Windows.Input.Keyboard> se zabývá především fokusem <xref:System.Windows.Input.FocusManager> klávesnice a zabývá se především logickým zaměřením, ale to není absolutní rozdíl.  Prvek, který má fokus klávesnice bude mít také logické fokus, ale prvek, který má logické fokus nemusí mít nutně fokus klávesnice.  To je zřejmé, <xref:System.Windows.Input.Keyboard> když použijete třídu k nastavení prvku, který má fokus klávesnice, pro také nastaví logické zaměření na prvek.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Fokus klávesnice  
 Fokus klávesnice odkazuje na prvek, který právě přijímá vstup z klávesnice.  Na celé ploše může být pouze jeden prvek, který má fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], prvek, který má <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> fokus klávesnice bude mít nastavena na `true`.  Statická <xref:System.Windows.Input.Keyboard.FocusedElement%2A> vlastnost <xref:System.Windows.Input.Keyboard> ve třídě získá prvek, který má aktuálně fokus klávesnice.  
  
 Aby prvek získal fokus klávesnice, <xref:System.Windows.UIElement.Focusable%2A> musí <xref:System.Windows.UIElement.IsVisible%2A> být vlastnosti a na `true`základních prvcích nastaveny na .  Některé třídy, <xref:System.Windows.Controls.Panel> například základní <xref:System.Windows.UIElement.Focusable%2A> třída, mají `false` nastaveny ve výchozím nastavení; proto je nutné <xref:System.Windows.UIElement.Focusable%2A> `true` nastavit, pokud chcete, aby takový prvek bylo možné získat fokus klávesnice.  
  
 Fokus klávesnice lze získat prostřednictvím interakce uživatele s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jako je například tabulátorem na prvek nebo kliknutím myši na určité prvky.  Fokus klávesnice lze také získat programově <xref:System.Windows.Input.Keyboard.Focus%2A> pomocí <xref:System.Windows.Input.Keyboard> metody na třídu.  Metoda <xref:System.Windows.Input.Keyboard.Focus%2A> se pokusí dát zadaný prvek fokus klávesnice.  Vrácený prvek je prvek, který má fokus klávesnice, což může být jiný prvek, než je požadováno, pokud buď starý nebo nový objekt fokus blokovat požadavek.  
  
 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> metodu k nastavení <xref:System.Windows.Controls.Button>fokusu klávesnice na .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Vlastnost <xref:System.Windows.UIElement.IsKeyboardFocused%2A> na třídy základní prvek získá hodnotu označující, zda prvek má fokus klávesnice.  Vlastnost <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> na třídy základní prvek získá hodnotu označující, zda prvek nebo některý z jeho vizuální podřízené prvky má fokus klávesnice.  
  
 Při nastavování počáteční fokus při spuštění aplikace prvek přijímat fokus musí být ve vizuálním <xref:System.Windows.UIElement.Focusable%2A> stromu počáteční okno načtené aplikací a prvek musí mít a <xref:System.Windows.UIElement.IsVisible%2A> nastavena na `true`.  Doporučené místo pro nastavení počátečního <xref:System.Windows.FrameworkElement.Loaded> zaostření je v obslužné rutině události.  Zpětné <xref:System.Windows.Threading.Dispatcher> volání lze také použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>voláním nebo .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Logické zaměření  
 Logické zaměření odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> na v oboru fokus.  Obor fokus je prvek, který <xref:System.Windows.Input.FocusManager.FocusedElement%2A> sleduje v rámci jeho oboru.  Když fokus klávesnice opustí obor fokusu, zaostřený prvek ztratí fokus klávesnice, ale zachová logické fokus.  Když se fokus klávesnice vrátí do oboru fokus, prvek zaměření získá fokus klávesnice.  To umožňuje fokus klávesnice změnit mezi více oborů fokus, ale zajišťuje, že prvek zaměření v oboru fokus znovu fokus klávesnice při fokus vrátí do oboru fokus.  
  
 Může existovat více prvků, které mají logické zaměření v aplikaci, ale může existovat pouze jeden prvek, který má logické zaměření v oboru určité fokus.  
  
 Prvek, který má fokus klávesnice má logické fokus pro obor fokus, do kterého patří.  
  
 Prvek lze převést na obor [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fokus <xref:System.Windows.Input.FocusManager> v <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> nastavení `true`připojené vlastnosti na .  V kódu prvek lze převést na obor <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>fokus voláním .  
  
 Následující příklad provede <xref:System.Windows.Controls.StackPanel> do oboru fokus <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> nastavením připojené vlastnosti.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>vrátí obor fokusu pro zadaný prvek.  
  
 Třídy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve kterých jsou <xref:System.Windows.Window> <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Controls.ToolBar>výchozím nastavení obory fokusu, jsou , , a <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>získá cílený prvek pro zadaný obor fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>nastaví zaostřený prvek v zadaném oboru fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>obvykle slouží k nastavení počáteční hozamovaný prvek.  
  
 Následující příklad nastaví prvek zaměření na obor fokus a získá cílený prvek oboru fokus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Navigace s použitím klávesnice  
 Třída <xref:System.Windows.Input.KeyboardNavigation> je zodpovědná za implementaci výchozí navigace fokusu klávesnice při stisknutí jedné z navigačních kláves.  Navigační klávesy jsou: klávesy TAB, SHIFT+TAB, CTRL+TAB, CTRL+SHIFT+TAB, UPARROW, DOWNARROW, LEFTARROW a RIGHTARROW.  
  
 Chování navigace navigačního kontejneru lze změnit nastavením <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>připojených <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation> vlastností , a .  Tyto vlastnosti <xref:System.Windows.Input.KeyboardNavigationMode> jsou typu a <xref:System.Windows.Input.KeyboardNavigationMode.Continue> <xref:System.Windows.Input.KeyboardNavigationMode.Local>možné <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>hodnoty <xref:System.Windows.Input.KeyboardNavigationMode.Once>jsou <xref:System.Windows.Input.KeyboardNavigationMode.None>, , , , a .  Výchozí hodnota <xref:System.Windows.Input.KeyboardNavigationMode.Continue>je , což znamená, že prvek není navigační kontejner.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> s počtem <xref:System.Windows.Controls.MenuItem> objektů.  Připojená <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> vlastnost je <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> nastavena <xref:System.Windows.Controls.Menu>na .  Při změně fokusu pomocí klávesy tab v rámci <xref:System.Windows.Controls.Menu>aplikace se fokus přesune z každého prvku a při dosažení posledního prvku se fokus vrátí k prvnímu prvku.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Programové navigování fokusu  
 Další rozhraní API pro <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A>práci s fokusem jsou a .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>změní zaměření na další prvek v aplikaci.  A <xref:System.Windows.Input.TraversalRequest> se používá k určení směru.   <xref:System.Windows.Input.FocusNavigationDirection> Předaný <xref:System.Windows.UIElement.MoveFocus%2A> určuje různé směry fokus lze <xref:System.Windows.Input.FocusNavigationDirection.First>přesunout, například , <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> a <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Následující příklad <xref:System.Windows.FrameworkElement.MoveFocus%2A> používá ke změně prvku cíle.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>vrátí objekt, který by získal fokus, pokud by se mělo změnit fokus.  V současné <xref:System.Windows.Input.FocusNavigationDirection.Up>době <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left>je <xref:System.Windows.Input.FocusNavigationDirection.Right> podporována <xref:System.Windows.FrameworkElement.PredictFocus%2A>pouze , , , a jsou podporovány .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Události fokusu  
 Události související s fokusem <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>klávesnice jsou <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>a <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> , .  Události jsou definovány jako připojené <xref:System.Windows.Input.Keyboard> události ve třídě, ale jsou snadněji přístupné jako ekvivalentní směrované události na třídy základní prvek.  Další informace o událostech naleznete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>je aktivována, když prvek získá fokus klávesnice.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>je aktivována, když prvek ztratí fokus klávesnice.  Pokud <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> je událost <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> nebo událost <xref:System.Windows.RoutedEventArgs.Handled%2A> zpracována `true`a je nastavena na , fokus se nezmění.  
  
 Následující příklad připojí <xref:System.Windows.UIElement.GotKeyboardFocus> <xref:System.Windows.UIElement.LostKeyboardFocus> a obslužné rutiny událostí na <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Když <xref:System.Windows.Controls.TextBox> získá fokus klávesnice, <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> je <xref:System.Windows.Media.Brushes.LightBlue%2A>změněn na .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Když <xref:System.Windows.Controls.TextBox> ztratí fokus klávesnice, <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> je změněn zpět na bílou.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Události související s logickým zaměřením jsou <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.  Tyto události jsou <xref:System.Windows.Input.FocusManager> definovány na jako <xref:System.Windows.Input.FocusManager> připojené události, ale nezveřejňuje obálky událostí CLR.  <xref:System.Windows.UIElement>a <xref:System.Windows.ContentElement> vystavit tyto události pohodlněji.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Přehled vstupu](input-overview.md)
- [Přehled základních elementů](base-elements-overview.md)
