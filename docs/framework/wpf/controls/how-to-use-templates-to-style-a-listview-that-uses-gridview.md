---
title: 'Postupy: Použití šablon na styl ListView používající GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 481d92d4301401f8ba87c4912cd44b17c5104b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553829"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Postupy: Použití šablon na styl ListView používající GridView
Tento příklad ukazuje způsob použití <xref:System.Windows.DataTemplate> a <xref:System.Windows.Style> objekty, které chcete určit vzhled <xref:System.Windows.Controls.ListView> ovládací prvek, který používá <xref:System.Windows.Controls.GridView> režimu zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklady zobrazují <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které přizpůsobení vzhledu záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které chcete nastavit <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> vlastnosti <xref:System.Windows.Controls.GridViewColumn>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost definuje obsah buňky sloupců.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> jsou pouze dvě několik vlastností, které můžete použít k přizpůsobení vzhledu záhlaví sloupců pro <xref:System.Windows.Controls.GridView> ovládacího prvku. Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , přizpůsobení vzhledu buněk v <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.DataTemplate> definovat obsah <xref:System.Windows.Controls.GridViewColumn> buňky. Tato šablona se používá namísto <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnosti, které se zobrazí v předchozí <xref:System.Windows.Controls.GridViewColumn> příklad.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
