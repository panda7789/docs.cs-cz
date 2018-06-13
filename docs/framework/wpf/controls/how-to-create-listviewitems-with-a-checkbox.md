---
title: 'Postupy: Vytváření ListViewItems pomocí CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 424bc25f9c584017d80ba1c8f1517211595fd247
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552672"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Postupy: Vytváření ListViewItems pomocí CheckBox
Tento příklad ukazuje, jak zobrazit sloupec <xref:System.Windows.Controls.CheckBox> ovládacích prvků do <xref:System.Windows.Controls.ListView> ovládací prvek, který používá <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Příklad  
 Chcete-li vytvořit sloupec, který obsahuje <xref:System.Windows.Controls.CheckBox> ovládacích prvků do <xref:System.Windows.Controls.ListView>, vytvoření <xref:System.Windows.DataTemplate> obsahující <xref:System.Windows.Controls.CheckBox>. Nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.  
  
 Následující příklad ukazuje <xref:System.Windows.DataTemplate> obsahující <xref:System.Windows.Controls.CheckBox>. V příkladu váže <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> hodnota vlastnosti <xref:System.Windows.Controls.ListViewItem> který ji obsahuje. Proto když <xref:System.Windows.Controls.ListViewItem> obsahující <xref:System.Windows.Controls.CheckBox> je vybraná, <xref:System.Windows.Controls.CheckBox> je zaškrtnuta možnost.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 Následující příklad ukazuje, jak vytvořit sloupec <xref:System.Windows.Controls.CheckBox> ovládací prvky. Chcete-li sloupec v příkladu je nastavena <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> vlastnost <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
