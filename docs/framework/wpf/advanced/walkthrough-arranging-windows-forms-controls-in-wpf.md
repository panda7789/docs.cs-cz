---
title: "Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF"
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
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f78da83657c4c1bd913f67c9e612264cc5dbdf99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF
Tento postup vám ukáže, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce rozložení uspořádat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikace.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Pomocí výchozího nastavení rozložení.  
  
-   Nastavení velikosti obsahu.  
  
-   Pomocí absolutní umístění.  
  
-   Určení velikosti explicitně.  
  
-   Nastavení vlastností rozložení.  
  
-   Principy pořadí z-order omezení.  
  
-   Ukotvení.  
  
-   Nastavení viditelnosti.  
  
-   Hostování ovládacího prvku, který není funkce stretch.  
  
-   Škálování.  
  
-   Otáčení.  
  
-   Nastavení odsazení a okraje.  
  
-   Použití dynamické rozložení kontejnerů.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [uspořádání ovládacích prvků Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Po dokončení bude mít k pochopení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikací.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu  
  
1.  Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Dvakrát klikněte na MainWindow.xaml a otevře se v zobrazení jazyka XAML.  
  
4.  V <xref:System.Windows.Window> elementu, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  V <xref:System.Windows.Controls.Grid> element sadu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost `true` a definovat pět řádků a tři sloupce.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Pomocí výchozího nastavení rozložení  
 Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává rozložení pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-use-default-layout-settings"></a>Chcete-li použít výchozí nastavení rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Zobrazí ovládací prvek v <xref:System.Windows.Controls.Canvas>. Je velikost hostované ovládacího prvku, na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je dimenzovány pro zvládnutí hostovaného ovládacího prvku.  
  
## <a name="sizing-to-content"></a>Nastavení velikosti obsahu  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajišťuje, že je správně zobrazit jeho obsah velikost hostované ovládacího prvku.  
  
#### <a name="to-size-to-content"></a>Velikost obsahu  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Jsou dvě nové ovládací prvky tlačítko dimenzované k zobrazení delší textového řetězce a zvětšení velikosti písma správně a <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou možnosti změnit velikost elementů zohlednit hostované ovládací prvky.  
  
## <a name="using-absolute-positioning"></a>Pomocí absolutní umístění  
 Absolutní umístění můžete použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> element kdekoli v uživatelském rozhraní (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Chcete-li použít absolutní umístění  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je umístěn 20 pixelů z na horní straně buňky mřížky a 20 pixelů od levého okraje.  
  
## <a name="specifying-size-explicitly"></a>Určení velikosti explicitně  
 Můžete zadat velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pomocí <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.  
  
#### <a name="to-specify-size-explicitly"></a>Chcete-li explicitně určit velikost  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je nastavena velikost 50 × široké 70 pixelů vysoké, což je menší než výchozí nastavení rozložení. Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je přeskupení odpovídajícím způsobem.  
  
## <a name="setting-layout-properties"></a>Nastavení vlastností rozložení  
 Vždy nastavit vlastnosti související s rozložením na hostované ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Nastavení vlastností rozložení přímo na hostované ovládací prvek předá neočekávaným výsledkům.  
  
 Nastavit vlastnosti související s rozložením hostované ovládacího prvku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Chcete-li zobrazit důsledky nastavení vlastnosti na hostované ovládací prvek  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  V Průzkumníku řešení klikněte dvakrát na MainWindow.xaml. vb nebo MainWindow.xaml.cs a otevře se v editoru kódu.  
  
3.  Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
5.  Klikněte **klikněte na tlačítko mi** tlačítko. `button1_Click` Sady obslužné rutiny událostí <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> vlastností hostovaného prvku. To způsobí, že hostovaný ovládací prvek změnit jejich umístění v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Hostitel udržuje stejné oblasti obrazovky, ale je oříznut hostovaného ovládacího prvku. Místo toho by měla vždycky vyplnění hostovaného ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
## <a name="understanding-z-order-limitations"></a>Seznámení s omezeními pořadí Z-Order  
 Ve výchozím nastavení viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy jsou vždy vykreslován nad dalších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky a nejsou ovlivněny pořadí z-order. Chcete-li povolit pořadí z-ordering, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-default-z-order-behavior"></a>Chcete-li zobrazit výchozí chování pořadí z-order  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Vymalovávání elementu přes do elementu label.  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a>Chcete-li zobrazit pořadí z-order chování, pokud IsRedirected hodnotu true  
  
1.  Nahradí předchozí příklad pořadí z-order následující XAML.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     Stisknutím klávesy F5 sestavení a spuštění aplikace. Do elementu label se vykresluje přes <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
## <a name="docking"></a>Ukotvení  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>element podporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení. Nastavte <xref:System.Windows.Controls.DockPanel.Dock%2A> přidružená vlastnost chcete ukotvit hostované ovládacího prvku <xref:System.Windows.Controls.DockPanel> elementu.  
  
#### <a name="to-dock-a-hosted-control"></a>Chcete-li ukotvit hostované ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element ukotven na pravé straně <xref:System.Windows.Controls.DockPanel> elementu.  
  
## <a name="setting-visibility"></a>Nastavení viditelnosti  
 Můžete provést vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení neviditelná nebo sbalit nastavením <xref:System.Windows.UIElement.Visibility%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Když je ovládací prvek neviditelná, se nezobrazí, ale zabírá prostor rozložení. Když ovládacího prvku sbalena, se nezobrazí, ani nemá zabírají prostor rozložení.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Chcete-li nastavit viditelnost hostované ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
4.  Klikněte na tlačítko **kliknutím na nastavit jako neviditelné** tlačítko, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element neviditelná.  
  
5.  Klikněte na tlačítko **kliknutím sbalit** tlačítko skrýt <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z rozložení úplně. Když [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení sbalena, okolního elementy jsou změněno tak, aby zabíral jeho místa.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který není funkce Stretch  
 Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky s pevnou velikostí mají a není roztáhnou tak, aby vyplnil celou dostupné místo v rozložení. Například <xref:System.Windows.Forms.MonthCalendar> zobrazí měsíce v pevné mezery.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>K hostování ovládacího prvku, který není funkce stretch  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je umístěn na střed v řádku mřížky, ale není roztažen tak, aby vyplňování dostupného místa. Pokud je okno dostatečně velké na to, uvidíte dvě nebo více měsíců zobrazuje hostované <xref:System.Windows.Forms.MonthCalendar> řízení, ale ty se na v řádku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modul rozložení centra prvky, které nemůže být dimenzovány pro vyplňování dostupného místa.  
  
## <a name="scaling"></a>Změna měřítka  
 Na rozdíl od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, většina [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nejsou nepřetržitě škálovatelné. Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element škáluje jeho hostované řízení, pokud je to možné.  Chcete-li povolit plnohodnotný škálování, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Škálování hostované ovládacího prvku pomocí výchozí chování  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované ovládací prvek a jeho okolního elementy jsou škálovat faktorem 0,5. Však není škálovat písma hostované ovládacího prvku.  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a>Škálování ovládacího prvku hostované nastavením IsRedirected na hodnotu true  
  
1.  Nahradí předchozí příklad škálování následující XAML.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované řízení, jeho okolního elementy a hostované ovládacího prvku písma jsou škálovat faktorem 0,5.  
  
## <a name="rotating"></a>Otáčení  
 Na rozdíl od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporuje otočení. Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element není otočit s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků při otočení transformací. Jakoukoli jinou hodnotu než 180 stupňů vyvolá otočení <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událostí.  Pokud chcete povolit, otáčení libovolném úhlu, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Pokud chcete vidět otočení v hybridní aplikace  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované ovládací prvek není otáčet, ale jeho elementy okolního jsou otáčet o úhel 180 stupňů. Možná budete muset změnit velikost okna zobrazíte elementy.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a>Pokud chcete vidět otočení v hybridní aplikace, pokud IsRedirected hodnotu true  
  
1.  Předchozí příklad otočení nahradí následující XAML.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Hostované ovládacího prvku otočen.  Všimněte si, že <xref:System.Windows.Media.RotateTransform.Angle%2A> může být nastavena na jakoukoli hodnotu. Možná budete muset změnit velikost okna zobrazíte elementy.  
  
## <a name="setting-padding-and-margins"></a>Nastavení odsazení a okraje  
 Odsazení a okraje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení jsou podobné odsazení a okraje v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Jednoduše nastavit <xref:System.Windows.Controls.Control.Padding%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Nastavení odsazení a okrajů pro hostované ovládací prvek  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Stisknutím klávesy F5 sestavení a spuštění aplikace. Nastavení odsazení a okrajů se použijí k hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejným způsobem, že by bylo možné provést v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Použití kontejnerů dynamické rozložení  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]poskytuje dvě dynamické rozložení kontejnery <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>. Můžete také použít tyto kontejnery v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Použít kontejner dynamické rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Přidejte volání `InitializeFlowLayoutPanel` metoda v konstruktoru.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Stisknutím klávesy F5 sestavení a spuštění aplikace. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element doplní <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízených ovládacích prvků ve výchozí <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Důležité informace o rozložení pro WindowsFormsHost Element](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Uspořádání Windows Forms – ovládací prvky v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
