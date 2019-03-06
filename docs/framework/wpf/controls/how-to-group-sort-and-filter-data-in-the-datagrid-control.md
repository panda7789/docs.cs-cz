---
title: 'Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 81fdb0a6d5602f612c55d7e790ca9a0fe56c144e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365045"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid

Často je užitečné, chcete-li zobrazit data <xref:System.Windows.Controls.DataGrid> seskupení, řazení a filtrování dat různými způsoby. Seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>, umožňuje vytvořit vazbu <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce. Pak můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez ovlivnění základního zdrojová data. V zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní (UI).

<xref:System.Windows.Data.CollectionView> Třída poskytuje seskupování a řazení funkce pro zdroj dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní. <xref:System.Windows.Data.CollectionViewSource> Třída umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.

V tomto příkladu kolekce `Task` objektům svázaným s <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.

![Seskupená data do ovládacího prvku DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") seskupená data do ovládacího prvku DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Pomocí kolekce CollectionViewSource jako vlastnost ItemsSource.

Pro seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid> ovládacího prvku, je vytvořit vazbu <xref:System.Windows.Controls.DataGrid> k <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce. V tomto příkladu <xref:System.Windows.Controls.DataGrid> je vázán na <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> z `Task` objekty.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Kolekce CollectionViewSource vytvořit vazbu ovládacího prvku DataGrid

1. Vytvořit kolekci dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní.

    Pokud používáte <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto vytvoření instance instance <xref:System.Collections.Generic.List%601>. To vám umožní vytvořit vazbu na data do kolekce v XAML.

    > [!NOTE]
    > Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a <xref:System.ComponentModel.IEditableObject> rozhraní, aby <xref:System.Windows.Controls.DataGrid> správně reagovat na změny vlastností a úpravy. Další informace najdete v tématu [implementace oznámení změn vlastností](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. V XAML, vytvoření instance třídy kolekce a nastavte [x: Key – direktiva](../../xaml-services/x-key-directive.md).

3. V XAML, vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [x: Key – direktiva](../../xaml-services/x-key-directive.md)a nastavte instance třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Vytvoření instance <xref:System.Windows.Controls.DataGrid> třídy a nastavit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Data.CollectionViewSource>.

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Pro přístup <xref:System.Windows.Data.CollectionViewSource> z vašeho kódu, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu k získání odkazu na <xref:System.Windows.Data.CollectionViewSource>.

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Seskupení položek do ovládacího prvku DataGrid

K určení způsobu seskupení položek v <xref:System.Windows.Controls.DataGrid>, je použít <xref:System.Windows.Data.PropertyGroupDescription> typ seskupení položek v zobrazení zdroje.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Seskupit položky v DataGrid pomocí XAML

1. Vytvoření <xref:System.Windows.Data.PropertyGroupDescription> , který určuje vlastnost, která má Seskupit podle. V XAML nebo v kódu, můžete zadat vlastnost.

   1. V XAML, nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, které chcete seskupit podle.

   2. V kódu předejte název vlastnosti Seskupit podle do konstruktoru.

2. Přidat <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.

3. Přidat další instance <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce přidejte další úrovně seskupení.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.

5. Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Po seskupení položek v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle> , který určuje vzhled každou skupinu. Můžete použít <xref:System.Windows.Controls.GroupStyle> tak, že ji přidáte <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekce v prvku DataGrid. Pokud máte více úrovní seskupení můžete použít různé styly pro každou úroveň skupiny. Styly použijí v pořadí, ve kterém jsou definovány. Například pokud definujete dvě styly, první se použije u skupin nejvyšší úrovně řádku. Druhý styl bude platí pro všechny skupiny řádku na druhé úrovni a nižší. <xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup> , který představuje skupiny.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Chcete-li změnit vzhled hlaviček skupiny řádků

1. Vytvoření <xref:System.Windows.Controls.GroupStyle> , která definuje vzhled elementů skupinu řádků.

2. Vložit <xref:System.Windows.Controls.GroupStyle> uvnitř `<DataGrid.GroupStyle>` značky.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Řazení položek do ovládacího prvku DataGrid

Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijete <xref:System.ComponentModel.SortDescription> typ řazení položek v zobrazení zdroje.

### <a name="to-sort-items-in-a-datagrid"></a>Chcete-li seřadit položky ovládacího prvku DataGrid

1. Vytvoření <xref:System.ComponentModel.SortDescription> , který určuje vlastnost, která má řadit. V XAML nebo v kódu, můžete zadat vlastnost.

    1. V XAML, nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> název vlastnosti, která má řadit.

    2. V kódu, předejte název vlastnosti seřadit podle a <xref:System.ComponentModel.ListSortDirection> konstruktoru.

2. Přidat <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.

3. Přidat další instance <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce seřadíte položky podle další vlastnosti.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrování položek do ovládacího prvku DataGrid

Pro filtrování položek v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, poskytuje logiku filtrování v obslužné rutině <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.

### <a name="to-filter-items-in-a-datagrid"></a>K filtrování položek do ovládacího prvku DataGrid

1. Přidání obslužné rutiny <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.

2. V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužná rutina události definujte logiku filtrování.

    Filtr se použijí pokaždé, když je zobrazení aktualizovat.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metodu, která poskytuje logiku filtrování a nastavení <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnosti použijte filtr. Příklad této metody naleznete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje seskupení, řazení a filtrování `Task` data v <xref:System.Windows.Data.CollectionViewSource> a zobrazení skupinových, seřazený a filtrovaný `Task` data v <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.

K otestování v tomto příkladu, je potřeba upravit název DGGroupSortFilterExample tak, aby odpovídaly název vašeho projektu. Pokud používáte Visual Basic, bude nutné změnit název třídy pro <xref:System.Windows.Window> následující.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Vytvoření a vytvoření vazby ke kolekci ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md)
- [Řazení dat v zobrazení](../data/how-to-sort-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
