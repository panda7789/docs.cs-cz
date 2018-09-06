---
title: 'Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 98b108be518a9fef03ee299d43ed591cf736f68f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786080"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF
Tento návod ukazuje, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí rozložení uspořádat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikaci.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu.  
  
-   Pomocí výchozího nastavení rozložení.  
  
-   Nastavení velikosti obsahu.  
  
-   Použití absolutní pozici.  
  
-   Určení velikosti explicitně.  
  
-   Nastavení vlastnosti rozložení.  
  
-   Principy omezení pořadí vykreslování.  
  
-   Ukotvení.  
  
-   Nastavení viditelnosti.  
  
-   Hostování ovládacího prvku, který není stretch.  
  
-   Škálování.  
  
-   Otáčení.  
  
-   Nastavení odsazení a okraje.  
  
-   Použití dynamického rozložení kontejnerů.  
  
 Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [uspořádání prvky Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971).  
  
 Až budete hotovi, budete mít znalost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení funkce v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>K vytvoření a nastavení projektu  
  
1.  Vytvoření projektu aplikace WPF s názvem `WpfLayoutHostingWf`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  Poklikejte na soubor MainWindow.xaml a otevřete ho v XAML zobrazení.  
  
4.  V <xref:System.Windows.Window> prvku, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  V <xref:System.Windows.Controls.Grid> set elementu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost `true` a definování pěti řádky a tři sloupce.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Pomocí výchozího nastavení rozložení  
 Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává rozložení pro hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-use-default-layout-settings"></a>Chcete-li použít výchozí nastavení rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Ovládací prvek zobrazí <xref:System.Windows.Controls.Canvas>. Hostovaného ovládacího prvku je velikost na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je dimenzovány pro zvládnutí hostovaného ovládacího prvku.  
  
## <a name="sizing-to-content"></a>Nastavení velikosti obsahu  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajišťuje, že je správně zobrazit jeho obsah velikost hostované ovládacího prvku.  
  
#### <a name="to-size-to-content"></a>Pro nastavení velikosti obsahu  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. Pro zobrazení delšího textový řetězec a větší velikost písma správně, je velikost dva nové ovládací prvky tlačítka a <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou velikost hostované ovládací prvky.  
  
## <a name="using-absolute-positioning"></a>Použití absolutní pozici  
 Absolutní umístění můžete použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek kdekoli v uživatelském rozhraní (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Chcete-li použít absolutní pozici  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nachází 20 pixelů v horním rohu buňky mřížky a 20 pixelů od levého okraje.  
  
## <a name="specifying-size-explicitly"></a>Explicitní určení velikosti  
 Můžete zadat velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> pomocí elementu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.  
  
#### <a name="to-specify-size-explicitly"></a>Chcete-li explicitně určit velikost  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je nastaven na velikost 50 pixelů na šířku a 70 pixelů na výšku, které je menší než nastavení výchozí rozložení. Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je odpovídajícím způsobem měnit.  
  
## <a name="setting-layout-properties"></a>Nastavení vlastnosti rozložení  
 Vždy nastavit vlastnosti související s rozložením hostovaného ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Nastavení vlastností rozložení přímo na hostovaného ovládacího prvku poskytne neočekávané výsledky.  
  
 Nastavení vlastností související s rozložením hostovaného ovládacího prvku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Abyste viděli efekt nastavování vlastností na hostovaného ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  V Průzkumníku řešení poklikejte na soubor MainWindow.xaml. vb nebo MainWindow.xaml.cs ho otevřete v editoru kódu.  
  
3.  Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
5.  Klikněte na tlačítko **klikněte na mě** tlačítko. `button1_Click` Sady obslužné rutiny události <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> vlastnosti hostovaného ovládacího prvku. To způsobí, že hostovaný ovládací prvek změnit umístění v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Hostitel udržuje stejné oblasti obrazovky, ale oříznut hostovaného ovládacího prvku. Místo toho by měla vždy zaplnit hostovaného ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
## <a name="understanding-z-order-limitations"></a>Principy omezení pořadí vykreslování  
 Viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou vždy vykreslován nad další prvky WPF a jsou ovlivněny pořadí vykreslování. Pokud chcete zobrazit toto chování pořadí vykreslování, postupujte takto:

1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Nad prvkem popisek vymalovávání elementu.  


## <a name="docking"></a>Ukotvení  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> podporuje prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení. Nastavit <xref:System.Windows.Controls.DockPanel.Dock%2A> přidružená vlastnost ukotvení hostované ovládacího prvku <xref:System.Windows.Controls.DockPanel> elementu.  
  
#### <a name="to-dock-a-hosted-control"></a>Chcete-li ukotvit hostovaného ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek ukotven k pravému okraji <xref:System.Windows.Controls.DockPanel> elementu.  
  
## <a name="setting-visibility"></a>Nastavení viditelnosti  
 Můžete provést vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídit neviditelný nebo sbalit nastavením <xref:System.Windows.UIElement.Visibility%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Když je ovládací prvek neviditelné, se nezobrazí, ale zabírá místo rozložení. Když je sbalen ovládací prvek, se nezobrazí ani nemá zabírat místo rozložení.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Chcete-li nastavit, zda se hostovaného ovládacího prvku  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
4.  Klikněte na tlačítko **kliknutím skrytí** tlačítka <xref:System.Windows.Forms.Integration.WindowsFormsHost> element neviditelné.  
  
5.  Klikněte na tlačítko **kliknutím sbalte** tlačítko skrýt <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z rozložení úplně. Když [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je sbalen ovládací prvek, okolního prvky jsou změnit jejich uspořádání tak, aby obsadily své místo.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který není Stretch  
 Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají pevnou velikost a ne roztáhnout tak, aby vyplnil dostupné místo v rozložení. Například <xref:System.Windows.Forms.MonthCalendar> ovládací prvek zobrazí v pevná mezera za měsíc.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>K hostování ovládacího prvku, který není stretch  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je uprostřed řádku mřížky, ale ta není roztažená tak, aby vyplnil dostupné místo. Pokud okna je příliš velká, může se zobrazit dvě nebo víc měsíců zobrazený hostovanou <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku, ale ty se na v řádku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modul rozložení centra pro prvky, které nelze mít velikost tak, aby vyplnil dostupné místo.  
  
## <a name="scaling"></a>Škálování  
 Na rozdíl od prvků WPF nejsou průběžně škálovatelné většina ovládacích prvků Windows Forms. Pokud chcete zadat vlastní škálování, přepíšete <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody. 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Škálování hostovaného ovládacího prvku s použitím výchozí chování  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. Hostovaného ovládacího prvku a jeho okolního prvky jsou měřítkem řídit 0,5. Však není škálovat písma hostovaného ovládacího prvku.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Otáčení  
 Na rozdíl od WPF elementů ovládacích prvků Windows Forms nepodporují otočení. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element není s jinými prvky WPF otočí, když je použita transformace otočení. Jakoukoli otočení jinou hodnotu než vyvolá 180stupňový rozsah s orientací <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událostí.
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>A vidět její účinek otáčení v hybridní aplikaci  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. Otočen hostovaného ovládacího prvku, ale jeho okolního prvky jsou otočit o úhel 180 stupňů. Budete muset změnit velikost okna zobrazení prvků.  
 

## <a name="setting-padding-and-margins"></a>Nastavení odsazení a okraje  
 Odsazení a okrajů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení jsou podobné odsazení a okraje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Stačí nastavit <xref:System.Windows.Controls.Control.Padding%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Nastavte odsazení a okrajů pro hostované ovládací prvek  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. Použijí se nastavení odsazení a okraj na hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejně, jako by být použity v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Pomocí kontejnerů dynamické rozložení  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] poskytuje dva kontejnery dynamického rozložení, <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>. Můžete také použít tyto kontejnery v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Použití kontejneru dynamické rozložení  
  
1.  Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Přidejte volání `InitializeFlowLayoutPanel` metoda v konstruktoru.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Stisknutím klávesy F5 sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek vyplní <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízených ovládacích prvků ve výchozím <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Předpoklady rozložení pro element WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Uspořádání Windows Forms ovládací prvky v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
