---
title: 'Postupy: Vytvoření ListViewItems pomocí CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 1ed623495529609c83c0ced68bfc1696c29d4570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682239"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Postupy: Vytvoření ListViewItems pomocí CheckBox
Tento příklad ukazuje, jak zobrazit sloupec <xref:System.Windows.Controls.CheckBox> ovládacích prvků v <xref:System.Windows.Controls.ListView> ovládací prvek, který se používá <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Příklad  
 Chcete vytvořit sloupec, který obsahuje <xref:System.Windows.Controls.CheckBox> ovládacích prvků v <xref:System.Windows.Controls.ListView>, vytvořit <xref:System.Windows.DataTemplate> , která obsahuje <xref:System.Windows.Controls.CheckBox>. Nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.  
  
 Následující příklad ukazuje <xref:System.Windows.DataTemplate> , která obsahuje <xref:System.Windows.Controls.CheckBox>. V příkladu vytvoří vazbu <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> hodnotu vlastnosti <xref:System.Windows.Controls.ListViewItem> , který jej obsahuje. Proto, když <xref:System.Windows.Controls.ListViewItem> , která obsahuje <xref:System.Windows.Controls.CheckBox> zaškrtnuto, <xref:System.Windows.Controls.CheckBox> je zaškrtnuté políčko.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 Následující příklad ukazuje, jak vytvořit sloupec <xref:System.Windows.Controls.CheckBox> ovládacích prvků. Chcete-li sloupec, příklad nastaví <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> vlastnost <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
