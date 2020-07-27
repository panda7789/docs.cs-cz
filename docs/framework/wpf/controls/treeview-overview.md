---
title: TreeView – přehled
description: Přečtěte si, jak Windows Presentation Foundation ovládací prvek TreeView zobrazuje informace v hierarchické struktuře pomocí uzlů, včetně jednoduchých příkladů.
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164529"
---
# <a name="treeview-overview"></a>TreeView – přehled
<xref:System.Windows.Controls.TreeView>Ovládací prvek poskytuje způsob zobrazení informací v hierarchické struktuře pomocí sbalitelných uzlů. Toto téma představuje <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.TreeViewItem> ovládací prvky a a poskytuje jednoduché příklady jejich použití.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Co je TreeView?  
 <xref:System.Windows.Controls.TreeView>je <xref:System.Windows.Controls.ItemsControl> vnoření položek pomocí <xref:System.Windows.Controls.TreeViewItem> ovládacích prvků. Následující příklad vytvoří <xref:System.Windows.Controls.TreeView> .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Vytvoření prvku TreeView  
 <xref:System.Windows.Controls.TreeView>Ovládací prvek obsahuje hierarchii <xref:System.Windows.Controls.TreeViewItem> ovládacích prvků. <xref:System.Windows.Controls.TreeViewItem>Ovládací prvek je <xref:System.Windows.Controls.HeaderedItemsControl> , který má <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekci.  
  
 Pokud definujete pomocí <xref:System.Windows.Controls.TreeView> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , můžete explicitně definovat <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsah <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku a položky, které tvoří kolekci. Předchozí ilustrace znázorňuje tuto metodu.  
  
 Můžete také zadat <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako zdroj dat a pak zadat <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> definovat <xref:System.Windows.Controls.TreeViewItem> obsah.  
  
 Chcete-li definovat rozložení <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku, můžete také použít <xref:System.Windows.HierarchicalDataTemplate> objekty. Další informace a příklad najdete v tématu [použití SelectedValue, SelectedValuePath a SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Pokud položka není <xref:System.Windows.Controls.TreeViewItem> ovládacím prvkem, je automaticky uzavřena <xref:System.Windows.Controls.TreeViewItem> ovládacím prvkem, když <xref:System.Windows.Controls.TreeView> je ovládací prvek zobrazen.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozbalení a sbalení TreeViewItem  
 Pokud uživatel rozbalí a <xref:System.Windows.Controls.TreeViewItem> , <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> vlastnost je nastavena na `true` . Můžete také rozbalit nebo sbalit <xref:System.Windows.Controls.TreeViewItem> bez akce přímého uživatele nastavením <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> vlastnosti na `true` (rozbalit) nebo `false` (sbalit). Při změně této vlastnosti dojde k <xref:System.Windows.Controls.TreeViewItem.Expanded> <xref:System.Windows.Controls.TreeViewItem.Collapsed> události nebo.  
  
 Když <xref:System.Windows.FrameworkElement.BringIntoView%2A> je metoda volána na <xref:System.Windows.Controls.TreeViewItem> ovládacím prvku, <xref:System.Windows.Controls.TreeViewItem> a jeho nadřazené <xref:System.Windows.Controls.TreeViewItem> ovládací prvky se rozšíří. Pokud <xref:System.Windows.Controls.TreeViewItem> není viditelná nebo částečně viditelný, <xref:System.Windows.Controls.TreeView> posune se na to, aby se zobrazily.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem výběr  
 Když uživatel klikne na <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, který ho má vybrat, <xref:System.Windows.Controls.TreeViewItem.Selected> dojde k události a <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> vlastnost je nastavená na `true` . <xref:System.Windows.Controls.TreeViewItem>Také se <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView> ovládacího prvku stala. Naopak, pokud se výběr změní z <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku, dojde k jeho <xref:System.Windows.Controls.TreeViewItem.Unselected> události a <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> vlastnost je nastavena na `false` .  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Vlastnost <xref:System.Windows.Controls.TreeView> ovládacího prvku je vlastnost jen pro čtení, proto ji nelze explicitně nastavit. <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Vlastnost je nastavena, pokud uživatel klikne na <xref:System.Windows.Controls.TreeViewItem> ovládací prvek nebo pokud <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> je vlastnost nastavena na hodnotu `true` na <xref:System.Windows.Controls.TreeViewItem> ovládacím prvku.  
  
 Vlastnost použijte <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> k určení typu <xref:System.Windows.Controls.TreeView.SelectedValue%2A> <xref:System.Windows.Controls.TreeView.SelectedItem%2A> . Další informace najdete v tématu [použití SelectedValue, SelectedValuePath a SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Můžete zaregistrovat obslužnou rutinu události pro <xref:System.Windows.Controls.TreeView.SelectedItemChanged> událost, aby bylo možné určit, kdy se mají vybrané <xref:System.Windows.Controls.TreeViewItem> změny změnit. , <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Který je poskytnut obslužné rutině události, určuje <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> , který je předchozí výběr, a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> , který je aktuálním výběrem. Jedna hodnota může být, `null` Pokud aplikace nebo uživatel neudělali předchozí nebo aktuální výběr.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView – styl  
 Výchozí styl <xref:System.Windows.Controls.TreeView> ovládacího prvku umístí do <xref:System.Windows.Controls.StackPanel> objektu, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládací prvek. Při nastavení <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> vlastností a pro <xref:System.Windows.Controls.TreeView> se tyto hodnoty použijí pro velikost <xref:System.Windows.Controls.StackPanel> objektu, který zobrazuje <xref:System.Windows.Controls.TreeView> . Pokud je obsah, který se má zobrazit, větší než oblast zobrazení, <xref:System.Windows.Controls.ScrollViewer> zobrazí se automaticky, aby uživatel mohl procházet <xref:System.Windows.Controls.TreeView> obsah.  
  
 Chcete-li přizpůsobit vzhled <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku, nastavte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost na hodnotu Custom (vlastní) <xref:System.Windows.Style> .  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A> hodnoty vlastností a pro <xref:System.Windows.Controls.TreeViewItem> ovládací prvek pomocí <xref:System.Windows.FrameworkElement.Style%2A> .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Přidávání obrázků a dalšího obsahu k položkám TreeView  
 Do obsahu objektu můžete zahrnout více než jeden objekt <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> . Chcete-li zahrnout více objektů v <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsahu, vložte objekty do ovládacího prvku rozložení, jako je například <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.StackPanel> .  
  
 Následující příklad ukazuje, jak definovat a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.TextBlock> , které jsou uzavřeny v <xref:System.Windows.Controls.DockPanel> ovládacím prvku.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.DataTemplate> , který obsahuje <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.TextBlock> , které jsou uzavřeny v <xref:System.Windows.Controls.DockPanel> ovládacím prvku. Můžete použít <xref:System.Windows.DataTemplate> k nastavení <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> nebo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pro <xref:System.Windows.Controls.TreeViewItem> .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [– postupy](treeview-how-to-topics.md)
- [Model obsahu WPF](wpf-content-model.md)
