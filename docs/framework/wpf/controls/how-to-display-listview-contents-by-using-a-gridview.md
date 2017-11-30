---
title: "Postupy: Zobrazení obsahu ListView použitím GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24560a1e9b663a3145b589b5a03af8a8b72236ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="94b9b-102">Postupy: Zobrazení obsahu ListView použitím GridView</span><span class="sxs-lookup"><span data-stu-id="94b9b-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="94b9b-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režim zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94b9b-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94b9b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="94b9b-104">Example</span></span>  
 <span data-ttu-id="94b9b-105">Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty.</span><span class="sxs-lookup"><span data-stu-id="94b9b-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="94b9b-106">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které k obsahu data, která je určená pro vytvoření vazby <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94b9b-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="94b9b-107">To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které jsou mapovány na `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94b9b-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="94b9b-108">Následující obrázek znázorňuje, jak tento příklad zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="94b9b-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="94b9b-109">![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="94b9b-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b9b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="94b9b-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="94b9b-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="94b9b-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="94b9b-112">Rutina GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="94b9b-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="94b9b-113">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="94b9b-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
