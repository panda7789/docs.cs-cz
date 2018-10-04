---
title: 'Návod: Připojení k datům v hybridních aplikacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 7128b23790588a604989cb18918a7a7e8b598191
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584192"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Návod: Připojení k datům v hybridních aplikacích
Vytvoření vazby zdroje dat k ovládacímu prvku je zásadní pro zároveň uživatelům poskytují přístup k podkladová data, ať používáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tento návod ukazuje, jak můžete datové vazby v hybridních aplikacích, které zahrnují oba [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření projektu.  
  
-   Definice šablony.  
  
-   Určení rozložení formuláře.  
  
-   Určení datové vazby.  
  
-   Zobrazení dat s využitím vzájemná spolupráce grafického subsystému.  
  
-   Přidání zdroje dat do projektu.  
  
-   Vytvoření vazby ke zdroji dat.  
  
 Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [datové vazby v ukázkové aplikace hybridní](https://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Až budete hotovi, budete mít znalost funkcí datové vazby v hybridních aplikacích.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio.  
  
-   Přístup k ukázkové databázi Northwind a systémem Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>K vytvoření a nastavení projektu  
  
1.  Vytvoření projektu aplikace WPF s názvem `WPFWithWFAndDatabinding`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  V <xref:System.Windows.Window> prvku, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oborů názvů.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Pojmenujte výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením <xref:System.Windows.FrameworkElement.Name%2A> vlastnost.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Definování šablon dat  
 Zobrazí se seznam zákazníků v <xref:System.Windows.Controls.ListBox> ovládacího prvku. Následující příklad kódu definuje <xref:System.Windows.DataTemplate> objekt s názvem `ListItemsTemplate` , která řídí vizuálního stromu <xref:System.Windows.Controls.ListBox> ovládacího prvku. To <xref:System.Windows.DataTemplate> je přiřazen <xref:System.Windows.Controls.ListBox> ovládacího prvku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost.  
  
#### <a name="to-define-the-data-template"></a>Definování šablon dat  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Určení rozložení formuláře  
 Rozložení formuláře je definována grid se třemi řádky a tři sloupce. <xref:System.Windows.Controls.Label> ovládací prvky jsou k dispozici k identifikaci jednotlivých sloupců v tabulce Zákazníci.  
  
#### <a name="to-set-up-the-grid-layout"></a>Nastavit rozložení mřížky  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Nastavit ovládací prvky popisku  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Určení datové vazby  
 Zobrazí se seznam zákazníků v <xref:System.Windows.Controls.ListBox> ovládacího prvku. Připojený `ListItemsTemplate` vytvoří vazbu <xref:System.Windows.Controls.TextBlock> ovládací prvek `ContactName` pole z databáze.  
  
 Podrobnosti o jednotlivých záznam zákazníka se zobrazují v několika <xref:System.Windows.Controls.TextBox> ovládacích prvků.  
  
#### <a name="to-specify-data-bindings"></a>Chcete-li určit datové vazby  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.  
  
     <xref:System.Windows.Data.Binding> Třídy vytvoří vazbu <xref:System.Windows.Controls.TextBox> ovládacích prvků na odpovídající pole v databázi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Zobrazení dat s využitím vzájemná spolupráce grafického subsystému  
 Zobrazení objednávek odpovídající k vybranému zákazníkovi v <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> ovládací prvek s názvem `dataGridView1`. `dataGridView1` Ovládací prvek vázán na zdroj dat v souboru kódu na pozadí. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je nadřazeného tohoto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>Zobrazení dat v ovládacím prvku DataGridView  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Přidání zdroje dat do projektu  
 Pomocí sady Visual Studio můžete snadno přidat zdroj dat do projektu. Tento postup přidá silně typované datové sady do vašeho projektu. Přidají také několik jiných tříd podpory, jako jsou adaptéry tabulek pro jednotlivé vybrané tabulky.  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
1.  Z **Data** nabídce vyberte možnost **přidat nový zdroj dat**.  
  
2.  V **Průvodce konfigurací zdroje dat**, vytvořit připojení k databázi Northwind pomocí datové sady. Další informace najdete v tématu [postupy: připojení k datům v databázi](https://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Po zobrazení výzvy **Průvodce konfigurací zdroje dat**, uložit připojovací řetězec jako `NorthwindConnectionString`.  
  
4.  Po zobrazení výzvy zvolte vaše databázové objekty, vyberte `Customers` a `Orders` tabulky a název generovaný sady dat `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Vytvoření vazby ke zdroji dat.  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Součást poskytuje jednotné rozhraní pro zdroj dat aplikace. Vazby ke zdroji dat je implementováno v souboru kódu na pozadí.  
  
#### <a name="to-bind-to-the-data-source"></a>K vytvoření vazby ke zdroji dat.  
  
1.  Otevřete soubor kódu na pozadí, který se nazývá soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs.  
  
2.  Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     Tento kód deklaruje <xref:System.Windows.Forms.BindingSource> komponenty a přidružené pomocné třídy, které se připojují k databázi.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3.  Zkopírujte následující kód do konstruktoru.

     Tento kód vytvoří a inicializuje <xref:System.Windows.Forms.BindingSource> komponenty.

     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4.  Otevřete soubor MainWindow.xaml.

5.  V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window> elementu.

6.  V okně Vlastnosti klikněte na tlačítko **události** kartu.

7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.

8.  Zkopírujte následující kód do <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.

     Tento kód přiřadí <xref:System.Windows.Forms.BindingSource> komponenty jako kontext dat a naplní `Customers` a `Orders` adaptér objekty.

     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Zkopírujte následující kód do `MainWindow` definici třídy.

     Tato metoda obsluhuje <xref:System.Windows.Data.CollectionView.CurrentChanged> událostí a aktualizuje aktuální položky datové vazby.

     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Datové vazby v ukázce hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=159983)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
