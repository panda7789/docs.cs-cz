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
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a>Postupy: Zobrazení data pomocí GridViewRowPresenter
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty, které chcete zobrazit data ve sloupcích.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit <xref:System.Windows.Controls.GridViewColumnCollection> který zobrazí <xref:System.DateTime.DayOfWeek%2A> a <xref:System.DateTime.Year%2A> z <xref:System.DateTime> objekt pomocí <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objekty. Tento příklad také definuje <xref:System.Windows.Style> pro <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
