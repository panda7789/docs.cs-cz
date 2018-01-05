---
title: "TreeView – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e5f6b3d0a185754bc0d8d8ee726ca13443ccdc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-overview"></a>TreeView – přehled
<xref:System.Windows.Controls.TreeView> Řízení poskytuje způsob, jak zobrazit informace v hierarchická struktura pomocí sbalitelné uzly. Toto téma představuje <xref:System.Windows.Controls.TreeView> a <xref:System.Windows.Controls.TreeViewItem> ovládací prvky a poskytuje jednoduché příklady, jak jejich použití.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>Co je elementu TreeView?  
 <xref:System.Windows.Controls.TreeView>je <xref:System.Windows.Controls.ItemsControl> který vnořena položek s použitím <xref:System.Windows.Controls.TreeViewItem> ovládací prvky. Následující příklad vytvoří <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Vytváření elementu TreeView  
 <xref:System.Windows.Controls.TreeView> Ovládací prvek obsahuje hierarchii <xref:System.Windows.Controls.TreeViewItem> ovládací prvky. A <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku <xref:System.Windows.Controls.HeaderedItemsControl> má <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce.  
  
 Pokud definujete <xref:System.Windows.Controls.TreeView> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], explicitně můžete definovat <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsah <xref:System.Windows.Controls.TreeViewItem> řízení a položky, které tvoří jeho kolekce. Předchozí obrázek ukazuje tuto metodu.  
  
 Můžete také určit, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako datový zdroje a pak zadejte <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> k definování <xref:System.Windows.Controls.TreeViewItem> obsah.  
  
 Chcete-li definovat rozložení <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, můžete použít také <xref:System.Windows.HierarchicalDataTemplate> objekty. Další informace a příklady naleznete v tématu [použití SelectedValue SelectedValuePath a SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Pokud položka není <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, je automaticky uzavřen podle <xref:System.Windows.Controls.TreeViewItem> řídit, kdy <xref:System.Windows.Controls.TreeView> ovládací prvek je zobrazen.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozbalení a sbalení TreeViewItem  
 Pokud uživatel rozšíří <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> je nastavena na `true`. Můžete rozbalit nebo sbalit <xref:System.Windows.Controls.TreeViewItem> bez jakéhokoli zásahu uživatele přímé nastavením <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> vlastnost `true` (expand) nebo `false` (sbalit). Při změně této vlastnosti <xref:System.Windows.Controls.TreeViewItem.Expanded> nebo <xref:System.Windows.Controls.TreeViewItem.Collapsed> dojde k události.  
  
 Když <xref:System.Windows.FrameworkElement.BringIntoView%2A> metoda je volána v <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, <xref:System.Windows.Controls.TreeViewItem> a jeho nadřazený objekt <xref:System.Windows.Controls.TreeViewItem> rozbalte ovládací prvky. Pokud <xref:System.Windows.Controls.TreeViewItem> není viditelný nebo částečně viditelná, <xref:System.Windows.Controls.TreeView> viditelné vytvořit viditelné.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Výběr TreeViewItem  
 Když uživatel klikne <xref:System.Windows.Controls.TreeViewItem> , vyberte ovládací prvek <xref:System.Windows.Controls.TreeViewItem.Selected> dojde k události a jeho <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `true`. <xref:System.Windows.Controls.TreeViewItem> Také změní <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView> ovládacího prvku. Naopak při výběru změní z <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, jeho <xref:System.Windows.Controls.TreeViewItem.Unselected> dojde k události a jeho <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Vlastnost <xref:System.Windows.Controls.TreeView> ovládací prvek je vlastnost jen pro čtení; proto nemůžete explicitně nastavit ho. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Vlastnost nastavena, když uživatel klikne na <xref:System.Windows.Controls.TreeViewItem> ovládací prvek nebo když <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `true` na <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
 Použití <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti k určení <xref:System.Windows.Controls.TreeView.SelectedValue%2A> z <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Další informace najdete v tématu [použití SelectedValue SelectedValuePath a SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Obslužné rutiny události můžete zaregistrovat na <xref:System.Windows.Controls.TreeView.SelectedItemChanged> událostí k určení, kdy vybrané <xref:System.Windows.Controls.TreeViewItem> změny. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> , Je zadané události určuje obslužné rutiny <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, tedy předchozí výběr a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, což je aktuální výběr. Může být buď hodnota `null` Pokud aplikaci nebo uživatele nebyla vytvořili výběr předchozí nebo aktuální.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView – styl  
 Výchozí styl pro <xref:System.Windows.Controls.TreeView> řízení nahradí uvnitř <xref:System.Windows.Controls.StackPanel> objekt, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Když nastavíte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti <xref:System.Windows.Controls.TreeView>, velikost se používají tyto hodnoty <xref:System.Windows.Controls.StackPanel> objekt, který zobrazí <xref:System.Windows.Controls.TreeView>. Pokud je větší než oblasti zobrazení obsahu k zobrazení <xref:System.Windows.Controls.ScrollViewer> se automaticky zobrazí tak, aby uživatel můžete procházet <xref:System.Windows.Controls.TreeView> obsah.  
  
 Chcete-li přizpůsobit vzhled <xref:System.Windows.Controls.TreeViewItem> , nastavte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, která má vlastní <xref:System.Windows.Style>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> hodnoty vlastností <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku pomocí <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Přidání bitové kopie a další obsah položkám TreeView  
 Může obsahovat více než jeden objekt v <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsah <xref:System.Windows.Controls.TreeViewItem>. Zahrnout více objektů v <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsahu, jako například uzavřete objekty uvnitř prvku rozložení <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.StackPanel>.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> z <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.TextBlock> , že jsou oba uzavřené v <xref:System.Windows.Controls.DockPanel> ovládacího prvku.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> obsahující <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.TextBlock> , jsou uzavřené v <xref:System.Windows.Controls.DockPanel> ovládacího prvku. Můžete použít <xref:System.Windows.DataTemplate> nastavit <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> nebo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pro <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [Model obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
