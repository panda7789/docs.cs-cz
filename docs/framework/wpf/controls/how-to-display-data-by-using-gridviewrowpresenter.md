---
title: 'Postupy: Zobrazení data pomocí GridViewRowPresenter'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: f68bc3a4ffff268138721a6750a0eb50c825377e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550787"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="e7fc7-102">Postupy: Zobrazení data pomocí GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="e7fc7-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="e7fc7-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty, které chcete zobrazit data ve sloupcích.</span><span class="sxs-lookup"><span data-stu-id="e7fc7-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7fc7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7fc7-104">Example</span></span>  
 <span data-ttu-id="e7fc7-105">Následující příklad ukazuje, jak určit <xref:System.Windows.Controls.GridViewColumnCollection> který zobrazí <xref:System.DateTime.DayOfWeek%2A> a <xref:System.DateTime.Year%2A> z <xref:System.DateTime> objekt pomocí <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty.</span><span class="sxs-lookup"><span data-stu-id="e7fc7-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="e7fc7-106">Tento příklad také definuje <xref:System.Windows.Style> pro <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="e7fc7-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="e7fc7-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7fc7-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="e7fc7-108">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="e7fc7-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
