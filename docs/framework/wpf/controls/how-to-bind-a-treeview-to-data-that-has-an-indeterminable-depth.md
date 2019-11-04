---
title: 'Postupy: Připojení TreeView k datům nezjistitelné hloubky'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458612"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Postupy: Připojení TreeView k datům nezjistitelné hloubky
Může nastat situace, kdy budete chtít vytvořit vazby <xref:System.Windows.Controls.TreeView> ke zdroji dat, jehož hloubka není známá.  K tomu může dojít, když jsou data rekurzivní, jako je třeba systém souborů, kde složky můžou obsahovat složky nebo organizační strukturu společnosti, kde zaměstnanci mají jiné zaměstnance jako přímé sestavy.  
  
 Zdroj dat musí mít hierarchický objektový model. Například třída `Employee` může obsahovat kolekci objektů zaměstnanců, které jsou přímými sestavami zaměstnance. Pokud jsou data reprezentována způsobem, který není hierarchický, je nutné vytvořit hierarchickou reprezentaci dat.  
  
 Když nastavíte vlastnost <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.ItemsControl> vygeneruje <xref:System.Windows.Controls.ItemsControl> pro každou podřízenou položku, pak podřízená <xref:System.Windows.Controls.ItemsControl> použije stejné <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> jako nadřazené. Například pokud nastavíte vlastnost <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> v <xref:System.Windows.Controls.TreeView>vázaných na data, každý generovaný <xref:System.Windows.Controls.TreeViewItem> použije <xref:System.Windows.DataTemplate> přiřazený k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> umožňuje zadat <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.TreeViewItem>nebo libovolné <xref:System.Windows.Controls.HeaderedItemsControl>v šabloně dat. Při nastavení vlastnosti <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> se tato hodnota používá při použití <xref:System.Windows.HierarchicalDataTemplate>. Pomocí <xref:System.Windows.HierarchicalDataTemplate>můžete rekurzivně nastavit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každý <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazby <xref:System.Windows.Controls.TreeView> k hierarchickým datům a použít <xref:System.Windows.HierarchicalDataTemplate> k určení <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro každý <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> se váže k datům XML reprezentujícím zaměstnance ve společnosti.  Každý prvek `Employee` může obsahovat další `Employee` prvky, které označují, kdo z nich sestavy. Vzhledem k tomu, že jsou data rekurzivní, lze <xref:System.Windows.HierarchicalDataTemplate> použít na každou úroveň.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
