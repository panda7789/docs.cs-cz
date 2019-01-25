---
title: 'Postupy: Zobrazení obsahu ListView použitím GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 0e2b37cb061cc92b34c3a4f94bcd42e8ffc69ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606004"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Postupy: Zobrazení obsahu ListView použitím GridView
Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režimu zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty. Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které svázat data obsah, který je zadán pro <xref:System.Windows.Controls.ListView> ovládacího prvku. To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které mapují `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , který je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak se zobrazí v tomto příkladu.  
  
 ![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
