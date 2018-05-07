---
title: 'Postupy: Připojení TreeView k datům nezjistitelné hloubky'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 30e328c94e1e1da4641e93dd5f5730eab2d8af1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Postupy: Připojení TreeView k datům nezjistitelné hloubky
Může dojít k situaci, kdy budete chtít vytvořit vazbu <xref:System.Windows.Controls.TreeView> ke zdroji dat, jejichž hloubka není znám.  Tato situace může nastat, když jsou data rekurzivní ve své podstatě, například systém souborů, složek, kde může obsahovat složky, nebo organizační struktury společnosti, kde zaměstnanci mají ostatní zaměstnanci jako přímé podřízené.  
  
 Zdroje dat musí být hierarchické objektový model. Například `Employee` třída může obsahovat kolekce zaměstnanec objekty, které jsou přímé podřízené zaměstnance. Pokud data představuje způsobem, který není hierarchické, musíte sestavit hierarchické reprezentace data.  
  
 Když nastavíte <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> vlastnost a pokud <xref:System.Windows.Controls.ItemsControl> generuje <xref:System.Windows.Controls.ItemsControl> pro každou podřízenou položku a pak podřízená <xref:System.Windows.Controls.ItemsControl> používá stejnou <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> jako nadřazená položka. Například pokud nastavíte <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost vázané na data <xref:System.Windows.Controls.TreeView>, každý <xref:System.Windows.Controls.TreeViewItem> který je generovaný používá <xref:System.Windows.DataTemplate> který byl přiřazen <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> Umožňuje určit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.TreeViewItem>, nebo jakoukoli <xref:System.Windows.Controls.HeaderedItemsControl>, v šabloně data. Když nastavíte <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> vlastnost, která hodnota je použít, když <xref:System.Windows.HierarchicalDataTemplate> platí. Pomocí <xref:System.Windows.HierarchicalDataTemplate>, můžete sadu rekurzivně <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každou <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TreeView> hierarchické dat a používání <xref:System.Windows.HierarchicalDataTemplate> k určení <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každou <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> Váže na data XML, který představuje zaměstnanci ve společnosti.  Každý `Employee` element může obsahovat jiné `Employee` elementy udávajících o podřízenosti. Protože data jsou rekurzivní, <xref:System.Windows.HierarchicalDataTemplate> lze použít pro každou úroveň.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)
