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
ms.workload: dotnet
ms.openlocfilehash: ee2885868c07b00f16290b6414e7f7bdd64fd68c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="da57f-102">Postupy: Zobrazení obsahu ListView použitím GridView</span><span class="sxs-lookup"><span data-stu-id="da57f-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="da57f-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režim zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da57f-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da57f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="da57f-104">Example</span></span>  
 <span data-ttu-id="da57f-105">Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty.</span><span class="sxs-lookup"><span data-stu-id="da57f-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="da57f-106">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které k obsahu data, která je určená pro vytvoření vazby <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da57f-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="da57f-107">To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které jsou mapovány na `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="da57f-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="da57f-108">Následující obrázek znázorňuje, jak tento příklad zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="da57f-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="da57f-109">![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="da57f-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da57f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="da57f-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="da57f-111">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="da57f-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="da57f-112">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="da57f-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="da57f-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="da57f-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
