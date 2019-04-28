---
title: TreeView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: c0967aa506b087120c776389c2891ec9e0b0b64d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761400"
---
# <a name="treeview-overview"></a>TreeView – přehled
<xref:System.Windows.Controls.TreeView> Ovládacího prvku poskytuje způsob, jak zobrazit informace v hierarchické struktuře pomocí sbalitelné uzly. Toto téma představuje <xref:System.Windows.Controls.TreeView> a <xref:System.Windows.Controls.TreeViewItem> ovládací prvky a poskytuje jednoduché příklady jejich použití.  

<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>Co je ovládací prvek TreeView?  
 <xref:System.Windows.Controls.TreeView> je <xref:System.Windows.Controls.ItemsControl> položky, které vnoří pomocí <xref:System.Windows.Controls.TreeViewItem> ovládacích prvků. Následující příklad vytvoří <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Vytvoření objektu TreeView  
 <xref:System.Windows.Controls.TreeView> Ovládací prvek obsahuje hierarchii <xref:System.Windows.Controls.TreeViewItem> ovládacích prvků. A <xref:System.Windows.Controls.TreeViewItem> je ovládací prvek <xref:System.Windows.Controls.HeaderedItemsControl> , který má <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce.  
  
 Pokud definujete <xref:System.Windows.Controls.TreeView> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete explicitně definovat <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsah <xref:System.Windows.Controls.TreeViewItem> ovládací prvek a v položkách, které tvoří jeho kolekce. Předchozí obrázek ukazuje tuto metodu.  
  
 Můžete také určit, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako datové zdroje a pak zadejte <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> definovat <xref:System.Windows.Controls.TreeViewItem> obsah.  
  
 Chcete-li definovat rozložení <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku, můžete použít také <xref:System.Windows.HierarchicalDataTemplate> objekty. Další informace a příklad najdete v tématu [použití SelectedValue, SelectedValuePath a SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Pokud položka není <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku, je automaticky uzavřen <xref:System.Windows.Controls.TreeViewItem> řídí, kdy se <xref:System.Windows.Controls.TreeView> se zobrazí ovládací prvek.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozbalení a sbalení TreeViewItem  
 Pokud je uživatel rozbalí <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> je nastavena na `true`. Můžete rozbalit nebo sbalit <xref:System.Windows.Controls.TreeViewItem> bez jakéhokoli zásahu uživatele s přímým přístupem tak, že nastavíte <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> vlastnost `true` (expand) nebo `false` (sbalit). Při změně této vlastnosti <xref:System.Windows.Controls.TreeViewItem.Expanded> nebo <xref:System.Windows.Controls.TreeViewItem.Collapsed> dojde k události.  
  
 Při <xref:System.Windows.FrameworkElement.BringIntoView%2A> metoda je volána na <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, <xref:System.Windows.Controls.TreeViewItem> a jeho nadřazený objekt <xref:System.Windows.Controls.TreeViewItem> rozbalit ovládací prvky. Pokud <xref:System.Windows.Controls.TreeViewItem> není viditelný nebo částečně viditelný <xref:System.Windows.Controls.TreeView> posouvání, aby byla viditelná.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Výběr položky TreeViewItem  
 Když uživatel klikne <xref:System.Windows.Controls.TreeViewItem> , vyberte ovládací prvek <xref:System.Windows.Controls.TreeViewItem.Selected> dojde k události a jeho <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `true`. <xref:System.Windows.Controls.TreeViewItem> Stane <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView> ovládacího prvku. Naopak při změně výběru z <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, jeho <xref:System.Windows.Controls.TreeViewItem.Unselected> dojde k události a jeho <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Vlastnost <xref:System.Windows.Controls.TreeView> ovládací prvek je vlastnost jen pro čtení, proto nelze nastavit explicitně ji. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Vlastnost nastavena, když uživatel klikne na <xref:System.Windows.Controls.TreeViewItem> ovládací prvek nebo když <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je nastavena na `true` na <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku.  
  
 Použití <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti k určení <xref:System.Windows.Controls.TreeView.SelectedValue%2A> z <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Další informace najdete v tématu [použití SelectedValue, SelectedValuePath a SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Obslužné rutiny události můžete zaregistrovat na <xref:System.Windows.Controls.TreeView.SelectedItemChanged> událostí, aby bylo možné určit, kdy vybrané <xref:System.Windows.Controls.TreeViewItem> změny. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> , Která je zadaná pro událost obslužná rutina udává <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, což je předchozí výběr a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, což je aktuální výběr. Může být buď hodnotu `null` Pokud aplikace nebo uživatel nebyl proveden předchozí nebo aktuální výběr.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView – styl  
 Výchozí styl <xref:System.Windows.Controls.TreeView> nahradí ovládací prvek uvnitř <xref:System.Windows.Controls.StackPanel> objekt, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Při nastavení <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti <xref:System.Windows.Controls.TreeView>, tyto hodnoty se použijí na velikost <xref:System.Windows.Controls.StackPanel> objekt, který se zobrazí <xref:System.Windows.Controls.TreeView>. Pokud je větší než oblasti zobrazení, obsah, který se zobrazí <xref:System.Windows.Controls.ScrollViewer> automaticky zobrazí tak, aby uživatel mohl procházet <xref:System.Windows.Controls.TreeView> obsah.  
  
 Přizpůsobení vzhledu <xref:System.Windows.Controls.TreeViewItem> , nastavte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost vlastní <xref:System.Windows.Style>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontSize%2A> hodnot vlastností pro <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku pomocí <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Přidávání obrázků a další obsah k položkám prvku TreeView  
 Může obsahovat více než jeden objekt <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsah <xref:System.Windows.Controls.TreeViewItem>. Zahrnout více objektů v <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsahu, uzavřete objektů uvnitř ovládacího prvku na rozložení, jako například <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.StackPanel>.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> z <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.TextBlock> , že jsou oba uzavřeny v <xref:System.Windows.Controls.DockPanel> ovládacího prvku.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , který obsahuje <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.TextBlock> , které jsou uzavřeny v <xref:System.Windows.Controls.DockPanel> ovládacího prvku. Můžete použít <xref:System.Windows.DataTemplate> nastavit <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> nebo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pro <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Témata s postupy](treeview-how-to-topics.md)
- [Model obsahu WPF](wpf-content-model.md)
