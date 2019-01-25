---
title: 'Postupy: Použití šablon na styl ListView používající GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: f1ff608f03c7e9acdba49ca7f76938caec527285
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664392"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Postupy: Použití šablon na styl ListView používající GridView
Tento příklad ukazuje způsob použití <xref:System.Windows.DataTemplate> a <xref:System.Windows.Style> objekty k určení vzhledu <xref:System.Windows.Controls.ListView> ovládací prvek, který se používá <xref:System.Windows.Controls.GridView> režim zobrazení.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty, které přizpůsobit vzhled pro záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 Následující příklad ukazuje, jak pomocí nich <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> objekty nastavit <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> vlastnosti <xref:System.Windows.Controls.GridViewColumn>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost definuje obsah buňky sloupce.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> jsou jenom dvě několik vlastností, které můžete použít k přizpůsobení vzhledu záhlaví sloupce <xref:System.Windows.Controls.GridView> ovládacího prvku. Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , který přizpůsobí vzhledu buněk v <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 Následující příklad ukazuje, jak pomocí tohoto <xref:System.Windows.DataTemplate> definovat obsah <xref:System.Windows.Controls.GridViewColumn> buňky. Tato šablona se používá namísto <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost, která se zobrazí v předchozím <xref:System.Windows.Controls.GridViewColumn> příklad.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
