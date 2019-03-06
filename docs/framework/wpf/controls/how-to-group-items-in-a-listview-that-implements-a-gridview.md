---
title: 'Postupy: Seskupení položek v objektu ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 3989f0fcdaf2e3d3003aca9feb27cbf02f949389
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364469"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="f2af5-102">Postupy: Seskupení položek v objektu ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="f2af5-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="f2af5-103">Tento příklad ukazuje, jak zobrazit skupiny položek v <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2af5-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2af5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2af5-104">Example</span></span>  
 <span data-ttu-id="f2af5-105">Chcete-li zobrazit skupiny položek v <xref:System.Windows.Controls.ListView>, definovat <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="f2af5-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="f2af5-106">Následující příklad ukazuje <xref:System.Windows.Data.CollectionViewSource> , která seskupuje datové položky podle hodnoty `Catalog` datové pole.</span><span class="sxs-lookup"><span data-stu-id="f2af5-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="f2af5-107">Následující příklad nastaví <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> k <xref:System.Windows.Data.CollectionViewSource> , který v předchozím příkladu je definována.</span><span class="sxs-lookup"><span data-stu-id="f2af5-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="f2af5-108">Příklad také definuje <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> , který implementuje <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2af5-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="f2af5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2af5-109">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="f2af5-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="f2af5-110">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="f2af5-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="f2af5-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="f2af5-112">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="f2af5-112">GridView Overview</span></span>](gridview-overview.md)
