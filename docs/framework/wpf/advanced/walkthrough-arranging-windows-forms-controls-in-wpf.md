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
ms.openlocfilehash: 484895db539b288bf388ff6c2ce3c29db55080b1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197839"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF

V tomto návodu se dozvíte, jak používat funkce rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k uspořádání [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikaci.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt.
- Používá se výchozí nastavení rozložení.
- Změna velikosti obsahu.
- Použití absolutního umístění.
- Explicitní určení velikosti
- Nastavení vlastností rozložení.
- Porozumění omezením pořadí vykreslování.
- Ukotvení.
- Nastavení viditelnosti.
- Hostování ovládacího prvku, který se nepřizpůsobuje.
- Změně.
- Otočné.
- Nastavení odsazení a okrajů
- Použití kontejnerů dynamického rozložení.

Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete v tématu [uspořádání model Windows Formsch ovládacích prvků v UKÁZCE WPF](https://go.microsoft.com/fwlink/?LinkID=159971).

Až budete hotovi, budete obeznámeni s funkcemi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení v aplikacích založených na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="creating-the-project"></a>Vytvoření projektu

Chcete-li vytvořit a nastavit projekt, postupujte podle následujících kroků:

1. Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.

2. V Průzkumník řešení přidejte odkazy na následující sestavení:

    - WindowsFormsIntegration
    - System. Windows. Forms
    - System. Drawing

3. Poklikejte na *MainWindow. XAML* a otevře se v zobrazení XAML.

4. V elementu <xref:System.Windows.Window> přidejte následující mapování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] oboru názvů.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. V prvku <xref:System.Windows.Controls.Grid> nastavte vlastnost <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na hodnotu `true` a definujte pět řádků a tři sloupce.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Použití výchozího nastavení rozložení

Ve výchozím nastavení prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> zpracovává rozložení pro hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek.

Chcete-li použít výchozí nastavení rozložení, postupujte podle následujících kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. V <xref:System.Windows.Controls.Canvas>se zobrazí ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>. Hostovaný ovládací prvek má velikost na základě jeho obsahu a prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> má velikost pro přizpůsobení hostovaného ovládacího prvku.

## <a name="sizing-to-content"></a>Změna velikosti obsahu

Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zajišťuje, že hostovaný ovládací prvek má velikost pro správné zobrazení obsahu.

Chcete-li nastavit velikost obsahu, postupujte podle těchto kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Dva nové ovládací prvky tlačítka mají velikost pro zobrazení delšího textového řetězce a větší velikosti písma a prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou změněna tak, aby vyhovovaly hostovaným ovládacím prvkům.

## <a name="using-absolute-positioning"></a>Použití absolutního umístění

Absolutní umístění lze použít k umístění elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> kdekoli v uživatelském rozhraní (UI).

Chcete-li použít absolutní umístění, postupujte podle následujících kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je umístěn 20 pixelů od horní strany buňky mřížky a 20 pixelů vlevo.

## <a name="specifying-size-explicitly"></a>Explicitní určení velikosti

Můžete určit velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu pomocí vlastností <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.

Pokud chcete určit velikost explicitně, postupujte takto:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> je nastaven na velikost 50 pixelů v šířce až 70 pixelů vysoké, což je menší než výchozí nastavení rozložení. Obsah ovládacího prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se odpovídajícím způsobem změní.

## <a name="setting-layout-properties"></a>Nastavení vlastností rozložení

V hostovaném ovládacím prvku vždy nastavte vlastnosti související s rozložením pomocí vlastností elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Nastavení vlastností rozložení přímo v hostovaném ovládacím prvku bude vracet neočekávané výsledky.

 Nastavení vlastností souvisejících s rozložením u hostovaného ovládacího prvku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.

Chcete-li zobrazit účinky nastavení vlastností u hostovaného ovládacího prvku, postupujte takto:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. V **Průzkumník řešení**poklikejte na *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs* a otevře se v editoru kódu.

3. Zkopírujte následující kód do definice třídy `MainWindow`:

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.

5. Klikněte na tlačítko **klepnutím na tlačítko** . Obslužná rutina události `button1_Click` nastaví vlastnosti <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> v hostovaném ovládacím prvku. Tím dojde k přemístění hostovaného ovládacího prvku v rámci elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Hostitel udržuje stejnou oblast obrazovky, ale hostovaný ovládací prvek je oříznutý. Místo toho by měl hostovaný ovládací prvek vždy vyplnit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.

## <a name="understanding-z-order-limitations"></a>Porozumění omezením pořadí vykreslování

Viditelné prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou vždy vykresleny nad ostatními prvky WPF a nejsou ovlivněny pořadím z. Chcete-li zobrazit toto chování z pořadí vykreslování, postupujte následovně:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je vykreslen nad prvkem Label.

## <a name="docking"></a>Ukotvení

element <xref:System.Windows.Forms.Integration.WindowsFormsHost> podporuje ukotvení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nastavte vlastnost <xref:System.Windows.Controls.DockPanel.Dock%2A> připojeno k ukotvení hostovaného ovládacího prvku v <xref:System.Windows.Controls.DockPanel> elementu.

Pro ukotvení hostovaného ovládacího prvku postupujte takto:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je ukotven na pravé straně elementu <xref:System.Windows.Controls.DockPanel>.

## <a name="setting-visibility"></a>Nastavení viditelnosti

Ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] můžete skrýt nebo ho sbalit nastavením vlastnosti <xref:System.Windows.UIElement.Visibility%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Když je ovládací prvek neviditelný, není zobrazený, ale zabírá prostor rozložení. Když je ovládací prvek sbalen, není zobrazen, ani nevyužívá prostor rozložení.

Chcete-li nastavit viditelnost hostovaného ovládacího prvku, použijte následující postup:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. V souboru *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*zkopírujte následující kód do definice třídy:

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.

4. Kliknutím na tlačítko **pro vytvoření neviditelného** tlačítka nastavíte prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> neviditelný.

5. Kliknutím na tlačítko **sbalit lze sbalit** skrýt prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> z rozložení zcela. Když je ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sbalený, okolní prvky jsou přeuspořádány tak, aby zabíraly místo.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který se roztáhne

Některé ovládací prvky [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mají pevnou velikost a nelze je roztáhnout, aby vyplnily dostupné místo v rozložení. Například ovládací prvek <xref:System.Windows.Forms.MonthCalendar> zobrazuje měsíc v pevném prostoru.

Chcete-li hostovat ovládací prvek, který se nepřizpůsobuje, postupujte podle následujících kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> je zarovnán na střed řádku gridu, ale není roztažen tak, aby vyplnil dostupné místo. Pokud je okno dostatečně velké, může se zobrazit dva nebo více měsíců zobrazených v ovládacím prvku Hosted <xref:System.Windows.Forms.MonthCalendar>, ale jsou umístěny na střed na řádku. Modul rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Centruje prvky, jejichž velikost nelze měnit, aby vyplnila dostupný prostor.

## <a name="scaling"></a>Změně

Na rozdíl od prvků WPF, většina model Windows Formsch ovládacích prvků není nepřetržitě škálovatelná. Chcete-li zajistit vlastní škálování, přepište metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.

Chcete-li škálovat hostovaný ovládací prvek pomocí výchozího chování, postupujte následovně:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Hostovaný ovládací prvek a jeho okolní prvky se škálují podle faktoru 0,5. Písmo hostovaného ovládacího prvku však není škálované.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Otočné

Na rozdíl od prvků WPF ovládací prvky model Windows Forms nepodporují otočení. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> se při použití transformace rotace neotáčí s jinými prvky WPF. Jakákoli hodnota rotace kromě 180 stupňů vyvolá událost <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.

Pokud chcete zobrazit efekt otočení v hybridní aplikaci, postupujte podle těchto kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Hostovaný ovládací prvek není otočen, ale jeho okolní prvky jsou otočeny o úhel 180 stupňů. Možná budete muset změnit velikost okna, aby se zobrazily elementy.

## <a name="setting-padding-and-margins"></a>Nastavení odsazení a okrajů

Odsazení a okraje v rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou podobné odsazení a okraje v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Jednoduše nastavte <xref:System.Windows.Controls.Control.Padding%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Margin%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

Chcete-li nastavit odsazení a okraje pro hostovaný ovládací prvek, postupujte podle následujících kroků:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. Nastavení odsazení a okraj se aplikují na ovládací prvky hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] stejným způsobem jako při použití v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="using-dynamic-layout-containers"></a>Použití kontejnerů dynamického rozložení

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] poskytuje dva kontejnery dynamického rozložení, <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>. Tyto kontejnery můžete použít také v rozloženích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Chcete-li použít dynamický kontejner rozložení, použijte následující postup:

1. Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. V souboru *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*zkopírujte následující kód do definice třídy:

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Přidejte volání metody `InitializeFlowLayoutPanel` v konstruktoru:

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> element vyplní <xref:System.Windows.Controls.DockPanel>a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízené ovládací prvky ve výchozím <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Předpoklady rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Uspořádání ovládacích prvků model Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
