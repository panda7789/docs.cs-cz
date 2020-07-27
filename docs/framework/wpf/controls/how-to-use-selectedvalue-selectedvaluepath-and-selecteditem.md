---
title: 'Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem'
description: Naučte se používat vlastnosti SelectedValue a SelectedValuePath k určení hodnoty pro SelectedItem prvku TreeView Windows Presentation Foundation.
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166271"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem
Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnosti a <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> k určení hodnoty pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> .  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Vlastnost poskytuje způsob, jak zadat <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> v <xref:System.Windows.Controls.TreeView> . <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Představuje objekt v <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekci a <xref:System.Windows.Controls.TreeView> zobrazí hodnotu jedné vlastnosti vybrané položky. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Vlastnost určuje cestu k vlastnosti, která se používá k určení hodnoty <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Vlastnosti. Příklady v tomto tématu ilustrují tento koncept.  
  
 Následující příklad ukazuje <xref:System.Windows.Data.XmlDataProvider> , který obsahuje informace o zaměstnancích.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 Následující příklad definuje <xref:System.Windows.HierarchicalDataTemplate> , který ukazuje `EmployeeName` a `EmployeeWorkDay` `Employee` . Všimněte si, že <xref:System.Windows.HierarchicalDataTemplate> neurčuje `EmployeeNumber` jako součást šablony.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.TreeView> , který používá dříve definovaný <xref:System.Windows.HierarchicalDataTemplate> a který nastavuje <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost na `EmployeeNumber` . Když vyberete `EmployeeName` v <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost vrátí `EmployeeInfo` datovou položku, která odpovídá vybranému `EmployeeName` . Protože je však <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> nastaveno na `EmployeeNumber` , <xref:System.Windows.Controls.TreeView.SelectedValue%2A> je nastavena na `EmployeeNumber` .  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView – přehled](treeview-overview.md)
- [– postupy](treeview-how-to-topics.md)
