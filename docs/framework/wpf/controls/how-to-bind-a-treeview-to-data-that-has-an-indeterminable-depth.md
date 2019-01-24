---
title: 'Postupy: Připojení TreeView k datům nezjistitelné hloubky'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 702a86f049635423a31e554d205dcc3cf4aa799d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605364"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Postupy: Připojení TreeView k datům nezjistitelné hloubky
Může nastat situace, kdy budete chtít vytvořit vazbu <xref:System.Windows.Controls.TreeView> ke zdroji dat, jejichž hloubky není znám.  Tato situace může nastat, když jsou data rekurzivní ze své podstaty, jako je například systém souborů, složek, ve kterém můžou obsahovat složky, nebo organizační struktury vaší společnosti, kde zaměstnanci mají ostatní zaměstnanci jako přímé podřízené.  
  
 Zdroje dat musí být hierarchický objekt modelu. Například `Employee` třídy mohou obsahovat kolekce objektů zaměstnanců, které jsou přímých podřízených zaměstnance. Pokud data je reprezentována způsobem, který není hierarchický, je nutné vytvořit Hierarchická reprezentace data.  
  
 Při nastavení <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> vlastnost a pokud <xref:System.Windows.Controls.ItemsControl> generuje <xref:System.Windows.Controls.ItemsControl> pro každou podřízenou položku a pak podřízené <xref:System.Windows.Controls.ItemsControl> používá stejný <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> jako nadřazený. Například, pokud jste nastavili <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost vázaný na data <xref:System.Windows.Controls.TreeView>, každý <xref:System.Windows.Controls.TreeViewItem> , který je generovaný používá <xref:System.Windows.DataTemplate> , který byl přiřazen <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> Umožňuje určit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.TreeViewItem>, ani na žádného <xref:System.Windows.Controls.HeaderedItemsControl>, na šabloně data. Při nastavení <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> vlastnost, která hodnota je použít, pokud <xref:System.Windows.HierarchicalDataTemplate> platí. Pomocí <xref:System.Windows.HierarchicalDataTemplate>, můžete sadu rekurzivně <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každou <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TreeView> hierarchická data a použít <xref:System.Windows.HierarchicalDataTemplate> zadat <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každou <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> Vytvoří vazbu na data XML, který představuje zaměstnanců ve společnosti.  Každý `Employee` element může obsahovat další `Employee` prvků, které mají označení o podřízenosti. Protože data je rekurzivní, <xref:System.Windows.HierarchicalDataTemplate> můžou uplatnit na každé úrovni.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)
