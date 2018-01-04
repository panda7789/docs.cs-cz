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
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Postupy: Zobrazení obsahu ListView použitím GridView
Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režim zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty. Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které k obsahu data, která je určená pro vytvoření vazby <xref:System.Windows.Controls.ListView> ovládacího prvku. To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které jsou mapovány na `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak tento příklad zobrazuje.  
  
 ![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
