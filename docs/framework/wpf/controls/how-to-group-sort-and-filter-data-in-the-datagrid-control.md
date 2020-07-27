---
title: 'Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
description: Naučte se navazovat Windows Presentation Foundation ovládací prvek DataGrid na CollectionView, který podporuje seskupení, řazení a filtrování dat v zobrazeních.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167668"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid

Často je užitečné zobrazovat data <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat. Chcete-li seskupit, seřadit a filtrovat data v <xref:System.Windows.Controls.DataGrid> , navážete ji na a <xref:System.Windows.Data.CollectionView> podporující tyto funkce. Pak můžete pracovat s daty v, <xref:System.Windows.Data.CollectionView> aniž by to mělo vliv na podkladová zdrojová data. Změny v zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní (UI).

<xref:System.Windows.Data.CollectionView>Třída poskytuje funkce seskupování a řazení pro zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní. <xref:System.Windows.Data.CollectionViewSource>Třída umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.

V tomto příkladu `Task` je kolekce objektů svázána s <xref:System.Windows.Data.CollectionViewSource> . <xref:System.Windows.Data.CollectionViewSource>Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid> . Seskupení, řazení a filtrování se provádí v <xref:System.Windows.Data.CollectionViewSource> a se zobrazí v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní.

![Seskupená data v objektu DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Seskupená data v objektu DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Použití CollectionViewSource jako ItemsSource

Chcete-li seskupovat, řadit a filtrovat data v <xref:System.Windows.Controls.DataGrid> ovládacím prvku, navážete na <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce. V tomto příkladu <xref:System.Windows.Controls.DataGrid> je svázána s objektem <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> `Task` objekty.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Svázání prvku DataGrid s CollectionViewSource

1. Vytvořte kolekci dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní.

    Použijete <xref:System.Collections.Generic.List%601> -li k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto instance instance <xref:System.Collections.Generic.List%601> . To umožňuje vytvořit datovou vazby ke kolekci v jazyce XAML.

    > [!NOTE]
    > Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a rozhraní, aby <xref:System.ComponentModel.IEditableObject> <xref:System.Windows.Controls.DataGrid> správně odpovídaly změnám a úpravám vlastností. Další informace najdete v tématu [implementace oznámení změny vlastností](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. V jazyce XAML vytvořte instanci třídy kolekce a nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md).

3. V jazyce XAML vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md)a nastavte instanci třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A> .

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Vytvořte instanci <xref:System.Windows.Controls.DataGrid> třídy a nastavte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na <xref:System.Windows.Data.CollectionViewSource> .

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Chcete-li získat přístup k <xref:System.Windows.Data.CollectionViewSource> z kódu, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu pro získání odkazu na <xref:System.Windows.Data.CollectionViewSource> .

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Seskupení položek v objektu DataGrid

Chcete-li určit, jak jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid> , použijte <xref:System.Windows.Data.PropertyGroupDescription> typ k seskupení položek v zobrazení zdroje.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Seskupení položek v prvku DataGrid pomocí jazyka XAML

1. Vytvořte <xref:System.Windows.Data.PropertyGroupDescription> , který určuje vlastnost, podle které se má seskupit. Můžete zadat vlastnost v jazyce XAML nebo v kódu.

   1. V jazyce XAML nastavte na <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> název vlastnosti, podle které chcete seskupit.

   2. V kódu předejte název vlastnosti k seskupení podle konstruktoru.

2. Přidejte <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.

3. Přidejte další instance <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce, abyste mohli přidat další úrovně seskupení.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Pokud chcete skupinu odebrat, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.

5. Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Když jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid> , můžete definovat <xref:System.Windows.Controls.GroupStyle> , který určuje vzhled každé skupiny. Použijete <xref:System.Windows.Controls.GroupStyle> ho přidáním do <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekce DataGrid. Pokud máte více úrovní seskupení, můžete pro každou úroveň skupiny použít různé styly. Styly jsou aplikovány v pořadí, ve kterém jsou definovány. Například pokud definujete dva styly, použije se jako první na nejvyšší úrovni skupiny řádků. Druhý styl bude použit pro všechny skupiny řádků na druhé úrovni a nižší. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> Je <xref:System.Windows.Data.CollectionViewGroup> , který skupina představuje.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Změna vzhledu záhlaví skupin řádků

1. Vytvořte <xref:System.Windows.Controls.GroupStyle> , který definuje vzhled skupiny řádků.

2. Vložte <xref:System.Windows.Controls.GroupStyle> dovnitř `<DataGrid.GroupStyle>` značek.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Řazení položek v objektu DataGrid

Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid> , použijte <xref:System.ComponentModel.SortDescription> typ k seřazení položek v zobrazení zdroje.

### <a name="to-sort-items-in-a-datagrid"></a>Řazení položek v objektu DataGrid

1. Vytvořte <xref:System.ComponentModel.SortDescription> , který určuje vlastnost, podle které se má řadit. Můžete zadat vlastnost v jazyce XAML nebo v kódu.

    1. V jazyce XAML nastavte na <xref:System.ComponentModel.SortDescription.PropertyName%2A> název vlastnosti, podle které chcete řadit.

    2. V kódu předejte název vlastnosti k řazení podle a <xref:System.ComponentModel.ListSortDirection> do konstruktoru.

2. Přidejte <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.

3. Přidejte další instance <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce, abyste je mohli seřadit podle dalších vlastností.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrování položek v objektu DataGrid

Chcete-li filtrovat položky v rámci <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource> , zadáte logiku filtrování v obslužné rutině <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> události.

### <a name="to-filter-items-in-a-datagrid"></a>Filtrování položek v prvku DataGrid

1. Přidejte obslužnou rutinu pro <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událost.

2. V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutině události definujte logiku filtrování.

    Filtr bude použit při každém obnovení zobrazení.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternativně můžete filtrovat položky v a <xref:System.Windows.Controls.DataGrid> vytvořením metody, která poskytuje logiku filtrování a nastavením <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnosti pro použití filtru. Příklad této metody najdete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Příklad

Následující příklad znázorňuje seskupení, řazení a filtrování `Task` dat v <xref:System.Windows.Data.CollectionViewSource> a zobrazení seskupených, seřazených a filtrovaných `Task` dat v <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Data.CollectionViewSource>Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid> . Seskupení, řazení a filtrování se provádí v <xref:System.Windows.Data.CollectionViewSource> a se zobrazí v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní.

Chcete-li otestovat tento příklad, budete muset upravit DGGroupSortFilterExample název tak, aby odpovídal názvu projektu. Pokud používáte Visual Basic, budete muset změnit název třídy <xref:System.Windows.Window> na následující.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Viz také

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Vytvoření a vazba na kolekci ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md)
- [Řazení dat v zobrazení](../data/how-to-sort-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení v jazyce XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
