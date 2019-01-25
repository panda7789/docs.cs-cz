---
title: 'Postupy: Seskupení položek v objektu ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 1570eab70dae690f508975162b7553de92be6f12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664353"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Postupy: Seskupení položek v objektu ListView s implementací GridView
Tento příklad ukazuje, jak zobrazit skupiny položek v <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Chcete-li zobrazit skupiny položek v <xref:System.Windows.Controls.ListView>, definovat <xref:System.Windows.Data.CollectionViewSource>. Následující příklad ukazuje <xref:System.Windows.Data.CollectionViewSource> , která seskupuje datové položky podle hodnoty `Catalog` datové pole.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 Následující příklad nastaví <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> k <xref:System.Windows.Data.CollectionViewSource> , který v předchozím příkladu je definována. Příklad také definuje <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> , který implementuje <xref:System.Windows.Controls.Expander> ovládacího prvku.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
