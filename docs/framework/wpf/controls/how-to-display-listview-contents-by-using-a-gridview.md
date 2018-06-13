---
title: 'Postupy: Zobrazení obsahu ListView použitím GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554048"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="47f55-102">Postupy: Zobrazení obsahu ListView použitím GridView</span><span class="sxs-lookup"><span data-stu-id="47f55-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="47f55-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režim zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="47f55-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47f55-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="47f55-104">Example</span></span>  
 <span data-ttu-id="47f55-105">Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty.</span><span class="sxs-lookup"><span data-stu-id="47f55-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="47f55-106">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které k obsahu data, která je určená pro vytvoření vazby <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="47f55-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="47f55-107">To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které jsou mapovány na `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="47f55-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="47f55-108">Následující obrázek znázorňuje, jak tento příklad zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="47f55-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="47f55-109">![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="47f55-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f55-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="47f55-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="47f55-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="47f55-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="47f55-112">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="47f55-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="47f55-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="47f55-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
