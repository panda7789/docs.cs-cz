---
title: 'Návod: Vytvoření první aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548348"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Návod: Vytvoření první aplikace
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje aplikacím reagovat na touch. Například můžete pracovat s aplikací pomocí jedné nebo více prsty, které na zařízení touch-velká a malá písmena, například dotykovou obrazovku tento návod vytvoří aplikaci, která umožňuje uživatelům přesunout, změnit velikost nebo otočení jednoho objektu pomocí touch.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Zařízení, které přijímá touch vstupu, například dotykovou obrazovku, který podporuje Windows Touch.  
  
 Kromě toho musí mít základní znalosti o tom, jak vytvořit aplikaci v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména jak se přihlásit k odběru a zpracování události. Další informace najdete v tématu [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Vytvoření aplikace  
  
#### <a name="to-create-the-application"></a>K vytvoření aplikace  
  
1.  Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `BasicManipulation`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Nahraďte obsah MainWindow.xaml následující XAML.  
  
     Tento kód vytvoří jednoduchou aplikaci, která obsahuje zobrazí červený <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Vlastnost <xref:System.Windows.Shapes.Rectangle> je nastaven na hodnotu true, aby ho přijme zpracování události. Aplikace se přihlásí k odběru <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, a <xref:System.Windows.UIElement.ManipulationInertiaStarting> události. Tyto události obsahují logiku pro přesun <xref:System.Windows.Shapes.Rectangle> když uživatel manipuluje ho.  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="BasicManipulation.MainWindow"` s `x:Class="MainWindow"`.  
  
4.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationStarting> obslužné rutiny události.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Dojde k události při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zjistí, že touch vstup začne pracovat s objekt. Kód určuje, že pozice manipulaci by měl být vzhledem k <xref:System.Windows.Window> nastavením <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.Input.ManipulationDelta> obslužné rutiny události.  
  
     <xref:System.Windows.Input.ManipulationDelta> Události dojde, když stiskem vstupní pozice změny a dochází při manipulaci s více než jednou. Události může dojít také po se vyvolá prstu. Pokud uživatel nastavuje tažením prstem napříč na obrazovce, například <xref:System.Windows.Input.ManipulationDelta> vícekrát jako přesune prstem dojde k události. Když uživatel vyvolá prstem na obrazovce, <xref:System.Windows.Input.ManipulationDelta> vyskytuje opakovaně událostí k simulaci nečinnosti.  
  
     Kód se vztahuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> k <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> ho přesunout, protože uživatel přesune touch vstup. Je také zkontroluje, zda <xref:System.Windows.Shapes.Rectangle> je mimo hranice <xref:System.Windows.Window> když dojde k události při nečinnosti. Pokud ano, aplikace volá <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metoda na konec manipulaci.  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationInertiaStarting> obslužné rutiny události.  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když uživatel vyvolá všech prstů na obrazovce. Kód nastaví počáteční rychlost a zpomalení přesun, rozšíření a oběh rámeček.  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  Sestavte a spusťte projekt.  
  
     Měli byste vidět červený čtvereček se zobrazí v okně.  
  
## <a name="testing-the-application"></a>Testování aplikace  
 K testování aplikace, zkuste následující manipulace. Všimněte si, že můžete provést více než jednu z těchto ve stejnou dobu.  
  
-   Přesunout <xref:System.Windows.Shapes.Rectangle>, umístí prstem <xref:System.Windows.Shapes.Rectangle> a přesuňte prstu po obrazovce.  
  
-   Ke změně velikosti <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a přesunout prsty blíže společně nebo dále vedle sebe navzájem.  
  
-   Obměna <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a otočit prsty kolem navzájem.  
  
 Chcete-li způsobit nečinnosti, rychle zvýšit prsty z obrazovky provádět předchozí manipulace. <xref:System.Windows.Shapes.Rectangle> Budou nadále přesunout, změnit velikost nebo otočit na několik sekund, než se zastavuje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
