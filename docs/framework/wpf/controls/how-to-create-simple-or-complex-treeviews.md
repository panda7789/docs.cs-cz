---
title: 'Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: d6f9653304b67948d8a8995d1582cb10b012ee06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609132"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews
Tento příklad ukazuje, jak vytvořit jednoduché nebo složité <xref:System.Windows.Controls.TreeView> ovládacích prvků.  
  
 A <xref:System.Windows.Controls.TreeView> se skládá z hierarchie <xref:System.Windows.Controls.TreeViewItem> ovládací prvky, které mohou obsahovat jednoduché textových řetězců a také mnohem složitější obsahu, jako například <xref:System.Windows.Controls.Button> ovládací prvky nebo <xref:System.Windows.Controls.StackPanel> s vložený obsah. Můžete explicitně definovat <xref:System.Windows.Controls.TreeView> obsah nebo zdroj dat může poskytovat obsahu. Toto téma obsahuje příklady těchto konceptů.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Vlastnost <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah, který <xref:System.Windows.Controls.TreeView> zobrazí pro danou položku. A <xref:System.Windows.Controls.TreeViewItem> může mít také <xref:System.Windows.Controls.TreeViewItem> ovládací prvky jako jeho podřízené prvky a můžete definovat pomocí těchto podřízených elementů <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.  
  
 Následující příklad ukazuje, jak explicitně definovat <xref:System.Windows.Controls.TreeViewItem> obsahu tak, že nastavíte <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost textový řetězec.  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Následující příklad ukazuje, jak definovat podřízené prvky <xref:System.Windows.Controls.TreeViewItem> definováním <xref:System.Windows.Controls.ItemsControl.Items%2A> , které jsou <xref:System.Windows.Controls.Button> ovládacích prvků.  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Data.XmlDataProvider> poskytuje <xref:System.Windows.Controls.TreeViewItem> obsah a <xref:System.Windows.HierarchicalDataTemplate> definuje vzhled elementů obsah.  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah <xref:System.Windows.Controls.DockPanel> ovládací prvky, které se mají vložit obsah.  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView – přehled](../../../../docs/framework/wpf/controls/treeview-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
