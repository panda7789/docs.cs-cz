---
title: "Postupy: Seskupení položek v objektu ListView s implementací GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30808e8ee0223c31085a65ff025fb188c0132057
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="1cc34-102">Postupy: Seskupení položek v objektu ListView s implementací GridView</span><span class="sxs-lookup"><span data-stu-id="1cc34-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="1cc34-103">Tento příklad ukazuje, jak zobrazit skupiny položek v <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cc34-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cc34-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cc34-104">Example</span></span>  
 <span data-ttu-id="1cc34-105">Zobrazit skupiny položek v <xref:System.Windows.Controls.ListView>, definovat <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="1cc34-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="1cc34-106">Následující příklad ukazuje <xref:System.Windows.Data.CollectionViewSource> , skupiny datových položek podle hodnoty `Catalog` datové pole.</span><span class="sxs-lookup"><span data-stu-id="1cc34-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="1cc34-107">Následující příklad nastavuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> k <xref:System.Windows.Data.CollectionViewSource> definující předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="1cc34-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="1cc34-108">Tento příklad také definuje <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> , která implementuje <xref:System.Windows.Controls.Expander> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cc34-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="1cc34-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cc34-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="1cc34-110">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="1cc34-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="1cc34-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="1cc34-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="1cc34-112">Rutina GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="1cc34-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
