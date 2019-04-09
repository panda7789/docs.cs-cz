---
title: 'Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169699"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti, které chcete zadat hodnotu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost poskytuje způsob, jak určit <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> v <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Představuje objekt <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce a <xref:System.Windows.Controls.TreeView> zobrazuje hodnotu jedné vlastnosti vybrané položky. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost určuje cestu k vlastnosti, která se používá k určení hodnoty <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost. Příklady v tomto tématu ilustrují tento koncept.  
  
 Následující příklad ukazuje <xref:System.Windows.Data.XmlDataProvider> , který obsahuje informace o zaměstnancích.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 Následující příklad definuje <xref:System.Windows.HierarchicalDataTemplate> , který se zobrazí `EmployeeName` a `EmployeeWorkDay` z `Employee`. Všimněte si, že <xref:System.Windows.HierarchicalDataTemplate> neurčuje `EmployeeNumber` jako součást šablony.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.TreeView> , která používá dříve definované <xref:System.Windows.HierarchicalDataTemplate> a nastaví se <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost `EmployeeNumber`. Když vyberete `EmployeeName` v <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vrátí vlastnost `EmployeeInfo` datová položka, která odpovídá vybrané `EmployeeName`. Ale protože <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tohoto <xref:System.Windows.Controls.TreeView> je nastavena na `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> je nastavena na `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView – přehled](treeview-overview.md)
- [– postupy](treeview-how-to-topics.md)
