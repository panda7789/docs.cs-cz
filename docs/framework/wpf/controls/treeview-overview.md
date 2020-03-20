---
title: TreeView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187374"
---
# <a name="treeview-overview"></a>TreeView – přehled
Ovládací <xref:System.Windows.Controls.TreeView> prvek poskytuje způsob, jak zobrazit informace v hierarchické struktuře pomocí sbalitelných uzlů. Toto téma <xref:System.Windows.Controls.TreeView> představuje <xref:System.Windows.Controls.TreeViewItem> ovládací prvky a poskytuje jednoduché příklady jejich použití.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Co je TreeView?  
 <xref:System.Windows.Controls.TreeView><xref:System.Windows.Controls.ItemsControl> je, který vnoří <xref:System.Windows.Controls.TreeViewItem> položky pomocí ovládacích prvků. Následující příklad vytvoří <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Vytvoření treeview  
 Ovládací <xref:System.Windows.Controls.TreeView> prvek obsahuje <xref:System.Windows.Controls.TreeViewItem> hierarchii ovládacích prvků. Ovládací <xref:System.Windows.Controls.TreeViewItem> prvek <xref:System.Windows.Controls.HeaderedItemsControl> je, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> který <xref:System.Windows.Controls.ItemsControl.Items%2A> má a a kolekce.  
  
 Pokud definujete <xref:System.Windows.Controls.TreeView> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete explicitně <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> definovat obsah <xref:System.Windows.Controls.TreeViewItem> ovládacího prvku a položky, které tvoří jeho kolekce. Předchozí obrázek ukazuje tuto metodu.  
  
 Můžete také zadat <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako zdroj dat a <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pak zadat <xref:System.Windows.Controls.TreeViewItem> a definovat obsah.  
  
 Chcete-li definovat <xref:System.Windows.Controls.TreeViewItem> rozložení ovládacího prvku, můžete také použít <xref:System.Windows.HierarchicalDataTemplate> objekty. Další informace a příklad naleznete v [tématech Použití selectedvalue, selectedvaluevavky a vybrané položky](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Pokud položka není <xref:System.Windows.Controls.TreeViewItem> ovládací prvek, je automaticky <xref:System.Windows.Controls.TreeViewItem> uzavřena <xref:System.Windows.Controls.TreeView> ovládacím prvkem při zobrazení ovládacího prvku.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozbalení a sbalení položky TreeViewItem  
 Pokud uživatel rozbalí <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> vlastnost je `true`nastavena na . Můžete také rozbalit <xref:System.Windows.Controls.TreeViewItem> nebo sbalit bez <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> jakékoli `true` přímé akce `false` uživatele nastavením vlastnosti na (rozbalit) nebo (sbalit). Když se tato <xref:System.Windows.Controls.TreeViewItem.Expanded> vlastnost <xref:System.Windows.Controls.TreeViewItem.Collapsed> změní, dojde k události nebo události.  
  
 Při <xref:System.Windows.FrameworkElement.BringIntoView%2A> volání metody na <xref:System.Windows.Controls.TreeViewItem> ovládací <xref:System.Windows.Controls.TreeViewItem> prvek a <xref:System.Windows.Controls.TreeViewItem> jeho nadřazené ovládací prvky rozbalit. Pokud <xref:System.Windows.Controls.TreeViewItem> a není viditelná nebo <xref:System.Windows.Controls.TreeView> částečně viditelná, posune ji tak, aby byla viditelná.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>Výběr položky TreeView  
 Když uživatel klepne <xref:System.Windows.Controls.TreeViewItem> na ovládací prvek <xref:System.Windows.Controls.TreeViewItem.Selected> a vybere jej, dojde k události a její <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> vlastnost je nastavena na . `true` Také <xref:System.Windows.Controls.TreeViewItem> se <xref:System.Windows.Controls.TreeView.SelectedItem%2A> stane <xref:System.Windows.Controls.TreeView> ovládacího prvku. Naopak při změně výběru <xref:System.Windows.Controls.TreeViewItem> z ovládacího prvku, <xref:System.Windows.Controls.TreeViewItem.Unselected> <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> jeho událost `false`nastane a jeho vlastnost je nastavena na .  
  
 Vlastnost <xref:System.Windows.Controls.TreeView.SelectedItem%2A> na <xref:System.Windows.Controls.TreeView> ovládací prvek je vlastnost jen pro čtení; proto jej nelze explicitně nastavit. Vlastnost <xref:System.Windows.Controls.TreeView.SelectedItem%2A> je nastavena, pokud uživatel <xref:System.Windows.Controls.TreeViewItem> klepne <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> na ovládací `true` prvek <xref:System.Windows.Controls.TreeViewItem> nebo když je vlastnost nastavena na ovládací prvek.  
  
 Pomocí <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti můžete <xref:System.Windows.Controls.TreeView.SelectedValue%2A> zadat <xref:System.Windows.Controls.TreeView.SelectedItem%2A>a . Další informace naleznete v [tématech Použití funkce SelectedValue, SelectedValuePath a SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Můžete zaregistrovat obslužnou rutinu události <xref:System.Windows.Controls.TreeView.SelectedItemChanged> <xref:System.Windows.Controls.TreeViewItem> na událost, aby bylo možné určit, kdy se změní vybrané. Který <xref:System.Windows.RoutedPropertyChangedEventArgs%601> je k dispozici obslužné rutiny události určuje <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, což je předchozí výběr a , což je aktuální výběr. Buď hodnota `null` může být, pokud aplikace nebo uživatel neprovedl předchozí nebo aktuální výběr.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Styl TreeView  
 Výchozí styl ovládacího <xref:System.Windows.Controls.TreeView> prvku umístí <xref:System.Windows.Controls.StackPanel> uvnitř objektu, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládací prvek. Pokud nastavíte <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti <xref:System.Windows.Controls.TreeView> <xref:System.Windows.FrameworkElement.Width%2A> a , tyto hodnoty <xref:System.Windows.Controls.StackPanel> se používají <xref:System.Windows.Controls.TreeView>k velikosti objektu, který zobrazuje . Pokud je obsah, který se má <xref:System.Windows.Controls.ScrollViewer> zobrazit, větší než oblast zobrazení, zobrazí se automaticky, aby uživatel mohl <xref:System.Windows.Controls.TreeView> obsah procházet.  
  
 Chcete-li přizpůsobit <xref:System.Windows.Controls.TreeViewItem> vzhled ovládacího <xref:System.Windows.FrameworkElement.Style%2A> prvku, <xref:System.Windows.Style>nastavte vlastnost na vlastní .  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A> nastavit hodnoty <xref:System.Windows.Controls.TreeViewItem> vlastností a <xref:System.Windows.FrameworkElement.Style%2A>ovládacího prvku pomocí .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Přidání obrázků a dalšího obsahu do položek zobrazení stromu  
 Do obsahu souboru <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem>můžete zahrnout více než jeden objekt. Chcete-li do <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> obsahu zahrnout více objektů, uzavřete <xref:System.Windows.Controls.Panel> objekty do ovládacího prvku rozložení, například nebo <xref:System.Windows.Controls.StackPanel>.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> definovat <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBlock> a a, které <xref:System.Windows.Controls.DockPanel> jsou oba uzavřeny v ovládacím prvku.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.DataTemplate> definovat, <xref:System.Windows.Controls.Image> který <xref:System.Windows.Controls.TextBlock> obsahuje a a, které jsou uzavřeny v ovládacím <xref:System.Windows.Controls.DockPanel> prvku. Můžete použít <xref:System.Windows.DataTemplate> k nastavení <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> nebo <xref:System.Windows.Controls.TreeViewItem>pro .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Témata s postupy](treeview-how-to-topics.md)
- [Model obsahu WPF](wpf-content-model.md)
