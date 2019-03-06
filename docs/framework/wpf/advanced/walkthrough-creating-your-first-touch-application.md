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
ms.openlocfilehash: 2ebf22775ab9308bc896829be0b4e8cc147a3b4c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374151"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Návod: Vytvoření první aplikace
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje aplikacím na dotykového ovládání. Například můžete pracovat s aplikací pomocí jedné nebo více prsty na dotyk zařízení, např. k tomu dotykovou obrazovku tento návod vytvoří aplikaci, která umožňuje uživateli přesunutí, změna velikosti nebo otočení jednoho objektu pomocí touch.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio.  
  
-   Zařízení, která přijímá dotykové ovládání, jako je například k tomu dotykovou obrazovku, který podporuje Windows Touch.  
  
 Kromě toho byste měli mít základní znalosti o tom, jak vytvořit aplikaci v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména jak přihlásit k odběru a zpracovat události. Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Vytvoření aplikace  
  
#### <a name="to-create-the-application"></a>Vytvoření aplikace  
  
1.  Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem `BasicManipulation`. Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
2.  Obsah souboru MainWindow.xaml nahraďte následující XAML.  
  
     Tento kód vytvoří jednoduchou aplikaci, která obsahuje červený <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Vlastnost <xref:System.Windows.Shapes.Rectangle> je nastavena na hodnotu true, tak, aby obdrží manipulace s událostmi. Aplikace se přihlásí k odběru <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, a <xref:System.Windows.UIElement.ManipulationInertiaStarting> události. Tyto události obsahují logiku pro přesun <xref:System.Windows.Shapes.Rectangle> když uživatel manipuluje s ním.  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Pokud používáte Visual Basic v prvním řádku souboru mainwindow.XAML, nahraďte `x:Class="BasicManipulation.MainWindow"` s `x:Class="MainWindow"`.  
  
4.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationStarting> obslužné rutiny události.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Dojde k události při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zjistí, že touch vstup začne pracovat s objektu. Kód určuje, že pozice manipulace by měl být vzhledem k <xref:System.Windows.Window> nastavením <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.Input.ManipulationDelta> obslužné rutiny události.

     <xref:System.Windows.Input.ManipulationDelta> Události dojde, když dotykem vstup změny pozice a může dojít k více než jednou při manipulaci s. Události může také dojít v případě prstem je vyvolána. Například, pokud uživatel přetáhne prstem obrazovce <xref:System.Windows.Input.ManipulationDelta> více než jednou jako přesune prstem dojde k události. Pokud uživatel prstem na obrazovce, <xref:System.Windows.Input.ManipulationDelta> udržuje pro simulaci nečinnost výskytu události.

     Kód se vztahuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> k <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> ji přesunout, jak uživatel přesouvá dotykem vstup. Také zkontroluje, zda <xref:System.Windows.Shapes.Rectangle> je mimo hranice <xref:System.Windows.Window> při výskytu události při nečinnosti. Pokud ano, aplikace volá <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metoda end manipulaci.

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6.  V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationInertiaStarting> obslužné rutiny události.

     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když uživatel vyvolá všechny prsty na obrazovce. Kód nastaví počáteční a zpomalení přesunu, rozšíření a otočení obdélníku.

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7.  Sestavte a spusťte projekt.

     Měli byste vidět v okně se zobrazí červený čtvereček.

## <a name="testing-the-application"></a>Testování aplikace
 K otestování aplikace, zkuste následující manipulací. Všimněte si, že můžete provést více než jednu z následujících akcí ve stejnou dobu.

-   Přesunout <xref:System.Windows.Shapes.Rectangle>, umístí prstem <xref:System.Windows.Shapes.Rectangle> a napříč obrazovkou se pohybují prstu.

-   Pro změnu velikosti <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a přesunout prsty blíže společně nebo jsou od sebe navzájem.

-   Obměna <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a otočení prsty kolem sebe navzájem.

 Způsobit nečinnost, rychle zvýšit prsty na obrazovce při provádění předchozího manipulací. <xref:System.Windows.Shapes.Rectangle> Budou i nadále přesunutí, změna velikosti nebo otočení na několik sekund, než přestane.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>