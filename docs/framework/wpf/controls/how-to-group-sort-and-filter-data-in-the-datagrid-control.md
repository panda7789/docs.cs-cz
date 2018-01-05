---
title: "Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid"
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
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e648b5a4a45c3583d496ac0ea6036d268d6d33a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid
Je často užitečné k zobrazení dat v <xref:System.Windows.Controls.DataGrid> seskupování, řazení a filtrování dat různými způsoby. Skupina, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>, navázat jej na <xref:System.Windows.Data.CollectionView> , která podporuje tyto funkce. Potom můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez ovlivnění základní zdrojová data. Změny v zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelské rozhraní (UI).  
  
 <xref:System.Windows.Data.CollectionView> Třída poskytuje seskupení a řazení funkce pro zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní. <xref:System.Windows.Data.CollectionViewSource> Vám umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.  
  
 V tomto příkladu kolekce `Task` objektů je vázána <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupování, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.  
  
 ![Seskupené data v DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")  
Seskupené Data v DataGrid  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Použití CollectionViewSource jako ItemsSource  
 Ke skupině, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid> řízení, vytvoření vazby <xref:System.Windows.Controls.DataGrid> k <xref:System.Windows.Data.CollectionView> , která podporuje tyto funkce. V tomto příkladu <xref:System.Windows.Controls.DataGrid> je vázána <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> z `Task` objekty.  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>K vytvoření vazby ovládacího prvku DataGrid CollectionViewSource  
  
1.  Vytvořte kolekci dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní.  
  
     Pokud používáte <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> místo konkretizaci instance <xref:System.Collections.Generic.List%601>. To vám umožní k vazbě dat na kolekce v jazyce XAML.  
  
    > [!NOTE]
    >  Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a <xref:System.ComponentModel.IEditableObject> rozhraní, aby <xref:System.Windows.Controls.DataGrid> správně reakce na změny vlastností a úpravy. Další informace najdete v tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  V jazyce XAML, vytvoření instance třídy kolekce a nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md).  
  
3.  V jazyce XAML, vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md)a nastavte instance třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  Vytvoření instance <xref:System.Windows.Controls.DataGrid> třídy a nastavte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost, která má <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  Pro přístup k <xref:System.Windows.Data.CollectionViewSource> z vašeho kódu pomocí <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu k získání odkazu na <xref:System.Windows.Data.CollectionViewSource>.  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a>Seskupení položek v DataGrid  
 Chcete-li určit způsob seskupení položek v <xref:System.Windows.Controls.DataGrid>, můžete použít <xref:System.Windows.Data.PropertyGroupDescription> typu chcete seskupit položky v zobrazení zdroje.  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Seskupit položky v DataGrid pomocí jazyka XAML  
  
1.  Vytvoření <xref:System.Windows.Data.PropertyGroupDescription> , určuje vlastnost do skupiny podle. Vlastnost můžete zadat v jazyce XAML, nebo v kódu.  
  
    1.  V jazyce XAML, nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, která má Seskupit podle.  
  
    2.  V kódu předejte název vlastnost do skupiny pomocí konstruktoru.  
  
2.  Přidat <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.  
  
3.  Přidat další instance <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce, které chcete přidat další úrovně seskupení.  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.  
  
5.  Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 Pokud budou seskupeny položky v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle> určující vzhled každé skupiny. Můžete použít <xref:System.Windows.Controls.GroupStyle> přidáním jeho <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekci DataGrid. Pokud máte více úrovní seskupení, můžete použít různé styly pro každou úroveň skupiny. Styly jsou použity v pořadí, ve kterém jsou definovány. Například pokud definujete dvě styly, první se použijí na nejvyšší úrovni řádek skupiny. Druhý styl bude použit na všechny skupiny řádků na úrovni druhé a nižší. <xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup> představující skupině.  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a>Chcete-li změnit vzhled záhlaví skupiny řádků  
  
1.  Vytvoření <xref:System.Windows.Controls.GroupStyle> , který definuje vzhled skupiny řádků.  
  
2.  Umístit <xref:System.Windows.Controls.GroupStyle> uvnitř `<DataGrid.GroupStyle>` značky.  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a>Řazení položek v DataGrid  
 Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijete <xref:System.ComponentModel.SortDescription> typ seřadíte položky v zobrazení zdroje.  
  
#### <a name="to-sort-items-in-a-datagrid"></a>Chcete-li řadit položky v DataGrid  
  
1.  Vytvoření <xref:System.ComponentModel.SortDescription> , určuje vlastnost, která má seřadit. Vlastnost můžete zadat v jazyce XAML, nebo v kódu.  
  
    1.  V jazyce XAML, nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> na název vlastnosti, která má seřadit.  
  
    2.  V kódu předat název vlastnosti pro řazení podle a <xref:System.ComponentModel.ListSortDirection> konstruktoru.  
  
2.  Přidat <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.  
  
3.  Přidat další instance <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce seřadit podle další vlastnosti.  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a>Filtrování položek v DataGrid  
 Filtrování položek v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, poskytovat logiku filtrování obslužné rutiny pro <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.  
  
#### <a name="to-filter-items-in-a-datagrid"></a>Filtrovat položky v DataGrid  
  
1.  Přidání obslužné rutiny <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.  
  
2.  V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutiny události, definovat filtrování logiku.  
  
     Filtr se použijí pokaždé, když je zobrazení aktualizovat.  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metodu, která poskytuje filtrování logiku a nastavení <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnost použít filtr. Příklad této metody naleznete v tématu [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje seskupování, řazení a filtrování `Task` data v <xref:System.Windows.Data.CollectionViewSource> a zobrazování seskupené, třídění a filtrování `Task` data <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>. Seskupování, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.  
  
 K testování v tomto příkladu, musíte upravit název DGGroupSortFilterExample tak, aby odpovídaly název projektu. Pokud používáte Visual Basic, budete muset změnit název třídy pro <xref:System.Windows.Window> pro následující.  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-  
  
## <a name="robust-programming"></a>Robustní programování  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vytvoření a vytvoření vazby ke kolekci ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
