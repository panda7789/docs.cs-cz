---
title: "Návod: Připojení k datům v hybridních aplikacích"
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
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1348f3a57dd04d58298c9746b74a7c3a1baf30c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Návod: Připojení k datům v hybridních aplikacích
Vytvoření vazby zdroje dat k ovládacímu prvku je nezbytné pro poskytuje uživatelům přístup k základní data, zda používáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tento návod ukazuje, jak můžete pomocí datové vazby v hybridní aplikace, které zahrnují oba [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Definování dat šablony.  
  
-   Určení rozložení formuláře.  
  
-   Zadání dat vazby.  
  
-   Zobrazení dat pomocí vzájemná spolupráce.  
  
-   Přidání zdroje dat do projektu.  
  
-   Vazba ke zdroji dat.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [datové vazby v ukázce hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Jakmile budete hotovi, budete mít k pochopení funkce vazby dat v hybridní aplikace.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Přístup k ukázková databáze Northwind systémem Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu  
  
1.  Vytvořte projekt aplikace WPF s názvem `WPFWithWFAndDatabinding`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otevřete MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  V <xref:System.Windows.Window> elementu, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování obory názvů.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Název výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením <xref:System.Windows.FrameworkElement.Name%2A> vlastnost.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Definování dat šablony  
 Hlavní seznamu zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacího prvku. Následující příklad kódu definuje <xref:System.Windows.DataTemplate> objekt s názvem `ListItemsTemplate` která řídí stromu visual <xref:System.Windows.Controls.ListBox> ovládacího prvku. To <xref:System.Windows.DataTemplate> je přiřazena k <xref:System.Windows.Controls.ListBox> ovládacího prvku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost.  
  
#### <a name="to-define-the-data-template"></a>Definování šablon dat  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Určení rozložení formuláře  
 Rozložení formuláře je definována mřížka s tři řádky a tři sloupce. <xref:System.Windows.Controls.Label>ovládací prvky jsou k dispozici k identifikaci každý sloupec v tabulce Zákazníci.  
  
#### <a name="to-set-up-the-grid-layout"></a>Nastavit rozložení mřížky  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Nastavit ovládací prvky popisek  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Určení datové vazby  
 Hlavní seznamu zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacího prvku. Připojený `ListItemsTemplate` váže <xref:System.Windows.Controls.TextBlock> řídit k `ContactName` pole z databáze.  
  
 Podrobnosti o všech vybraných záznamech zákazníka se zobrazují v několika <xref:System.Windows.Controls.TextBox> ovládací prvky.  
  
#### <a name="to-specify-data-bindings"></a>Chcete-li určit datové vazby  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.  
  
     <xref:System.Windows.Data.Binding> Třídy vazby <xref:System.Windows.Controls.TextBox> ovládacích prvků na odpovídající pole v databázi.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Zobrazení dat pomocí vzájemná spolupráce  
 Objednávky odpovídající vybraného zákazníka se zobrazují v <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> ovládací prvek s názvem `dataGridView1`. `dataGridView1` Ovládací prvek vázán ke zdroji dat v souboru kódu na pozadí. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je nadřazený tohoto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>K zobrazení dat v ovládacím prvku DataGridView  
  
-   Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Přidání zdroje dat do projektu  
 S [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], můžete snadno přidat zdroje dat do projektu. Tento postup přidá silného typu datové sady do projektu. Také se přidají několik jiné třídy, které podporují, jako je například adaptéry tabulek pro každou z vybrané tabulky.  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
1.  Z **Data** nabídce vyberte možnost **přidat nový zdroj dat**.  
  
2.  V **Průvodce konfigurací zdroje dat**, vytvořit připojení k databázi Northwind pomocí datové sady. Další informace najdete v tématu [postupy: připojování k datům v databázi](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Po zobrazení výzvy pomocí **Průvodce konfigurací zdroje dat**, uložit připojovací řetězec jako `NorthwindConnectionString`.  
  
4.  Po zobrazení výzvy zvolte databázové objekty, vyberte `Customers` a `Orders` tabulky a název generované datové sady `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Vytvoření vazby ke zdroji dat  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Součást poskytuje jednotné rozhraní pro zdroj dat aplikace. Vazba ke zdroji dat je implementovaná v souboru kódu na pozadí.  
  
#### <a name="to-bind-to-the-data-source"></a>Při vytváření vazby ke zdroji dat  
  
1.  Otevřete soubor kódu, který se nazývá MainWindow.xaml.vb nebo MainWindow.xaml.cs.  
  
2.  Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     Tento kód deklaruje <xref:System.Windows.Forms.BindingSource> součásti a přidružené pomocných tříd, které se připojují k databázi.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Zkopírujte následující kód do konstruktoru.  
  
     Tento kód vytvoří a inicializuje <xref:System.Windows.Forms.BindingSource> součásti.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  Open MainWindow.xaml.  
  
5.  V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.  
  
6.  V okně vlastností klikněte **události** kartě.  
  
7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
8.  Zkopírujte následující kód do <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  
  
     Tento kód přiřadí <xref:System.Windows.Forms.BindingSource> součásti jako kontextu dat a naplní `Customers` a `Orders` adaptér objekty.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Zkopírujte následující kód do `MainWindow` definici třídy.  
  
     Tato metoda zpracovává <xref:System.Windows.Data.CollectionView.CurrentChanged> událostí a aktualizuje aktuální položky datové vazby.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Datové vazby v ukázce hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
