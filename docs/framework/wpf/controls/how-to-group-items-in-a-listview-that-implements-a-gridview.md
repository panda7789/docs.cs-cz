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
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="3e37b-102">Postupy: Seskupení položek v objektu ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="3e37b-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="3e37b-103">Tento příklad ukazuje, jak zobrazit skupiny položek v <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3e37b-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e37b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e37b-104">Example</span></span>  
 <span data-ttu-id="3e37b-105">Zobrazit skupiny položek v <xref:System.Windows.Controls.ListView>, definovat <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="3e37b-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="3e37b-106">Následující příklad ukazuje <xref:System.Windows.Data.CollectionViewSource> , skupiny datových položek podle hodnoty `Catalog` datové pole.</span><span class="sxs-lookup"><span data-stu-id="3e37b-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="3e37b-107">Následující příklad nastavuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> k <xref:System.Windows.Data.CollectionViewSource> definující předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="3e37b-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="3e37b-108">Tento příklad také definuje <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> , která implementuje <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3e37b-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="3e37b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e37b-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="3e37b-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3e37b-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="3e37b-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="3e37b-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="3e37b-112">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="3e37b-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
