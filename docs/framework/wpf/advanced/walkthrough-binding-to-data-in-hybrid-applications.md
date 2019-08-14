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
ms.openlocfilehash: ef5f14cdbecab8bc780cb7b2a642429970a25316
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972281"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Návod: Připojení k datům v hybridních aplikacích

Vytvoření vazby zdroje dat k ovládacímu prvku je nezbytné pro poskytování přístupu uživatelům s přístupem k podkladovým datům, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ať [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]už používáte nebo. Tento návod ukazuje, jak můžete použít datovou vazbu v hybridních aplikacích, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahují ovládací prvky i.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt.

- Definování šablony dat.

- Určení rozložení formuláře

- Zadání datových vazeb.

- Zobrazení dat pomocí meziprovozu.

- Přidání zdroje dat do projektu.

- Vazba na zdroj dat.

Úplný výpis kódu úloh, které jsou znázorněné v tomto návodu, najdete v tématu [Ukázka datových vazeb v hybridních aplikacích](https://go.microsoft.com/fwlink/?LinkID=159983).

Až budete hotovi, budete obeznámeni s funkcemi datových vazeb v hybridních aplikacích.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio.

- Přístup k ukázkové databázi Northwind běžící na Microsoft SQL Server.

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1. Vytvořte projekt aplikace WPF s názvem `WPFWithWFAndDatabinding`.

2. V Průzkumník řešení přidejte odkazy na následující sestavení.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Otevřete MainWindow. XAML v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4. V elementu přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oborů názvů. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Pojmenujte <xref:System.Windows.Controls.Grid> výchozí `mainGrid` prvek přiřazením <xref:System.Windows.FrameworkElement.Name%2A> vlastnosti.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Definování šablony dat

Hlavní seznam zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacím prvku. Následující příklad kódu definuje <xref:System.Windows.DataTemplate> objekt s názvem `ListItemsTemplate` , který ovládá vizuální strom <xref:System.Windows.Controls.ListBox> ovládacího prvku. Toto <xref:System.Windows.DataTemplate> je přiřazeno <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnosti ovládacího prvku.

### <a name="to-define-the-data-template"></a>Definování šablony dat

- Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> deklarace elementu.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Určení rozložení formuláře

Rozložení formuláře je definováno mřížkou, která má tři řádky a tři sloupce. <xref:System.Windows.Controls.Label>k identifikaci každého sloupce v tabulce Customers jsou k dispozici ovládací prvky.

### <a name="to-set-up-the-grid-layout"></a>Nastavení rozložení mřížky

- Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> deklarace elementu.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Nastavení ovládacích prvků popisek

- Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> deklarace elementu.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Určení datových vazeb

Hlavní seznam zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacím prvku. Připojený `ListItemsTemplate` <xref:System.Windows.Controls.TextBlock> ovládací prvek váže k `ContactName` poli z databáze.

Podrobnosti o jednotlivých záznamech zákazníka se zobrazí v několika <xref:System.Windows.Controls.TextBox> ovládacích prvcích.

### <a name="to-specify-data-bindings"></a>Určení datových vazeb

- Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> deklarace elementu.

     <xref:System.Windows.Data.Binding> Třída váže<xref:System.Windows.Controls.TextBox> ovládací prvky k příslušným polím v databázi.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Zobrazení dat pomocí spolupráce

Objednávky odpovídající vybranému zákazníkovi se zobrazí v <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> ovládacím prvku s názvem. `dataGridView1` `dataGridView1` Ovládací prvek je svázán se zdrojem dat v souboru kódu na pozadí. Ovládací prvek je nadřazený tomuto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacímu prvku. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-display-data-in-the-datagridview-control"></a>Zobrazení dat v ovládacím prvku DataGridView

- Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> deklarace elementu.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Přidání zdroje dat do projektu

Se sadou Visual Studio můžete snadno přidat zdroj dat do projektu. Tento postup přidá do projektu datovou sadu silného typu. Přidávají se také některé další třídy podpory, například adaptéry pro tabulky pro každou z vybraných tabulek.

### <a name="to-add-the-data-source"></a>Přidání zdroje dat

1. V nabídce **data** vyberte **Přidat nový zdroj dat**.

2. V **Průvodci konfigurací zdroje dat**vytvořte připojení k databázi Northwind pomocí datové sady. Další informace najdete v tématu [jak: Připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. Po zobrazení výzvy **Průvodce konfigurací zdroje dat**uložte připojovací řetězec jako `NorthwindConnectionString`.

4. Když se zobrazí výzva k výběru databázových objektů, vyberte `Customers` tabulky a `Orders` a pojmenujte vytvořenou datovou sadu. `NorthwindDataSet`

## <a name="binding-to-the-data-source"></a>Vazba na zdroj dat

<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Komponenta poskytuje jednotné rozhraní pro zdroj dat aplikace. Vazba na zdroj dat je implementována v souboru kódu na pozadí.

### <a name="to-bind-to-the-data-source"></a>Vytvoření vazby na zdroj dat

1. Otevřete soubor kódu na pozadí, který má název MainWindow. XAML. vb nebo MainWindow.xaml.cs.

2. Zkopírujte následující kód do `MainWindow` definice třídy.

     Tento kód deklaruje <xref:System.Windows.Forms.BindingSource> komponentu a přidružené pomocné třídy, které se připojují k databázi.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Zkopírujte následující kód do konstruktoru.

     Tento kód vytvoří a inicializuje <xref:System.Windows.Forms.BindingSource> komponentu.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Otevřete MainWindow. XAML.

5. V zobrazení zobrazení Návrh nebo XAML vyberte <xref:System.Windows.Window> prvek.

6. V okno Vlastnosti klikněte na kartu **události** .

7. Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> na událost.

8. Zkopírujte následující kód do <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.

     Tento kód přiřadí <xref:System.Windows.Forms.BindingSource> komponentu jako datový kontext a naplní `Customers` objekty adaptéru a `Orders` .

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Zkopírujte následující kód do `MainWindow` definice třídy.

     Tato metoda zpracovává <xref:System.Windows.Data.CollectionView.CurrentChanged> událost a aktualizuje aktuální položku datové vazby.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Ukázka datových vazeb v hybridních aplikacích](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Návod: Hostování model Windows Forms složeného ovládacího prvku v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
