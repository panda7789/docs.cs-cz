---
title: 'Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 622b64fd7738b02cd72131e7e9fe91c04314b1d0
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559471"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid

Často je užitečné zobrazit data v <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat. K seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>je svážete s <xref:System.Windows.Data.CollectionView>, která tyto funkce podporuje. Pak můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez vlivu na podkladová zdrojová data. Změny v zobrazení kolekce se projeví v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid> (UI).

Třída <xref:System.Windows.Data.CollectionView> poskytuje funkce seskupování a řazení pro zdroj dat, který implementuje rozhraní <xref:System.Collections.IEnumerable>. Třída <xref:System.Windows.Data.CollectionViewSource> umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.

V tomto příkladu je kolekce objektů `Task` svázána s <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a zobrazují se v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>.

![Seskupená data v objektu DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Seskupená data v objektu DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Použití CollectionViewSource jako ItemsSource

K seskupení, řazení a filtrování dat v ovládacím prvku <xref:System.Windows.Controls.DataGrid> svážete <xref:System.Windows.Controls.DataGrid> s <xref:System.Windows.Data.CollectionView>, které tyto funkce podporují. V tomto příkladu je <xref:System.Windows.Controls.DataGrid> svázán s <xref:System.Windows.Data.CollectionViewSource>, která poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> objektů `Task`.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Svázání prvku DataGrid s CollectionViewSource

1. Vytvořte kolekci dat, která implementuje rozhraní <xref:System.Collections.IEnumerable>.

    Použijete-li <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto vytvoření instance <xref:System.Collections.Generic.List%601>. To umožňuje vytvořit datovou vazby ke kolekci v jazyce XAML.

    > [!NOTE]
    > Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a rozhraní <xref:System.ComponentModel.IEditableObject>, aby <xref:System.Windows.Controls.DataGrid> správně reagovala na změny a úpravy vlastností. Další informace najdete v tématu [implementace oznámení změny vlastností](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. V jazyce XAML vytvořte instanci třídy kolekce a nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md).

3. V jazyce XAML vytvořte instanci třídy <xref:System.Windows.Data.CollectionViewSource>, nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md)a nastavte instanci třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Vytvořte instanci třídy <xref:System.Windows.Controls.DataGrid> a nastavte vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Chcete-li získat přístup k <xref:System.Windows.Data.CollectionViewSource> z kódu, použijte metodu <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> a získejte odkaz na <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Seskupení položek v objektu DataGrid

Chcete-li určit, jak jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid>, použijte typ <xref:System.Windows.Data.PropertyGroupDescription> k seskupení položek v zobrazení zdroje.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Seskupení položek v prvku DataGrid pomocí jazyka XAML

1. Vytvořte <xref:System.Windows.Data.PropertyGroupDescription>, který určuje vlastnost, podle které se má seskupit. Můžete zadat vlastnost v jazyce XAML nebo v kódu.

   1. V jazyce XAML nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, podle které chcete seskupovat.

   2. V kódu předejte název vlastnosti k seskupení podle konstruktoru.

2. Přidejte <xref:System.Windows.Data.PropertyGroupDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>.

3. Přidáním dalších instancí <xref:System.Windows.Data.PropertyGroupDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> přidáte další úrovně seskupení.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.

5. Chcete-li odebrat všechny skupiny, zavolejte metodu <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Pokud jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle>, která určuje vzhled každé skupiny. <xref:System.Windows.Controls.GroupStyle> použijete tak, že ji přidáte do kolekce <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> prvku DataGrid. Pokud máte více úrovní seskupení, můžete pro každou úroveň skupiny použít různé styly. Styly jsou aplikovány v pořadí, ve kterém jsou definovány. Například pokud definujete dva styly, použije se jako první na nejvyšší úrovni skupiny řádků. Druhý styl bude použit pro všechny skupiny řádků na druhé úrovni a nižší. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup>, které skupina představuje.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Změna vzhledu záhlaví skupin řádků

1. Vytvořte <xref:System.Windows.Controls.GroupStyle> definující vzhled skupiny řádků.

2. Vložte <xref:System.Windows.Controls.GroupStyle> dovnitř značek `<DataGrid.GroupStyle>`.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Řazení položek v objektu DataGrid

Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijte typ <xref:System.ComponentModel.SortDescription> k řazení položek v zobrazení zdroje.

### <a name="to-sort-items-in-a-datagrid"></a>Řazení položek v objektu DataGrid

1. Vytvořte <xref:System.ComponentModel.SortDescription>, který určuje vlastnost, podle které se má řadit. Můžete zadat vlastnost v jazyce XAML nebo v kódu.

    1. V jazyce XAML nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> na název vlastnosti, podle které chcete řadit.

    2. V kódu předejte název vlastnosti k řazení podle a <xref:System.ComponentModel.ListSortDirection> do konstruktoru.

2. Přidejte <xref:System.ComponentModel.SortDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>.

3. Přidejte další instance <xref:System.ComponentModel.SortDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> k seřazení podle dalších vlastností.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrování položek v objektu DataGrid

Chcete-li filtrovat položky v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, zadejte logiku filtrování v obslužné rutině pro událost <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

### <a name="to-filter-items-in-a-datagrid"></a>Filtrování položek v prvku DataGrid

1. Přidejte obslužnou rutinu pro událost <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.

2. V obslužné rutině události <xref:System.Windows.Data.CollectionViewSource.Filter> definujte logiku filtrování.

    Filtr bude použit při každém obnovení zobrazení.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metody, která poskytuje logiku filtrování a nastavením vlastnosti <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> na použití filtru. Příklad této metody najdete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Příklad

Následující příklad znázorňuje seskupení, řazení a filtrování `Task` dat v <xref:System.Windows.Data.CollectionViewSource> a zobrazení seskupených, seřazených a filtrovaných `Task` dat v <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a zobrazují se v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>.

Chcete-li otestovat tento příklad, budete muset upravit DGGroupSortFilterExample název tak, aby odpovídal názvu projektu. Pokud používáte Visual Basic, budete muset změnit název třídy pro <xref:System.Windows.Window> na následující.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Vytvoření a vytvoření vazby ke kolekci ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md)
- [Řazení dat v zobrazení](../data/how-to-sort-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
