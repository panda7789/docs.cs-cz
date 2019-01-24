---
title: 'Postupy: Zobrazení data pomocí GridViewRowPresenter'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: b60fe0e78883b166688377c42113a093c78d7751
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607956"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="1d147-102">Postupy: Zobrazení data pomocí GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="1d147-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="1d147-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty pro zobrazení dat ve sloupcích.</span><span class="sxs-lookup"><span data-stu-id="1d147-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d147-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d147-104">Example</span></span>  
 <span data-ttu-id="1d147-105">Následující příklad ukazuje, jak určit <xref:System.Windows.Controls.GridViewColumnCollection> , který se zobrazí <xref:System.DateTime.DayOfWeek%2A> a <xref:System.DateTime.Year%2A> z <xref:System.DateTime> s použitím <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty.</span><span class="sxs-lookup"><span data-stu-id="1d147-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="1d147-106">Příklad také definuje <xref:System.Windows.Style> pro <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="1d147-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="1d147-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d147-107">See also</span></span>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [<span data-ttu-id="1d147-108">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="1d147-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
