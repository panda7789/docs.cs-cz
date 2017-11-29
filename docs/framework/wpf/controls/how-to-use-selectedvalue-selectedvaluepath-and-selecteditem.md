---
title: "Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdc478d62ca97f8f61c26fbbf1ee6c3ea8b4e189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti můžete zadat hodnotu pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost poskytuje způsob, jak určit <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> v <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Představuje objekt v <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce a <xref:System.Windows.Controls.TreeView> zobrazí hodnotu vlastnosti jediné vybrané položky. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost určuje cestu k vlastnosti, která se používá k určení hodnotu <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost. Příklady v tomto tématu ilustrují tento koncept.  
  
 Následující příklad ukazuje <xref:System.Windows.Data.XmlDataProvider> obsahující informace o zaměstnancích.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 V následujícím příkladu definuje <xref:System.Windows.HierarchicalDataTemplate> , zobrazí `EmployeeName` a `EmployeeWorkDay` z `Employee`. Všimněte si, že <xref:System.Windows.HierarchicalDataTemplate> neurčuje `EmployeeNumber` v rámci šablony.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.TreeView> používající dříve definovaný <xref:System.Windows.HierarchicalDataTemplate> a nastaví se <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost, která má `EmployeeNumber`. Vyberete-li `EmployeeName` v <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost vrátí `EmployeeInfo` datová položka, která odpovídá vybrané `EmployeeName`. Ale protože <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tohoto <xref:System.Windows.Controls.TreeView> je nastaven na `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> je nastaven na `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView – přehled](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
