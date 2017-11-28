---
title: "Přehled fokusu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4e10f7136b636829f99da34388db7676810cd06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="focus-overview"></a>Přehled fokusu
V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existují dvě hlavní koncepty, které se týkají fokus: fokus a logické fokus klávesnice.  Fokus klávesnice vztahuje k elementu, který přijímá vstup z klávesnice a logické fokus odkazuje na element v fokus obor, který má právě fokus.  Tyto koncepty jsou podrobněji v tomto přehledu.  Vysvětlení rozdílu v tyto koncepty je důležité pro vytvoření složitých aplikací, které mají více oblastech, kde lze získat fokus.  
  
 Hlavní třídy, které jsou součástí správy fokus <xref:System.Windows.Input.Keyboard> třídy, <xref:System.Windows.Input.FocusManager> třídy a prvku základní třídy, jako <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>.  Další informace o základní prvky najdete v tématu [základní přehled elementy](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  
  
 <xref:System.Windows.Input.Keyboard> Třídy se týká především fokus klávesnice a <xref:System.Windows.Input.FocusManager> se zajímají hlavně logické fokus, ale nejedná se o absolutní odlišení.  Element, který má právě fokus klávesnice, bude mít i logické fokus, ale element, který má právě fokus logické nemá nutně fokus klávesnice.  Toto je zřejmá při použití <xref:System.Windows.Input.Keyboard> třída elementu, který má fokus klávesnice pro ni nastavit také nastaví logické fokus na elementu.  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Fokus klávesnice  
 Fokus klávesnice odkazuje na element, který je aktuálně přijímá vstup z klávesnice.  Může existovat pouze jeden element celkově plochy, který má právě fokus klávesnice.  V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bude mít elementu, který má právě fokus klávesnice <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> nastavena na `true`.  Statické vlastnosti <xref:System.Windows.Input.Keyboard.FocusedElement%2A> na <xref:System.Windows.Input.Keyboard> třída získá elementu, který má právě fokus klávesnice.  
  
 V pořadí pro daný element získat fokus klávesnice <xref:System.Windows.UIElement.Focusable%2A> a <xref:System.Windows.UIElement.IsVisible%2A> vlastnosti na základní elementy musí být nastavena na `true`.  Některé třídy, jako <xref:System.Windows.Controls.Panel> základní třídy, mít <xref:System.Windows.UIElement.Focusable%2A> nastavena na `false` ve výchozím nastavení; proto musíte nastavit <xref:System.Windows.UIElement.Focusable%2A> k `true` Pokud chcete mít možnost získat fokus klávesnice takový prvek.  
  
 Nelze získat fokus klávesnice prostřednictvím interakce uživatele s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jako jsou například pomocí klávesy tabulátor do elementu nebo kliknutím na tlačítko myši na některé prvky.  Fokus klávesnice jsou k dispozici prostřednictvím kódu programu pomocí <xref:System.Windows.Input.Keyboard.Focus%2A> metodu <xref:System.Windows.Input.Keyboard> třídy.  <xref:System.Windows.Input.Keyboard.Focus%2A> Metoda se pokusí předat fokus klávesnice zadaný element.  Vrácený element je element, který má fokus klávesnice, což může být element jiný než požadováno, pokud buď staré nebo nové zaměřit bloku object žádosti.  
  
 Následující příklad používá <xref:System.Windows.Input.Keyboard.Focus%2A> metodu a nastavit fokus klávesnice na <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Vlastnost třídy base element získá hodnotu označující, zda má element fokus klávesnice.  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Vlastnost třídy base element získá hodnotu označující, zda element nebo kterékoli z jeho visual podřízené elementy má fokus klávesnice.  
  
 Při nastavování počáteční fokus při spuštění aplikace, elementu, který chcete získat fokus musí být ve vizuální strojové struktuře okna počáteční načíst aplikací a musí mít element <xref:System.Windows.UIElement.Focusable%2A> a <xref:System.Windows.UIElement.IsVisible%2A> nastavena na `true`.  Je doporučené místo na nastavit počáteční fokus <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  A <xref:System.Windows.Threading.Dispatcher> zpětného volání lze také voláním <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Logické fokusu  
 Logické fokus odkazuje <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> v oboru fokus.  Fokus obor je element, který sleduje <xref:System.Windows.Input.FocusManager.FocusedElement%2A> ve svém oboru.  Když fokus klávesnice opustí obor fokus, cílených elementu dojde ke ztrátě fokus klávesnice, ale zachovají logické fokus.  Když se fokus klávesnice vrátí do oboru fokus, bude cílených element získat fokus klávesnice.  To umožňuje fokus klávesnice změnit mezi více obory fokus, ale zajišťuje, že cílených element v oboru fokus získal fokus klávesnice když se fokus vrátí do oboru fokus.  
  
 Může být více elementů, které mají logické fokusu v aplikaci, ale může existovat pouze jeden element, který má právě fokus logické v konkrétní výběr oboru.  
  
 Element, který má právě fokus klávesnice, má logické fokus, které patří do oboru fokus.  
  
 Element mohou být změněny na obor fokusu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nastavením <xref:System.Windows.Input.FocusManager> přidružená vlastnost <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> k `true`.  V kódu element mohou být změněny na obor fokus voláním <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.StackPanel> do oboru fokus nastavením <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> přidružená vlastnost.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>Vrátí fokus rozsah pro zadaný element.  
  
 Třídy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] který jsou obory fokus ve výchozím nastavení jsou <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, a <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>Získá cílených element pro obor zadaný fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>Nastaví cílených element v oboru zadaný fokus.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>se obvykle používá k nastavení počátečního cílených elementu.  
  
 Následující příklad nastaví element cílených na obor fokus a získá cílených elementu obor fokus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Navigace pomocí klávesnice  
 <xref:System.Windows.Input.KeyboardNavigation> Třída je odpovědná za implementace navigační fokus klávesnice výchozí při stisknutí jeden z klíčů navigace.  Navigační klávesy, jsou: karta, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, UPARROW, DOWNARROW, šipka vlevo a šipka vpravo klíče.  
  
 Navigační chování navigační kontejner může změnit nastavení připojený <xref:System.Windows.Input.KeyboardNavigation> vlastnosti <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, a <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Tyto vlastnosti jsou typu <xref:System.Windows.Input.KeyboardNavigationMode> a možné hodnoty jsou <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, a <xref:System.Windows.Input.KeyboardNavigationMode.None>.  Výchozí hodnota je <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, což znamená, že element není kontejner navigace.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> s počtem <xref:System.Windows.Controls.MenuItem> objekty.  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> Je připojená vlastnost nastavená na <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> na <xref:System.Windows.Controls.Menu>.  Při změně fokus pomocí klávesy tab v rámci <xref:System.Windows.Controls.Menu>, fokus přesune z každého prvku a když je dosaženo posledním elementem fokus vrátí do první prvek.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Navigace fokus prostřednictvím kódu programu  
 Další [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pro práci s fokus jsou <xref:System.Windows.UIElement.MoveFocus%2A> a <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>změny fokus na další prvek v aplikaci.  A <xref:System.Windows.Input.TraversalRequest> slouží k určení směru.   <xref:System.Windows.Input.FocusNavigationDirection> Předaný <xref:System.Windows.UIElement.MoveFocus%2A> Určuje jinou pokynů fokus lze přesunout, například <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> a <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.MoveFocus%2A> změnit cílených elementu.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>Vrátí objekt, který by získat fokus, kdyby se musí změnit fokus.  V současné době pouze <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, a <xref:System.Windows.Input.FocusNavigationDirection.Right> podporuje <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Fokus události  
 Události související s fokus klávesnice jsou <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> a <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Události jsou definované jako připojené události na <xref:System.Windows.Input.Keyboard> třídy, ale jsou více snadno přístupné jako ekvivalentní směrované události na třídy base element.  Další informace o událostech, najdete v článku [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>se vyvolá, když elementu získává fokus klávesnice.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>se vyvolá, když element ztratí fokus klávesnice.  Pokud <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> události nebo <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> událost je zpracovávána a <xref:System.Windows.RoutedEventArgs.Handled%2A> je nastaven na `true`, pak se fokus nedojde ke změně.  
  
 Následující příklad připojí <xref:System.Windows.UIElement.GotKeyboardFocus> a <xref:System.Windows.UIElement.LostKeyboardFocus> obslužných rutin událostí pro <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Když <xref:System.Windows.Controls.TextBox> získá fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> se změní na <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Když <xref:System.Windows.Controls.TextBox> ztratí fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.TextBox> se změní zpět na prázdné.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Události související s logické fokus jsou <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.  Tyto události jsou definovány na <xref:System.Windows.Input.FocusManager> jako připojené události, ale <xref:System.Windows.Input.FocusManager> nevystavuje obálky události CLR.  <xref:System.Windows.UIElement>a <xref:System.Windows.ContentElement> snadněji vystavit tyto události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [Vstupní – přehled](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled základní prvky](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
