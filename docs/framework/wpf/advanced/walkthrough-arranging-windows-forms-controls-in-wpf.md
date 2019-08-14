---
title: 'Návod: Uspořádání ovládacích prvků Windows Forms ve WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972308"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Návod: Uspořádání ovládacích prvků Windows Forms ve WPF

V tomto návodu se dozvíte, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak používat funkce rozložení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] k uspořádání ovládacích prvků v hybridní aplikaci.

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

Až budete hotovi, budete mít přehled o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] funkcích rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacích založených na aplikaci.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1. Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.

2. V Průzkumník řešení přidejte odkazy na následující sestavení.

    - WindowsFormsIntegration

    - System.Windows.Forms

    - System. Drawing

3. Poklikejte na MainWindow. XAML a otevře se v zobrazení XAML.

4. V elementu přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. V elementu nastavte vlastnost na `true` a definujte pět řádků a tři sloupce. <xref:System.Windows.Controls.Grid.ShowGridLines%2A> <xref:System.Windows.Controls.Grid>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Použití výchozího nastavení rozložení

Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek zpracovává rozložení pro hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek.

### <a name="to-use-default-layout-settings"></a>Použití výchozího nastavení rozložení

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Ovládací prvek se zobrazí v <xref:System.Windows.Controls.Canvas>. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Hostovaný ovládací prvek má velikost na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element má velikost pro přizpůsobení hostovaného ovládacího prvku.

## <a name="sizing-to-content"></a>Změna velikosti obsahu

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajistí, že hostovaný ovládací prvek má velikost pro správné zobrazení obsahu.

### <a name="to-size-to-content"></a>Chcete-li nastavit velikost obsahu

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Dva nové ovládací prvky tlačítka mají velikost pro zobrazení delšího textového řetězce a větší velikosti písma a <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou změněna tak, aby vyhovovaly hostovaným ovládacím prvkům.

## <a name="using-absolute-positioning"></a>Použití absolutního umístění

Absolutní umístění lze použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu kdekoli v uživatelském rozhraní (UI).

### <a name="to-use-absolute-positioning"></a>Použití absolutního umístění

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je umístěn 20 pixelů od horní strany buňky mřížky a 20 pixelů zleva.

## <a name="specifying-size-explicitly"></a>Explicitní určení velikosti

Můžete určit velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.FrameworkElement.Width%2A> pomocí vlastností a <xref:System.Windows.FrameworkElement.Height%2A> .

### <a name="to-specify-size-explicitly"></a>Explicitní určení velikosti

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je nastaven na velikost 50 pixelů v šířce až 70 pixelů vysoké, což je menší než výchozí nastavení rozložení. Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku se odpovídajícím způsobem změní.

## <a name="setting-layout-properties"></a>Nastavení vlastností rozložení

V hostovaném ovládacím prvku vždy nastavte vlastnosti související s rozložením pomocí vlastností <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Nastavení vlastností rozložení přímo v hostovaném ovládacím prvku bude vracet neočekávané výsledky.

 Nastavení vlastností souvisejících s rozložením v hostovaném ovládacím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvku v nemá žádný vliv.

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Postup zobrazení efektů nastavení vlastností u hostovaného ovládacího prvku

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. V Průzkumník řešení dvakrát klikněte na MainWindow. XAML. vb nebo MainWindow.xaml.cs jej otevřete v editoru kódu.

3. Zkopírujte následující kód do `MainWindow` definice třídy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.

5. Klikněte na tlačítko **klepnutím na tlačítko** . Obslužná rutina <xref:System.Windows.Forms.Control.Top%2A>událostinastaví vlastnosti <xref:System.Windows.Forms.Control.Left%2A> a u hostovaného ovládacího prvku. `button1_Click` Tím dojde k přemístění hostovaného ovládacího prvku v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Hostitel udržuje stejnou oblast obrazovky, ale hostovaný ovládací prvek je oříznutý. Místo toho by měl hostovaný ovládací prvek vždy vyplnit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.

## <a name="understanding-z-order-limitations"></a>Porozumění omezením pořadí vykreslování

Viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou vždy vykresleny nad ostatními prvky WPF a nejsou ovlivněny pořadím z. Chcete-li zobrazit toto chování z pořadí vykreslování, postupujte následovně:

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je vykreslen nad prvkem popisku.

## <a name="docking"></a>Ukotvení

<xref:System.Windows.Forms.Integration.WindowsFormsHost>prvek podporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení. Nastavte připojenou vlastnost pro ukotvení hostovaného ovládacího prvku <xref:System.Windows.Controls.DockPanel> v elementu. <xref:System.Windows.Controls.DockPanel.Dock%2A>

### <a name="to-dock-a-hosted-control"></a>Ukotvení hostovaného ovládacího prvku

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Prvek je ukotven na pravé straně <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="setting-visibility"></a>Nastavení viditelnosti

Můžete nastavit, aby [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] byl ovládací prvek neviditelný nebo sbalen, <xref:System.Windows.UIElement.Visibility%2A> nastavením vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku. Když je ovládací prvek neviditelný, není zobrazený, ale zabírá prostor rozložení. Když je ovládací prvek sbalen, není zobrazen, ani nevyužívá prostor rozložení.

### <a name="to-set-the-visibility-of-a-hosted-control"></a>Nastavení viditelnosti hostovaného ovládacího prvku

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.

4. Klikněte na tlačítko **kliknutím a vytvořte neviditelné** tlačítko, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby se element neviditelní.

5. Kliknutím na tlačítko **sbalit pro sbalení** zcela skryjete <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek z rozložení. Když je [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek sbalen, okolní prvky jsou přeuspořádány tak, aby zabíraly místo.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který se roztáhne

Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají pevnou velikost a nelze je roztáhnout, aby vyplnily dostupné místo v rozložení. Například <xref:System.Windows.Forms.MonthCalendar> ovládací prvek zobrazuje měsíc v pevném prostoru.

### <a name="to-host-a-control-that-does-not-stretch"></a>Hostování ovládacího prvku, který se roztáhne

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je zarovnán na střed řádku mřížky, ale není roztažen tak, aby vyplnil dostupné místo. Pokud je okno dostatečně velké, může se zobrazit dva nebo více měsíců zobrazených v hostovaném <xref:System.Windows.Forms.MonthCalendar> ovládacím prvku, ale tyto řádky jsou zarovnány na střed. Modul [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení vycentruje prvky, jejichž velikost nelze měnit, aby vyplnila dostupný prostor.

## <a name="scaling"></a>Škálování

Na rozdíl od prvků WPF, většina model Windows Formsch ovládacích prvků není nepřetržitě škálovatelná. Chcete-li zajistit vlastní škálování, přepište <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metodu.

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Škálování hostovaného ovládacího prvku pomocí výchozího chování

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Hostovaný ovládací prvek a jeho okolní prvky se škálují podle faktoru 0,5. Písmo hostovaného ovládacího prvku však není škálované.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Otočné

Na rozdíl od prvků WPF ovládací prvky model Windows Forms nepodporují otočení. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element se při použití transformace rotace neotáčí s jinými prvky WPF. Jakákoli hodnota rotace s <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> výjimkou 180 stupňů vyvolá událost.

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Zobrazení efektu rotace v hybridní aplikaci

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Hostovaný ovládací prvek není otočen, ale jeho okolní prvky jsou otočeny o úhel 180 stupňů. Možná budete muset změnit velikost okna, aby se zobrazily elementy.

## <a name="setting-padding-and-margins"></a>Nastavení odsazení a okrajů

Odsazení a okraje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení se podobají odsazení a okrajům v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Jednoduše nastavte <xref:System.Windows.Controls.Control.Padding%2A> vlastnosti a <xref:System.Windows.FrameworkElement.Margin%2A> u <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku.

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Nastavení odsazení a okrajů pro hostovaný ovládací prvek

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Nastavení odsazení a okraj se aplikují na hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejným způsobem jako při použití v. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]

## <a name="using-dynamic-layout-containers"></a>Použití kontejnerů dynamického rozložení

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]poskytuje dva kontejnery <xref:System.Windows.Forms.FlowLayoutPanel> dynamického rozložení a <xref:System.Windows.Forms.TableLayoutPanel>. Tyto kontejnery můžete také použít v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozloženích.

### <a name="to-use-a-dynamic-layout-container"></a>Použití dynamického kontejneru rozložení

1. Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Přidejte volání `InitializeFlowLayoutPanel` metody v konstruktoru.

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Stisknutím klávesy F5 Sestavte a spusťte aplikaci. Element vyplní a uspořádá<xref:System.Windows.Forms.FlowLayoutPanel> své podřízené ovládací prvky ve výchozím nastavení <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>. <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Controls.DockPanel>

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Předpoklady rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Uspořádání ovládacích prvků model Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Návod: Hostování model Windows Forms složeného ovládacího prvku v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
