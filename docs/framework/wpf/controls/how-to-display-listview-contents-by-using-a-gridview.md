---
title: 'Postupy: Zobrazení obsahu ListView použitím GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910491"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="2dd91-102">Postupy: Zobrazení obsahu ListView použitím GridView</span><span class="sxs-lookup"><span data-stu-id="2dd91-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="2dd91-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režimu zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2dd91-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dd91-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2dd91-104">Example</span></span>  
 <span data-ttu-id="2dd91-105">Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty.</span><span class="sxs-lookup"><span data-stu-id="2dd91-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="2dd91-106">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které svázat data obsah, který je zadán pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2dd91-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="2dd91-107">To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které mapují `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , který je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2dd91-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="2dd91-108">Následující obrázek znázorňuje, jak se zobrazí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="2dd91-108">The following illustration shows how this example appears.</span></span>  
  
 ![Snímek obrazovky zobrazující ListView s výstupem ovládacího prvku GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="2dd91-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dd91-110">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="2dd91-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="2dd91-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="2dd91-112">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="2dd91-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="2dd91-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2dd91-113">How-to Topics</span></span>](listview-how-to-topics.md)
