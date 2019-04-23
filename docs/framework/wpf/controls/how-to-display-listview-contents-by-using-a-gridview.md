---
title: 'Postupy: Zobrazení obsahu ListView použitím GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112785"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Postupy: Zobrazení obsahu ListView použitím GridView
Tento příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> režimu zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Můžete definovat režim zobrazení <xref:System.Windows.Controls.GridView> zadáním <xref:System.Windows.Controls.GridViewColumn> objekty. Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridViewColumn> objekty, které svázat data obsah, který je zadán pro <xref:System.Windows.Controls.ListView> ovládacího prvku. To <xref:System.Windows.Controls.GridView> příklad určuje tři <xref:System.Windows.Controls.GridViewColumn> objekty, které mapují `FirstName`, `LastName`, a `EmployeeNumber` pole `EmployeeInfoDataSource` , který je nastaven jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak se zobrazí v tomto příkladu.  
  
 ![Snímek obrazovky zobrazující ListView s výstupem ovládacího prvku GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView – přehled](listview-overview.md)
- [GridView – přehled](gridview-overview.md)
- [Témata s postupy](listview-how-to-topics.md)
