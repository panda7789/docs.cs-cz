---
title: "Postupy: Vytváření ListViewItems pomocí CheckBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6ebb3671dcc65d690fde5d4796c9034553eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: témata](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Rutina GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
