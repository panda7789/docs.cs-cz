---
title: 'Postupy: Seskupení položek v objektu ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551905"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Postupy: Seskupení položek v objektu ListView s implementací GridView
Tento příklad ukazuje, jak zobrazit skupiny položek v <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Zobrazit skupiny položek v <xref:System.Windows.Controls.ListView>, definovat <xref:System.Windows.Data.CollectionViewSource>. Následující příklad ukazuje <xref:System.Windows.Data.CollectionViewSource> , skupiny datových položek podle hodnoty `Catalog` datové pole.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 Následující příklad nastavuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> k <xref:System.Windows.Data.CollectionViewSource> definující předchozí příklad. Tento příklad také definuje <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> , která implementuje <xref:System.Windows.Controls.Expander> ovládacího prvku.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
