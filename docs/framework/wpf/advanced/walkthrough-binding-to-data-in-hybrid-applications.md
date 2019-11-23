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
ms.openlocfilehash: 92d267ee9e87e9d204fe76172ca7e0fe33cf1a1b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976584"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Návod: Připojení k datům v hybridních aplikacích

Vytvoření vazby zdroje dat k ovládacímu prvku je nezbytné pro poskytování přístupu uživatelům s přístupem k podkladovým datům, ať už používáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tento návod ukazuje, jak můžete použít datovou vazbu v hybridních aplikacích, které zahrnují ovládací prvky [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

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

    - System. Windows. Forms

3. Otevřete MainWindow. XAML v Návrháři WPF.

4. V elementu <xref:System.Windows.Window> přidejte následující mapování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] obory názvů.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Pojmenujte výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením vlastnosti <xref:System.Windows.FrameworkElement.Name%2A>.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Definování šablony dat

Hlavní seznam zákazníků se zobrazí v ovládacím prvku <xref:System.Windows.Controls.ListBox>. Následující příklad kódu definuje objekt <xref:System.Windows.DataTemplate> s názvem `ListItemsTemplate`, který ovládá vizuální strom ovládacího prvku <xref:System.Windows.Controls.ListBox>. Tato <xref:System.Windows.DataTemplate> je přiřazena k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ovládacího prvku <xref:System.Windows.Controls.ListBox>.

### <a name="to-define-the-data-template"></a>Definování šablony dat

- Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Určení rozložení formuláře

Rozložení formuláře je definováno mřížkou, která má tři řádky a tři sloupce. pro identifikaci každého sloupce v tabulce Customers jsou k dispozici <xref:System.Windows.Controls.Label> ovládací prvky.

### <a name="to-set-up-the-grid-layout"></a>Nastavení rozložení mřížky

- Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Nastavení ovládacích prvků popisek

- Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Určení datových vazeb

Hlavní seznam zákazníků se zobrazí v ovládacím prvku <xref:System.Windows.Controls.ListBox>. Připojené `ListItemsTemplate` váže ovládací prvek <xref:System.Windows.Controls.TextBlock> k poli `ContactName` z databáze.

Podrobnosti o jednotlivých záznamech zákazníka se zobrazí v několika ovládacích prvcích <xref:System.Windows.Controls.TextBox>.

### <a name="to-specify-data-bindings"></a>Určení datových vazeb

- Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.

     Třída <xref:System.Windows.Data.Binding> váže ovládací prvky <xref:System.Windows.Controls.TextBox> k příslušným polím v databázi.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Zobrazení dat pomocí spolupráce

Objednávky odpovídající vybranému zákazníkovi se zobrazí v ovládacím prvku <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> s názvem `dataGridView1`. `dataGridView1` ovládací prvek je svázán se zdrojem dat v souboru kódu na pozadí. Ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je nadřazeným prvkem tohoto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ho ovládacího prvku.

### <a name="to-display-data-in-the-datagridview-control"></a>Zobrazení dat v ovládacím prvku DataGridView

- Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Přidání zdroje dat do projektu

Se sadou Visual Studio můžete snadno přidat zdroj dat do projektu. Tento postup přidá do projektu datovou sadu silného typu. Přidávají se také některé další třídy podpory, například adaptéry pro tabulky pro každou z vybraných tabulek.

### <a name="to-add-the-data-source"></a>Přidání zdroje dat

1. V nabídce **data** vyberte **Přidat nový zdroj dat**.

2. V **Průvodci konfigurací zdroje dat**vytvořte připojení k databázi Northwind pomocí datové sady. Další informace najdete v tématu [Postup: připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. Po zobrazení výzvy **Průvodce konfigurací zdroje dat**uložte připojovací řetězec jako `NorthwindConnectionString`.

4. Když se zobrazí výzva k výběru databázových objektů, vyberte tabulky `Customers` a `Orders` a pojmenujte vygenerovanou sadu dat `NorthwindDataSet`.

## <a name="binding-to-the-data-source"></a>Vazba na zdroj dat

Komponenta <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> poskytuje jednotné rozhraní pro zdroj dat aplikace. Vazba na zdroj dat je implementována v souboru kódu na pozadí.

### <a name="to-bind-to-the-data-source"></a>Vytvoření vazby na zdroj dat

1. Otevřete soubor kódu na pozadí, který má název MainWindow. XAML. vb nebo MainWindow.xaml.cs.

2. Zkopírujte následující kód do definice třídy `MainWindow`.

     Tento kód deklaruje komponentu <xref:System.Windows.Forms.BindingSource> a přidružené pomocné třídy, které se připojují k databázi.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Zkopírujte následující kód do konstruktoru.

     Tento kód vytvoří a inicializuje komponentu <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Otevřete MainWindow. XAML.

5. V zobrazení zobrazení Návrh nebo XAML vyberte prvek <xref:System.Windows.Window>.

6. V okno Vlastnosti klikněte na kartu **události** .

7. Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.

8. Zkopírujte následující kód do obslužné rutiny události <xref:System.Windows.FrameworkElement.Loaded>.

     Tento kód přiřadí komponentu <xref:System.Windows.Forms.BindingSource> jako kontext dat a naplní `Customers` a `Orders` objekty adaptéru.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Zkopírujte následující kód do definice třídy `MainWindow`.

     Tato metoda zpracovává událost <xref:System.Windows.Data.CollectionView.CurrentChanged> a aktualizuje aktuální položku datové vazby.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Ukázka datových vazeb v hybridních aplikacích](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
